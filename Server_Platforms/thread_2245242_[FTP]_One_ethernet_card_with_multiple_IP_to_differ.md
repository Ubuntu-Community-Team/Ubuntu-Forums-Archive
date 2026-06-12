---
title: "[FTP] One ethernet card with multiple IP to different FTP folders"
date: 2014-09-22
forum: Server Platforms
---

### Post by hitachicc on 2014-09-22
Hello everyone,

I have my ubuntu server in my local network with one ethernet card, and FTP service
I want attribute to this ubuntu server few local IP adress. 
After this, equipement in my local network could see differents folder when they're connecting to one or other adress ip.
Example : 
Equipement 1 -> 192.168.1.4 (ftp) -> eth0 (Ubuntu server 1) -> **Folder 1**
Equipement 1 -> 192.168.1.5 (ftp) -> eth0 (Ubuntu server 1) -> **Folder 2**
Equipement 1 -> 192.168.1.6 (ftp) -> eth0 (Ubuntu server 1) -> **Folder 3**
Equipement 1 -> 192.168.1.7 (ftp) -> eth0 (Ubuntu server 1) -> [B]Folder 4

[/B]
What's the best way to do this ?

Thanks you for you help,

Hitacc

---

### Post by Lars Noodén on 2014-09-22
The best way?  Maybe without FTP.  Are you sure you don't want a secure connection instead?  FTP is terminally insecure and all the Ubuntu file managers now support SFTP.  

SFTP can provide a secure alternative for file transfer.  As far as your question about file transfer, but using SFTP, the package openssh-server provides SFTP out of the box and the configuration for SFTP can be set in /etc/ssh/sshd_config.  Using that, there would be two ways of steering SFTP to a particular folder based on the IP address connected to.  One would be to set the starting directory, the other would be to set a chroot.

A starting directory can be set using [ForceCommand](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html)

```

Match LocalAddress 192.168.1.4
     ForceCommand internal-sftp -d /home/foo/folder_1/

Match LocalAddress 192.168.1.5
     ForceCommand internal-sftp -d /home/foo/folder_2/

..etc...

```

Alternately, something similar could be done with [ChrootDirectory](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html), if you do not want them to be able to work back up in the file system hierarchy.

```

Match LocalAddress 192.168.1.4
     ForceCommand internal-sftp
     ChrootDirectory /home/foo/folder_1/

Match LocalAddress 192.168.1.5
     ForceCommand internal-sftp
     ChrootDirectory /home/foo/folder_2/

..etc...

```

The drawback / advantage to both of those is that those users cannot connect to a regular shell connection, only SFTP.  You'll need an additional IP address for shell connections or some other work-around.

---

### Post by hitachicc on 2014-09-22
Hello Lars !

Thanks you for your answer, I'll work on it.

---

### Post by irv on 2014-09-22
If you are trying to setup so you can transfer files around I use Nautilus and sftp from one to another. Just open Nautilus and select [Ctrl] "L" to open address bar and type:
sftp://username@servername/directoryname/
It will ask for password 
you can open as many sections of Nautilus as you want to transfer files around.
[ATTACH=CONFIG]256604[/ATTACH]

Also see this howto I made on youtube.
[https://www.youtube.com/watch?v=9S4DV1PluzA&list=UUFGShDMhsNAeDALKN98bVnw]("https://www.youtube.com/watch?v=9S4DV1PluzA&list=UUFGShDMhsNAeDALKN98bVnw")

---

### Post by hitachicc on 2014-09-23
Hello,

I'll need to use FTP service because all equipments which I need to be interfaced are developed to work on it. 
These equipments are asking one IP with defined port and user/password on local network.
If these equipments

I didn't try to define few local IP (.4, .5, .6, .7) to only one ethernet card (eth0).
I suppose each ethernet card are defined by one MAC address and just one IP could be addressed. I'm wrong ? 
Can I assign few IP adress to one ethernet card ? Maybe I need a special converter with 4 ethernet card -> usb connected to my ubuntu server ? 

My goal is : If an equipment do a telnet ask to .4, I answer by a value 1
If an equipment do a telnet ask to .5, I answer by a value 2
.6, .7 same thing.
So, Can I have 4 IP address on my eth0 or I need to have 4 ethernet card ?

Thanks you,

---

### Post by Michael_McKenney on 2014-09-23
I think you would be better off using multiple accounts each tied to one folder instead of using FTP.  You could use SSH and lock down each user to that folder only.   I would not do it by IP address.  Too complicated to setup.  SAMBA and SSH along with security would be better.  You could get SFTP secured FTP and user accounts.

---

### Post by Lars Noodén on 2014-09-24
> **hitachicc said:**
> 
So, Can I have 4 IP address on my eth0 or I need to have 4 ethernet card ?


One network interface can have many ip addresses, if they are assigned statically.  I'm not sure about DHCP, I think that allows only one, but if you can set the addresses manually there is no real limit.  

> **hitachicc said:**
> 
These equipments are asking one IP with defined port and user/password on local network.


Maybe I misunderstood in the first post about which side of the connection had multiple addresses.  I thought that you described many hosts would be connecting to a single machine which had multiple ip addresses on a single interface.  If you meant instead for many ip addresses to be contacting a single machine, yet get different folders, that's doable to.  Just substitute Address for LocalAddress in the Match statement and that will sort on the incoming address rather than the destination address.

But as Michael_McKenney mentions, using different user accounts can give different folders as a destination as determined by their assigned home directories.  That applies to both SFTP, SSH and even Telnet.  But why are you mentioning telnet? 

What devices are still using Telnet or FTP in 2014?

---

### Post by Michael_McKenney on 2014-09-24
I still have many applications that use telnet and ftp.  Cisco routers upgrade via TFTP and FTP.  If it is behind a router and firewall.  They are safe to use.  A lot depends on how secure you want it and how fast you want it.  Secured connections can affect speed of data transfers.

---

### Post by lukeiamyourfather on 2014-09-24
> **hitachicc said:**
> I'll need to use FTP service because all equipments which I need to be interfaced are developed to work on it. 
These equipments are asking one IP with defined port and user/password on local network.

In my opinion it would be best to setup one IP address for the machine and then run multiple FTP servers on different ports. The default is port 20/21 but you could use ports 2000, 2100, 2200, 2300 or something like that. Using a bunch of IP addresses like that is sloppy, wasteful, and confusing if someone were to come in and pickup where you left off. Then point each piece of equipment to the same IP address but with different port number.

---

### Post by Michael_McKenney on 2014-09-24
Seems like your adding a lot of overhead with multiple FTP servers to maintain and configure.  Assigning it my user rights to folders would be simpler to do and maintain.  I could easily add a 5th user and folder for another app.

---

### Post by lukeiamyourfather on 2014-09-25
> **Michael_McKenney said:**
> Seems like your adding a lot of overhead with multiple FTP servers to maintain and configure.  Assigning it my user rights to folders would be simpler to do and maintain.  I could easily add a 5th user and folder for another app.

If this equipment allows specific enough configuration to do so then yeah, multiple users would be better than multiple servers, but if you must have multiple servers then it's better to do it with more than one port versus more than one IP address.

---

