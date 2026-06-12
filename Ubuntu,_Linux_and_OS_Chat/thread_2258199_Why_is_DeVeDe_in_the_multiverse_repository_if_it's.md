---
title: "Why is DeVeDe in the multiverse repository if it's free and open source?"
date: 2014-12-25
forum: Ubuntu, Linux and OS Chat
---

### Post by GigabyteProduction on 2014-12-25
I keep my multiverse source disabled to prevent myself from accidentally installing software that isn't open source for security reasons, but DeVeDe appears to be under GPL3 license. I understand I can just install from the deb files or something, but I want to know if there's a reason it's not in the universe repository. Is it dependent on something that isn't open source?

---

### Post by grahammechanical on 2014-12-25
The Multiverse repository is for software that is restricted by copyright and legal issues. I am quoting from here.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

The main code base of this software might well be released under an open source licence but it may pull in codecs that are not free and open source and may cause legal issues in some countries. Also, software in Multiverse is not supported by Ubuntu developers.

> 
[LIST]
[*=left]Select other repositories to gain access to proprietary drivers, copyrighted material, source code, etc.[FONT=inherit][/FONT]
[LIST]
[*=left]"Community-maintained Open Source software - (universe)"[FONT=inherit][/FONT]
[*=left]"Proprietary drivers for devices (restricted)" - Commonly used software which is not available under a completely free license. This software is supported by the Ubuntu team.[FONT=inherit][/FONT]
[*=left]"Software restricted by copyright or legal issues (multiverse)" - Software that is "not free" and may require licensing. This software is not supported.
[/LIST]
[/LIST]


Regards.

---

