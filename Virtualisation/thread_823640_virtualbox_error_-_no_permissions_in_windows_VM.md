---
title: "virtualbox error - no permissions in windows VM"
date: 2008-06-09
forum: Virtualisation
---

### Post by KingTermite on 2008-06-09
OK, I installed Virtualbox yesterday. I didn't have any issues...installation went fine. I added myself and "root" to the Vboxusers (or whatever name is) group.

I boot up my windows xp in Virtualbox and notice I don't have any sound. So I think, OK...probably drivers. So I have a CD with my windows xp drivers. I try to install the drivers.

Everything I tried to install either ended immediately or I saw some errors with something about not having permission.

I'm using the only account created during installation "Administrator" with admin rights. 

Why am I having issues about installing software? Any ideas?

---

### Post by Ameneon on 2008-06-10
To get sound you have to enable the option for that virtual machine, don't recall what the exact setting is as I'm at work now but I do not believe it requires any driver at all. As far as the permissions issue goes, there's another setting that lets you access the cd drive directly but again, don't recall which setting this is specifically.

---

### Post by KingTermite on 2008-06-10
> **Ameneon said:**
> To get sound you have to enable the option for that virtual machine, don't recall what the exact setting is as I'm at work now but I do not believe it requires any driver at all. As far as the permissions issue goes, there's another setting that lets you access the cd drive directly but again, don't recall which setting this is specifically.

OK Thanks. I had already found the setting to enable sound (last night), but then when it went in to Windows it still gave some error about the sound drive being incorrect or something like that.

I'll look for the other setting you mention and see if that will let me install the normal Windows sound drivers and solve the problem or not.

---

### Post by Naturofix on 2011-04-14
Hi I have similar issues with permission in virtualbox. I'm trying to install software that requires DOTNET.
I'm running Windows 7 in VirtualBox 3.2.8 in Ubuntu 10.4

When I try to install the program I get the following error

Privilege Violation: You must be logged in as administrator in order to install the product

There are only administrator users on this installation. 

How do I get around this problem?

---

