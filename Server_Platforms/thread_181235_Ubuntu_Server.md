---
title: "Ubuntu Server"
date: 2006-05-23
forum: Server Platforms
---

### Post by NeoGreen on 2006-05-23
Here is my question:  I want to be able to have a server for my home, in this server I want it to be able to store files, pictures, and applications.  How do I go about doing this if I want to use Ubuntu as my OS for my server?  I want to be able to log onto the server from different computers in my house and maybe even work and be able to retrieve files or picture as well as safe them from any location.  I also want to be able to log on and us applications.  Could this be a good project for me to learn how to maintain a server.  I am sort of new to servers and want to be able to learn as I go.  Any advice will help.  Thank You.:)

---

### Post by NeoGreen on 2006-05-23
Anybody got any advice?????:(

---

### Post by NeoGreen on 2006-05-24
Is anybody out there?  Help me please.:(

---

### Post by Almighty on 2006-05-24
For a basic file server, its pretty easy. Its about as straight forward as any other Ubuntu install. I too am very new to servers, especially Linux servers, but I have a simple set up very much like what you are looking for.

-Basically all I did was install the server version of Ubuntu, partition your disc(s) so you have a nice and organized system. I personally have the OS on one hard drive and the stored files on another just to be safe. If I had the money I would have set up a RAID I will move to that sometime in the future. 

-Then install a window manager, mainly to keep things as simple as possible.

-Since I will have a windows machine on the network, I aslo installed Samba so all the machines can talk to one another. You will want to take a look at the Samba section on the Wiki because I got stuck there for quite some time. TAKE YOUR TIME AND FOLLOW THE INSTRUCTIONS CAREFULLY. 

You may also want to look into Ubuntu Center to have a nice pretty GUI when browsing for your files. Its still in Beta so there are some rough edges but not bad software at all.

If you have any questions about anything post up and I will help you as much as I can.

---

### Post by Iowan on 2006-05-24
[http://www.howtoforge.com/samba_setup_ubuntu_5.10]("http://www.howtoforge.com/samba_setup_ubuntu_5.10")
This is a good place to start.

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=samba&fullsearch=Text]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=samba&fullsearch=Text")
Some Samba articles from the wiki.

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10")

---

### Post by NeoGreen on 2006-05-24
Thanks for the support and the info.  I'll you keep you updated on my project.:)

---

### Post by NeoGreen on 2006-05-24
Quick question, I have a Linksys wireless router in my network.  The router is connected to my DSL modem, from the Linksys router I have one Desktop XP attached wired, my print server and a switch which connects 4 other desktops.  On top of that I have two laptops connected wirelessly.  Where would I attach my server in my network?  The wireless router is DHCP enabled, will this conflict if my server is also running DHCP.  If so, what do recommend I do?  Run DHCP from my server or wireless router?  ](*,)

---

### Post by Almighty on 2006-05-24
You can put your server anywhere you want. If you are connecting the server directly to the Router so it's physical location will have no effect on your network. Also you should have a static IP for your server.

---

### Post by NeoGreen on 2006-05-24
Okay, so I should have my router configure a static IP address for my server.  So it will have a permanent IP address.  Does that sound right?

---

### Post by superjet on 2006-05-24
Yes, that is correct. A static IP will assure you will be able to find the box all the time.
When you do that, I would also suggest going into your router and make sure your router does not try and give that IP address out to another machine via DHCP.

---

### Post by NeoGreen on 2006-05-24
Okay, I got to the part about quotas and close to the end it asked me to run this command:
touch /quota.user /quota.group  **WORKED**chmod 600 /quota.* **WORKED**
mount -o remount /  WORKED
touch /home/quota.user /home/quota.group  **WORKED**
chmod 600 /home/quota.*  **WORKED**
mount -o remount /home **WORKED**
quotacheck -avugm **DID NOT WORK**
quotaon -avug **DID NOT WORK**

The last two commands did not work.  I went in and followed the insturction step by step.  I configured /etc/fstab and added,usrquota,grpquota to the partitions with the mount point / and /home using vi.](*,)

---

### Post by basketcase on 2006-05-24
[QUOTE=superjet]Yes, that is correct. A static IP will assure you will be able to find the box all the time.
When you do that, I would also suggest going into your router and make sure your router does not try and give that IP address out to another machine via DHCP.[/QUOTE]
On your linksys router you probably have DHCP setup to give out something like 192.168.1.100-150 Set your IP address of the server outside of this range (or change the range for your DHCP server on the router).  No need to do DHCP on the Ubuntu box. 

