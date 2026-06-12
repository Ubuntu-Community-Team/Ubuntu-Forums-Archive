---
title: "Cannot mount truecrypt volume over network"
date: 2008-11-05
forum: Security
---

### Post by olepi on 2008-11-05
Is it possible to mount a truecrypt container located on another computer on the local network? I'm connected to the other computer via ssh, but when I browse to the file container on the other computer, I get a "permission denied" error when I try to mount it. I am running truecrypt 6.1 and ubuntu 8.04.

---

### Post by randy78 on 2008-11-05
Have you checked the permissions of the Truecrypt container on the other machine? Does it belong to another user?

In a terminal, type: ls -l /location/of/truecrypt/container (/home/test/containers/container1, etc)

---

### Post by hyper_ch on 2008-11-06
use sshfs instead to mount the remote folder into the local filesystem.

---

### Post by olepi on 2008-11-06
It seems that I have read/write permissions on the truecrypt container. I have also tried connecting to the other computer using sshfs and still get the 'permission denied' error when I attempt to mount the volume.

I can even create a new truecrypt volume on the other computer over the network, just can't mount it.

---

### Post by lannatwin on 2008-11-10
> **olepi said:**
> It seems that I have read/write permissions on the truecrypt container. I have also tried connecting to the other computer using sshfs and still get the 'permission denied' error when I attempt to mount the volume.

I can even create a new truecrypt volume on the other computer over the network, just can't mount it.

I'm having identical problems in 8.10.

---

### Post by pendimethalin on 2008-11-12
> **olepi said:**
> It seems that I have read/write permissions on the truecrypt container. I have also tried connecting to the other computer using sshfs and still get the 'permission denied' error when I attempt to mount the volume.

I can even create a new truecrypt volume on the other computer over the network, just can't mount it.

I am having the same issue. I can connect via sshfs and create new TC containers over the network. However, when I try to mount it I get a 'permission denied' error. I have also tried creating a container locally and I'm able to mount it. Then transferring the container over to my server and attempting to remount it but I get the same error. Anyone out there actually able to do this or get it working? Thanks.

---

### Post by randy78 on 2008-11-12
Hey guys... you might want to try the Truecrypt forums: [http://forums.truecrypt.org/]("http://forums.truecrypt.org/")

Take Care and Good Luck :D

PS. If you find a solution, be sure to post it back here and mark this as solved so everybody can use it :guitar:

---

### Post by linuxfascist on 2008-11-17
Hi 
I did it like this :
1. Mount the volume or container on the host machine with the option umask=000 , this allows to acces the volume as guest.
2. share the folder for the network with samba

---

### Post by 0dB on 2009-04-05
To get TrueCrypt to work over a network, you need the mount option "allow_other" (and also setting "user_allow_other" in /etc/fuse.conf). I had the same problem when trying to access a TrueCrypt volume on a USB stick attached to a thin client (LTSP = Linux Terminal Server Project, often associated with Edubuntu). In my case the network file system is "ltspfs", for others it is sshfs or nfs. Check what it is for you.

This is how I restarted ltspfs with the "allow_other" option (which mtab showed was missing):

```
sudo ltspfs 192.168.1.24:/var/run/drives/usbdisk-sdb1 /media/myusername/usbdisk-sdb1 -oallow_other
```

(The IP address was assigned to the thin client by the DHCP server.) Now TrueCrypt can open the .tc file, and "mount" shows:

```
ltspfs on /media/myusername/usbdisk-sdb1 type fuse.ltspfs (rw,nosuid,nodev,allow_other)
```

I have not figured out how to have "allow_other" automatically be set when mounting the USB stick over the network.

---

### Post by 7tisix on 2009-06-13
c|8^)  Finally!  Mounting Truecrypt Volumes across network, no more Permission denied:  8^)      c|8^)

8^) Edit fuse.conf and add one line, my command on next line.

thomas@ubuntu:~$ sudo gedit /etc/fuse.conf

8^)   Add the line below to /etc/fuse.conf on its own line exactly as shown:

user_allow_other



8^)  I used sshfs with the syntax shown below (DON'T FORGET SUDO!!!!)

thomas@ubuntu:~$ sudo sshfs thomas@192.168.1.193:/ /home/thomas/mnt/tc -o allow_other 


8^)  Happy mounting!!!  :D

---

### Post by kartal on 2009-11-02
Hi

I am trying to mount some /media/mount folders and I am failing badly with truecrypt ones. I do not know how to change the user permissions on the mounted drives. I tried with "sudo nautilus" but sudo itself could not change the permission on the drives.


