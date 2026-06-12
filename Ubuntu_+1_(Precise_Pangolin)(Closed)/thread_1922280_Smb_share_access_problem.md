---
title: "Smb share access problem"
date: 2012-02-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by calanor on 2012-02-08
Hi,

I am not able to access smb shared drives from nautilus, whereas the same drive opens under kubuntu in dolphin. This problem has been going on from ubuntu 11.04 (didn't try on earlier versions). In 11.04 it showed some free desktop error message. In ubuntu 12.04 it just keeps asking for password again and again. Sorry for providing no details, I don't know how to find any additional info to help point the problem. Any help is highly appreciated.

---

### Post by effenberg0x0 on 2012-02-08
I am using samba and NFS in my PP machines to access my home PP server normally. Windows and android devices can access it too. It has been working non-stop since Oneiric Alpha (previously the server was running Maverick and machines had different versions - now it's all aligned). 

I think this is not related at all to PP. But lets investigate it.
**On the server:**
- Make sure you have samba-related packages installed:
```
sudo apt-get install --reinstall samba samba-common
```- The server must have a valid hostname
```
$ sudo cat /etc/hostname
SOMENAME

```- And the server firewall should be opened to connections from the clients in your LAN. The ports are:
```
$ grep -i netbios /etc/services
netbios-ns    137/tcp                # NETBIOS Name Service
netbios-ns    137/udp
netbios-dgm    138/tcp                # NETBIOS Datagram Service
netbios-dgm    138/udp
netbios-ssn    139/tcp                # NETBIOS session service
netbios-ssn    139/udp

```- So check that UFW is active and has this ports opened
```
sudo service ufw status
To                         Action      From
--                         ------      ----
137                        ALLOW       192.168.1.0/24
138                        ALLOW       192.168.1.0/24
139                        ALLOW       192.168.1.0/24
```- Make sure samba is running:
```
$ ps ax | grep -i smb
 1248 ?        Ss     0:00 smbd -F
 1323 ?        S      0:00 smbd -F
$ sudo service smbd status
[sudo] password for ahsl: 
smbd start/running, process 1248

```- Make sure you have a valid samba config in /etc/samba/smb.conf (the file is pretty much self explanatory and there are tutorials for it all over the net).
```
$ sudo nano /etc/samba/smb.conf
```- Also check if you have valid names inside /etc/samba/smbusers
```
$ sudo nano /etc/samba/smbusers
```- You'll most likely need nmbd to be running too:
```
$ ps ax | grep nmbd
 1529 ?        Ss     0:01 nmbd -D
15825 pts/0    S+     0:00 grep --color=auto nmbd
$ sudo service nmbd status
nmbd start/running, process 1529

```**On the client machines:**
- Make sure you have samba-related packages installed:
```
sudo apt-get install --reinstall samba-common
```- Ping the server IP address.
```
$ ping -c 3 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
64 bytes from 192.168.1.3: icmp_req=1 ttl=64 time=0.331 ms
64 bytes from 192.168.1.3: icmp_req=2 ttl=64 time=0.224 ms
64 bytes from 192.168.1.3: icmp_req=3 ttl=64 time=0.200 ms

--- 192.168.1.3 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.200/0.251/0.331/0.059 ms
```- Also try to ping using the server hostname. In my case, my SMB server is named HOME-OFFICE. So:
```
$ ping -c 3 home-office
PING HOME-OFFICE (192.168.1.3) 56(84) bytes of data.
64 bytes from HOME-OFFICE (192.168.1.3): icmp_req=1 ttl=64 time=0.224 ms
64 bytes from HOME-OFFICE (192.168.1.3): icmp_req=2 ttl=64 time=0.308 ms
64 bytes from HOME-OFFICE (192.168.1.3): icmp_req=3 ttl=64 time=0.308 ms
--- HOME-OFFICE ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.224/0.280/0.308/0.039 ms
```- If you have set security=user on the server smb.conf, you will need to create a password for each user:
```
$ sudo smbpasswd -r YourServerHostNameHere eachloginhere
Old SMB password:
New SMB password:
Retype new SMB password:
Password changed for user ahsl on home-office.
```- Users should be on the smb group sambashare:
```
$ id ahsl
uid=1000(ahsl) gid=1000(ahsl) groups=1000(ahsl),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),**123(sambashare)**,1003(media-daemons)
```If you successfully set all of this and still can't access the smb shared via Ubuntu and Windows Clients, check:
- That you don't have your router filtering packets on the LAN side.
- That you don't have two samba servers on the LAN
- That your smb.conf in the server is really correct
- The smb shares in the server are read/write for the smbusers
- Client-side firewalls are not blocking outgoing packets or incoming packets from the server IP
- Grep Server-side logs (/var/log/*) for samba/smb/nmbd related messages.
- Grep Client-side logs (/var/log/*) for samba/smb/nmbd related messages.
Example for grepping logs:
```
sudo grep -inHr "samba" /var/log/* -R
```
Regards,
Effenberg

---

### Post by calanor on 2012-02-09
Hi,

Thanks for your informative reply. I do not have control over the servers. Its a corporate environment, windows users have access to that folder, so do I, if I use KDE (dolphin). But nautilus just keeps asking for password. Of course the server is reachable as I am getting the password prompt. Its something else, related to GNOME I think.

I am a member of sambashare group. There are no logs in /var/log/samba.

---

### Post by dcstar on 2012-02-13
> **calanor said:**
> Hi,

I am not able to access smb shared drives from nautilus, whereas the same drive opens under kubuntu in dolphin. This problem has been going on from ubuntu 11.04 (didn't try on earlier versions). In 11.04 it showed some free desktop error message. In ubuntu 12.04 it just keeps asking for password again and again. Sorry for providing no details, I don't know how to find any additional info to help point the problem. Any help is highly appreciated.

See if anything is in the auth.log file when you try to connect.

---

### Post by cariboo on 2012-02-13
I saw this in a bug report #[lpbug]510059[/lpbug]:

> in /etc/samba/smb.conf add the following to the bottom of the [global]
section:

client lanman auth = yes
client ntlmv2 auth = no

See if that helps.

---

### Post by snivek on 2012-02-17
I am having the same problem.  Nautilus keeps asking for a password when trying to authenticate to a CIFS/SMB share.  This only started to occur when I upgraded to 12.04.

---

### Post by calanor on 2012-02-20
I solved all my problems by using the smb.conf file from OpenSuse 12.1 install. Now I can open all the shares without any problems.

/etc/samba/smb.conf
```
# smb.conf is the main Samba configuration file. You find a full commented
# version at /usr/share/doc/packages/samba/examples/smb.conf.SUSE if the
# samba-doc package is installed.
# Date: 2011-11-02
[global]
	workgroup = eapac
	passdb backend = tdbsam
	printing = cups
	printcap name = cups
	printcap cache time = 750
	cups options = raw
	map to guest = Bad User
	include = /etc/samba/dhcp.conf
	logon path = \\%L\profiles\.msprofile
	logon home = \\%L\%U\.9xprofile
	logon drive = P:
	usershare allow guests = No
	security = domain
[homes]
	comment = Home Directories
	valid users = %S, %D%w%S
	browseable = No
	read only = No
	inherit acls = Yes
[profiles]
	comment = Network Profiles Service
	path = %H
	read only = No
	store dos attributes = Yes
	create mask = 0600
	directory mask = 0700
[users]
	comment = All users
	path = /home
	read only = No
	inherit acls = Yes
	veto files = /aquota.user/groups/shares/
[groups]
	comment = All groups
	path = /home/groups
	read only = No
	inherit acls = Yes
[printers]
	comment = All Printers
	path = /var/tmp
	printable = Yes
	create mask = 0600
	browseable = No
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/drivers
	write list = @ntadmin root
	force group = ntadmin
	create mask = 0664
	directory mask = 0775
```

---

### Post by calanor on 2012-02-20
Thanks for your help, everyone :)

---

### Post by jerrylamos on 2012-02-20
Lucid Lynx 10.04 no problem with network sharing.  Well, a few learning bumps.

Since then with "Unity" style Narwhal, Ocelot, Pangolin I have to fiddle with this and that and try this and that on every install to get it going. Sometimes. I finally did google to:

[https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)

which got this mini.iso Lubuntu going.  It's side by side with a "Unity" netbook, did the same things.  This Lubuntu 12.04  can network the Unity Ubuntu 12.04 but not the other way around yet.....

Jerry

---

### Post by calanor on 2012-02-21
From what I understand, Unity has no relation whatsoever to accessing network drives. Its nautilus accessing shares via smbclient, both packages have no unity dependency.

---

### Post by joshiss on 2012-03-06
> **cariboo907 said:**
> i saw this in a bug report #[lpbug]510059[/lpbug]:



See if that helps.
thanks for the help this solved my problem in 12.04 beta 1

---

### Post by d97ulf on 2012-03-08
This also worked for me. However, on of the accounts it did not work and after some investigation I noticed that there was a .smb directory in the account's home directory containing an smb.conf file with the wrong settings. After removing the .smb directory everything worked.

---

