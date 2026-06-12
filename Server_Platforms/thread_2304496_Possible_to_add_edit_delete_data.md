---
title: "Possible to add edit delete data ?"
date: 2015-11-27
forum: Server Platforms
---

### Post by soamz on 2015-11-27
Hi, I have a Dell 2950 server. 
I have 4 x 2TB disks in there right now done into 1 using RAID0. 
And Ubuntu server is installed. 


Now, I have installed Plex Media Server into the same server. 
And I need to copy around 6TB of data into the disks. 

How do I copy ?

Is there an easy way like copy paste we do in windows PC ?

Also, if I add a new 2TB, and keep it filled and then insert into the server, will the server detect it fine ?
And will the plex server immediately recognize 5 disks instead of 4 ?

---

### Post by TheFu on 2015-11-27
Use sftp to put the data onto the server where ever you've configured Plex to look for the different types of media. TV, Movies, Music, videos, photos all must be stored in different areas.  There are 50+ different sftp clients. All Linux file managers support it out-of-the-box.
 
Or you can setup samba, if security doesn't matter.

If the data is already only the box, just use any file-manager or the shell to "mv" the files/directories where ever needed. Normal Unix permissions will matter, of course. That is often an issue for noobs. We were all noobs at some point. Learn file/directory permissions sooner than later to avoid lots of frustration. Unix (and linux) are multi-user OSes at their core. Different processes run under different userids - this is core to the system security. Plex runs as the plex userid with an effective groupid of plex. Media files/directories must respect this for plex to work. Save the frustration and learn this sooner than later.  Every new service installed will follow this pattern. If this cannot be learned, then Unix/Linux isn't the OS you want. It isn't hard, but does require "thinking multi-user" for file/directories.

BTW, RAID0 is highly dangerous. If any 1 of the disks fail, all data on all the disks will be lost. I'd hate to see you back here after a failure. For media, plex can  have multiple storage locations per media type. No need for RAID0 and the added risks involved.

---

### Post by soamz on 2015-11-27
> **TheFu said:**
> Use sftp to put the data onto the server where ever you've configured Plex to look for the different types of media. TV, Movies, Music, videos, photos all must be stored in different areas.  There are 50+ different sftp clients. All Linux file managers support it out-of-the-box.
 
Or you can setup samba, if security doesn't matter.

If the data is already only the box, just use any file-manager or the shell to "mv" the files/directories where ever needed. Normal Unix permissions will matter, of course. That is often an issue for noobs. We were all noobs at some point. Learn file/directory permissions sooner than later to avoid lots of frustration.

BTW, RAID0 is highly dangerous. If any 1 of the disks fail, all data on all the disks will be lost. I'd hate to see you back here after a failure. For media, plex can  have multiple storage locations per media type. No need for RAID0 and the added risks involved.


1. sftp will take forever to upload the files. I was expecting a method like simple windows explorer or mac explorer and copy paste files from external hard drive to the internal drive. 

2. Isn't Ubuntu Server comes with a desktop like graphical interface, so I can see the drives clearly and simply copy paste files ?

3. Okay so I have 3 HD. So, instead of RAID0, do RAID1 or RAID5 ? What to do ? 
Without RAID, the server doesnt detect the HD, so I guess RAID is must. Just let me know, which RAID to do.

---

### Post by TheFu on 2015-11-27
Linux servers don't have a GUI.

You can attach a USB disk, manually mount it, use mv or cp to move/copy the files over.
Don't forget to 'umount' the disk when done. Don't just yank it.  I'd probably use rsync, but there are many ways to solve this issue. "Best" is up to you and your needs.

Don't use RAID if you don't need HA - High Availability. Regardless, backups are 1000x more important than RAID.

If you need RAID help, that is a different question and depends on the type of RAID HW, SW, Fake-RAID used. I don't know anything about Dell HW-RAID. Sorry.

Oh....you can load a GUI, if the server actually has a graphics card. Many do not. They aren't needed or wanted in a server.

---

### Post by darkod on 2015-11-27
1. Why would sftp take forever? If you are on local gigabit network the bottleneck will be the usb ext hdd, not the sftp connection. In any case, if you think 6TB will copy fast over usb you are very wrong. You can plug the ext hdd into the server and use ssh session to copy. Depending how the folder structure is organized, you might need to recursively copy only few folders.

