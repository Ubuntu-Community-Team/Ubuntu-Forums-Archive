---
title: "installing network file server"
date: 2012-01-01
forum: Server Platforms
---

### Post by jmate24 on 2012-01-01
How do I install an NFS on Lubuntu so that I may share my music and videos with 2 Ubuntu Live CDs and or one install running on 2 separate computers.

Or can I better achieve this with Samba? and use windows and VLC Media Player.

I have OGV videos, MP3s and Flac audio files I can convert the Flac files to MP3 though.

And I am running a wired network 10/100. And all of the computers are on the same floor.

---

### Post by rsvancara on 2012-01-01
1. sudo apt-get install nfs-kernel-server
2. vim /etc/exports

```
/local/exports/share.music      10.10.155.0/255.255.255.0(rw,sync,no_subtree_check)
```

The above line is just an example, you could also make it look like this:

```
/local/exports/share.music      *
```

Which is the simplest, least restrictive file share

From your client you can run:

```
sudo /sbin/showmount -e thenameofyourserver
```

This will show the mounts available.  Note, you may have to run apt-get install nfs-common to install the client tools.

---

### Post by jmate24 on 2012-01-09
thank you but i have a couple more questions.

How do I share my NFS server with Windows?
I would like to not have to install *buntu on either Windows machine.
Or would I share them with Samba?
I would also like for it to be secure because Machine #1 tends to get hacked a lot nowadays since Windows XP is at its EOL. 

And each machine is as follows:

Machine #1 Desktop

Intel Celeron P4
2GB RAM
DVD-ROM That Does not Work with Windows But will work with *buntu live CD (driver problems with Windows XP)
Intel Graphics
40GB HDD
IBM that is about 6-9 years old
Windows XP Home that is EOL
10/100 Ethernet

Machine #2 Desktop

Intel Core 2 Duo
2GB Ram
DVD-RAM (that works)
Intel Graphics
10/100 Ethernet
500GB HDD
FOXCONN that is new. (Bare-bones PC from [www.newegg.com](www.newegg.com))
May Be able to set up dual-boot environment
Windows 7 Pro & Lubuntu

Machine #3 Desktop

AMD Dual Core
4GB Ram
DVD-RAM
10/100 Ethernet
450GB Laptop HDD (85% Full)
Nvidia Geforce GT series
10/100 Ethernet
Windows 7 Pro
MMORPG Gamer Machine

Machine #4 Desktop 
(my Machine NFS server and all the Videos and Music I wish to share securely without them getting deleted.) I would prefer if I could have this machine be able to stream the video when they open the folder and click on the video to VLC Media Player for windows. And the music to both iTunes and Windows Media Player. All Music is in MP3 format and all Videos are in OGV.)

AMD Quad Core
750GB HDD 98% Full of music and Videos (but will be getting a new 750GB HDD in February (p.s. hard drives have gotten expensive since the floods in Thailand.))
ATI Radeon 5670
3 DVD-RAM Drives
10/100/1000 Ethernet
Lubuntu 11.10

Thanks for the help.

---

### Post by papibe on 2012-01-09
> **jmate24 said:**
> How do I share my NFS server with Windows?
...
Or would I share them with Samba?
Only higher version of Windows support NFS. If I remember correctly just XP Professional, and Windows 7 Ultimate support it.

In all other cases you'll have to use Samba instead.

BTW, you can share the same folder using both NFS and Samba without any problem.

Regards.

---

### Post by jmate24 on 2012-01-10
Now how would i go about configuring my samba shares so Windows 7 Pro and Windows XP Home can see them?
Is there a GUI that I can use?

I also did a little reasearch and found my Ubuntu 10.04 Server Book and searched the forums for 'samba' and this is what I was able to come up with for my smb.conf file is this correct? I am also wondering if I have to change these words in red to match my [COLOR="Red"]WORKGROUP[/COLOR] and my server to my computer network name [COLOR="DarkGreen"]myname-1lubuntu1[/COLOR] in smb.conf?

```
 [global]
   workgroup = [COLOR="Red"]WorkGroup[/COLOR]
   server string = %h [COLOR="DarkGreen"]server[/COLOR]
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = no
[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mask = 0700
   directory mask = 0700
   valid users = %S
   hide files = .*
[myVideos]
   path = /home/justin/Videos
   comment = Justin's Videos
   writable = no
   browsable = yes
   read only = yes
   valid users = derek kim justin
[myMusic]
   path = /home/justin/Music
   comment = Justin's Music
   writable = no
   browsable = yes
   read only = yes
   valid users = derek kim justin 
```

---

