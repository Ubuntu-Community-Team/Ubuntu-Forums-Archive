---
title: "ProFtpd vs. VsFtpd"
date: 2009-07-15
forum: Server Platforms
---

### Post by chrisinspace on 2009-07-15
I am about to put an FTP solution in place and I've been doing some research.  I know there are a lot of solutions out there, but here is my criteria: 

[LIST=1]
[*]SECURE - This is critical. I plan to do an FTP over SSL (FTPS) implementation.  This server will reside in a DMZ.

[*]Well-documented - I'm fairly new at this.  I've been using Linux on the desktop for a few years now and I have a little experience managing an Ubuntu server, but I need somewhere to turn if I get stuck.

[*]Good community support - goes hand-in-hand with the previous point about documentation.

[*]Not too hard for end-users who will be connecting to the server - I need to be able to walk semi-savvy users through the process of connecting to my FTP server using common clients such as Core FTP, Filezilla, CuteFTP, etc.
[/LIST]
I've narrowed it down to ProFtpd and VsFtpd.  Can anyone make any recommendations as to one over the other?  Are there any key features that differentiate them?  One thing that I heard about VsFtpd that I like is that there is a Webmin plugin available for managing the server.  I have Webmin set up on another Ubuntu server and I use it for general admin, Apache, and MySQL.  It would be nice to centralize on that platform if possible.  I'd really appreciate any advice.

---

### Post by chrisinspace on 2009-07-16
I'd really like to get moving on this.  Does anyone have any feedback?  I'm hoping the community can help point me in the right direction.

---

### Post by scorp123 on 2009-07-16
You've already done all research. What do you expect? That we toss a coin for you? :D

I personally would not bother with FTP at all and stick to OpenSSH instead. The entire exercise with setting up a FTP server and enabling SSL certificates so you'd get "FTPS" seems highly redundant to me, when instead you could simply stick to SSH and use SFTP which already provides this functionality right out of the box.

---

### Post by giggins on 2009-07-16
I've got to agree with scorp123 on this one. SFTP meets all the things you have listed, plus it has numerous clients available for virtually every platform. FTP with security is a hacked abomination of an already pretty old and broken protocol. See [http://en.wikipedia.org/wiki/FTPS](http://en.wikipedia.org/wiki/FTPS) for more details, especially the section about "Firewall incompatibilities". If your goal is to provide a secure way for users to connect, using SFTP is a great way to go, and it will allow you to use PAM for authentication, so you can use MySQL, LDAP, or whatever else you want for auth.

If that's not to your liking, you can try using WebDAV with Apache2. If you're trying to setup FTP for web developers, then this is a great alternative, as it allows them to directly edit the files they can then view through their hosted sites. Here's a link to help with that: [http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10](http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10).

I guess to be fair though, if the only thing you want to compare are ProFtpd and VsFtpd, then its really a matter of personal preference. They both use standards, both have decent records as far as security is concerned, both have been around for a while, and they both have a ton of documentation and features. Try them both and let us know which one you choose and why.

---

### Post by lykwydchykyn on 2009-07-16
There's a webmin module for proftpd that comes built-in to webmin.  I believe the vsftpd module is third-party.

I've always used proftpd or pure-ftpd, and been happy with both.

---

### Post by chrisinspace on 2009-07-16
> **scorp123 said:**
> You've already done all research. What do you expect? That we toss a coin for you? :D

Actually, I was hoping maybe you'd just volunteer to come install it for me.  ;) :biggrin:

@scorp123 and giggins,

My goal is to enable users to move one large file (~100MB) a day.  They'll be expecting to use an FTP client.  Will SFTP work for that?  I found these instructions:

