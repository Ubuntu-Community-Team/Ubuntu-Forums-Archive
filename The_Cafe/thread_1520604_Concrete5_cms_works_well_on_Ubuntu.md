---
title: "Concrete5 cms works well on Ubuntu"
date: 2010-06-29
forum: The Cafe
---

### Post by kapi on 2010-06-29
Just letting you know that I'm testing the cms Concrete5 on Karmic and its fine, no not fine but great.

Wanted to share the little gem to all other linux users.

Hope it helps

---

### Post by Timmer1240 on 2010-06-30
Thats great Open source is a good choice and if it works good then use and enjoy have fun with it and ubuntu too!"free is the key"

---

### Post by fredbird67 on 2010-07-10
Doesn't work for me -- I got the following errors:

```
Strict Standards: Non-static method Loader::database() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php  on line 23

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 139

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 140

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 141

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 142

Strict Standards: Declaration of dbTable::create() should be compatible with that of dbObject::create() in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/3rdparty/adodb/adodb-xmlschema03.inc.php on line 642

Strict Standards: Declaration of dbIndex::create() should be compatible with that of dbObject::create() in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/3rdparty/adodb/adodb-xmlschema03.inc.php on line 806

Strict Standards: Declaration of dbData::create() should be compatible with that of dbObject::create() in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/3rdparty/adodb/adodb-xmlschema03.inc.php on line 1051

Strict Standards: Declaration of dbQuerySet::create() should be compatible with that of dbObject::create() in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/3rdparty/adodb/adodb-xmlschema03.inc.php on line 1302

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 143

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 26

Strict Standards: Non-static method Cache::startup() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 27

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/cache.php on line 58

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 30

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 31

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 32

Strict Standards: Non-static method Localization::init() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 25

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 5

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 33

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 34

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 35

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 36

Strict Standards: Declaration of DatabaseItemList::sortBy() should be compatible with that of ItemList::sortBy() in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/item_list.php on line 8

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 37

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 38

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 39

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 40

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 41

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 42

Strict Standards: Declaration of BlockController::setupAndRun() should be compatible with that of Controller::setupAndRun() in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/block_controller.php on line 317

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 43

Strict Standards: Declaration of AttributeTypeView::action() should be compatible with that of View::action() in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/attribute/view.php on line 124

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 44

Strict Standards: Declaration of AttributeTypeController::setupAndRun() should be compatible with that of Controller::setupAndRun() in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/attribute/controller.php on line 168

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 52

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 53

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 54

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 55

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 56

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 57

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Declaration of PendingAttributeType::getList() should be compatible with that of AttributeType::getList() in /opt/lampp/htdocs/cbc-concrete5/concrete/models/attribute/type.php on line 242

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 58

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 59

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 60

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/models/file.php on line 3

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 61

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 62

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 63

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 64

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 65

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 66

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 67

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 68

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 69

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Declaration of Page::add() should be compatible with that of Collection::add() in /opt/lampp/htdocs/cbc-concrete5/concrete/models/page.php on line 2010

Strict Standards: Declaration of Page::duplicate() should be compatible with that of Collection::duplicate() in /opt/lampp/htdocs/cbc-concrete5/concrete/models/page.php on line 2010

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 70

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 71

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 72

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 73

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method Loader::model() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/dispatcher.php on line 74

Strict Standards: Non-static method Loader::legacyModel() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 44

Strict Standards: Non-static method View::getInstance() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/config/theme_paths.php on line 4

Warning: session_start() [function.session-start]: Cannot send session cookie - headers already sent by (output started at /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php:11) in /opt/lampp/htdocs/cbc-concrete5/concrete/startup/session.php on line 18

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php:11) in /opt/lampp/htdocs/cbc-concrete5/concrete/startup/session.php on line 18

Strict Standards: Non-static method FileTypeList::getInstance() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/config/file_types.php on line 15

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method Localization::getTranslate() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 28

Strict Standards: Non-static method Loader::library() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 10

Strict Standards: Non-static method Cache::getLibrary() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php on line 11

Strict Standards: Non-static method View::getInstance() should not be called statically in /opt/lampp/htdocs/cbc-concrete5/concrete/startup/config_check_complete.php on line 6

Strict Standards: Non-static method Loader::controller() should not be called statically, assuming $this from incompatible context in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/view.php on line 599

Strict Standards: Non-static method Loader::db() should not be called statically, assuming $this from incompatible context in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/loader.php on line 326

Warning: Cannot modify header information - headers already sent by (output started at /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/localization.php:11) in /opt/lampp/htdocs/cbc-concrete5/concrete/libraries/view.php on line 758
```

