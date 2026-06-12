---
title: "yppasswd not working on NIS client"
date: 2006-07-31
forum: Server Platforms
---

### Post by anindya_m on 2006-07-31
Hi,
    I am trying to use nis to authenticate users. Logins are working fine. If I run yppasswd on the server I can change passwords. But on the nis client I get the error:

yppasswd: yppasswdd not running on NIS master host ("localhost.localdomain")

but everything else works fine. My question is: why is yppasswd reading localhost.localdomain as the server name while everything else (ypbind, ypwhich, etc.) correctly gets the nis server? Is there any file other than yp.conf and nsswitch.conf which I need to edit?

Thanks in advance for any help.

---

### Post by anindya_m on 2006-07-31
Sorry to post on my own topic but I found the error. I had deleted the ypservers map by mistake (so stupid of me :-x ). I generated it manually with make and now everything is fine.

---

### Post by knichel on 2007-09-17
I am having a similar issue.  Can you tell me what you did to correct this?  I just installed NIS and the users cannot change their passwords using yppasswd.

Thanks.

---

### Post by anindya_m on 2008-01-10
I had mistakenly run make before running ypinit -m (I know, very bad for a sysad :)). You just need to run the ypinit script first and then make. It should work fine. Please also have  a look at [[COLOR="Blue"]this[/COLOR]]("https://help.ubuntu.com/community/SettingUpNISHowTo") page.

---

### Post by knichel on 2008-01-10
Do you mean
 
#cd /usr/lib/yp
#make
#ypinit -m

Why make?

--
Thanks

---

### Post by anindya_m on 2008-02-16
The make command is necessary to build the initial yp databases, and also later to update them. The usual procedure is to run ypinit, then make. Hope this helps.

---

### Post by rome-NY on 2008-02-20
As I remember you have to modify one the etc files on the server that allows you to change the passwords from the client. Out of the box the nis server doesn't allow changing the passwords from clients. If I want to change a password for someone I remote into the server and use yast to change user info.

---

### Post by anindya_m on 2008-02-20
On the server, the Makefile in the /var/yp directory has to be edited to point to the location of the passwd file (in /etc/ or in some other directory). You also need to set up proper access control. It is true that some of the yp related config files need to be edited to set up things, but that's part of the routine setup for NIS.

If all this is done correctly, then yppasswd will allow a normal user to change his/her own password from any client. I have not faced any problem in the many networks I have configured. It helps to have the same distro on the client and server, but it is not necessary. Works even across OS's; for example I have IRIX and Solaris clients connected to a linux server.

When changing a user's password as root, I usually log into the server and use yppasswd from there. I have to enter the root/admin password once again in this case.

---

### Post by rome-NY on 2008-02-25
how did you get nis on the client to work? If I ypcat passw.byname i get my passwd file so I think I have everything OK. I even nfs'd my home files and the login screen shows the users from the nis server. But when i select a user and enter a password for the login screen it says login failed. I'm really close but I have followed everything that I have read from the how-tos. Is there something that isn't documented that I might have missed?

---

### Post by anindya_m on 2008-02-25
Okay many people seem to have a problem with NIS so I will just describe briefly how I configure it on Linux/Ubuntu. Please ask questions if something is not clear. Also [_[COLOR="Blue"]this[/COLOR]_]("https://help.ubuntu.com/community/SettingUpNISHowTo") page has a good general description, so please go through it.

First, the server: 

We will assume here the NIS domain is called "buffy".

1. First file to edit is /etc/ypserv.conf. I uncomment the two lines related to mangling passwords so ypcat does not dump the passwords (still not secure enough though):
```

*                          : *       : passwd.byname    : port/mangle       
*                          : *       : passwd.byuid     : port/mangle

```

2. Next edit the file /etc/yp.conf. Note that the server is also a client in my case, so these steps are necessary. Let us assume that the server is called giles.sunnydale.net. So we need to add a line at the end of this file:
```

ypserver giles.sunnydale.net

```

3. The file /etc/defaultdomain has to exist on the system; it contains the name of the NIS domain name. So in our case the contents will be:
/etc/defaultdomain contents
```

buffy

```

