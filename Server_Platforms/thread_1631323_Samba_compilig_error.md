---
title: "Samba compilig error:"
date: 2010-11-26
forum: Server Platforms
---

### Post by leonardo07746 on 2010-11-26
this is my output when I try to compile samba 4.0.0 alpha 7 in Ubuntu using the spec file provided in the samba packages:

bin/mergedobj/samba-util.o: In function `file_lines_parse':
(.text+0x595c): undefined reference to `_talloc_steal'
bin/mergedobj/samba-util.o: In function `data_blob_talloc_named':
(.text+0x5ee7): undefined reference to `_talloc_steal'
bin/mergedobj/samba-util.o: In function `data_blob_talloc_reference':
(.text+0x5f3b): undefined reference to `_talloc_reference'
bin/mergedobj/samba-util.o: In function `data_blob_free':
(.text+0x6012): undefined reference to `talloc_free'
bin/mergedobj/samba-util.o: In function `directory_create_or_exist':
(.text+0x65e7): undefined reference to `talloc_free'
bin/mergedobj/samba-util.o: In function `directory_create_or_exist':
(.text+0x6664): undefined reference to `talloc_free'
bin/mergedobj/samba-util.o: In function `directory_create_or_exist':
(.text+0x66dd): undefined reference to `talloc_free'
bin/mergedobj/samba-util.o: In function `directory_create_or_exist':
(.text+0x675c): undefined reference to `talloc_free'
bin/mergedobj/samba-util.o:(.text+0x68ff): more undefined references to `talloc_free' follow
[B]collect2: ld returned 1 exit status
make: *** [bin/regpatch] Error 1

[/B]any tip?

---

### Post by windependence on 2010-11-26
[https://bugzilla.samba.org/show_bug.cgi?id=6269](https://bugzilla.samba.org/show_bug.cgi?id=6269)
 
[https://bugzilla.samba.org/show_bug.cgi?id=6270](https://bugzilla.samba.org/show_bug.cgi?id=6270)
 
Bug reports are filed at the above links with fixes.
 
Why are you compiling SAMBA? Is there a feature in the alpha release you need or are you just one of those people who thinks they need the latest and greatest of everything? Newest is not always best, in fact most times it's not in Linux/Unix.
 
-Tim

---

