---
title: "Active Directory Domain Integration"
date: 2010-05-13
forum: Server Platforms
---

### Post by btrichardson on 2010-05-13
Hello All,

The company I work for, as usual, is Microsoft-centric. I'm attempting to integrate my Ubuntu server into the domain to allow domain users to authenticate to the server and access file shares using Samba. Here's my current configuration:

```

Ubuntu Server 9.10
Single local account that is NOT a domain account (I use public-private SSH keys to access the account remotely)
Currently part of the Active Directory domain (domain admin pushed server onto account, wbinfo -u and -g correctly list domain users and groups)
Kerberos installed and configured (kinit <domain-user> successfully acquires kerberos ticket)
Samba installed and (I think) configured to use kerberos and winbind

```

I can see and interact with the domain using wbinfo, and I can generate kerberos tickets for valid domain users. The problem I'm having is authenticating domain users without having to have a local machine account.

When I try to map a Samba share on the Ubuntu server from a Windows machine using a domain account, I get an error in /var/log/samba/<windows-machine-name>.log that says "Username <domain-user> is invalid on this system". I temporarily created a local user with the username <domain-user> and I was then able to successfully map a network drive from a Windows machine.

I logged onto a Red Hat Enterprise Linux server that is correctly configured for the domain, and when I ran "id <domain-user>" it listed my domain account and groups correctly. However, when I run "id <domain-user>" from my Ubuntu server I get "id: <domain-user>: No such user". The Red Hat Enterprise Linux server has a Samba configuration exactly like the one that's on my Ubuntu server, so I can only assume the configuration I'm using is correct.

I assume it has something to do with my PAM configuration files, but I don't know enough about PAM to successfully get things working. I even considered configuring the PAM modules on my Ubuntu server similarly to the PAM modules on the Red Hat Enterprise Linux server but decided against it. I'm leary of doing too much with the PAM configs without knowing more about it because I do know enough to know that I could end up locking my local machine account. As such, I have not attempted to run "pam-auth-update" or configure the PAM modules according to [this guide]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto").

Ultimately I'd like to have the Ubuntu server configured to where my administrator account stays a local machine account and domain users can access Samba shares using their domain username and password without having to have local accounts on the server. It looks to me like the guide I linked to above could lead to that type of configuration, but I'd like to know a little more about the PAM configuration options before using them.

Would anyone be interested in walking me through how PAM works and helping me to understand how I can get my Ubuntu server configured like I want? I'd really appreciate it! :)

--
Thanks!
Bryan

---

### Post by windependence on 2010-05-14
Unfortunately, distros like Red Hat and SuSE have much better Micro$oft support than Ubuntu does. There are many reasons for this, some have to do with software patent agreements with SuSE and some other proprietary software. If I was going to convince management to integrate Linux and Windows, I hate to say it but Ubuntu would not be my first choice. I wish you well in your endeavor, but I think you have a long hard road ahead of you.

-Tim

---

