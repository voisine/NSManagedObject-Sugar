NSManagedObject-Utils
=====================

NSManagedObject category providing a cleaner, simpler way to use CoreData.

Example:

    #import "NSManagedObject+Utils.h"

    ...

        // create a new instance of a core data entity
        MyEntity *entity = [MyEntity managedObject];

        // fetch all stored instances of an entity
        NSArray *a = [MyEntity allObjects];
    
        // fetch instances matching a predicate query
        a = [MyEntity objectsMatching:@"attribute == %@", @"value"];
    
        // fetch all instances, sorted by attribute
        a = [MyEntity objectsSortedBy:@"attribute" ascending:YES];
    
        // fetch instances using a custom fetch request
        NSFetchRequest *req = [MyEntity fetchRequest];
    
        req.predicate = [NSPredicate predicateWithFormat:@"attribute != %@", @"value"];
        req.sortDescriptors = @[[NSSortDescriptor sortDescriptorWithKey:@"attribute" ascending:YES]];
        a = [MyEntity fetchObjects:req];
        
        // count how many stored instances of an entity exist
        NSUInteger count = [MyEntity countAllObjects];
        
        // count how many instances match a predicate query
        count = [MyEntity countObjectsMatching:@"attribute == %@", @"value"];

        // thread safe valueForKey:
        id value = entity[@"attribute"];

        // thread safe setValue:forKey:
        entity[@"attribute"] = value;        

        // delete an instance of an entity
        [entity deleteObject];
        
        // persist changes (this happens automatically when the app terminates)
        [NSManagedObject saveContext];
        
    ...
    
