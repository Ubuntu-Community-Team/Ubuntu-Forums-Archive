---
title: "PeaZip 2.1 released"
date: 2008-05-20
forum: The Cafe
---

### Post by Giorgio tani on 2008-05-20
PeaZip 2.1, which I tested succesfully on 8.04 LTS Hardy Heron, was released yesterday.
Two the main updates: 

1) The main program's interface is now a general purpose file manager capable of browsing and searching in the filesystem as well as in archives.

2) It is now possible to use keyfiles for two factor authentication with all supported archive formats, enhancing security against dictionary and some forms of social engineering attacks. 
Keyfiles are hashed with SHA256 and the Base64-encoded (RFC 4648) hash is pre-pended to the password; this allows to not break compatibility with other applications supporting only passwords-based encryption since archives encrypted in that way can be opened simply calculating the hash and prepending it to the password. 

[http://peazip.sourceforge.net](http://peazip.sourceforge.net)

---

### Post by bone2006 on 2008-06-19
would be nice if this was in the repository.  I'm not sure if there's even anything that competes with it?

Even wikipeida knows what it's lacking LOL
[http://en.wikipedia.org/wiki/File_Roller](http://en.wikipedia.org/wiki/File_Roller)

# File Roller doesn't provide an interface for advanced configurations such as setting the compression level of a format type.
# File Roller doesn't support multi-volume archives for the 7z format (the ability to view or create archives divided into multiple files)

I don't think ark can split archives.......... so really not sure if there's an alternative gui with this capability.

---