4. We must now tell the system that it should search the yp maps for login, and it should do it only if it does not find the username on the local system. The file is /etc/nsswitch.conf. Here's what mine looks like (comments removed):
/etc/nsswitch.conf contents
```

passwd:         compat nis
group:          compat nis
shadow:         compat nis

hosts:          files wins dns
networks:       files

protocols:      db files nis
services:       db files nis
ethers:         db files nis
rpc:            db files nis

netgroup:       nis

```

5. On Ubuntu some config options are set in /etc/default/nis. On the  server machine you only need to change the following line:
```

NISSERVER=master

```

6. Next, /var/yp/Makefile. I have several customizations here because on my old system I had login, nfs, netgroups and some other stuff using NIS. For now however, we need to change only the default GID's, otherwise the group memberships for system groups (e.g., audio, plugdev, etc.) are not exported correctly. On my system UID's for normal users start from 1001, so I have made the following changes:
```

MINUID=1000  ->  MINUID=1001
MINGID=1000  ->  MINGID=20

```
Please double check this on your system so that you don't export any unnecessary groups (like root, for example). I am assuming here that the NIS user accounts will be in the server's /etc/passwd. Otherwise you will need to change the Makefile to point to a custom directory.

7. Okay now we can init the server, and restart services:
```

sudo ypinit -m
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nis restart

```

The client:
Repeat steps 2-4 on the client. Then execute step 7 without the ypinit command. Note that most login services (gdm, sshd, etc) will need to be restarted to use NIS.

This should get NIS up and running. Add users normally on the server, then run
```

sudo make -C /var/yp

```
to propagate the changes to the clients. yppasswd should allow any normal user to change his/her password from anywhere. To change passwords as root, login to the server and run yppasswd as root.

Some more tuneups are possible, but there are good sources on the net for that  :wink:

---

### Post by knichel on 2008-02-26
Thanks for the update.  I tried eveything you posted and still get an error on the client saying that yppasswdd not running on master server... but
on the server....
admin@Server:~$ ps aux | grep yppasswdd
root      8154  0.0  0.0   1952   428 ?        S    12:08   0:00 /usr/sbin/rpc.yppasswdd -D /etc -e chsh

SO, still at a loss...

---

### Post by anindya_m on 2008-02-26
yppasswd still reports the server as "localhost.localdomain" yes? Okay. Can you please check your /var/yp/youryp directory, whre youryp is the NIS domain name. There should be a file called ypservers. This file is created by the ypinit -m command on the server. It is necessary for yppasswd to work correctly.

Another thing to check is your /etc/hosts file. Frequently on Ubuntu systems I have seen the following mistake (set up by the installer).
Assume that the fully qualified host name is giles.sunnyvale.net and it has ip 192.168.0.1. The correct /etc/hosts entry should be (listing the relevant parts only):
```

127.0.0.1     localhost.localdomain     localhost
192.168.0.1   giles.sunnyvale.net       giles

```
and *not*
```

127.0.0.1     localhost.localdomain     giles
192.168.0.1   giles.sunnyvale.net       giles

```
i.e., the localhost line should not contain any reference to the actual hostname.

Please also check if you are able to use yppasswd  on the server as a normal user. You will know it's fixed if it reports the actual hostname of the master server and not "localhost.localdomain".

---

### Post by knichel on 2008-02-27
OK, I have ypserver file in my /var/yp/mydomainname.
My /etc/hosts file is as you suggest
I can run yppasswd on the server and it reports the domain name as it should.

SO, I am wondering if it is a firewall issue?  What port should I have open?  Does yppasswd run as tcp or udp?  I allow all tcp to traffic destined for the server.

Again, thanks for the assistance.

Mike

---

### Post by anindya_m on 2008-02-27
Hi, it may be a firewall issue. By default the NIS servers (yppasswdd included) will use a random UDP port below 1024 (you can check this with the command  rpcinfo -p). So just for a test you may temporarily allow all UDP traffic through your firewall. See if that works. If this works then you can change the NIS startup scripts and configure the daemons to bind to a static port, and then allow connections to only those ports through your firewall. Actually I am using such a setup, but I skipped that in my update for simplicity.

---

