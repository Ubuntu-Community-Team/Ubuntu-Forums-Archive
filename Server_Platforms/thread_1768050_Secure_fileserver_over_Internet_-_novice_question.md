---
title: "Secure fileserver over Internet - novice question"
date: 2011-05-26
forum: Server Platforms
---

### Post by Fubini on 2011-05-26
Thanks for taking the time to read my post!

I'd like to set up a fileserver for myself and a few trusted individuals. I'm computer savvy and I use various linux servers frequently for work, but this is my first time trying to setup my own. Is it possible to have a Samba server setup so it is both secure and facing the Internet? 

Two questions: 

Will opening Samba ports make my default Ubuntu server particularly vulnerable to penetration? More than having an SSH server running?

Does Samba/ can Samba be configured to encrypt traffic or is it sent plainly? If so, does Windows and Mac support this secure communication? 


If not, what would you suggest? I'd like to achieve something like a network drive and at a difficulty level that my parents could use this if they really wanted to. I will be storing things like financial information and tax returns, but no weapons-grade secrets.

---

### Post by deconstrained on 2011-05-26
**EVERY** WAN-facing service you run is a vulnerability. Your server is only as secure as its weakest e-orifice. WAN-facing Samba with private information = big mistake.

I recommend setting up either VPN or SSH tunnelling, and then making all other services accessible through them. Both can be configured to be very secure and require different kinds of authentication. If you have a FreeBSD server on your local net then you can easily use its native IPSec service (which is well-documented). Otherwise I recommend OpenVPN, which can be a pain to configure and get working properly but has more versatility and security-hardening features than anything else out there you can get for free.

Edit: I forgot to mention that traffic that goes through SSH and most kinds of VPNs (including IPSec and OpenVPN) is always encrypted by default.

---

### Post by Fubini on 2011-05-26
What I'm really asking is whether it's an acceptable risk.

If I've got my Samba server configured to use user based authentication (i.e. "security = user") then will the Samba authentication be any less secure then running SSH (which, in my case, use the same user database)?

Unless it can be done automatically and easily I'd like to stay away from VPN or SSH tunneling because the whole point of this would be to have something both convenient AND secure. I don't want to sit down with my wife and teach her how to do SSH tunneling.

---

### Post by deconstrained on 2011-05-26
And I'm telling you it's not an acceptable risk. Samba is not known for being secure.

What you could do is throw together a configuration file and client/tls-auth key for OpenVPN, test them on a sandbox client running windows (OpenVPN client available for Windows) and send them the keys/conf file in a rar/zip. In the Windows OpenVPN client it should just a matter of selecting "import configuration" or the like to set up the connection.

Since you're the one more adept at Linux, Unix and networking I'd say that finding a way to package it up and make it as easy as possible for them to use is your responsibility, especially since it's the security of your system we're talking about.

---

### Post by moonpup on 2011-05-26
I agree, putting a samba share on the internet is a very bad idea. First off it's authentication process will not be encrypted and everyone scanning for net bios shares will attempt to log in.

Just install ssh and have everyone use an sftp client to get and put files. If you want to be really secure you can disable ssh password authentication and setup public/private key and change the default port of 22 to something else.

---

### Post by wlraider70 on 2011-05-26
If you want to be secure and you are going with SSH.

I think you have to either change the port or use RSA keys.
I was astounded with how many ssh attempts I got on my SSH server everyday. 

If you want convenient RSA keys can be sent automatically if you don't have physical security issues.

---

### Post by deconstrained on 2011-05-26
> **moonpup said:**
> Just install ssh and have everyone use an sftp client to get and put files. If you want to be really secure you can disable ssh password authentication and setup public/private key and change the default port of 22 to something else.
Actually, **this is** the simplest/easiest solution.

FileZilla  + SSH on unprivileged port + RSA Key host authentication.

---

### Post by Lars Noodén on 2011-05-27
> **deconstrained said:**
> Actually, **this is** the simplest/easiest solution.

FileZilla  + SSH on unprivileged port + RSA Key host authentication.

FileZilla is actually SFTP. And speaking of SFTP, there is a second way using SSHFS.  That's competitive in the easy/simple question.

---

### Post by deconstrained on 2011-05-27
SFTP **IS** ssh; it's a subsystem that's included in OpenBSD's standard distribution of it.

---

### Post by Lars Noodén on 2011-05-28
> **deconstrained said:**
> SFTP **IS** ssh; it's a subsystem that's included in OpenBSD's standard distribution of it.

Correct, and FileZilla can use it even though it is marketed as a "FTP" application.  It's definitely the easiest way to go either via FileZilla (SFTP) or SSHFS (SFTP, again).

---

