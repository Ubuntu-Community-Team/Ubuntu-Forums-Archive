---
title: "Disabled my login password - bad idea?"
date: 2010-10-16
forum: Security
---

### Post by listerdl on 2010-10-16
Hi I just have a simple BIOS password when I boot into my machine.

Should I also have the standard login passowrd as well?

In other words, what benefit does the login at the boot up, (after BIOS) really give and would you recommend a good or better security process?

THANKS!

---

### Post by shibbe on 2010-10-16
BIOS  password = entered right after powering your server on?
wouldnt use that if other people have physical access to your server, because removing the motherboards battery resets all bios settings and removes the password protection. 

sorry if i'm getting you wrong

---

### Post by Rocket2DMn on 2010-10-16
Good security is achieved in layers, just having one piece of security is not an effective way to keep out the bad guys. Having a BIOS password means that you have to type in a password before the machine will even boot, but once it is up and running, anybody can access the system without needing a login password since you disabled it.

Having a BIOS password is really only needed if you are worried about somebody accessing the system and booting up from a secondary device like a LiveCD, flash disk, or root console. Having a login password prevents others from logging in to your system while it is up and running. You normally want a login password, and you want the screen to lock when it is idle so if you walk away, somebody else can't use the system while you're not there.

What is the environment that your computer exists in? Home? Work? Do you have roommates, family members, or friends that you don't want accessing the computer without your permission?

---

