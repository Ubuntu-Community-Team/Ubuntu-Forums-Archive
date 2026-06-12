---
title: "Can I rely on FileZilla on Linux after hack from FileZilla on Windows ..."
date: 2011-05-20
forum: Security
---

### Post by mind_exploit on 2011-05-20
Hello,

I am a web developer, and this month, suddenly a lot of the sites we've done appeared to be hacked. All of the infected sites were made from a friend, who was on Windows, using the Avira antivirus. (?!?!?) Now she's not working on them, and I'm cleaning the sites. I am on Linux - Fedora and Ubuntu on both my laptops.

From the hosting company we received an email, where the system administrators said to us NOT to use FileZilla. And my question is:

On windows a virus or worm could go into FileZilla, cause there are too much trojans and viruses that uses exactly FileZilla ... so a worm could easily connect to the sites and do practically everything. This was the way the sites were infected actually. BUT - could something like this happen on Linux?

(Or maybe this depends on some settings? ... configuration? cause I know that if something attempts to install itself - I'll be asked for root password ...so there is no way this to happen without my knowledge ...)

Regards,
Peter

---

### Post by aysiu on 2011-05-20
I don't see how FileZilla could be a problem. Maybe it's using FTP instead of SFTP?

---

### Post by mind_exploit on 2011-05-20
> **aysiu said:**
> I don't see how FileZilla could be a problem. Maybe it's using FTP instead of SFTP?
Yes ... it is ...

---

### Post by HermanAB on 2011-05-21
Well, first off, why the heck are you using FTP and not SSH?  Secondly, your security is generally only as secure as your passwords.  A kewl 4 character password is insecure.  Ensure that all passwords are at least 9 characters and things will be better.  I use 16 character semi-pronounceable passwords.

---

### Post by bodhi.zazen on 2011-05-21
The problem is probably with ftp and not FileZilla.

ftp is commonly used by web developers, and many web applications, such as wordpress, advise you use ftp.

But ftp is insecure, passwords are not encrypted.

Better to use ssh (scp). There are graphical clients for windows, winscp.

Use keys and disable passwords.

---

### Post by mind_exploit on 2011-05-27
Hello,

The passwords were strong enough actually ... not 4 or 5 characters. Actually - the problem was that the worm/virus stole the credentials for the sites.

So my question is if this could happen in Linux. Or - in other words - are there any such exploits for FileZilla, but running on Linux?

PS: The administrators of the server changed all the credentials (username/password) as well as the port for FTP - for all the sites on the server.

---

### Post by bodhi.zazen on 2011-05-27
> **mind_exploit said:**
> Hello,

The passwords were strong enough actually ... not 4 or 5 characters. Actually - the problem was that the worm/virus stole the credentials for the sites.

So my question is if this could happen in Linux. Or - in other words - are there any such exploits for FileZilla, but running on Linux?

PS: The administrators of the server changed all the credentials (username/password) as well as the port for FTP - for all the sites on the server.

You are asking a theoretical question , so yes in theory Linux, or any other OS , can be cracked.

In practice the exact exploit you are asking about has not been described and it is much harder, not impossible, just harder to crack into a Linux box.

You would have to look at the internals of the worm, but the problem is that FTP is not a secure protocol as it passes passwords in plain text. As long as you use an insecure protocol (ftp) over the internet you will remain vulnerable.

A better practice, rather then changing the passwords, is to switch to ssh (sftp). There are graphical clients for sftp (winscp on windows). Not sure on Linux but filezilla or gftp would almost certainly support sftp.

---

### Post by DodgeV83 on 2011-05-27
> **mind_exploit said:**
> Hello,

The passwords were strong enough actually ... not 4 or 5 characters. Actually - the problem was that the worm/virus stole the credentials for the sites.

So my question is if this could happen in Linux. Or - in other words - are there any such exploits for FileZilla, but running on Linux?

PS: The administrators of the server changed all the credentials (username/password) as well as the port for FTP - for all the sites on the server.

I agree with bodhi.zazen.  It doesn't matter which FTP client or OS you use, which port FTP is using, how long your passwords are, or how many times you change them...

If you're using plain FTP, your passwords are being transmitted in the clear and you are vulnerable to this type of attack.

Use sftp.

---

### Post by deconstrained on 2011-05-27
Ask the admins. Maybe they want you to log in using SSL if available, and they may even tell you how.

---

### Post by Lars Noodén on 2011-05-28
> **DodgeV83 said:**
> ...Use sftp.

FWIW, I've added a ticket at FileZilla with a [feature request that the profile of SFTP support be raised a bit](http://trac.filezilla-project.org/ticket/7359).  There are valid use cases for Anonymous FTP, but precious few legitimate ones for regular FTP anymore.  

Raising the profile of SFTP in the right places can do a lot towards retiring FTP.

---

### Post by sefs on 2011-05-28
> **bodhi.zazen said:**
> ... There are graphical clients for sftp (winscp on windows). Not sure on Linux but filezilla or gftp would almost certainly support sftp.

Yes, FileZilla3 supports sftp, and with keys as well.

---

### Post by CharlesA on 2011-05-29
> **sefs said:**
> Yes, FileZilla3 supports sftp, and with keys as well.

Indeed it does. Last I checked, it didn't allow passphrases on the keys.

---