If you want to access your Ubuntu box from outside your local Network (from the internet) enabling dyndns makes access your box a lot easier.  I wouldn't set this server in a DMZ, but just setup port forwarding -- you can change the default ports if you'd like.  

All depends on what you want to do.  I had a fedora box up for over a year on my home DSL connection.  I rebuilt it with Breezy, but it has since become a Mythtv box.

---

### Post by NeoGreen on 2006-05-24
So if my IP address on my ubuntu box is 192.168.1.110 I should change my DHCP range from 192.168.1.100 to 192.168.1.109?  Also how do I install a File server or service and window manager on my ubuntu box? Thanks for the help and the info.

---

### Post by adamkane on 2006-05-24
Are you file serving Linux2Linux or Linux2Windows?

Linux2Linux: Use NFS.
Linux2Windows: Use Samba

---

### Post by NeoGreen on 2006-05-24
Well, actually both I have several linux machines and windows machines.  Do you think this will conflict with my server?

---

### Post by basketcase on 2006-05-24
Exactly on the DHCP

Now...do you want to be able to access this from outside your local network (192.168.1.x)?


Do you want to use FTP? Web?

---

### Post by adamkane on 2006-05-24
That's interesting. You'll use Samba to connect the Windows PCs to the server, and use NFS to connect the Linux PCs to the server. 

Let me know, if you want me to post my NFS settings.

Some people may say that all you need is SAMBA. I guess this is true as long as you always have a Windows PC booted up to maintain the Windows network neighborhood. Not the best way to run a Linux server.

---

### Post by basketcase on 2006-05-25
[QUOTE=NeoGreen]Well, actually both I have several linux machines and windows machines.  Do you think this will conflict with my server?[/QUOTE]
Not entirely sure how it would conflict....SMB shares in Dapper is even easier than before.

---

### Post by NeoGreen on 2006-05-25
Please do post your NFS settings.  Also, which one do you think is better FTP or Web?   While configuring Cupsys I ran into a problem when configuring it, here is what I did; **Set AuthGroupName to shadow in the section Security Options:**

AuthGroupName **shadow  **
Now where do I input this information?  Do I erase the part where it talks about groups and just input shadow?  I did that and know I'm getting this weird output on my command prompt:  **root@neoserver1:~# river-gimpprint-data (4.2.7-10) ...**
 this is popping up when I am not even pushing any keys on my keyboard.

Another question, if I screwed up my /etc/cusys.conf file how can I restore it, it says something on there about restore but I couldn't understand it. 
Thanks for the help and the information.:)

---

### Post by adamkane on 2006-05-25
Server:
```

sudo apt-get install nfs-server

``` 
Client:
```

sudo gedit /etc/fstab

``` 
Add some lines:

server_ip:/server_folder /local_folder nfs noatime,rsize=32768,wsize=32768,bg 0 0

Example
192.168.0.10:/media/docs /media/docs nfs noatime,rsize=32768,wsize=32768,bg 0 0

Be sure to create some folders on the client:
```

sudo mkdir /media/docs
sudo chmod +x /media/docs

``` If you want to move files around, you have to use the client to do this.

---

### Post by NeoGreen on 2006-05-25
Should I create the media folders for the server also?  So do I have to create and install NFS on all the clients that run on linux also?  And do I have to install samba on my windows clients and create the same media folder you stated on the post?  Sorry for all the question, I am just being overwhelmed with all this info.  Thanks

---

### Post by Iowan on 2006-05-25
[QUOTE=NeoGreen]And do I have to install samba on my windows clients ...  [/QUOTE]Samba lets Unix boxes speak SMB - Windows boxes were born speaking it (or at least knowing how), so they don't need a translator... so to speak.

---

### Post by NeoGreen on 2006-05-25
Oh, okay.  Thanks for the information:)

---

### Post by Iowan on 2006-05-25
[QUOTE=adamkane]
Some people may say that all you need is SAMBA. I guess this is true as long as you always have a Windows PC booted up to maintain the Windows network neighborhood. Not the best way to run a Linux server.[/QUOTE]
I _presume_ that if Samba (machine) is set as master browser, it should maintain the Windows network neighborhood, or did I miss the function of the master browser setting :confused:
   I have a mixed network (XP and Ubuntu), and can share files from the Samba server to my Linux boxes.  Probably not the most efficient, but functional enough to K.I.S.S.