2. No, most linux servers by default have no GUI.

---

### Post by soamz on 2015-11-27
Why not install Ubuntu desktop instead of server edition ?
Or server edition is needed ?

---

### Post by TheFu on 2015-11-27
> **soamz said:**
> Why not install Ubuntu desktop instead of server edition ?
Or server edition is needed ?

You are the poster. 

Why did you install server instead of a desktop release? Sorry, I don't understand the question.

---

### Post by mikodo on 2015-11-27
> **TheFu said:**
>  Normal Unix permissions will matter, of course. That is often an issue for noobs. We were all noobs at some point. Learn file/directory permissions sooner than later to avoid lots of frustration.
Just to piggy-back on this sage advice. I expect I will never be anything but a casual user. But, to be able to follow advice, I need to have guidance to understand what is told to me. I am not suggesting you are like me in that, you may well be on your way, to becoming an expert of unix/linux administration. 

Luckily, there is wealth of information on line for reference to guide us.

Here is one [Ubuntu Community Tutorial]("https://help.ubuntu.com/community/FilePermissions") that I can suggest on File Permissions. They are many tutorials available, of course. Google: linux file permissions shows lots.

---

### Post by soamz on 2015-11-27
> **TheFu said:**
> You are the poster. 

Why did you install server instead of a desktop release? Sorry, I don't understand the question.

I mean, is there any special speciality with the server edition ?

I basically need need a web server to host my website and Plex. 

So, if desktop can still do it, then I will better install Desktop, as it has interface and many more. 


But if server edition doesnt something specific jobs, then I will stay with server. 

Just want to know the difference.

Is this possible ?
I have got 2 x 2TB Internal drives now.

I have placed them in windows 10 PC and filled both 2TB disks with the data.

I just need it to be pulled in the ubuntu server's plex media library. 

Can I simply take out and place into the Dell 2950 and it will auto detect ?

or has to do RAID config again ?
But if I do RAID, then the data will go what I have filled it with ?

