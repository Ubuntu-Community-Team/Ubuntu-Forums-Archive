---
title: "recovery mode question"
date: 2010-01-09
forum: Security
---

### Post by Mickser_52 on 2010-01-09
I have recently had to use recovery mode because of a problem rebooting ubuntu (which has now been solved.)

In the recovery mode you have various options e.g. rebooting as normal or entering at root level.

My question is this: When I try to update, upgrade, load a package with synaptic manager and various other activities I have to supply my password or other activities using terminal use sudo requires entering a password. Why is it then that anyone can boot into root level in recovery mode without being asked for a password? and carry out many of the previously mentioned acivities.

---

### Post by adam814 on 2010-01-09
Physical access = root access.

If you're in a situation where you're worried about users doing this set a bootloader password.  I haven't done this myself, but I found this guide for doing it: [http://ubuntuguide.net/how-to-setup-boot-password-for-grub2-entries](http://ubuntuguide.net/how-to-setup-boot-password-for-grub2-entries)

There's probably a way around it, but it's better than nothing.  You can also edit /etc/default/grub to disable the recovery listings, but users could do that much and worse from a GRUB command line anyway.

---

### Post by cariboo on 2010-01-10
If someone knows what they are doing, removing the recovery mode menu selection doesn't help one bit to secure your system as adam814 said, physical access=root access. All you need is a Live CD and you have access to everything. 

The only way to protect your data is to encrypt it.

---

### Post by Mickser_52 on 2010-01-10
Thanks for your replies and explanations. I am still left wondering why have to enter passwords on so many occasions when it is so easy for someone to get around it?

---

### Post by iponeverything on 2010-01-10
> **Mickser_52 said:**
> Thanks for your replies and explanations. I am still left wondering why have to enter passwords on so many occasions when it is so easy for someone to get around it?

I think you are still missing the point. If someone does not have physical access to your machine, they can not boot into recovery mode. 

It is not easy for someone to get around it. They need physical access to the machine. It might be easy depending on whether or not you lock your doors and the proximity of the the person to your house, but generally speaking, it is not easy breaking into someone's house just so that they can boot your pc into recovery mode...

---

### Post by BkkBonanza on 2010-01-10
The reason that no special protections are put on recovery mode is that it would be useless to do so. Anyone who has physical access can also mount your drive as a seond drive on another system, or boot off a cdrom/usb stick and achieve the same result. 

That's to say that without encryption a hard is just a hard disk... you can always mount it on another system and get at the data regardless of having permissions during boot. ie. there's no real protection offered by requiring a password during boot.

A bios password helps a bit but by reseting the cmos memory it can be bypassed too.

If you want to be sure that your data is safe when someone steals your system the closest thing is either full drive encryption, or more coveniently, an encrypted home. Ubuntu now offers encrypted home as an install option, which works well, or you can convert your home to encrypted afterwards.

---

### Post by Mickser_52 on 2010-01-10
I may be missing the point or maybe not explaining my point clearly enough. 

When, for example, I want to update/upgrade I can do so either using update manager or the terminal, in each case I am asked for my password. Supposedly this is to prevent an unauthorised person **with access to my machine** from performing this task or possibly something more serious. In this situation they could get around this by booting into recovery mode.

I suppose my question should be why have this password protection at all?
Is it to protect against someone remotely accessing the computer possibly?

---

### Post by adam814 on 2010-01-10
In theory you could ssh into the machine remotely.  You could also run an X session over the network on another machine or run some kind of remote desktop software (VNC, NX, RDP) and be at that same terminal or menu option.

It would be a weird setup where someone could remotely access your machine and choose boot options.

Also sudo goes beyond just password-protecting potentially dangerous commands, it also logs relevant info to var/log/auth.log.  Usually it's the date/time, username, tty, current directory, who command was run as (usually root), and the actual command that was run.  There's accountability built-in (unless they remove the log file I suppose).

It's also configurable to grant different groups/users permission to run only the commands they need.

---

### Post by Mickser_52 on 2010-01-10
Thanks adam814 for your explanation. In the case of home use, with little or no sensitive data or risk of unauthorised access, having to enter a password for apparently simple tasks can be a minor irritation at times.

---

### Post by adam814 on 2010-01-10
Ah, I see where this is going.  On my home computer I set up sudo to not require a password for users in group sudo, then added my user to the group.  Now I only enter my password on login.

It was just a matter of un-commenting one line in /etc/sudoers.  Be sure to use "sudo visudo" to edit it though.  Then "adduser <your user> sudo" should do the trick.

---

### Post by Mickser_52 on 2010-01-10
Thanks again adam814 looks like you guessed one of my next questions. That is working and presumably updates the logs etc. that you mentioned before. 

In relation to my original question I have learned that it is almost impossible to prevent access to a computer as password protection can easily be got around. To quote a wise man;) physical access = root access. 
Looking for passwords to perform certain tasks is more relevant in a network situation with multiple users involved or where a computer may be accessed remotely. So with help from you and others my question has been answered.

---

### Post by cariboo on 2010-01-10
> **Mickser_52 said:**
> I may be missing the point or maybe not explaining my point clearly enough. 

When, for example, I want to update/upgrade I can do so either using update manager or the terminal, in each case I am asked for my password. Supposedly this is to prevent an unauthorised person **with access to my machine** from performing this task or possibly something more serious. In this situation they could get around this by booting into recovery mode.

I suppose my question should be why have this password protection at all?
Is it to protect against someone remotely accessing the computer possibly?

You are missing the point, when you are asked for a password to do an uppdate or install a program, it is because your user does not have permission to write to any directories, but your home directory. 

Linux was designed from the start to be a multiuser system, if you have several people logged in at the same time, it wouldn't be a good idea to let them change the file system, or look at the files in your home directory.

The first thing I do when setting up a system, is change the permissions of home directories to 700, so that only the owner of that directory can access it. The Ubuntu default is to set the permissions to 755, so every one can access each others home directories

---

