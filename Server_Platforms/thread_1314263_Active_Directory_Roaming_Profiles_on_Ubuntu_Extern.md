---
title: "Active Directory Roaming Profiles on Ubuntu External HD"
date: 2009-11-04
forum: Server Platforms
---

### Post by iTrascurato on 2009-11-04
Hey guys, 

I was wondering if anybody has any experience setting up an interesting organization of services like this..

I have a Ubuntu 9.10 desktop, with an external HD shared via Samba, with some users and folders on it.  I have another computer on the network running Winblows Server 03', handling Active Directory (that I am still setting up and testing before any serious implementation.)  

I've been testing GPOs I am building on an XP SP3 virtual machine that is running off my Ubuntu desktop as well, that I joined to the AD domain.

However, the Domain Controller doesn't have a very big hard drive, and I'd like to take advantage of having 930GB free on this external hard drive for roaming user profiles, especially since I backup all of the drive contents every week.  This would simplify a lot for me.

What would you recommend is the best way to go about setting this up with my Samba configuration?  I have a feeling /media/Slave/UserProfiles permissions will get somewhat complex.

Thanks for any input.

---

### Post by iTrascurato on 2009-11-05
Didn't.. think.. so

---

### Post by koenn on 2009-11-05
essentially you'd do this the same way you'd do Windows with NAS: you set your users' profile path to \\sambaserver\share[\subdir]\%username%

you'll have to set the appropriate permissions; if the disk in question has an ext3 fs, you probably have to install and setup acl, and set the permissions using setfacl (or from Windows, through the share). 
see MS's documentation about the required permissions for profile folders



> **iTrascurato said:**
> Didn't.. think.. so
what?

---

### Post by whoop on 2009-11-07
I don't really understand what the question is but this is the most complete tutorial on this topic:
[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

It was written for ubuntu 7.10 but it also works with 8.04 (LTS).

As this tutorial is the most complete one out there and it is outdated, everyone should understand that we need updated documentation on this subject. So please **vote**:[http://brainstorm.ubuntu.com/idea/22151/](http://brainstorm.ubuntu.com/idea/22151/)

---