:(

---

### Post by cariboo on 2015-11-27
Why make things complicated for yourself, if your computers are connected to your home network via Ethernet cables, use Winscp, it's free, and works very well.

---

### Post by soamz on 2015-11-28
> **cariboo said:**
> Why make things complicated for yourself, if your computers are connected to your home network via Ethernet cables, use Winscp, it's free, and works very well.


How ?

---

### Post by TheFu on 2015-11-28
> **soamz said:**
> How ?

My profile here under "visitor messages" has many links for this stuff. There are links to both desktop and server Guides there.

Sorry, I didn't realize you were this new to Unix and networking. Most people who go to the trouble to get server hardware have lots of networking experience and already use ssh/scp/sftp daily.

We were all new at some point.  If you are coming from Windows, there are many important differences:
[http://blog.jdpfu.com/Lin_4_Win_Users](http://blog.jdpfu.com/Lin_4_Win_Users) tries to explain. Start with that link before all the others.
 
Steps:
* install openssh-server on the server (best if the server is configured with a static IP)
* install fail2ban on the server to protect against brute-force password attacks
* use any ssh/scp/sftp client from any other machine on your network to connect to the linux machine. Use IP addresses for now. putty, winscp, filezilla are examples for windows. Androd and every unix-based OS have great tools too. Most have sftp built-in to their file managers - URL sftp://192.x.x.x/ you get the idea.
* be happy.

ssh/sftp/scp are secure enough to be used from anywhere in the world securely. Of course, passwords shouldnt be used. Use ssh-keys for authentication. Lots of  how-tos for that plus each non-Linux client does it a little differently. For Linux clients, it is trivial to create and copy the ssh keys to a remote server using ssh-copy-id.

---

### Post by soamz on 2015-11-28
> **TheFu said:**
> My profile here under "visitor messages" has many links for this stuff. There are links to both desktop and server Guides there.

Sorry, I didn't realize you were this new to Unix and networking. Most people who go to the trouble to get server hardware have lots of networking experience and already use ssh/scp/sftp daily.

We were all new at some point.  If you are coming from Windows, there are many important differences:
[http://blog.jdpfu.com/Lin_4_Win_Users](http://blog.jdpfu.com/Lin_4_Win_Users) tries to explain. Start with that link before all the others.
 
Steps:
* install openssh-server on the server (best if the server is configured with a static IP)
* install fail2ban on the server to protect against brute-force password attacks
* use any ssh/scp/sftp client from any other machine on your network to connect to the linux machine. Use IP addresses for now. putty, winscp, filezilla are examples for windows. Androd and every unix-based OS have great tools too. Most have sftp built-in to their file managers - URL sftp://192.x.x.x/ you get the idea.
* be happy.

ssh/sftp/scp are secure enough to be used from anywhere in the world securely. Of course, passwords shouldnt be used. Use ssh-keys for authentication. Lots of  how-tos for that plus each non-Linux client does it a little differently. For Linux clients, it is trivial to create and copy the ssh keys to a remote server using ssh-copy-id.


Wow, the URL looks interesting. I will go through. 

And I have been using Linux commands for years now, but for basic work only. I use a cloud server till date. 

Now I have setup the server in house, so more worried, if doing right or wrong. 

So you say, instead of looking for copy paste method like Windows, simply use SFTP client and drag drop the file to location by logging into the server ?

So no other way ?

I was basically looking to copy 118 folders with 3.8TB of data into my server folder of MOVIES. 
Thats all I needed. 

There are like 1171 mp4 files inside those 118 folders. 

Need an easier way to copy paste the Plex Server media library.

---

### Post by TheFu on 2015-11-28
> **soamz said:**
> So no other way ?

I was basically looking to copy 118 folders with 3.8TB of data into my server folder of MOVIES. 
Thats all I needed. 

There are like 1171 mp4 files inside those 118 folders. 

Need an easier way to copy paste the Plex Server media library.

Yes, there are 500 other ways. We're only telling you the easiest, but for some reason you think this is too hard? scp, ssh, sftp are BONEHEAD.  Setting up plain-FTP is much harder and 10,000x less secure - Plain FTP should have disappeared in 1993 along with telnet. Heck, if you'd just done this last night with WinSCP, it would have finished already. Right?  WinSCP is a GUI for Windows. Select all, connect the server (use the IP and your login credentials), then drag-n-drop the files.

Simple.

You can also use rsync ... that that works over .... wait for it ... ssh.  ssh is the Swiss Army Knife for Unix networking. Get used to it.  Fighting that will end in your system being hacked .... by a script (not even a real person).

I've been running Plex MS for a few years. Trust me. We are telling you the easy ways that aren't just for Plex, but for moving files around the internet where ever you have ssh access.

[http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh) - ssh is amazing.

---

### Post by soamz on 2015-11-28
> **TheFu said:**
> Yes, there are 500 other ways. We're only telling you the easiest, but for some reason you think this is too hard? scp, ssh, sftp are BONEHEAD.  Setting up plain-FTP is much harder and 10,000x less secure - Plain FTP should have disappeared in 1993 along with telnet. Heck, if you'd just done this last night with WinSCP, it would have finished already. Right?  WinSCP is a GUI for Windows. Select all, connect the server (use the IP and your login credentials), then drag-n-drop the files.

Simple.

You can also use rsync ... that that works over .... wait for it ... ssh.  ssh is the Swiss Army Knife for Unix networking. Get used to it.  Fighting that will end in your system being hacked .... by a script (not even a real person).

I've been running Plex MS for a few years. Trust me. We are telling you the easy ways that aren't just for Plex, but for moving files around the internet where ever you have ssh access.

[http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh) - ssh is amazing.


yes, I know SSH!
But the question is, SFTP will take forever to upload the files. 
Lets say, if I want to upload 10 movie files into the Plex Media Server, and its 10GB, then SFTP will take really forever, as it will simple upload at upload speed, not as local file transfer. 

or am I missing something ?

---

### Post by darkod on 2015-11-28
You are missing a lot obviously... :)

According to the said so far (and your other posts), the server is right there with you at your home, right? Or is it purchased server from a provider on the internet?

If the server is in your local home network, the transfer speed to it from your desktop will depend only on your local network speed (not the internet). If you have wired (cable) network of 1Gb, that will be the upload speed to the server.

If the server is on the internet, then the speed will depend on your internet upload speed but that will be the same more or less regardless which protocol/program you use to upload the data...

We already gave you option to transfer by attaching the usb hdd to the server directly too, but you seem to be avoiding that...

So the real question right now would be, what more do you want from us??? :)

---

### Post by TheFu on 2015-11-28
It is clear that you are missing a number of things .... local transfers over a 1 GigE network are relatively fast.  It has NOTHING to do with the WAN/Router speed, unless the router is only 10/100 ... in that case, buy a $15 GigE switch and connect all the computers to it, with 1 "uplink" connection to the router.  All local transfers will be GigE that way.  Trust us.  I have a 10/100 router AND a few $15 GigE switches. It works.  The router is only involved with WAN traffic, not local.

10G should take ... let me do the math ...

Transferring 10G of data on a GigE network should take ... 89 seconds (assuming 920Mbps which is what I get from a chromebook to a server).  USB2 will limit that transfer speed to about 30 Mbps in my testing.

All your transfers would have been done if you'd just done it already.  Just do it overnight.
```

10		GigaBytes
10240	MBytes
81920	Mbits
89.04	sec at 920Mb/s
```
Feel free to check my math. ;)

