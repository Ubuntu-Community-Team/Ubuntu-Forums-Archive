---
title: "Install Mac OSX on VirtualBox?"
date: 2010-06-12
forum: Virtualisation
---

### Post by phr33k-dc on 2010-06-12
Hi, im just wondering if its possible to install a mac os on a virtualbox?

I know it just shouldnt be done because of verious EULA agreements etc, but i'd just like to know IF its possible. thanks

---

### Post by |I|I|I|I| on 2010-06-14
I know you can do it on VMWare Player so I'm assuming you can do it on VirtualBox as well. Have a search on Google lots of people have done it, if i remember correctly it's not a straight install though, there's a few extra steps to go through as officially they don't support OSX.

---

### Post by stmiller on 2010-06-15
It works fine with Virtualbox 3.2 and newer though you have to use any various hackintosh boot loaders.

[http://i.imgur.com/1xj8D.jpg](http://i.imgur.com/1xj8D.jpg)


Need:

- Empire EFI boot CD ( [http://prasys.co.cc/2010/01/empire-efi-v-1-085-is-out/](http://prasys.co.cc/2010/01/empire-efi-v-1-085-is-out/) )
- Retail OS X 10.6 DVD
- Coffee


Setup Virtualbox instance as OS X.

Change these things:

System: UNcheck Enable EFI

USB: UNcheck USB(!) 

Hard disk should be on IDE (ICH6)

----

Boot the Empire EFI CD, then it's like installing on a hackintosh as normal.


At the Empire CD boot screen, swap out the disc with a retail OS X DVD, and continue OS install as normal.

At the end of the install it will either say 'Installation FAILED' or kernel panic. This is normal. Shut it down, and reboot with the Empire CD. At the Empire boot screen, choose the hard disk to boot from, and continue to Mac desktop.

At the desktop, run the post-install utilities from the Empire Boot CD.

After reboot, shutdown and go back to CHECK USB on. Otherwise keyboard/mouse may not work.

---

