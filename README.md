Artsy Mogenerator Template
================

Based on Tony Arnold's template, which will be based on Wolf Rensch's template.

This is an extremely minimalized template, as the template files are reduced in readability but the machine generated files are enhanced in readabilty. It's a trade-off that I think is fair as I don't have to maintain the official templates and I will be seeing the generated files a lot more often than the templates. This makes it very hard to read the actual templates themselves.

The results look like this:

```
// DO NOT EDIT. This file is machine-generated and constantly overwritten.
// Make changes to Document.h instead.

#import <CoreData/CoreData.h>
#import "ARManagedObject.h"

extern const struct DocumentAttributes {
	__unsafe_unretained NSString *filename;
	__unsafe_unretained NSString *hasFile;
	__unsafe_unretained NSString *humanReadableSize;
	__unsafe_unretained NSString *size;
	__unsafe_unretained NSString *slug;
	__unsafe_unretained NSString *url;
	__unsafe_unretained NSString *version;
} DocumentAttributes;

extern const struct DocumentRelationships {
	__unsafe_unretained NSString *album;
	__unsafe_unretained NSString *artist;
	__unsafe_unretained NSString *show;
} DocumentRelationships;

extern const struct DocumentUserInfo {
} DocumentUserInfo;

@class Album;
@class Artist;
@class Show;

@interface DocumentID : ARManagedObjectID {}
@end

@interface _Document : ARManagedObject {}
+ (id)insertInManagedObjectContext:(NSManagedObjectContext *)moc_;
+ (NSString *)entityName;
+ (NSEntityDescription *)entityInManagedObjectContext:(NSManagedObjectContext *)moc_;
- (DocumentID *)objectID;

@property (nonatomic, strong) NSString* filename;
@property (nonatomic, strong) NSNumber* hasFile;
@property (nonatomic, strong) NSString* humanReadableSize;
@property (nonatomic, strong) NSNumber* size;
@property (nonatomic, strong) NSString* slug;
@property (nonatomic, strong) NSString* url;
@property (nonatomic, strong) NSNumber* version;
@property (nonatomic, strong) Album  *album;
@property (nonatomic, strong) Artist  *artist;
@property (nonatomic, strong) Show  *show;


@end



@interface _Document (CoreDataGeneratedPrimitiveAccessors)

- (Album  *)primitiveAlbum;
- (void)setPrimitiveAlbum:(Album *)value;

- (Artist  *)primitiveArtist;
- (void)setPrimitiveArtist:(Artist *)value;

- (Show  *)primitiveShow;
- (void)setPrimitiveShow:(Show *)value;

@end
```

I use this in a Makefile, with a command like this:

```
mogenerate:
	@printf 'What is the new Core Data version? '; \
		read CORE_DATA_VERSION; \
		mogenerator -m "Resources/CoreData/ArtsyPartner.xcdatamodeld/ArtsyFolio v$$CORE_DATA_VERSION.xcdatamodel/" --base-class ARManagedObject --template-path config/mogenerator/artsy --machine-dir Classes/Models/Generated/ --human-dir /tmp/ --template-var arc=true
```

( you might not want the `--human-dir /tmp/` but I'm providing the real thing. )
