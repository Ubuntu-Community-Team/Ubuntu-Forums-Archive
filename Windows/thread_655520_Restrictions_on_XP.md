---
title: "Restrictions on XP"
date: 2008-01-01
forum: Windows
---

### Post by Ensamvarg on 2008-01-01
Hello all =]
I'm currently on my computer which I share with a number of other users, all family. 1 member simply loves to install programs, change settings, etc etc, and basically things that just don't need to be done. Are there any freeware programs out there that can help me restrict users from these type of things?
Thanks alot.

---

### Post by LaRoza on 2008-01-01
yes.

Make a new account for general use, with limited rights.

Never allow people to share accounts and keep rights limited to what is needed.

[http://sudowin.sourceforge.net/how.html](http://sudowin.sourceforge.net/how.html) sudo for Windows

---

### Post by Ensamvarg on 2008-01-01
I've changed the other users to be restricted users, but it says that it only restricts installing -some- programs, doesnt say anything about settings either. The ones i particularly want to restrict are for the monitor. One keeps changing the DPI to 120 instead of 96, requiring a reboot for every time I want to use the computer with a normal sized screen.

---

### Post by KOld Iron on 2008-01-01
If you really want to get into this you could use the local group policies. That pretty much allows you to tweak any setting for any user on that computer. However, this is a complex thing to do and may not be worth the effort. You have to read up on the details at the Microsoft website. Since I am using XP Pro, I am not sure, whether this would work with XP Home.
To get started type at the "Run ..." prompt:"mmc c:\windows\system32\gpedit.msc", but be careful, this is certainly dangerous administrative work, and you can really mess up your system, if you don't know what are you doing.

---

### Post by kerry_s on 2008-01-01
> **Ensamvarg said:**
> I've changed the other users to be restricted users, but it says that it only restricts installing -some- programs, doesnt say anything about settings either. The ones i particularly want to restrict are for the monitor. One keeps changing the DPI to 120 instead of 96, requiring a reboot for every time I want to use the computer with a normal sized screen.

that's ridicules, having to jump through hoops. you need to show them the proper way to change font size. see pic. 
demand they do it right or not at all.

---

### Post by amingv on 2008-01-01
gpedit.msc is not available for XP Home.

If your main concern is changed settings/installed software you might want to have a look at [Shadowuser](http://www.storagecraft.com/products/ShadowUser/) (but it's not free in either ways).

I only suggest this software to a certain extent, since it can effectively prevent you from using your computer.

...or maybe you and this user need to have "the talk". Does he need to make these changes to use the computer? Does he know alternatives? If they are things that shouldn't be done explain them to him. I'm sure he can develop respect for his family.
[SIZE="1"]Disclaimer: he in this context means 'he' xor 'she' :/[/SIZE]

---

### Post by Ensamvarg on 2008-01-07
To KoldIron - I am a newbie to command prompt, I have no idea what I am doing and don't want to be held responsible for killing the machine =P

To Kerry - Aye its my 10 year old brother that decides to be a pain in the ****. He does it to be awkward.

To Amingv - Yeah I've tried "the talk" several times. It just doesn't work. The people using the computer haven't got a clue how to use a computer without buggering it up for the other users.

Thanks!

---

### Post by got awesome? on 2008-01-07
Just change his account to a base "User" (not power user), he can use programs but can't install anything, or change system settings.

Right click on " My Computer", select "Manage", open the "Local Users" tree, and right click on his user name and select "Properties", and select the "Member Of" tab. Add the "user" group, and delete all other groups.

You can also modify group policy but this is a more advanced step and probably not needed, unless you want to carefully modify the restrictions (like allow him to install certain types of programs, or modify certain system settings, but not others). For a 10yr old who delights in being "awkward", I would just lock him out of the system completely with a base user account and let him play games, browse the net, etc... there's nothing worse than a tinkerer with admin rights who doesn't know what they're doing!

---

### Post by Ensamvarg on 2008-01-09
I think you hit the nail on the head their Awesome, thanks a bunch =]

---

### Post by Lord DarkPat on 2008-01-12
setup a pre-boot password(maybe ur BIOS doesn't support it) and he will need to ask you before switching it on. If he installs s'thing, ground him by not coming when he asks you to.

---

