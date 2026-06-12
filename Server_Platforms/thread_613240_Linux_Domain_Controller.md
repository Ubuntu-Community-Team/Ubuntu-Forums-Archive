---
title: "Linux Domain Controller?"
date: 2007-11-14
forum: Server Platforms
---

### Post by measekite on 2007-11-14
Currently I have a Windows 2K Advanced Server that is a Domain Controller and 2 Linux Desktops running Feisty.

Soon I would temporarily like to disconnect the Server and maybe connect it later.

So let say I build a new computer that I will designate as a server.  Here are my questions:

[COLOR=Red]1.  What server version of Ubuntu would be best?
[/COLOR]
[COLOR=Red]2.  How can I make this the domain controller of mydomain.com. [/COLOR] This is an intranet and does not ventura out beyond the LAN to the WAN.

[COLOR=Red]3.  After all this works how can I add my Win server back?[/COLOR]  He still thinks he is a domain controller so I guess I would have to demote him.

[COLOR=Red]4.  If Linux does not have a concept of a domain controller than how do I create a Linux Domain and have all 3 machines join that domain.[/COLOR]

[COLOR=Red]5.  Where can I find documentation that deals with this?[/COLOR]

---

### Post by prezbedard on 2007-11-14
You can find everything you need on the samba.org website.

and it really doesn't matter which version of linux you use

as far as disconnecting the W2K server you can reconnect it without having to demote it. W2K domains don't have primary and backup all domain controllers have the same role. I'd keep it a dc cause even though you can turn a linux box into a dc there are number of items group policy for example it won't be able to keep. plus the ad database

---

### Post by koenn on 2007-11-14
> **prezbedard said:**
> 
as far as disconnecting the W2K server you can reconnect it without having to demote it. W2K domains don't have primary and backup all domain controllers have the same role. I'd keep it a dc cause even though you can turn a linux box into a dc there are number of items group policy for example it won't be able to keep. plus the ad database
That's not entirely correct. Although Win2k and newer domains - so called 'Active Directory Domains' - don't distinguish between Primary and Backup Domain Controller, the first installed DC assumes a couple of roles that are unique and that the other domain controllers don't have, such as the role of Schema Master. So you can't just have two of those. 

And if you're looking at samba to act as an AD Domain controller, you'll have to wait for version 4. The current version can join an AD domain, but only as a member, not as a domain controller.

---

### Post by prezbedard on 2007-11-14
> **koenn said:**
> That's not entirely correct. Although Win2k and newer domains - so called 'Active Directory Domains' - don't distinguish between Primary and Backup Domain Controller, the first installed DC assumes a couple of roles that are unique and that the other domain controllers don't have, such as the role of Schema Master. So you can't just have two of those. 

And if you're looking at samba to act as an AD Domain controller, you'll have to wait for version 4. The current version can join an AD domain, but only as a member, not as a domain controller.

you're right. forgot about that 

d'oh

---

### Post by prezbedard on 2007-11-14
I do believe there is a way to have a Linux domain controller if you all use Linux and don't have any windows servers. I know I read it somewhere before

---

### Post by prezbedard on 2007-11-14
ya can can act as dc emulating  NT DC which of course is obsolete or at least should be

---

### Post by koenn on 2007-11-14
> **prezbedard said:**
> ya can can act as dc emulating  NT DC which of course is obsolete or at least should be

Well, it does give you centralized user management so if that's the main or only concern, its (still) a valuable and viable option - eg for small businesses. 
If, however, the thing is to replace an AD DC with all the bells and wisthles, that's an other story.

---

### Post by Gone fishing on 2007-11-15
I'm using a Linux domain controller. It works fine, I can control who can logs onto the system etc, all users have a space on the controller mapped to drive H and limited access to other Windows shares. I don't know how it compares to Win 2000 as I've never used it.

I also use the box as a proxy using Squid and for mail.

I would install Webmin it comes with all the documentation for setting up SAMBA and give you a lot of useful tools for managing SAMBA, for example I can control the Box remotely and create a batch file from our student database that adds users automatically (if you have to add  500 users this is dead handy)

---

