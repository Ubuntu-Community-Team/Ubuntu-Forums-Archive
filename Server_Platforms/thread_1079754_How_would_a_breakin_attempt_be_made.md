---
title: "How would a breakin attempt be made ?"
date: 2009-02-24
forum: Server Platforms
---

### Post by mistypotato on 2009-02-24
I have my ftp server set to ONLY allow one user access.

So if you try to access the fto on my server it says...

530 Permission denied.



So where and how does someone attempting to break-in actually enter a username and password?

silly question but I'm new to ubuntu and clueless.

---

### Post by memilanuk on 2009-02-24
Just speaking in general terms, as it's been a while since I really got 'into' the whole *nix security scene... things may have changed since then.

FTP by default is not an encrypted service - when you login with username and password, you are logging in via what is referred to as  'plain text', i.e. no scrambling or encryption of the data.  Someone who wanted in could theoretically use a network packet sniffer to capture the stream of data packets being exchanged while you login... and be able to view both your username and password as plain ASCII text.  Then, they can log in as *you*, and do whatever harm they want (limited only by what your account is allowed access to).

If it's a home network that uses hard-wired ethernet connections, odds are pretty slim of someone being able to gain access to your physical network without you knowing it - there are ways, IIRC, but if someone is willing to go to those lengths to get at your information, they'd be better off to just break into your house and steal the machine ;)

If it's a wireless network, I suppose your neighbor's kid could possibly capture your login via wifi and then get into your stuff.  Not good.

HTH,

Monte

---

### Post by hictio on 2009-02-24
I guess you should really re-post on the [Security Discussion Forum](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=338), but, given that you are running FTP (without even SSL) there is really not much to do, all the information (including login and passwd) is sent on the clear, so if *they* can plant a traffic analyzer, *they* can easily get a way inside your box w/o a lot of effort.

You should change to an encrypted service, like SFTP, setup a firewall on the box, so only the allowed IPs/ networks that have to connect can connect to the service.

---