---

### Post by adamkane on 2006-05-25
All I'm saying is that you need a Windows machine on at all times to maintain the Windows Network Neighborhood. If your Windows machine is off for some reason, than your Network will be down. Not a good setup for a Linux server.

To each his own. I'm not telling anyone what to do.

---

### Post by adamkane on 2006-05-25
You need to create folders on Linux clients.

The folders are already on your server. You then need to "map" the folders onto the Linux clients. You "map" them by creating folders on the clients, and then using fstab to "map" the server folders onto the clients.

---

### Post by NeoGreen on 2006-05-25
Oh, okay. I get it so I should create the folders for my linux clients.  Then I need to go to each client and configure the folder to map with my linux box using fstab.  I got it thanks.:)

---

### Post by NeoGreen on 2006-05-25
I was trying to use fstap to configure my linuxclients, my question is what do I input in this file for it to work?  This is what I get when I type sudo gedit /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

where do I input the configuration?  :-k

---

### Post by adamkane on 2006-05-26
Create a new line:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
192.168.0.10:/media/docs /media/docs nfs noatime,rsize=32768,wsize=32768,bg 0 0


Then save and close the file.

---

### Post by adamkane on 2006-05-26
You may need to install nfs-kernel-server, not nfs-server on your Linux server.

---

### Post by NeoGreen on 2006-05-26
Oh, okay so 192.168.0.10:/media/docs /media/docs nfs noatime,rsize=32768,wsize=32768,bg 0 0 has to be added to the .conf file.  Does it matter where you put it?  So I have to install  the nfs kernel server.  Okay, I'll try it.  Thanks for the information:)

---

