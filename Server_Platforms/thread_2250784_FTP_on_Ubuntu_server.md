---
title: "FTP on Ubuntu server"
date: 2014-10-31
forum: Server Platforms
---

### Post by ronnie4 on 2014-10-31
Hello,
I have been fiddling around for many hours trying to configure my server for remote access while I am away from home. At first I wanted to set up a simple vpn server with my ubuntu server running 14.04 but no matter what I did I couldn't get it to work. Ultimately I would love help with that but I just got lost generating all the keys and configuring everything threw terminal and I just became stumped. Anyways, for the time being I have successfully been able to create an ssh server in which I can ftp into my server using filezilla. Here is what a need help with:

I have two servers: my ubuntu one runs minecraft server, vnc, and ssh. My other server runs freenas
my ubuntu server has my freenas server mapped as a network drive so I can access all my files on it (its a mapped drive which is displayed in the networking section of the file explorer). The problem is, when I ftp into my ubuntu server through ssh, there isn't a file directory to display the mapped drive I have on the ubuntu server. Here is that chain: My laptop>ubuntu server (ssh) > freenas server (mapped drive). My goal is to be able to view the freenas drive (which is mapped in my ubuntu server) in filezile so I can access and back up files. I don't want to directly setup ssh on my freenas server for obvious security reasons. I have realvnc configured so I can easily work on the server remotely to fix things, and ssh is also fully functional.

I hope I explained it clearly enough, let me know if I worded it too confusing.

Thanks for your help,

Ron

---

### Post by nerdtron on 2014-10-31
On the ubuntu server, what path is the NAS mounted? On filezilla you can go to that path to access the NAS.

---

### Post by ronnie4 on 2014-11-05
Hello nerdtron,
That is what I am unaware of. In the file explorer, my freenas server shows up under "network" and if i hover the mouse about it, it displays smb://freenas/data. In filezilla I cannot find the actual directory though. I appreciate your help as I need this solved asap.

Thanks for your assistance,
Ron

---

### Post by ronnie4 on 2014-11-05
This is what it looks like in file explorer.

---

### Post by steeldriver on 2014-11-05
If the share is mounted via the nautilus file manager, it should appear as a gvfs mount - depending on what Ubuntu version you are running that should be under either $HOME/.gvfs (up to 12.04) or /run/user/*uid*/gvfs (where *uid *is your login account's numeric user ID - after 12.04)

---

### Post by ronnie4 on 2014-11-07
Hello steeldriver,

Navigating to it in filezilla did not show the folder but on my server I could see it. Although it's not visible, if I manually enter the directory in filezilla it navigates to it. Thank you so much now I can do my backups again!

With much appreciation,
Ron

---

### Post by TheFu on 2014-11-09
I hope you are using SFTP, not plain FTP. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) these are VERY DIFFERENT THINGS. 1 is secure, the other is NOT.

Also - I hope you are only using VNC through an SSH tunnel, also for security reasons.

So - if you want to use sftp to connect to 1 server (A) with storage from another server (B), then A must mount the storage from B so that it appears to be local. While you can do that through nautilus, that probably is NOT the best way.  If B is running freenas, then I'd use NFS.  If B is always on, just add the mount to your /etc/fstab on A, but if B is not always running, use autofs (which is a little more involved).

---

