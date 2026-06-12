---
title: "win8.1 guest won't open with com1 enabled"
date: 2014-02-07
forum: Virtualisation
---

### Post by thane1 on 2014-02-07
I have an ubuntu (linux mint 16 64bit) host with virtualbox running xp and it starts up fine with an attached com1 port, which I need.  Today I purchased windows 8.1 64 bit as shortly I won't be able to get xp updates.  When I set the 8.1 guest to use the com1 port (with as far as I can tell) the same settings as in the xp guest, the 8.1 guest will not open.  If I disable the com1 in settings, the 8.1 guest will open fine.  Tried a number of times with the same result.  The error message on non-startup is, Failed to open a session for the virtual machine windows8.1.
Failed to open host device '/dev/ttys0' (VERR_FILE_NOT_FOUND). And the "details" are, 
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {8ab7c520-2442-4b66-8d74-4ff1e195d2b6}

Below are screenshots from vboxmanage and from the Settings page:

---

