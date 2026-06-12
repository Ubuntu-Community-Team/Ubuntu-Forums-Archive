---
title: "New to Linux"
date: 2008-09-30
forum: Server Platforms
---

### Post by JoeKramer on 2008-09-30
Ok I'm a windows guy primarily and have tried verious Linux packages in the past with no real luck (usualy video driver issues).

My Firewall at home is failing and I don't want to spend any $$$ on another one right now so I thought I would see if I can build a little firewall/router with a Linux distribution and maybe run IPCop.
My work has a stack of old Dell Optiplex GX150's and said I can have as many of them as I want.  They are PIII 1Gig, 20Gig HD, 512Mg RAM with CDROMs, enough to run a nice little Linux box.

I downloaded the server version of ubuntu and installed it on the GX150.  Everything went fine.  

I was going to try and load software from a CD but when I tried to mount the CDROM it kicks back and says only 'root' can do that.  Durring the install I thought that the user name and password I setup had this access.

Am I doing something wrong?

Thanks guys!

(please no MS/Windows bashing  LOL)

---

### Post by kustomjs on 2008-09-30
dude just download a copy of smoothwall or clark connect.

---

### Post by gombadi on 2008-09-30
If your new machine has access to the Internet then it is best to remove the cdrom lines so it will download the latest packages from the Internet.

Log on to the machine and then as root use you favorite editor to edit /etc/apt/sources.list

At the top of the file you will see some lines that start deb cdrom. Just put a # in front of these lines then as root run apt-get update.

From then on the system will pull packages from the Internet and not the cdrom.

---

### Post by JoeKramer on 2008-10-01
kustomjs:  Thanks man.  I will look into them.

gombadi: Cool.  It is on a DHCP DSL line so does it setup TCP/IP on the NIC without me messing with it?  I assume its old enough that Linux installed everything without any fuss.  Does this version automaticly sets up the protocal for DHCP?  I have done no configing for anything, its 'out of the box' right now.

Still don't have the 'root' answer I was looking for.

Guess I need to be more clear.  How do I log on as 'root'?  I have no password for that...

Thanks again!

---

### Post by HermanAB on 2008-10-01
To answer the original question. On Ubuntu, you need to use sudo for root commands:
$ sudo mount -t iso9660 /dev/cdrom /mnt/cdrom

---

### Post by lykwydchykyn on 2008-10-01
Networking is typically configured by default, and it defaults to DHCP.  "ifconfig" should tell you if you have an IP or not.

---

