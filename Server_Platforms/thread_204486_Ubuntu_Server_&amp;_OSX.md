---
title: "Ubuntu Server &amp; OSX"
date: 2006-06-27
forum: Server Platforms
---

### Post by Jeeevs2001 on 2006-06-27
I have finally got round to setting up my Ubuntu 6.06 server at home and finally got ssh running. Now I am looking to use this as a FTP server and fileserver. Really I just want some advice that I am on the right track! 

I am running the basic server install on my 'server' and trying to access files using a MacBook running OSX. I have so far installed ssh and got that working ok. 
Now I would like to fix the IP address of the server and possibly give it a 'name' rather than an IP address for remoting in. If I am correct all I need to do to give it a static IP is to edit /etc/network/interfaces and change it to static and fill in the relevant info, eg: 
address 192.168.1.10        
netmask 255.255.255.0        
network 192.168.1.1        
broadcast 192.168.0.255        
gateway 192.168.1.1

As for setting it up with a 'name' instead of IP I have looked this up and can't find a way to do this which works (I tried to follow the instructions here [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3) but never seemed to get it to work) so any advice would be great! 

Beyond this I was looking to set up a NFS file share following the instructions here - [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing). 

and a ftp server following - [http://www.ubuntuforums.org/showthread.php?t=154511&highlight=proftp](http://www.ubuntuforums.org/showthread.php?t=154511&highlight=proftp)

So that is the plan, what I really wanted was some pointers if anyone has done anything similar and agrees / disagrees that this is the right way before I head down the path! 

Thanks in advance,

---

### Post by scxtt on 2006-06-27
your static setup looks good to me - my file is similar and i use a static IP address (don't have that "network" entry, but ...)

as for using a "name", you'll want to define it in the /etc/hosts file of the box you're connecting from ... if you have 2 boxes (names: box_1 and box_2, IPs: 192.168.1.100 and 192.168.1.101) you'll have a setup like this:

box_1's /etc/hosts:
```
192.168.1.101     box_2
```
box_2's /etc/hosts:
```
192.168.1.100     box_1
```

then from box_1 you can do:
[indent]$user@box_1 $ ssh $user@box_2[/indent]

then from box_2 you can do:
[indent]$user@box_2 $ ssh $user@box_1[/indent]

---

### Post by Jeeevs2001 on 2006-06-27
when you say 
"you'll want to define it in the /etc/hosts file of the box you're connecting from" 
I am connecting from my Mac, do I need to edit files on the Mac? 

Also they connect through a wireless adsl router (4 ports, 1 of which is the 'server' and the laptop is wireless) does this make any difference (ie do I need to change settings on the router)? 

Thanks for your quick reply.

---

### Post by scxtt on 2006-06-27
[QUOTE=Jeeevs2001]when you say 
"you'll want to define it in the /etc/hosts file of the box you're connecting from" 
I am connecting from my Mac, do I need to edit files on the Mac?[/quote]if you want to use a "named" convention, you'll need to tell the mac that 'when i use this name, translate it into this address' -- using /etc/hosts on linux is how that's accomplished, not sure how macs do it ...[quote=Jeeevs2001]Also they connect through a wireless adsl router (4 ports, 1 of which is the 'server' and the laptop is wireless) does this make any difference (ie do I need to change settings on the router)?[/QUOTE]nah, the router deals directy w/ IP addresses ... i've seen routers that list the "name" along w/ the  IPaddress in the DHCP table, but that didn't work w/ linux ...

---

### Post by Jeeevs2001 on 2006-06-28
Thanks for the info, I have got it working ok using the IP address but not the 'name'. For now I am giving up and looking at other problems such as: 

I have successfully set up SSH, Webmin and (pro)FTP. but now when doing a 'port scan' from the mac there are loads of ports open and I have gone from knowing exactly what they all where to not having a clue - need to read up I think!

I am trying to set up some sort of fileshare but I can't get ether NFS or samba to work. I have set them both up to go to my 2nd hard disk, which is mounted automatically in fstab. The problem is that although the server appears in my network (from the mac) when I try to use it the mac tells me that the 'alias is broken' and I can't get to it. I assume this is using Samba, do I need to have my windows pc on for this to work (if that is the case I need to find a new way because I hope to be rid of the window pc soon!)?

The NFS, I set this up through webmin but can't seem to 'mount' the drive from the mac, all the instructions I have seen use 'sudo' in the terminal, which doesn't work on the mac (root is disabled). 
The other instructions to 'mount' the remote drive involve typing in the address bar in finder, which doesn't have an address bar (that I can see). 

The end aim of this is to get my mac to use the fileserver to store all my files like music and movies etc. I can't just use FTP (which is working perfectly) as I would like to set it up to store my iTunes library on the server so it needs to see it as a 'drive' on the mac. 

Has anyone done anything similar and got it to work? 

Thanks in advance.

---

### Post by scxtt on 2006-06-28
what ports are open?

i've gotten Samba and NFS working from Ubuntu --> Windows XP (Samba) and Ubuntu --> Xubuntu, but honestly the whole Mac aspect makes it difficult for me to be able to help (i've never used one for more than 10 minutes) ... so i know what packages and configs you'd need for both, but i don't know what you'll need for Macs (or even how they mount samba or NFS) ...

---

### Post by Jeeevs2001 on 2006-06-28
Open TCP Port:     21	ftp
Open TCP Port: 	22	ssh, pcanywherestat
Open TCP Port: 	111	NFS
Open TCP Port: 	139	NetBIOS 
Open TCP Port: 	445	SMB (NetBIOS over TCP)
Open TCP Port: 	731	Print share? 
Open TCP Port: 	790	
Open TCP Port: 	2049	bgmp, NFS 
Open TCP Port: 	1000	Webmin
Open TCP Port: 	50764	

These are the open ports and what I have managed to find out they are for, I think! The two which are left I have no idea what they do. 

I remember reading some where that I need to have a windows PC in the network for samba to work, is this true?

Also what does bgmp mean (port 2049)?

---

### Post by scxtt on 2006-06-28
no, i can use samba b/t my Ubuntu host and Xubuntu VM ... it's just generally a "no brainer" getting samba to work in XP ...

bgmp just seems to be a reference to port 264, no idea what it is or why ... i've only seen 111 and 2049 used for NFS ...

no idea on 790, but i wouldn't worry too much about 50764 - i have weird high ports being used too:
```
:> netstat | more
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost:45874         localhost:59448         ESTABLISHED
tcp        0      0 localhost:59448         localhost:45874         ESTABLISHED
```tho they're associated w/ my box ...

---

### Post by Jeeevs2001 on 2006-06-29
I have (at last) got samba working! My Mac and Ubuntu box communicate fine and I can also get my Windows PC to appear (on the rare occasion I use it). 
I t all seems well, thank you for your assistance, now all I have to do is work out how to use IP routing on my router so I can SSH into my box from work. 

As a side, the Ubuntu box seems to have a 'name' (rather than IP) in the network so I seem to have solved that problem too!

---

### Post by PanzerMKZ on 2006-06-29
Any idea has to how you got it to be named on your network?


Panzer

---

### Post by NeoGreen on 2006-06-29
Man, thanks for the info, I have been trying to get my server running the same way.:)

---

