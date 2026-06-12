---
title: "[SOLVED] how to install the latest dev version of firefox?"
date: 2007-07-09
forum: Ubuntuzilla
---

### Post by w9fyi on 2007-07-09
HOw does one install the latest dev version of firefox.  Is there a way to make ubuntuzilla do this?  I need this so that i can get orca to work.. Thanks.

---

### Post by nanotube on 2007-07-09
> **w9fyi said:**
> HOw does one install the latest dev version of firefox.  Is there a way to make ubuntuzilla do this?  I need this so that i can get orca to work.. Thanks.

well, you'd have to make some slight changes to the code in order for it to get gran paradiso alpha 6 (or any other dev version). 

easiest way would be to just hard-code the download url to whatever it is you want (e.g, for granparadiso alpha 6, to [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/granparadiso/alpha6/linux-i686/en-US/granparadiso-alpha6.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/granparadiso/alpha6/linux-i686/en-US/granparadiso-alpha6.tar.bz2)

then you'd have to modify the tar command to use bzip instead of gzip (so -j instead of -z option)

and probably some other places that will come out when you try running it and it errors out. :)

so, if i were you, i'd avoid all that and just follow the manual installation instructions, available here:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