At least I got the "Install Concrete" dialogs after all that mess...

---

### Post by sandyd on 2010-07-11
> **fredbird67 said:**
> Doesn't work for me -- I got the following errors:



At least I got the "Install Concrete" dialogs after all that mess...

turn off your php warning settings you little bugger ;)

---

### Post by fredbird67 on 2010-07-11
I tried that -- didn't work.

I'm using XAMPP and tried turning off all the "display_errors" entries -- no go, at least not yet...

---

### Post by sandyd on 2010-07-11
> **fredbird67 said:**
> I tried that -- didn't work.

I'm using XAMPP and tried turning off all the "display_errors" entries -- no go, at least not yet...

change error_reporting to "E_ALL & ~E_NOTICE"

because a lot of people simply don't follow coding standards, the "E_STRICT" is generally disabled, don't know why it was enabled in the first place.

---

### Post by fredbird67 on 2010-07-12
Carlee, I tried something different entirely.  I got rid of XAMPP and decided to try the Apache, PHP, and MySQL (don't remember the exact names of all the packages involved) packages in the repositories.  I've copied Concrete5's files from my desktop into the /var/www/cbc-concrete5/ directory ("CBC" standing for Castlewood Baptist Church, plus I'm putting in the name of the CMS, as I've been trying out several), and I'm happy to say that I'm now getting the installation page with no other errors! There is, of course, that red X beside the entry for making certain directories writable by the web server, but that's easily fixed. :-)

I may very well have to give this a whirl tonight after I get home from work.  I gotta fix breakfast, shower, get dressed and go to work for now, but I'll definitely be trying this out tonight. :-)

---

### Post by Ricalsin on 2011-03-21
Yes, for those of you who do not know, Concrete5 is an amazing CMS.  It looks very simple and in fact is simple to use for people who do not want to get heavily into the code.  Without much trouble, you can load up a capable website with permissions, file uploading, front-end editing capability and LOT more.  

If you are into more advanced coding then you've just met your match for many years.  The system requires some getting used to from a core perspective.  You've got to have your mind around Object Oriented Programming (initialize, instantiate, instance) and the class structure (public, private, protected).  It uses a HIGHLY customizable methodology that facilitates a LOT of control over what you can produce and how addons are easily built for it.  It's loosely built on the MVC approach - loosely in that it does it in a way that is beyond what you would read in any book to date.  (There is a guy in Germany who is about to have a book published on it: Remo Laubacher.)  But, keep in mind, it's not easy to conceptually get the core code structure at first.  However, once you do, you'll see that this system was designed for and by coders.  It was conceived KNOWING that coders would be coming to hack it up in order to make it do what they want it to do.  (Keep in mind, this is well beneath the "easy-happy" stuff that most developers would use to build a website.)  

It has lacked some great documentation but that has improved a lot of late.  Now that I know it, I can understand why.  The only way to REALLY understand this system through-and-through is to READ the code.  By the time someone wrote it all for you in English to read you would - most likely - be lost if you didn't understand code on a deep level.  That said, the concrete5.org website is actively maintained and has a great spirit of help.  There are now some significant addons in the marketplace.  Yes, the core code is free and so too are many of the addons.  A great site can be built for free.  But the web is complicated now and there requires a lot of commitment for people to spend the time to develop the many addons that are required to solve a myraid of options.  To me, what they sell for is clearly worth the price.  Plus, C5 doesn't allow just any hacked up code to make it to their marketplace.  It's tested and known to not have interference with other code before released.  Most importantly, the addons and the system works so that everything can be manipulated IF you know what's going on under the hood.  

Personally, I know that when I get into a significant code base (CMS) it's going to take my time to learn it.  So I was looking for a system that I didn't max out shortly after I learned it.  I was willing to invest my time so I was looking for a signifcant return on that investment.  I am very happy with my choice to go with C5.

I am not a member of the core team, have no addons in the marketplace and do not get compensated in any way from C5.  This review is purely from experience and use.

Rick :: aka(Ricalsin, c5, member)

---

