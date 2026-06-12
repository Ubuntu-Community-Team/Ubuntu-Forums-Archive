---
title: "Fileshare on Ubuntu Server 18.04"
date: 2018-09-17
forum: Server Platforms
---

### Post by mrsixty7 on 2018-09-17
Hi guys. Ubunutu/Linux beginner here.

I have just installed Ubuntu Server 18.04 on an old laptop I have kicking about the place (home setup).

My first objective is to create a fileshare that enables me to access files centrally from any devices I am using in and away from home. I have just set up a static IP with my ISP (PlusNet UK), which I am hoping will make the external connectivity easier, and I will try to figure out later. I would add that I am not looking to set up a cloud solution specifically, just a central file share location.

In the meantime, I am looking for recommendations in terms of the physical fileshare. The laptop has only a 500GB HDD so I am looking at an external USB device that offers RAID1 for file redundancy. At the moment, I just have a 12TB MyBook DUO connected to my big rig (W10) but of course this is not powered up all the time.

If you have - or are aware of - a similar setup, I welcome your recommendations. Not actually sure if I can just plug the DUO into the Ubuntu laptop, add its path through SAMBA and away we seamlessly go (nothing is ever that easy, right?). I don't really want to risk losing several TB of important data 'testing' if this will work.

Many thanks in advance.

/Danny

---

### Post by TheFu on 2018-09-17
Welcome to the forums.

Don't use RAID when you are a beginner.  NEVER use RAID over USB connections. Use backups.  You need backups anyways, even with RAID1 or RAID10.  There is no substitute for backups, ever.  For media backups, use rsync over ssh.  This is common and works very efficiently.  For OS and document backups, use a real backup tool like duplicity or rdiff-backup.

If you have a DAS or NAS device and there is a RAID1 mode built in, go ahead and use that, if you like, but really RAID1 should only be used for 2 needs. High availability and better performance.  Neither are really possible with USB connections.  That's just the way life is.

For remote access to the system, use **ssh**.  For remote access to files on the system, use sftp, which works over the ssh port and uses ssh authentication.  From the internet, never use passwords for access. Always use ssh-keys or ssh-certs.  Every networked OS has a good sftp client solution.  Windows has WinSCP for an sftp client.

Secure the ssh, sftp, rsync, scp, etc ... connection by blocking most of the internet using your firewall/router and block the places you will likely come from using fail2ban.  No need to allow Russia or China to hack at your ssh port all day.  You can find full-country subnet block lists.  They aren't perfect, but better than allowing the world access when you are only 15 miles from home and need access.

You cannot use samba/cifs over the internet, thank god.  Most ISPs block those ports.  Using CIFS over a VPN is a bad idea too due to the overhead.  Plus security of cifs is a joke, a bad joke.   If you must, setup CIFS/samba on your LAN, but lock it down to only the Windows systems, not the entire subnet.  There are reasons.

There are other solutions, but these are generally too complicated for someone new to Linux to setup in a secure manner.  You'll always need ssh, so start there.  ssh is the most capable, secure, way for different devices to be accessed over the internet.

[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) probably is a good enough place to start.

There are better answers for LAN Unix-to-Unix file sharing, but they aren't trivial.  
There are good answers for Android-to-Unix connectivity using VPNs, but they aren't trivial.  You can use sftp to start.

openssh-server is the sshd package. It includes the sftp server program.
fail2ban is the fail2ban package. It protects all ssh-based services.
Learn to use **ssh-keygen**, **ssh-copy-id** to setup convenient connectivity between ssh clients and servers.

After you get ssh/sftp and the other ssh-based services working on the LAN, please ask more about security.

NEVER use passwords over the internet.  Passwords are a complete security failure. Use key-based authentication whenever possible.

You don't specifically need a static IP, but it does make things a little easier.  You can use dynamic-DNS services.  No-ip, dyndns, most consumer routers have a few other providers built-in.  If you like, you can get a domain ($$) registrar, and public DNS ($$), to let people use a name to get to your IP/system(s).  Do not run your own public DNS. That is a good way to be hacked. Pay someone else.  I'd also suggest keeping the DNS and Registrar separate to prevent issues that will happen.  No need to pay for "privacy registration" anymore thanks to EU laws.  If you need more details about this, ask.  I can post an article about this stuff.

---

### Post by HermanAB on 2018-09-18
Well, you can use passwords, but make them very long - at least 16 characters.

---

### Post by TheFu on 2018-09-18
> **HermanAB said:**
> Well, you can use passwords, but make them very long - at least 16 characters.

Herman and I have different opinions about this. Over the internet, I want 30+ characters for passwords and they need to be randomly generated.  16 characters **can** work, but only if 100% random, not words, mostly symbols, very hard to type passwords.  I attend hacking conferences and know length and not using anything that looks like a word is critical. **Humans are terrible at picking passwords and we aren't exactly as cleaver as we think we are.**  The XKCD method of using 2-3 words is well known know and part of the hacking techniques.

ssh-keys are 10,000 easier and much more convenient. Take the 15 minutes to learn these and you'll have trivial access between systems for the next 18+ months.

---

### Post by slickymaster on 2018-09-18
*Thread moved to **Server Platforms**.*

---

### Post by mrsixty7 on 2018-09-19
Thanks for the response guys. Clearly there is much to learn here and I am surely in the right place to learn it!

Already got the bug. Have been a hobby coder for some time now but it's great to learn the back end platform side of things to give me more of a 'bigger picture' perspective.

I am finding myself spending more time than I expect to, searching Google for answers, but I do hate to come to the forum with what may be trivial questions to you guys.

/Danny

---

