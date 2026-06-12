---
title: "Encrypt a file in nautails"
date: 2009-11-03
forum: Security
---

### Post by zenkaon on 2009-11-03
Hello,

In Jaunty, when I wanted to encrypt a file in nautails I would right click on it and select encrypt.

This seems to be gone in karmic, am I missing something? Does anyone know where this has gone and how I get it back?

I have my personal key loaded into seahorse.

---

### Post by tubbygweilo on 2009-11-03
Zenkaon, 
Although not a fix but someone with the [same]("http://ubuntuforums.org/showthread.php?t=1291980&highlight=encrypt+nautilus") [problem]("http://ubuntuforums.org/showthread.php?t=1299564&highlight=encrypt+nautilus") plus a few suggestions.

PS. Launchpad has a few entries relating to your problem [#390744]("https://bugs.launchpad.net/ubuntu/+source/seahorse-plugins/+bug/390744") + [#393645]("https://bugs.launchpad.net/seahorse-plugins/+bug/393645") and a few more.

---

### Post by mt1234 on 2009-11-06
Thanks for posting those links. I looked through the entries on LaunchPad and found that seahorse-plugins is not installed by default. 

So, the solution is open Synaptic Package Manager, find, then install the seahorse-plugin.

I had to reboot. Then "encrypt" and "sign" are options in Nautilus. ...very cool feature.

---

### Post by tubbygweilo on 2009-11-07
Glad I have been of help to you. May I suggest you take a look at [Truecrypt.org]("http://www.truecrypt.org/docs/") as another means of securing your data? Truecrypt is a product that many forum readers support and use as do I.

---

### Post by Locke_99GS on 2009-12-06
I hadn't even realised seahorse-plugins wasn't installed by default anymore, until I tried to use it today. 

Search win's again.

edit: I had to restart X for the entry to be added to nautilus.

---

