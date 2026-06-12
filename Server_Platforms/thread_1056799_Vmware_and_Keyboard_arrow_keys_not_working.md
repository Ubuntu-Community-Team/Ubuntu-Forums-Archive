---
title: "Vmware and Keyboard arrow keys not working"
date: 2009-02-01
forum: Server Platforms
---

### Post by yurtboy on 2009-02-01
I know there are a number of Closed threads that mention how to fix this. And maybe I missed the obvious. But to save others some time.
1. All the threads say to edit /etc/vmware/config
2. And some do say to edit ~/.vmare/config

#2 is in your home folder.

#1 is what I did and it did not work. I see now why it did not work, which was obvious, the /etc/vmware/config was on the server and I think some of these threads where people using vmware on their desktop. ???

So #2 worked right away by

1. nano .vmware/config
It may not exist
2. xkeymap.nokeycodeMap = true

And start up the vmware machine and it all should work.

Good luck,

---

### Post by bizna on 2009-09-10
This is indeed the proper solution.

Too bad that there are so many hacks and workarounds that need to be done, in order to get VMWare work properly on Ubuntu.

Thank you for the helpful post!

Dotan

---

### Post by Al Ricco on 2009-10-20
True you did save me some time : this works perfectly and patch location is definitively the most correct one. Thanks !

By the way I guess this setting should be reported in Community documentation under a troubleshooting section.

---

### Post by Adizere on 2010-10-20
This topic is kinda old.

Was ~/.vmware/config replaced by ~/.vmware/preferences ?

I edited both the preferences file and the /etc/vmware/config
file, restarted the machine but still no effect.

Anyhow, when I start the machine the following hint pops-up:

> A language-specific mapping from X keysyms to machine scancodes will be used, based on the detected keyboard type of "us101". However, this program's language-specific mapping may not be correct for your keyboard in all the details, because X keyboard mappings vary.
You can override specific key mappings in the virtual-machine configuration.
For more information, please see VMware Player documentation available on our Web site at "http://vmware.com/info?id=10".

Any ideeas?

---