I can mount some of the folders from the /media but not the truecrypt one. How is this done?


Any suggestions?

thanks

---

### Post by Niva on 2009-11-28
hmmm, found this thread which is attempting to address the issue I'm having.  It's entirely too complicated.  I wonder what is different about mounting network drives within linux than within windows because this stuff works in Windows without a hitch.

---

### Post by cariboo on 2009-11-28
Mounting shares is just as easy, as windows. The most common way is to use Samba which uses Windows protocols. As was cover in this thread, you can also use sshfs. Another way is to use nfs if you want to share directories between two or more linux based systems.

If you need help, we need more info.

---

### Post by lmicu on 2010-02-25
> **7tisix said:**
> c|8^)  Finally!  Mounting Truecrypt Volumes across network, no more Permission denied:  8^)      c|8^)

8^) Edit fuse.conf and add one line, my command on next line.

thomas@ubuntu:~$ sudo gedit /etc/fuse.conf

8^)   Add the line below to /etc/fuse.conf on its own line exactly as shown:

user_allow_other



8^)  I used sshfs with the syntax shown below (DON'T FORGET SUDO!!!!)

thomas@ubuntu:~$ sudo sshfs thomas@192.168.1.193:/ /home/thomas/mnt/tc -o allow_other 


8^)  Happy mounting!!!  :D

This worked for me also, Thank you! Keep on Linux-ing!

---

### Post by aston4 on 2010-09-11
can someone please explain where that path comes from in the post above?

I'm trying to get to a network share truecrypt volume via tomato installed on a router, & tomato assigns really weird names and paths to mounted disks.

I need to know which part of that command above is a path on the local machine, and which part of the path related to the remote volume.

---

### Post by cariboo on 2010-09-12
If you are refering to this line:

> thomas@ubuntu:~$ sudo sshfs thomas@192.168.1.193:/ /home/thomas/mnt/tc -o allow_other 

The location on the remote computer is this:

> thomas@192.168.1.193:/

The path on the local computer is this:

> /home/thomas/mnt/tc

For info on the sshfs switches, have a look at man sshfs

---

### Post by aston4 on 2010-10-01
I'm still not getting the path right.  I have a truecrypt file named "Volume"  It is on a remote drive hanging off a Tomato router.  Tomato assigns a name to this drive, the name is:  "disc0_1 on 192.168.1.198"  So if I want to get to that drive through Nautilus, or whatever, I go to:  "/home/me/.gvfs/disc 0_1 on 192.168.1.198"    When I try something like this:  sudo sshfs Volume@192.168.3.198://"disc0_1 on 192.168.3.198"/ /home/me/mnt/tc -o allow_other   or 29 other permutations of the above just always return this error:  "read:  Connection reset by peer"  I wish it would just work like it does on the windows side of my machine... sigh.  I've been trying to make this work for two months.

---

### Post by Jack0239 on 2010-10-30
I have the same problem above and I have still no idea how to fix it. Is there anyone out there who can help us?

---

### Post by doublemeat on 2011-09-06
Actually the solution couldn't be simpler. You just need to add an option to the "mount" command:
```
uid=*{local username}*
```
The complete command (in the case of CIFS/SMB) being:
```
sudo mount -t cifs //*{host}*/*{share}* *{local mount point}* -o user=*{remote username}*,**uid=*{local username}***
```
*Note: Without specifying the password as an option (always a good idea to avoid plaintexting your passwords and/or in a way that bash history collects, IMO), this command would then prompt you for the remote password (after first prompting you for the sudo password of course).*

All this does is mounts the share in a way that you (the user) can read and write to. Then, TrueCrypt has no problems accessing an encrypted volume stored on that share (assuming no other issues of course).

I don't know why this isn't widely discussed on the internets. I had to dig through the mount man page to discover this, after a fruitless internet search to this particular problem.

This is also not a hack or workaround. It's how *mount* was designed to work.

[B]I should also point out that the previous solution discussed here is potentially dangerous, as it obviates the user-based security built-in to FUSE, and that TrueCrypt (and other FUSE modules such as EncFS) rely on: That is, by default only the current user can see the mounted volume! Modifying /etc/fuse.conf to add "user_allow_other", and specifying "allow_other" on the command line, overrides this behavior and allows *any user* to see your decrypted data.

If you've encrypted your data in the first place, there's a fairly good chance you wouldn't want this side effect![/B]

---

