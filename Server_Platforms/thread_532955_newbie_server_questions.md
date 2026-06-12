---
title: "newbie server questions"
date: 2007-08-23
forum: Server Platforms
---

### Post by zeusdo on 2007-08-23
I'm trying to find a solution to a problem. I'm a total newbie with servers, I've never worked with one. Here is my situation and what I'm trying to accomplish. I run a small office that has 5 desktops and 1 laptop, all running WinXP and connected wireless to a Linksys (WRT350N) router with a DSL connection. The most important thing that I'm trying to accomplish is networking them all together so we all have access to our Quickbooks software. My idea was to use 1 of the desktop computers (it's an old Pentium 4 with 512 of RAM) as a server that would host the Quickbooks application. We also need to connect all computers to the printer (HP laser 2840). 

First, is this the right way I should be doing this?
Second, is running a server more reliable than networking the desktops together as they are?
Third, can the printer be connected directly to the server computer? (The printer has network capability but I'm having a problem see it threw the router) 
Lastly, is this an easy task for someone with a LOT of WinXP experience but NO server experience at all?

---

### Post by p_quarles on 2007-08-23
First of all, you will not be able to use a Linux server to host Quickbooks. You'd need a Windows server for that.

It would be relatively simple, however, to set up one machine to host the Quickbooks data (using Samba) and act as a printserver. The Quickbooks application would still need to be run separately on each workstation, though. 

As for reliability, that's very dependent on your situation. Linux is generally much more stable, and has vastly better uptime, than Windows. But only you can know whether you would benefit from this. Are you having problems with the networked Windows workgroup? Is data being lost or improperly handled? 

On your last question, the answer is no. Linux is a complete operating system. If you're willing to put in the time to learn it, it's fantastic, and much more flexible than any closed source software. However, no amount of experience with Windows is going to help with that. Longtime Windows users are frequently more frustrated with Linux than complete computer newbies. They expect things to work as they do with MS software, and they don't.

---

### Post by zeusdo on 2007-08-24
So it sounds like I can run the Ubuntu server but all the windows computers will be connected throu Samba, and I guess the printer functions will run trou Samba as well. 
As for Quickbooks, the main reason I want to do this, QB has a muliti-user mode built in. Currently, all of the desktops have the QB application installed, but 3 of the desktops are sharing the QB data file being hosted from the other one.
Here is the question, if I put the QB data file on the Ubuntu server using Samba, can all the Windows computers use it simultaneously like they are now?

I will try this all in a temporary situation before I commit to it, I just don't want to waste time if it is not possible.

---

### Post by p_quarles on 2007-08-24
I didn't know the answer to this question, but I found [this web page]("http://www.howtoforge.com/samba_quickbooks_incompatibility") which addresses the issue. The bad news:

> QuickBooks uses a file-locking mechanism that is not compatable with Samba because it involves changing file ownership. Shame on you, Intuit.
This is just one person's experience, obviously, but it'd be fairly easy to confirm this by paying a visit to Intuit's support pages.

---

### Post by zeusdo on 2007-08-24
I thank you for that information but I also found [this]("http://support.quickbooks.intuit.com/support/DoSearch.aspx?kbID=1000759&sg=SG_ALLQUICKBOOKSPREMIER2007_1_3_Fam&mod=7-30-2007+2:7:35")

Maybe it was that he, in the article, was using the 2006 version but I'm using the 2007.

But [this]("http://quickbooksenterprise.intuit.com/resources/linux.jhtml") also is interesting. "QuickBooks Database Server Supported on Linux"

By the way, I can't seem to find a tutorial on how to install Ubuntu server.

---

### Post by p_quarles on 2007-08-24
Cool. I guess Intuit came around.

A couple good setup guides:
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

EDIT: On a second look, I noticed that Intuit's database server is *only *available as an rpm package. While it's possible to get this working in Ubuntu, it could be a headache. My advice would be to look into an rpm-based distro, such as CentOS. Not only will it save you the headache of dealing with incompatible package managers, but CentOS actually has a really good program that mostly automates server setup.

---

### Post by zeusdo on 2007-08-24
I have no idea what a rpm-based distro is and I have never heard of CentOS. I guess I have alot more research to do. I came here, to Ubuntu, because it was the first time I ever tried a linux OS and waspretty happy with it but I did have problems. The forums here are unlike anywhere else, so many people willing to help others!

---

### Post by p_quarles on 2007-08-24
RPM = "Redhat Package Manager." CentOS is a great version of Linux that is based on Redhat. Redhat is one of the standards for enterprise use of Linux, which is why Intuit would release this kind of package first.

Ubuntu and Debian use the "apt" package manager, which is newer and more powerful, but less established for enterprise use. Applications are put together differently for each package manager.

If you do want to use Ubuntu, you can try using the "alien" application, which purports to convert .rpm packages to .deb packages. I understand its record is kind of spotty, though.

And, yes, these forums are second to none.

---