I move 20G files around ALL-THE-TIME. Here's a 2+G file transfer ... 
```
    599,818,240  19%  112.40MB/s    0:00:20 
```
ssh transfers aren't that slow ... I'm getting 896 Mbit/sec there. That's real-world, with ssh (actually using rsync+ssh).

---

### Post by soamz on 2015-11-28
Oops! Yes!
Will try now. 
Lets see. 

Thanks Thanks!

> **darkod said:**
> You are missing a lot obviously... :)

According to the said so far (and your other posts), the server is right there with you at your home, right? Or is it purchased server from a provider on the internet?

If the server is in your local home network, the transfer speed to it from your desktop will depend only on your local network speed (not the internet). If you have wired (cable) network of 1Gb, that will be the upload speed to the server.

If the server is on the internet, then the speed will depend on your internet upload speed but that will be the same more or less regardless which protocol/program you use to upload the data...

We already gave you option to transfer by attaching the usb hdd to the server directly too, but you seem to be avoiding that...

So the real question right now would be, what more do you want from us??? :)

Oh USB method ?
Where ?
I might have missed it.

---

### Post by TheFu on 2015-11-28
Post #4.

---

### Post by soamz on 2015-11-28
> **TheFu said:**
> Linux servers don't have a GUI.

You can attach a USB disk, manually mount it, use mv or cp to move/copy the files over.
Don't forget to 'umount' the disk when done. Don't just yank it.  I'd probably use rsync, but there are many ways to solve this issue. "Best" is up to you and your needs.

Don't use RAID if you don't need HA - High Availability. Regardless, backups are 1000x more important than RAID.

If you need RAID help, that is a different question and depends on the type of RAID HW, SW, Fake-RAID used. I don't know anything about Dell HW-RAID. Sorry.

Oh....you can load a GUI, if the server actually has a graphics card. Many do not. They aren't needed or wanted in a server.


Okay so I have a external hard drive, the 4TB one. 
So I simply connect it to the server and then mount it in terminal ? 

Then do rsync from its folder to the ubuntu server folder, where I need ? 

After done, simply umount the USB ? 

And which GUI addon you recommend in ubuntu server ?

---

### Post by cariboo on 2015-11-28
> **soamz said:**
> And which GUI addon you recommend in ubuntu server ?

No gui needed, I run Ubuntu 99% of the time, and use the file manager to transfer files via sftp. Any configuration files that need editing, I use nano. The only real difference is that you use the keyboard instead of a mouse.

---

### Post by soamz on 2015-11-28
but Ubuntu server has no GUI interface. 
So, cannot install any APP or reach its interface. 
So, will install FILEZILLA in a windows PC in the same LAN network and login to server from FileZilla and do drag drop.
I hope it works.

Okay I installed WINSCP on my windows and logged in and tried to drag drop a file and it says permission denied. 

Ubuntu server dont let you know the root password.

So how to do it then ?

How do I move a file ?

See screenshot. 
[ATTACH=CONFIG]265828[/ATTACH]

---

### Post by TheFu on 2015-11-29
Post #8 answers.  Please review.

---

### Post by soamz on 2015-11-29
> **TheFu said:**
> Post #8 answers.  Please review.

Checked, doesnt say anything about winSCP. 

Can you tell how to login or work as root within WINSCP ?

---

### Post by cariboo on 2015-11-30
What are the permissions of the directory you are trying to copy files to?

