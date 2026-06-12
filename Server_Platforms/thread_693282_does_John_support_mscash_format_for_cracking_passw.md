---
title: "does John support mscash format for cracking passwords?"
date: 2008-02-10
forum: Server Platforms
---

### Post by iansane on 2008-02-10
Hi, Not sure if this is the right forum. 

I'm a network security student assessing my schools security for an assignment. 

I want to dump the windows password cache from a local machine on the domain  and then use my system to try and crack the hashed passwords. I have permission to attempt this for password auditing purposes only.

I have installed John from synaptic and found a tutorial on installing patches for support of mscash hash type for an older version.

My question is, does the new version already support this type? I read the man pages and found that it supports LM and many other types. Is LM the hash type  that windows would use for hashing cashed passwords or do I still need to find a patch for this new version? The tutorial for the older one doesn't seem to work with the new version. 

Thanks

---

### Post by Dr Small on 2008-02-10
> John can
       use  a  dictionary or some search pattern as well as a password file to
       check for passwords. John supports different cracking modes and  under&#8208;
       stands  many  ciphertext  formats,  like  several DES variants, MD5 and
       blowfish. It can also be used to extract AFS and Windows NT  passwords.

Directly from the man page.

---

### Post by Rhubarb on 2008-02-10
I'm no security expert, but you might want to have a look at Ophcrack.
[http://ophcrack.sourceforge.net/](http://ophcrack.sourceforge.net/)

You can grab the live cd or the app to do it.

---

### Post by iansane on 2008-02-11
The tutorial for the older version says use the command, "-format:mscash" and that doesn't appear to be an option for "-format" according to the man page.

Well I guess I should work on getting the dumped file first and just see what this new version can do. Thanks a lot :-)

---

### Post by iansane on 2008-02-17
Found Cain and Abel live DVD

[http://www.dxdrive.com/cain/forums/](http://www.dxdrive.com/cain/forums/)

Have to register to download

It works without the need for dumping the file from the windows machine. I'll stick with it while I try to figure out "John"

---