### Post by HermanAB on 2010-05-14
This may help:
[http://www.aeronetworks.ca/LinuxActiveDirectory.html](http://www.aeronetworks.ca/LinuxActiveDirectory.html)

That guide dates back to way before yoincs, when the Mandriva and Red Hat wizards still did not work with ADS - pretty much the situation Ubuntu is still in.

Good Luck!

---

### Post by btrichardson on 2010-05-14
Thanks for the link Herman. That's pretty much what I've done already, but to no avail. :(

Tim, while I get your point and understand the relationship Microsoft has with Red Hat, it seems to me that, with what I have working, it is an Ubuntu thing and not a connection-to-Microsoft thing. If I can see domain users with the wbinfo command, that tells me the Ubuntu server is successfully talking to Active Directory. So wouldn't the utilization of that successful communication be on the Ubuntu side? If I have /etc/nsswitch.conf configured to use winbind for hosts and groups, shouldn't the "id" command be seeing the domain users too?

/etc/nsswitch.conf
```

passwd:         compat winbind
group:          compat winbind
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

Thanks to both of you for responding!

--
Bryan

---

### Post by HermanAB on 2010-05-14
It won't help much asking questions here - you won't get meaningful answers.

You need to test your system systematically:
Is the time the same as the server?
Can you join the domain?
Does Kerberos work?
Can you see users?
Can you see groups?
Can you authenticate?
Can PAM make a home directory?

and you have to debug each level before proceeding to the next.  Just jumping to the end and then wondering why it doesn't work, won't get you anywhere.

---

### Post by btrichardson on 2010-05-14
Thanks again Herman for responding. I am aware that jumping to the end then wondering why it doesn't work won't get me anywhere. I've worked with enough open source software to have learned my lesson. :)

That's why, as I tried to explain in my first post (obviously not very well), I have tested my configuration systematically. Here's my answers to your questions:

Is the time the same as the server?

Yes, I'm using the same NTP server as the Kerberos and Active Directory servers and the time on my server is updated twice a day with ntpdate.

Can you join the domain?

Yes, I am currently on the domain. A domain administrator added my server to the domain and verified that it had joined.

Does Kerberos work?

Yes, I can get a kerberos ticket with kinit using my domain username.

Can you see users?

I can see domain users via "wbinfo -u", but not via "getent passwd".

Can you see groups?

I can see domain groups via "wbinfo -g", but not via "getent group".

Can you authenticate?

In terms of connecting to a Samba share using a domain username, no I cannot. The error I get in the Samba logs is "Username <domain-user> is invalid on this system". Executing "id <domain-user>" also returns "id: <domain-user>: No such user".

Can PAM make a home directory?

I don't have PAM configured to do so because I don't want directories created for each domain user when they log into the server. I'm mainly only wanting to support Active Directory domain authentication to manage access to existing Samba shares.

Does this help at all?

--
Thanks again!
Bryan

---

### Post by capscrew on 2010-05-14
> **btrichardson said:**
> ...

Can you see users?

I can see domain users via "wbinfo -u", [COLOR="Red"]**but not via "getent passwd"**[/COLOR].

Can you see groups?

I can see domain groups via "wbinfo -g", [COLOR="red"]**but not via "getent group"**[/COLOR].

...

Can PAM make a home directory?

I don't have PAM configured to do so because I don't want directories created for each domain user when they log into the server. I'm mainly only wanting to support Active Directory domain authentication to manage access to existing Samba shares.

Does this help at all?

--
Thanks again!
Bryan

The getent sets off all kinds of red flags and you need PAM configured for AD.  See [**_here_**]("http://wiki.samba.org/index.php/Samba_%26_Active_Directory"), specifically the "Setting up PAM Authentication for Active Directory." section.

---

### Post by koenn on 2010-05-15
yes, the getent problem is suspect.

I suggest you try nsswitch.conf without the compat, just to see what gives,
eg something like this
```

	passwd:     files winbind
	shadow:     files 
	group:      files winbind

```

---

### Post by iversonm on 2010-05-16
[Likewise open]("http://www.likewise.com/products/likewise_open/") is a fairly straightforward package to setup and use for this purpose.

---

### Post by gmoore777 on 2010-07-16
although what iverson said may have been true for HardyHeron,
likewise-open does NOT support SAMBA shares in LucidLynx.
Hence I was forced to get everything working via default
installations of winbind and samba.

I have everything working fine on LucidLynx except
I also have the issue of `getent passwd` and `getent group` only
showing local users and groups. 
(I have this same problem on my HardyHeron installations and they are using Likewise-Open)
This hasn't been a problem so far in regards to users logging in
and accessing Samba shares that they own.
(but I think in a couple of weird problems that I have encountered over the past 6 months, I think this getent problem may be the source of the problem. Hence why I stumbled upon this posting.)

---

### Post by capscrew on 2010-07-16
> **gmoore777 said:**
> although what iverson said may have been true for HardyHeron,
likewise-open does NOT support SAMBA shares in LucidLynx.
Hence I was forced to get everything working via default
installations of winbind and samba.

I have everything working fine on LucidLynx except
I also have the issue of `getent passwd` and `getent group` only
showing local users and groups. 
(I have this same problem on my HardyHeron installations and they are using Likewise-Open)
This hasn't been a problem so far in regards to users logging in
and accessing Samba shares that they own.
(but I think in a couple of weird problems that I have encountered over the past 6 months, I think this getent problem may be the source of the problem. Hence why I stumbled upon this posting.)

I believe the situation is really a Samba/Kerbros/AD integration problem.  Not a Ubuntu specific for *"getent"*.  I think if you add the developer packages you can view the man pages.```
man getent
```  Or you can use ***strace ***to follow what calls are made.

---

### Post by gmoore777 on 2010-07-16
well, i just got `getent passwd` and `getent group` to give me
the ActiveDirectory results as well.
I uncommented out these 2 entries in /etc/samba/smb.conf:

   winbind enum groups = yes
   winbind enum users = yes

They are commented out by default.

`getent group` took 10s of seconds to finish. So I can see why
they warn you about turning these entries on in the smb.conf.
(some subsequent calls returned immediately, some stuttered through it.)

Thanks for the tip. i ran `strace getent passwd`. I saw it open 
/lib/libnss_winbind.so.2 so I knew it was reading the nsswitch.conf correctly, but just not getting any information from winbind. (and then I thought about the smb.conf file and what windbind related parameters I could change.)

---

### Post by capscrew on 2010-07-16
> **gmoore777 said:**
> well, i just got `getent passwd` and `getent group` to give me
the ActiveDirectory results as well.
I uncommented out these 2 entries in /etc/samba/smb.conf:

   winbind enum groups = yes
   winbind enum users = yes

They are commented out by default.

`getent group` took 10s of seconds to finish. So I can see why
they warn you about turning these entries on in the smb.conf.
(some subsequent calls returned immediately, some stuttered through it.)

Thanks for the tip. i ran `strace getent passwd`. I saw it open 
/lib/libnss_winbind.so.2 so I knew it was reading the nsswitch.conf correctly, but just not getting any information from winbind. (and then I thought about the smb.conf file and what windbind related parameters I could change.)

I was looking at [**_this_**]("http://www.linuxquestions.org/questions/linux-networking-3/samba-problem-getent-differs-from-wbinfo-493615/")earlier and it has roughly the same answer in the last post.

[COLOR="Teal"]**Edit**[/COLOR]: You could try limiting the range of UID/GID for a bit more speed.  But in the end, once the database is slurped up you should be okay.
Glad you solved the puzzle.  :D

---

### Post by atworkwithjf on 2010-10-12
> **gmoore777 said:**
> although what iverson said may have been true for HardyHeron,
likewise-open does NOT support SAMBA shares in LucidLynx.
Hence I was forced to get everything working via default
installations of winbind and samba.

I have everything working fine on LucidLynx except
I also have the issue of `getent passwd` and `getent group` only
showing local users and groups. 
(I have this same problem on my HardyHeron installations and they are using Likewise-Open)
This hasn't been a problem so far in regards to users logging in
and accessing Samba shares that they own.
(but I think in a couple of weird problems that I have encountered over the past 6 months, I think this getent problem may be the source of the problem. Hence why I stumbled upon this posting.)

Just following up with you on this issue.  I'm curious if you are using the distro based Likewwise-Open package (via apt-get in the Ubuntu distro) or using the updated version directly from Likewise (version 6.0).

There have been a large number of fixes in 6.0 and if you're not using 6.0 I'd strongly si=uggest you upgrade.

---

### Post by gmoore777 on 2010-10-12
no, not using any Likewise on our LucidLynx machines cause Likewise didn't support Samba shares.(and now it doesn't matter if they do, cause I don't see what value-add Likewise provides.)

---

