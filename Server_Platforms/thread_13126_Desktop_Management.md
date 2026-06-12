---
title: "Desktop Management"
date: 2005-01-29
forum: Server Platforms
---

### Post by HappyBoy on 2005-01-29
Hi All,

This is my first time coming here. I'm very impressed with Ubuntu. However, I have a question regarding the Desktop Management in Ubuntu. 

Is Ubuntu able to do desktop management such as centralized desktop configuration, patch management, etc. With Desktop configuration, all client computer settings can be managed from a server computer. 

Most businesses/enterprises slowly adapt Linux because most Linux distributions don't have this feature while M$ Windows fully support Desktop Management through its Active Directory Group Policy and SMS server.

Does ubuntu have this feature already or someday it will available in the future version? I do hope so... :D 

Regards,

Hendry

---

### Post by Jad on 2005-01-29
My friend had same problem, he want to adapt Linux in his Internet cafe, but Control over other machines was hard without a Desktop management.

---

### Post by mendicant on 2005-01-30
Mounting filesystems via NFS is the usual mechanism for this, with /var (including /tmp) mounted locally.  That way, there's only one system to maintain.  Also see documentation on automounting home directories (via automount and nis).  You could also look into the Linux Terminal Server Project: [http://www.ltsp.org/](http://www.ltsp.org/).  Lots of other places do this kind of thing (schools, for instance).

---

### Post by HappyBoy on 2005-01-31
I think I found a workaround, by installing systemimager ([www.systemimager.org](www.systemimager.org)) and do mounting filesystems via NFS 

SystemImager can roll out automatic Linux patch/installation, configuration, and best of all this is a GPL project. I think It'd be great if Ubuntu server version integrat this software by default.

These two combinations can at least do what M$ SMS (System Management Server) do

I'm going to do research on systemimager and NFS in my spare time.

BTW, I still hope in the future Ubuntu has its own Desktop Management Solution  :D

---

### Post by nocturn on 2005-01-31
[QUOTE=HappyBoy]I think I found a workaround, by installing systemimager ([www.systemimager.org](www.systemimager.org)) and do mounting filesystems via NFS 

SystemImager can roll out automatic Linux patch/installation, configuration, and best of all this is a GPL project. I think It'd be great if Ubuntu server version integrat this software by default.

These two combinations can at least do what M$ SMS (System Management Server) do

I'm going to do research on systemimager and NFS in my spare time.

BTW, I still hope in the future Ubuntu has its own Desktop Management Solution  :D[/QUOTE]


I hope so too.  This is one thing were Linux is lacking somewhat behind.  Although I have worked with SMS and it is horrible.

---

### Post by twistedpair on 2005-01-31
[QUOTE=nocturn]I hope so too.  This is one thing were Linux is lacking somewhat behind.  Although I have worked with SMS and it is horrible.[/QUOTE]

Active Directory behaves better.

---

### Post by mendicant on 2005-01-31
I'm not sure why you need systemimager, unless you have computers that can't boot from the network.  Usually, you would just do a network boot, it grabs the kernel remotely, starts running it, and as a user logs in, it NFS mounts the correct home directory.   Other directories can also be mounted on an as-needed basis, given the correct permissions.

---

### Post by houstonbofh on 2007-11-07
Ancient bump!
Any changes here.  There was some buzz about Conical Landscape a while back, then nothing.  Is there a solution for a poor bofh with a growing desktop base managed by hand right now?

---

### Post by technodigifreak on 2007-11-08
Well there are a few options actually.

To roll out pristine clients you can use System Imager, or setup your own PXE/NetBoot server.

The easiest way to handle patch management is to setup a local apt repository on your network, point all of your local desktops to it, and have them automatically pull the latest packages once a day or week or month, whichever you choose.  This page may be of some use to you [http://www.debianhelp.co.uk/pkgadm.htm]("http://www.debianhelp.co.uk/pkgadm.htm") .  This has two distinct benefits: It saves on your WAN bandwidth, and it updates ALL of the software on your clients, not just some of the software like some other OS's (We're looking at you Mr. Start Button....)

Centralized logins can be managed with LDAP.  [http://times.usefulinc.com/2005/09/25-ldap]("http://times.usefulinc.com/2005/09/25-ldap") is a bit dated, but still valuable reference.  LDAP can be a particularly good option if you already have an Active Directory infrastructure in place, afterall why shouldn't you take advantage of all that? You may want to consider an OS X Server, it is designed to quickly and easily integrate *nix's with AD/OpenLDAP.

I would make the clients as dumb(READ: replaceable) as possible and have the user's home directory auto-mounted from a network drive.  This also has the side benefit of making your backup strategy GREATLY simplified.

Some ideas to get you started.  Let me know if any of it is useful.

Something else you may want to consider, if you are going to rolling this out to a business/enterprise network, you may want to give Canonical/RedHat/Suse a call and work with them to find the solution that works best for you, and buy a support package for it.  Because sooner or later, every system breaks, and then the only thing that matters is who you can call to get it working again.

---

### Post by houstonbofh on 2007-11-09
A few problems...  The systems are distributed all over.  A max of 3 systems in a given location.  What I need is a way to know what is current, and what needs patching or upgrading.  They also need to stand alone, and operate when the net is down.

As to "Who ya gonna call?"  Well, thats me. :)

---