---

### Post by soamz on 2015-11-30
> **cariboo said:**
> What are the permissions of the directory you are trying to copy files to?

The folder is at the root /

I have created it there using sudo mkdir foldername

but for WINSCP to upload, it wont let me upload, since Im logged into WINSCP as a ubuntu server user login, and not as root. 


So, either I have to know the root password of the server or else find a way how to change the user to root permission within WINSCP.

I even did this :

> [COLOR=#111111][FONT=Consolas]sudo passwd root[/FONT][/COLOR]

Then it said, new root password successfully set. 

But when I try the new password with username root in WINSCP, it still doesnt let me in.
Says, wrong password.

Im lost now.

---

### Post by darkod on 2015-11-30
You need to read more about folder/file permissions. The tutorial linked in post #8 and many other tutorials on the internet explain that. That's why TheFu said post #8 answers your question.

You don't need to use winscp as root but you do need to configure proper permissions on your server. That's basic, for both windows and linux servers.

---

### Post by soamz on 2015-11-30
> **darkod said:**
> You need to read more about folder/file permissions. The tutorial linked in post #8 and many other tutorials on the internet explain that. That's why TheFu said post #8 answers your question.

You don't need to use winscp as root but you do need to configure proper permissions on your server. That's basic, for both windows and linux servers.

So run what command on the SSH, which would let me upload files to my root ?

---

### Post by cariboo on 2015-11-30
I have all my hard drives on my server mounted in /media, they are owned by  my user and have  read/write access. This server will never be open to the world, so the permissions are set to 755 which would look something like this:

```
drwxr-xr-x  53 cariboo cariboo     4096 Jun 13 13:03 alexis
```

My server was set up in 2012, when at the time /media was the preferred place to mount drives/partition, today, /srv seems to be the recommended place.

---

### Post by soamz on 2015-11-30
> **cariboo said:**
> I have all my hard drives on my server mounted in /media, they are owned by  my user and have  read/write access. This server will never be open to the world, so the permissions are set to 755 which would look something like this:

```
drwxr-xr-x  53 cariboo cariboo     4096 Jun 13 13:03 alexis
```

My server was set up in 2012, when at the time /media was the preferred place to mount drives/partition, today, /srv seems to be the recommended place.


If you see my screenshot, my /emymedia folder has 755 permissions only, still it doesnt let me upload file to it, when Im logged as user. 

And do you mean, I shall upload everything to /srv folder so it goes to my hard disks and the Ubuntu SSD partition ??

---

### Post by soamz on 2015-12-01
Solved it with chown.

---

### Post by TheFu on 2015-12-05
Happy you were able to solve it.

That is what posts #2 and #8 were about, BTW - learning and controlling directory and file permissions. Unix is very different from Windows, especially in this regard.

Anyway, if solved, please mark this thread as solved using the "Thread Tools."

---

### Post by soamz on 2015-12-05
That is solved but Im not able to mount a drive to a folder. 

[COLOR=#000000][COLOR=#000000]I have successfully mounted sdb1.[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]But sdc1 is not getting mounted and it shows this error. [/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]Can you please look ?[/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000][I]root@ubuntu:/# mount /dev/sdb1 /mnt/disk1root@ubuntu:/# df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 78G 15G 60G 20% /
none 4.0K 0 4.0K 0% /sys/fs/cgroup
udev 16G 4.0K 16G 1% /dev
tmpfs 3.2G 1.2M 3.2G 1% /run
none 5.0M 0 5.0M 0% /run/lock
none 16G 8.0K 16G 1% /run/shm
none 100M 0 100M 0% /run/user
/dev/sdb1 3.6T 68M 3.4T 1% /mnt/disk1
root@ubuntu:/# cd /
root@ubuntu:/# ls
bin data embymedia home initrd.img.old lib lost+found mnt proc run srv tmp var vmlinuz.old
boot dev etc initrd.img jetplexmedia lib64 media opt root sbin sys usr vmlinuz
root@ubuntu:/# cd mnt
root@ubuntu:/mnt# ls
disk1 external
root@ubuntu:/mnt# mkdir disk2
root@ubuntu:/mnt# cd
root@ubuntu:~# mount /dev/sdc1 /mnt/disk2
mount: special device /dev/sdc1 does not exist[/I][/COLOR][/COLOR]

---

