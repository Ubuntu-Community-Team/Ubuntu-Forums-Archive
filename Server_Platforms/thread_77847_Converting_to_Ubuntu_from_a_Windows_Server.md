---
title: "Converting to Ubuntu from a Windows Server?"
date: 2005-10-17
forum: Server Platforms
---

### Post by Rhyselsworth on 2005-10-17
Hi,
I apologise if this is in the wrong thread, its my first post.

About 18mnths ago I set up a server system to run 5 clients on a domain for the company I work for. I have since left for University. Since I knew nothing about Lunix/Unix at the time I opted to use Windows Server 2003. Recently I'm having a string of annoying authentication errors and performance isssues that I'm failing to fix. I wondered perhaps if it was time to make the change to using a Unix based operating system to run the server and if this might solve some of the niggly errors. Basically I would need it to perform the following tasks:

 - Central File Sharing
 - Checking multiple POP3 E-mail addresses and routing it to the appropriate users mailbox (I use Exchange at the moment)
 - Automatically backup important data using a tape drive
 - Offer printing services to client computers (The main printers will be connected directly to the server itself) 
 - Assign IP Addresses to clients using DHCP
 - Copy users Windows account data to the server when they logon and logoff, so that they can retain thier settings, but more importantly thier data. I don't mind having a standard desktop.)
 - Authenticate client logon to the domain
 - Clients will continue to use WinXP as thier operating system

To add to the complication the server is a dual Xeon machine, with a SATA RAID enabled accross two drives which form its main hard disk.

I realise this is a pretty tall order, but I'm curious to see how feasible using Ubuntu/Linux is and if anyone has any thoughts on it (Or has already switched). Could switching be a good long term solution?

Sorry about the long post!  :-p

Rhys

---

### Post by t1mmy on 2005-10-17
Howdy, using Linux to do those things is not a tall order at all.  But you won't do it by installing linux on the server one evening, set it up, and make it home in time for dinner.
You'll be wanting to set up an interim server, get everything working on it, put it in place, and then reimplement it on the real server in one of several ways.
* - Central File Sharing*
SaMBa can do that for ya.
* Checking multiple POP3 E-mail addresses and routing it to the appropriate users mailbox (I use Exchange at the moment)*
A short shell script, fetchmail, and the mta will do that for you.  They don't need calendaring apparently?
* - Automatically backup important data using a tape drive*
tar.
* - Offer printing services to client computers (The main printers will be connected directly to the server itself) *
CUPS.
* - Assign IP Addresses to clients using DHCP*
The server is called dhcp, and you edit a file in /etc to set up your scope.
*- Copy users Windows account data to the server when they logon and logoff, so that they can retain thier settings, but more importantly thier data. I don't mind having a standard desktop.)*
That might be a thinker.  SaMBa maybe, or some kind of login script on server or client side.
You're probably going to need to fix the Windows server first.  Good luck.

---

### Post by faulkner132 on 2005-10-17
Rhyselsworth,

Speaking from experience, Windows XP (usually) doesn't like any server except Windows... especially when it comes to the Domain part.  I would stick with your Windows setup and just hammer through the problems.  Server 2003 is pretty straight-forward and for the most part can run with little maintenance unless you are using it as a terminal server as well.

I agree with t1mmy that it will take a lot of work and (at least in my opinion) would not be worth switching.

---

### Post by Rhyselsworth on 2005-10-18
Thanks for the suggestions :) I think I'll try to set up an interim server as suggested, but that could take me a fair while so It'll be a bit of a side project. In the meanwhile I'll try and work through the Windows problems and get the existing server working. 

Thanks again,
Rhys

---

### Post by Shiner on 2005-10-18
My thought on this would be to keep the windows server/domain for authentication and profile settings and use linux for all else.

---