[http://blog.markvdb.be/2009/01/sftp-on-ubuntu-and-debian-in-9-easy.html](http://blog.markvdb.be/2009/01/sftp-on-ubuntu-and-debian-in-9-easy.html)

Does that look right?  After it is set up do you just control user access by creating local users on the Ubuntu server?

Once I get the files on the Ubuntu server they have to be read by an application on a Windows machine.  I'm guessing I'll have to set up Samba for that.  Will that open up more security vulnerabilities?

Sorry for the string of questions, but I'm new to Linux server administration.  I don't want to fall back to MS Server just because that's what I know.  I'm trying to use this as an opportunity to pick up some new skills.

---

### Post by chrisinspace on 2009-07-16
> **lykwydchykyn said:**
> There's a webmin module for proftpd that comes built-in to webmin.  I believe the vsftpd module is third-party.

Didn't know that.  Thanks.

---

### Post by scorp123 on 2009-07-17
> **chrisinspace said:**
>   My goal is to enable users to move one large file (~100MB) a day.  They'll be expecting to use an FTP client. Use WinSCP ... it has a easy to use interface and it can use SCP (secure-copy) and SFTP (both "scp" and "sftp" are SSH sub-protocols).

[http://winscp.net/](http://winscp.net/)


If you want a command-line client for Windows (so you could use it in batch jobs), you could use "Putty". It has SCP and SFTP clients (e.g. "pscp.exe"):

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

---

### Post by Vishal Agarwal on 2009-07-17
> **chrisinspace said:**
> 
My goal is to enable users to move one large file (~100MB) a day.  They'll be expecting to use an FTP client.  Will SFTP work for that?  I found these instructions:


I am using VsFtpd, and did not faced any problem. Also it transfers the data at good enough speed. Mostly I am downloading from my Debian server, But a very few times I have uploaded.
With cuteFTP client it gives me access to create/modify my files as logged in user home folder.

---

### Post by zehner on 2009-07-17
If you plan to chroot your users, then its easier to setup a FTP server, than to chroot an instance of the SSH server. ProFTPD and VSFTPD have both an inbuilt feature to chroot your logins.

I have both servers in productive use, both are very stable and secure servers. I prefer ProFTPD, because of its SQL- and LDAP-Features. But on a few RHEL-instances I have VSFTPD running and no problem with it until now

=> It's your choice, think about your needs (SQL, LDAP, ...) and you don't be spoilt for choice :-)

---

### Post by scorp123 on 2009-07-17
> **zehner said:**
> If you plan to chroot your users, then its easier to setup a FTP server, than to chroot an instance of the SSH server. Not true. Just see the link he posted above. You can use mechanisms such as "scponly" so that users could use SCP and SFTP but not login via a shell. And limiting such users to certain directories can easily be achieved via user and file permissions. Or file ACL's if you're like me prefer to use that feature :D

---

### Post by chrisinspace on 2009-07-24
> **giggins said:**
> I guess to be fair though, if the only thing you want to compare are ProFtpd and VsFtpd, then its really a matter of personal preference. They both use standards, both have decent records as far as security is concerned, both have been around for a while, and they both have a ton of documentation and features. Try them both and let us know which one you choose and why.

I had to move quickly on this, so I did decide to go with FTPS.  SSH sounds really interesting and extremely well-suited to many remote-access solutions, but I already had a basic understanding of FTPS and I'm only concerned with file transfer, so I went that route.  I will definitely give SSH a shot in the future when I have more time to research it.  

The main reason I chose FTPS is that I wanted to do local user management and authentication on the FTP server so the LDAP integration wouldn't be that useful to me since the FTP server lives in my DMZ and can't communicate from the DMZ to my internal network.  The internal network can, however, talk to the FTP server in the DMZ.  I specifically chose ProFTP because it has some great user/server security controls and its setup and administration in Ubuntu are really well documented.  I was able to get the server up and running quickly.  The part that took a little more time was securing it with the SSL certificate.  I worked on that issue alone for a full day then stopped, took a deep breath, and did some more research.  I found [this posting]("http://forums.proftpd.org/smf/index.php?action=printpage;topic=3957.0") which solved my problem.  The issue I was having was that the module mod_tls.c wasn't loading so the TLS functionality wasn't enabled.  All I had to do was add:
```
LoadModule mod_tls.c
```to the top of my proftpd.conf file and it worked right away.  This step was not mentioned in any of the tutorials I read, even those specifically talking about enabling SSL/TLS in ProFTPd.  I was surprised because I didn't build it from source, it came out of the Ubuntu repository, so I would think this is a common issue.  Once that was in place, everything worked like a charm.  

Thanks to all of you for your input to this thread.  You have really raised my curiosity about SSH, so I'm going to start looking into that and experimenting with it a bit.

---

### Post by scorp123 on 2009-07-26
> **chrisinspace said:**
> I had to move quickly on this, so I did decide to go with FTPS.  That's like saying: "I am in a hurry, so I'll pick the 60 years old VW Beetle over the brand-new Ferrari Formula-1 car ...."

No insult intended. But let's face it: How many hours did you spend to get FTPS working???  Getting SSH (and therefore SFTP too!) up and running is just a matter of a few minutes. :D

---

### Post by shredkingj on 2009-07-26
I've setup up both, and I'd say both take about the same amount of time...vsftpd has been easy to get running for FTPS and chroot in the past or me.  But I agree, SFTP is the best way to go in nearly every way.

---

### Post by chrisinspace on 2009-07-27
> **scorp123 said:**
> That's like saying: "I am in a hurry, so I'll pick the 60 years old VW Beetle over the brand-new Ferrari Formula-1 car ...."

No insult intended. But let's face it: How many hours did you spend to get FTPS working???  Getting SSH (and therefore SFTP too!) up and running is just a matter of a few minutes. :D

Isn't FTP actually supposed to be faster at moving files?  If I don't need any of the remote access capabilities offered by SSH, then what are its benefits over FTPS?  I'm not trying to argue the point; I'm trying to learn more about SSH.  Now that I have a solution in place, I can take a little time to understand it better.

---

### Post by scorp123 on 2009-07-27
> **chrisinspace said:**
> Isn't FTP actually supposed to be faster at moving files?  This is only valid for pure unencrypted FTP. As the protocol isn't encrypted it has far less overhead than an encrypted connection such as SSH/SCP/SFTP. So yes, unencrypted FTP could be noticeably faster.

But between FTPS and SFTP/SCP I'd doubt you see a lot of a difference. Both use some form of SSL to encrypt their traffic, hence there should be similar overhead.

> **chrisinspace said:**
>  If I don't need any of the remote access capabilities offered by SSH, then what are its benefits over FTPS?  SSH and its sub-protocols are pretty much compliant to any networking standard (IETF, RFC and what not) that you can find and especially firewalls --no matter what brand-- should not have any troubles whatsoever with SSH and its sub-protocols, whether you just wish to transfer files via SCP or SFTP, administrate systems remotely via SSH, mount a server's remote filesystems via SSHFS or use SSH's extensive tunnelling capabilities --- it should all just work. With any firewall. Period. SSH server software such as OpenSSH is constantly being improved and I am not aware of any serious security issue that would currently exist for the current incarnation of the SSH protocol.

FTPS however is a dirty dirty hack: you put a complicated SSL layer over an already complicated and outdated and highly insecure two-way protocol that already without that hack had plenty of troubles of its own. It may work or it may not work with your firewall, with your business partner's firewall, with their client software .... In other words --and this has already been pointed out to you-- FTPS is prone to having troubles. Good luck troubleshooting that if it ever misbehaves.


Stuff you might want to read:

[http://en.wikipedia.org/wiki/SSHFS](http://en.wikipedia.org/wiki/SSHFS)
[http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html](http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html)

---

### Post by hessiess on 2009-07-27
Amusing your 100~ meg file is a single file, and slowly changes over time using a protocol which supports delta uploading such as RSync, Unison or any of the recent version control systems would be substantially faster than re-uploading the entire file every time.

If you are ever stuck inside a network, which only has ports 80 and 443 available, with 80 proxied and filtered you will see just how bad FTP is, tunnelling SSH, and thus sftp over port 443 is relativity easy, but as FTP runs on multiple ports, it is not easy to tunnel. Though in the above situation the best option is WebDAV or Subversion over WebDAV, the latter is faster as it does delta transfers.

---

### Post by chrisinspace on 2009-07-27
Well, thanks to all of you. I've learned a lot.

---

### Post by scorp123 on 2009-07-28
> **hessiess said:**
> Amusing your 100~ meg file is a single file, and slowly changes over time using a protocol which supports delta uploading such as RSync, Unison or any of the recent version control systems would be substantially faster than re-uploading the entire file every time. Fully agree to that. Let's take "rsync" for example: it "just works" with SSH. In my example I will assume that the SSH server is listening on port 2222 (instead of the standard port 22).

So instead of using SCP every time to copy a 100 MB file in full ...
```
scp -P 2222 -r /path/to/local/file user@server:/path/to/remote/location
``` ... one could simply use rsync to transfer just the deltas:
```
rsync -e "ssh -p 2222" -a -v /path/to/local/file user@server:/path/to/remote/location

```

(... I hope I got the syntax right :D ... )

---

### Post by alecz20 on 2010-06-03
The only reason I wanted to set up a FTP server was to share a folder with some users without letting them see the whole filesystem.

Some people here suggested setting permissions on the filesystem, but I really doubt it is a good idea to alter the default permissions.

Other have mentioned chroot. But from what I saw in a few guides:
```

http://www.howtoforge.com/chrooted_ssh_howto_debian_p2

```
it seems that it involves creating scripts, and users, and putting . in their home address.

A lot of hassle when I actually want to share a directory such as "/home/share" without them being able to go higher than that.

If you guys no any simple and clean solution for chroot and SSH, then I would say that FTP is obsolete, but until then... I am still looking for the FTP server that does this easily.

---

### Post by TechZilla on 2012-07-21
SFTP is great, no question about it, but it does not replace FTP over SSL verbatim.

First, to get an FTP like setup, where the user root / directory, is not the server root / directory.  You must chroot, this is not trivial by any means, except when running OpenSSH &#8805; 4.9p1. Which at the time of the OP, was far from default.  Today it's another story, with distributions providing OpenSSH &#8805; 5.0.  Ubuntu has always provided fairly recent software releases, but that's one of it's unique selling points, not something common to most distributions.  

Secondly SFTP is the obvious choice, for admins who already have system accounts.  When dealing with developers, you would not want every user transferring files to have an actual system account. You could work around this, with something via PAM, etc....   Although at that point, SFTP losses it's Transparent user configuration.  You would have to get granular, groups for developers, groups for systems admins, possibly even groups for vendors.

As far as what I recommend, which is also what I normally implement, SFTP for Systems Admin's and FTP for others. If you normally have a system account, than SFTP is acceptable, otherwise it's a new FTP Account.  This situation might change, hopefully one day it will, especially due to OpenSSH feature improvements. 

Regarding which FTP server?
Pure-FTPd, performance and security.

Regarding Encryption?
Require Explicit FTP over SSL.

If you need some feature which Pure-FTPd does not provide, go ProFTPd.  Although that would be a last choice option, as Pure-FTPd is really my primary FTP server.

---

### Post by chrisinspace on 2012-08-24
Wow...cool to see this thread is still alive and generating some discussion.  Since the time I originally posted my question, I have become much more familiar with SFTP, but I still haven't replaced my ProFTPd installation.  It works great for what I intended.  The comments about developers maintaining files or using rsync to upload the deltas don't reply to my scenario.  I have clients that send me a new unique files every day.  ProFTPd has worked really well.  It's easy to administer the users and keep them isolated in their home directories.  I was able to apply my Digicert SSL certificate.  It has nice logs showing when users connect and when they transfer files.  All in all, I've been very happy and would recommend it in that specific circumstance.  I've also set up SFTP on a personal server for the use of me and a few of my friends.  It's been fantastic, too.  It was very simple to get going and it's been very reliable.  My friends have no problem connecting to it using Filezilla.  

Thanks to scorp123 and the other posters on this thread, I was able to find the right solution to my original issue and learn a lot about other solutions. I hope others find this thread as useful as it was for me.

---

### Post by aerokid240 on 2013-03-08
Ain't nothing wrong with using FTPS (once you get it working nicely with your firewall). Try both SFTP and ftps (vsftpd or pro-ftpd) and which ever one looks like the least amount of hassle to maintain for you then that might be the winner. I wont say there is a substantial enough reason to shy you away from using FTPs. I would say, for alot of users (that require their own login, but not shell access), i would prefer to use vsftpd or proftpd with virtual users as it has been far easier to setup for me.

---

