---
title: "ActiveDirectory compared to NFS/NIS"
date: 2009-08-23
forum: Server Platforms
---

### Post by skullmunky on 2009-08-23
We've been using NFS/NIS for a long time and have been pretty happy with it.  This year for the first time ever we have this radical experimental new operating system in our organization called "windows xp" or something, so we're trying to see about getting the same functionality that we have for the linux machines.  An ideal scenario would actually be a triple-OS heterogeneous environment, where Linux, OSX, and Windows clients could all authenticate against the same controller and serve profiles and the same user directory for each.  

Is Active Directory a good choice?  Do I have to have a windows server to run it?  Will it be a regression for the linux clients?  Can NFS/NIS work on OSX and Windows?  

thanks,

skullmunky, the reluctant admin

---

### Post by windependence on 2009-08-23
This is going to be largely a matter of opinion. Since I am running all three of these OSs, I'll give you mine.

Although people will argue that AD is more full featured than the Unux/Linux solutions, and in some ways they are right, I would never run my SERVER stuff on Windows in a mixed environment. The main thing that makes me say that is Security and stability, neither of which Windoze is particularly known for. If you want to run AD, YES, you need Windoze since it is their product and it only runs there. It also costs lots of money to run all that Mickey$oft stuff.

NFS and NIS will work fine with Mac OSX. I don't know about Windoze, but I doubt it. There are of course other protocols like SAMBA that would work with all three OS choices but may not be the fastest solution. You could always run a combination of protocols to integrate everything.

-Tim

---

### Post by scorp123 on 2009-08-23
> **skullmunky said:**
>  An ideal scenario would actually be a triple-OS heterogeneous environment, where Linux, OSX, and Windows clients could all authenticate against the same controller and serve profiles and the same user directory for each.   We use Novell SLES 11 for that. Works tip top and it's extremely easy to setup. Linux users see their home directories as NFS mount points, SAMBA users see the same directories as SMB mounts, exchanging data between the Linux and Windows sessions is just a matter of opening the same folder icon.

But if you prefer to avoid Novell ... well, here are instructions to replicate all the functionality on Ubuntu. But be warned, it's quite a lot of work. But it does work and will do what you want: Windows machines see the server as "Domain Controller", Linux machines see the server as LDAP directory, and both Windows and Linux happily authenticate against it ...

[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

The author also posted the same instructions into the forum:
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

Even though these instructions were originally written with Ubuntu 7.10 in mind according to the messages in the thread it more or less all still works with newer Ubuntu releases too (a few config files might now be in a sub-directory with a slightly different name); the few differences (if you even run into them) are apparently not hard to figure out.

---

### Post by castrojo on 2009-08-23
You can have your Windows AD controller serve out NFS and NIS to your Linux and OSX clients. It's built into 2k3 server R2 and newer, if you have an older windows server you want to make sure that "Services for UNIX" is installed.

EDIT: Though, you should take this opportunity to just have the Linux machines auth against the domain controller via winbind and get rid of NIS or do LDAP/Kerberos or something.

---

### Post by HermanAB on 2009-08-23
Note that instead of Win2003 ADS, you could the Win2000 ADS clone made by the Samba project.  It is not as featureful as Win2003 ADS, but you likely don't need the newer features.

---