### Post by peanut butter on 2006-05-26
the person who said you have to have a windows box up all the time is not correct,  i use smb from my kubuntu and ubuntu machines and barely have a windows box running, in fact i havent had one up for at least a week so that is false. 
i used this guide to set up the machine: [http://www.ubuntuforums.org/showthread.php?t=76647](http://www.ubuntuforums.org/showthread.php?t=76647)

---

### Post by NeoGreen on 2006-05-26
Why is it when I try to create a directory using this command: 
sudo mkdir /media/docs it won't let me? Do I have to create first the directory /media then go into it and create the sub directory /docs, or is docs a file?
:confused:

---

### Post by adamkane on 2006-05-27
What does this say?:

```

cd /media

``` 
Also NFS works better than SAMBA. The transfers are faster and more reliable. You can use SAMBA, if you like, but it isn't as well developed. 

Also see:
-----
[http://us1.samba.org/samba/docs/FAQ/]("http://us1.samba.org/samba/docs/FAQ/")
**What is Samba?**

  Samba is a suite of programs that enables interoperability between Linux/Unix  servers and Windows clients.
-----

Samba is not for Linux-to-Linux filesharing.

---

### Post by NeoGreen on 2006-05-27
Okay, once all is configured how do I use my server to save files.  I have installed Samba, NFS, and Proftpd.  What else am I missing?:confused:

---

### Post by adamkane on 2006-05-27
Each client will have folders mapped to folders on the servers. Save files into these new folders, and they will appear on the server.

Client:
Save files to /media/docs or whatever. If /media/docs to a folder on the server, then the files will actually be saved on the server.

Server:
Browse to /media/docs or /hd2/docs or /home/user/docs or wherever the folders were mapped to find the saved files on the server.

---

### Post by NeoGreen on 2006-05-27
What command do I use to map the directory /media to my server?  I created the same directory to my linux machines and my windows machines.  The name of the directory is /media but how do I map ?  I was tryin to use mount -t /media but it doesn't work.:confused:

---

### Post by adamkane on 2006-05-27
Just add the lines to fstab, and reboot or:

[sudo]
sudo mount -a
[/sudo]

---

### Post by NeoGreen on 2006-05-27
I did sudo mount -a command on the client linux machine and I got this response:
[B]neogreen@ubuntulinux:~$ sudo mount -a
Password:
mount: RPC: Program not registered
mount: backgrounding "192.168.1.110:/media/docs"[/B]
Do I have to input this information on the fstab on the server too?  Something like this
192.168.1.103:/media/docs /media/docs nfs noatime,rsize=32768,wsize=32768,bg 0 0
192.168.1.103 being the clients IP address.](*,)

---

### Post by NeoGreen on 2006-05-28
Okay, this is what I did, I created a file in /media/docs. Named file2, I then used command mount -a /media/docs.  I then ssh'd to my server and checked to see if the file saved and it didn't.  :confused:

---

### Post by linuxone on 2006-05-28
Hi,

[QUOTE=adamkane]All I'm saying is that you need a Windows machine on at all times to maintain the Windows Network Neighborhood. If your Windows machine is off for some reason, than your Network will be down. Not a good setup for a Linux server.[/QUOTE]

the Network Neighborhood has nothing the do with Windows itself. This is a feature of the **Netbui** protocol. Depending on OS internal specifications one machine is selected as "master browser", holding a list of all known machines into the (Netbui!) networks.
Newer Windows versions does Netbui over TCP/IP. Windows 9x/ME was the last release with a selectable Netbui protocol.

Into the UNIX/LINUX world this netbui issue could be handled from **Samba**. If you check the samba logs you can see notices about becoming a master browser .... and more. You can force Samba to become a master browser by setting a higher OS level (required if Samba will be used as PDC), see smb.conf man pages.

This will also work without a single Windows machine into the network. If using samba into a network without Windows machines is usefull or not is another question outside this thread. :confused: 

Thomas

---

### Post by linuxone on 2006-05-28
Hi,

[QUOTE=NeoGreen]What command do I use to map the directory /media to my server?  I created the same directory to my linux machines and my windows machines.  The name of the directory is /media but how do I map ?  I was tryin to use mount -t /media but it doesn't work. :confused:[/QUOTE]

/media is the main system directory using as default directory to mount additional path.
If you insert a CD to your cd drive, this will automaticly be added to /media/cdrom. If you attach a formatted USB hard disc, this will automaticly be added to (for example) /media/sda1. If you attach a formatted USB memory stick, this will be added (for example) to /media/sdb1.

As far as I understand your problems .... you don't need to map drives. It seems to be a missunderstanding.
If you use samba, you need to configure at least one samba share. Means: a physical path on your linux box will become a share into your network. This is a config line in your smb.conf file, but basicly not a mounted partition.

I don't have NFS experiences but run samba as a Linux file server into a Windows network since years. From my network experiences I doubt it is usefull to use the same physical path for different network protocols like NFS and SMB (samba).

To be honest, I'm a little bit confused. After reading this entire thread I don't know what you really want. The thread length is a good sign for the entire confusion. :confused: 

I suggest you think about your needs. Really think about everything. Don't want all  - that is unimpossible. Define your real and usefull needs. Then tell us what you really want - after reading the related manuals and man pages .... :)

For example: NFS/Samba and FTP were quite different issues. Not comparable, usefull to very different needs. And it is certainly NOT usefull to use the same physical path for NFS and samba and FTP. Furthermore it is a very different issue to install a server for a closed Intranet or the worldwide Internet. Do you really want to use a sole server for both? Did you think about security?!

Thomas

---

### Post by NeoGreen on 2006-05-28
Yeah, I did kinda start getting lost.  This is what I wanted:  I server that I can use to store files. Kinda like a large File Server.  On this server I want to be able to store files, pictures and also be able to get to it outside my network via internet.  I have  small network at home with several windows and linux machines and I want all machines to be able to access the server for any file saving or sharing.  :) I've installed samba, nfs and ftp.

---

### Post by NeoGreen on 2006-05-28
So to have a sort of storage file server, I would have to install nfs, samba and ntfs on my server and on my clients (enable samba and ntfs on my linux clients).  After installing these programms or applications on my server I need to configure my clients on to the server and configure my server onto the clients.  I think that is the process I need to do.  I did some of it but I got lost close to the end.  Does that sound right?  Also I was wanting to be able to run apache so that I could post my web comic on it too.  Could that be posible if I am running a small home network?  I heard that I may need to configure my server so that my DSL can issue my server an IP address so people out of my network can view my web comic.  This only what I understand, correct me if I am wrong Please.:)

---

### Post by FredSambo on 2006-05-28
you can do anything and everything you want.

try this tutorial, which was linked to earlier...

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

it isn't perfect but it will get you up and running so that you can view your /var/www/ directory via IP or localhost.

good luck n00b!

---

### Post by NeoGreen on 2006-05-28
Thanks, I'll try it again.  I am learning alot from this experience and I think that it pretty good.:)

---

