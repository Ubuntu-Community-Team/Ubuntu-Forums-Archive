---
title: "Can't get Samba to work on new server"
date: 2009-11-23
forum: Server Platforms
---

### Post by grandsatrap on 2009-11-23
Hi,
I am completely unable to get SAMBA working on my newly installed Ubuntu 9.04 server (called Ajax) at 192.168.1.13. It is running Samba 3.0.28a  (the latest one). The part that is not working is accessing it from Windows XP.

I have an old server (called Hector) that is running Ubuntu 7.04 at 192.168.1.11. It is running SAMBA version 3.0.24  [I want to switch to my faster new server.]

I have no problem connecting to my music share on Hector:  "\\192.168.1.11\music" (I have a different username from my Windows login name: alpha).

I have set the new server to be as similar to the old one as possible. Windows XP does not see Ajax at all. Not when I type in \\192.168.1.13\music , nor when I type in smb://192.168.1.13 nor when I go through the entire network and look at Microsoft Windows Network.

From Hector I can type: smbclient \\\\192.168.1.13\\music -U alpha   and I can connect to the share no problem. So the share is working -- but only for Ubuntu!!!

From my Windows computer, I can ping 192.168.1.13 so it is able to communicate with it.
All three computers are part of the same workgroup. 
(Note: so is my laptop, it can too connect to Hector, but not Ajax.)
---------------------------------------------------------------

```
#This is a list of all commands entered to configure the system so far:

sudo apt-get update

#Install WebMin. Download the file below, and then ...
sudo dpkg --install webmin_1.490_all.deb
sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

#sudo vi /etc/hosts.allow /etc/hosts.deny

#install squid
sudo apt-get install squid

#fix up SSH
sudo vi /etc/ssh/sshd_config
sudo /etc/init.d/ssh restart

#fix up squid
sudo vi /etc/squid/squid.conf
#set up squid passwords -- I forget how
sudo /etc/init.d/squid reload

#fix up samba
sudo vi /etc/samba/smb.conf
sudo testparm /etc/samba/smb.conf
touch /etc/samba/smbpasswd
chmod 644 smbpasswd
smbpasswd -a alpha
sudo /etc/init.d/samba restart
smbclient -L ajax

#add user alpha & password to Ubuntu
sudo adduser alpha
 
#make music folder and set permissions (this is the folder pointed to in smb.conf)
sudo mkdir /home/music
sudo chown /home/music alpha
sudo chgrp /home/music users
sudo chmod g+w /home/music

```
--------------------------------------------
Should I add my complete smb.conf file too?

Please help!
Thanks.

---

### Post by Blond_Knight on 2009-11-23
Ive had issues setting up samba in the past.  It can be frustrating, dont worry you'll get it.
A stab in the dark, did you restart samba once you created the folder?
Are you running a firewall or something in iptables?

---

### Post by grandsatrap on 2009-11-23
Yes, I have repeately tried tweaking smb.conf and restarting Samba, rebooting the computer, etc. I haven't used IP tables on either computer, just hosts.allow/deny.  Unless there was something I did long ago on the old server that got Samba working and I can't remember it anymore. It doesn't make sense to me.

Note: I can SSH to all computers in my LAN without a problem.

---

### Post by Blond_Knight on 2009-11-23
Do you get prompted for authentication when you try to connect from the windows box? 
Have you checked the connections on your windows box? Maybe trying removing the connection to the new linux box, 
> net use \\192.168.1.13\music /delete

---

### Post by Denbert on 2009-11-23
> **grandsatrap said:**
> 
Should I add my complete smb.conf file too?

Please help!
Thanks.

the smb.conf file is always interesting to see, but for a fast samba setup try this fantastic howto:

[http://www.howtoforge.com/ubuntu-8.10-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-8.10-samba-standalone-server-with-tdbsam-backend)

Has always done the job for me :lolflag:

p.s. in order to give root access do this:

```
sudo passwd root
```

---

### Post by grandsatrap on 2009-11-23
MEA CULPA ? No. A mystery unsolved.

For the first time, today I actually saw my new server (192.168.1.13) show up on my "Microsoft Windows Network". There were still no shares accessible. I then disabled my firewall, and bingo! I can now connect to my new ubuntu server. 

This is really weird. I am sure that I checked my Zonealarm settings thoroughly. On my desktop I didn't include 192.168.1.13 in my trusted zone. However... it was included on my laptop's trusted zone. So why did my laptop not work?

Does it take a day or two for things to propagate between 3 computers in one building??

Now, my old server still shows up as the MASTER for the workgroup when I type "smbclient -L . -N" I wonder what will happen when the old server no longer exists.

**It's working now, but I don't know why. Thanks everyone.**

---

