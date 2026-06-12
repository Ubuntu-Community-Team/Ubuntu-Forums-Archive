---
title: "Ubuntu and Windows.  Can they coexist?"
date: 2011-07-19
forum: Server Platforms
---

### Post by mcarrara on 2011-07-19
For the last several years I have been running my network as a NT domain with Samba acting as the PDC.  I had 8 Ubuntu servers and one Windows server.  Life was good and I had only a few minor issues with networks.  Now I thought it was time to install Windows 7 on the users computers.  First issue is Win7 clients can't join a NT style domain.  I purchase a Windows Server 2008 license and 250 CALS.  Next issue is DDNS must be running.  I am working on that.

What is next?  I have read that Windows 2008 AD will not work with a DDNS unless it is a Windows DDNS.  So now I need to run an new DNS server?  Will my Win7 clients connect a to a Samab server for files and CUPS?  Is there more gotya's hiding up ahead?  I would love to here from people who have made the journey before.  Can Windows 2008 AD, Windows 7 and Ubuntu coexist on a network?

---

### Post by collisionystm on 2011-07-19
Windows 7 can join a samba domain. You only have to add a registry fix to join it.

You can set ubuntu to sync with your windows PDC using ldap. 

Question, how do you plan on integrating your Xp machines with your windows 7? You will be running them on 2 seperate domains unless you migrate everyone over to windows?

I have a nix box running as my PDC and file server with Several windows 7 and xp clients. Hasn't been a problem yet.

---

### Post by mcarrara on 2011-07-20
Our original plan was to move just about everyone to Win7.  We have a few netbooks and I don't think Win7 will work on them.  They may stay Win XP.

I guess we move forward.  Today we install Windows DNS, yippee!!

---

### Post by headvampyre@hotmail.co.uk on 2011-07-23
Why no just run ubuntu on every server? There was a hack to get Samba3 and Windows 7 working on an NT4 style Domain.

If you know what your doing, you could always upgrade form Samba3 to Samba4(They've created scripts for it, or if your using LDAP, you could just install the Samba4 Schema for that).

Ooh, and if your awesome, you could replicate the 2008 domain onto a 2008_R2 Samba4 DC.

Only issue is Samba4 is only in alpha stages, but I've found it to be very stable, and it could be used in production.

This would also enable you to use Samba3 or Samba4 for filesharing, aswell as Bind9, thus making your network close to costless :)

---

### Post by Ed_Ziffel on 2011-07-23
Unless something outside of my control, say like having to use Windows IE to use some third party web application, real estate listing programs for example, I don't use windows at all.  No doubt you have such requirements or why not just 86 windows all together?

---

