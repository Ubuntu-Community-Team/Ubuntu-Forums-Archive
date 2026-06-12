---
title: "Samba 100x slower than FTP?"
date: 2007-04-26
forum: Server Platforms
---

### Post by teeks99 on 2007-04-26
I have a brand new machine running Feisty (Dual core chip, 4gb ram, 1gbps Ethernet).  I have set it up for both Samba shares and FTP connections on my local LAN.  

The problem is: I can transfer a 1GB file in under two minutes over FTP, but when I try to transfer the exact same file between the same two computers over samba it takes ~120 minutes.  Is there anything I need to check in my configuration off the bat? 

 I tried searching the forum, but I think search is broken now....I typed in Samba and it didn't give me any results anywhere.

Thanks!
Tom

---

### Post by teeks99 on 2007-04-26
Just to verify, I have confirmed that this is a problem when transferring files to both windows and linux boxes.

I have done:
Ubuntu (server) -> Windows
Ubuntu (server) -> Fedora Core 5 smbclient

Both run at the same, very slow, rate.

//Edit
This is only a problem when downloading from the server.  File transfers back to ubuntu run fine.
Windows -> Ubuntu (server) -- full speed

---

### Post by huygens on 2007-04-27
Do you use manual mount point for Samba (with smbfs) or how do you access the Samba shares?
Smbfs is not as maintained as it use to be in the newest kernel, because CIFS is replacing it. Just try to remount your disk with CIFS instead. The options are slightly different though.
To use CIFS, you could look at this thread :-) [http://ubuntuforums.org/showthread.php?t=400413](http://ubuntuforums.org/showthread.php?t=400413)

I did not understood in which cases you have good performances and which you have bad ones.

Could you summarise with this "table":[LIST]
[*]You are on Windows[LIST]
[*]Downloading from a Linux box
[*]Uploading to a Linux box[/LIST] 
[*]You are on Linux[LIST]
[*]Downloading from a Windows box
[*]Uploading to a Windows box[/LIST] [/LIST]Which cases are "failing"?

By the way, Samba has more overhead to transfer files than FTP and would be slower. But you should not really see the difference on a LAN.

---

### Post by teeks99 on 2007-04-27
> **huygens said:**
> Do you use manual mount point for Samba (with smbfs) or how do you access the Samba shares?

I do not mount them.  When I tried accessing the share from another Linux computer, I used the command line smbclient program (works like command line ftp).

Also, I tried this (using smbclient) from the localhost, and encountered the SAME problem downloading!  To me this definitely indicates some issue with SAMBA, since there's no network involved.

Could you summarize with this "table":[LIST]
[*]You are on Windows[LIST]
[*]Downloading from a Linux box <- PROBLEM!
[*]Uploading to a Linux box <- Fine [/LIST] 
[*]You are on Ubuntu (the install in question)[LIST]
[*]Downloading from a Windows box <- Fine
[*]Uploading to a Windows box <- PROBLEM!
[*]Downloading from a Linux box <- Fine
[*]Uploading to a Linux box <- Untested[/LIST]
[*]You are on Fedora[LIST]
[*]Downloading from a Linux box <- PROBLEM!
[*]Uploading to a Linux box <- Untested[/LIST]
[*]On the same box (connecting to //thisbox/share)[LIST]
[*]Download from the same box <- PROBLEM!
[*]Uploading to the same box <- Fine[/LIST] [/LIST] I put the status of each scenario at the end, and added a few that you didn't include.  

> 
By the way, Samba has more overhead to transfer files than FTP and would be slower. But you should not really see the difference on a LAN.

I agree.

---

### Post by teeks99 on 2007-04-27
Here's a rundown of what happens in the logs.  I have:
	socket options = TCP_NODELAY SO_RCVBUF=16384 SO_SNDBUF=16384
	log level = 2 

sudo /etc/init.d/samba restart

log.smbd
```

[2007/04/27 03:27:11, 0] smbd/server.c:main(847)
  smbd version 3.0.24 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2007/04/27 03:27:11, 2] param/loadparm.c:do_section(3712)
  Processing section "[homes]"
[2007/04/27 03:27:11, 2] param/loadparm.c:do_section(3712)
  Processing section "[printers]"
[2007/04/27 03:27:11, 2] param/loadparm.c:do_section(3712)
  Processing section "[print$]"
[2007/04/27 03:27:11, 2] param/loadparm.c:do_section(3712)
  Processing section "[fs]"
[2007/04/27 03:27:11, 2] lib/interface.c:add_interface(81)
  added interface ip=192.168.0.207 bcast=192.168.0.255 nmask=255.255.255.0
[2007/04/27 03:27:11, 2] lib/tallocmsg.c:register_msg_pool_usage(61)
  Registered MSG_REQ_POOL_USAGE
[2007/04/27 03:27:11, 2] lib/dmallocmsg.c:register_dmalloc_msgs(71)
  Registered MSG_REQ_DMALLOC_MARK and LOG_CHANGED
[2007/04/27 03:27:11, 2] smbd/server.c:open_sockets_smbd(384)
  waiting for a connection

```

log.nmbd
```

[2007/04/27 03:27:11, 0] nmbd/nmbd.c:main(699)
  Netbios nameserver version 3.0.24 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2007/04/27 03:27:11, 2] nmbd/nmbd.c:main(723)
  Becoming a daemon.
[2007/04/27 03:27:11, 2] lib/tallocmsg.c:register_msg_pool_usage(61)
  Registered MSG_REQ_POOL_USAGE
[2007/04/27 03:27:11, 2] lib/dmallocmsg.c:register_dmalloc_msgs(71)
  Registered MSG_REQ_DMALLOC_MARK and LOG_CHANGED
[2007/04/27 03:27:11, 2] lib/interface.c:add_interface(81)
  added interface ip=192.168.0.207 bcast=192.168.0.255 nmask=255.255.255.0
[2007/04/27 03:27:11, 2] nmbd/nmbd_subnetdb.c:make_subnet(144)
  making subnet name:192.168.0.207 Broadcast address:192.168.0.255 Subnet mask:255.255.255.0
[2007/04/27 03:27:11, 2] nmbd/nmbd_subnetdb.c:make_subnet(144)
  making subnet name:UNICAST_SUBNET Broadcast address:0.0.0.0 Subnet mask:0.0.0.0
[2007/04/27 03:27:11, 2] nmbd/nmbd_subnetdb.c:make_subnet(144)
  making subnet name:REMOTE_BROADCAST_SUBNET Broadcast address:0.0.0.0 Subnet mask:0.0.0.0
[2007/04/27 03:27:11, 2] nmbd/nmbd_lmhosts.c:load_lmhosts_file(41)
  load_lmhosts_file: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory

```

Open windows explorer, go to \\client\share

log.smbd
```

nothing new

```

log.nmbd
```

nothing new

```

log.192.168.0.xxx
```

[2007/04/27 03:28:51, 2] smbd/reply.c:reply_special(496)
  netbios connect: name1=MYHOSTNAME            name2=MYCLIENTNAME           
[2007/04/27 03:28:51, 2] smbd/reply.c:reply_special(503)
  netbios connect: local=myhostname remote=myclientname, name type = 0
[2007/04/27 03:28:51, 2] smbd/sesssetup.c:setup_new_vc_session(799)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2007/04/27 03:28:51, 2] smbd/sesssetup.c:setup_new_vc_session(799)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.

```

log.myclientname
```

[2007/04/27 03:28:51, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [myusername] -> [myusername] -> [myusername] succeeded
[2007/04/27 03:28:51, 2] smbd/reply.c:reply_tcon_and_X(711)
  Serving IPC$ as a Dfs root
[2007/04/27 03:28:51, 1] smbd/service.c:make_connection_snum(950)
  myclientname (192.168.0.202) connect to service fs initially as user myusername (uid=1000, gid=1000) (pid 15500)
[2007/04/27 03:28:51, 2] smbd/reply.c:reply_tcon_and_X(711)
  Serving fs as a Dfs root
[2007/04/27 03:29:01, 1] smbd/service.c:close_cnum(1150)
  myclientname (192.168.0.202) closed connection to service fs

```

Successful File Copy
File Size 8mb - takes 30sec instead of less than 5

log.smbd
```

nothing new

```

log.nmbd
```

nothing new

```

log.192.168.0.xxx
```

(continueing after what was shown above)
[2007/04/27 03:29:54, 2] smbd/sesssetup.c:setup_new_vc_session(799)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2007/04/27 03:29:54, 2] smbd/sesssetup.c:setup_new_vc_session(799)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2007/04/27 03:30:15, 2] smbd/reply.c:reply_special(496)
  netbios connect: name1=MYHOSTNAME            name2=MYCLIENTNAME           
[2007/04/27 03:30:15, 2] smbd/reply.c:reply_special(503)
  netbios connect: local=myhostname remote=myclientname, name type = 0
[2007/04/27 03:30:15, 2] smbd/sesssetup.c:setup_new_vc_session(799)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2007/04/27 03:30:16, 2] smbd/sesssetup.c:setup_new_vc_session(799)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2007/04/27 03:30:16, 2] smbd/sesssetup.c:setup_new_vc_session(799)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2007/04/27 03:30:16, 2] smbd/sesssetup.c:setup_new_vc_session(799)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2007/04/27 03:30:16, 2] smbd/sesssetup.c:setup_new_vc_session(799)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2007/04/27 03:30:16, 2] smbd/sesssetup.c:setup_new_vc_session(799)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2007/04/27 03:30:16, 2] smbd/reply.c:reply_special(496)
  netbios connect: name1=MYHOSTNAME            name2=MYCLIENTNAME           
[2007/04/27 03:30:16, 2] smbd/reply.c:reply_special(503)
  netbios connect: local=myhostname remote=myclientname, name type = 0
[2007/04/27 03:30:16, 2] smbd/sesssetup.c:setup_new_vc_session(799)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2007/04/27 03:30:16, 2] smbd/sesssetup.c:setup_new_vc_session(799)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.

```

log.myclientname
```

(continueing after what was shown above)
[2007/04/27 03:29:54, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [myusername] -> [myusername] -> [myusername] succeeded
[2007/04/27 03:29:54, 2] smbd/reply.c:reply_tcon_and_X(711)
  Serving IPC$ as a Dfs root
[2007/04/27 03:30:16, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [myusername] -> [myusername] -> [myusername] succeeded
[2007/04/27 03:30:16, 1] smbd/service.c:make_connection_snum(950)
  myclientname (192.168.0.202) connect to service fs initially as user myusername (uid=1000, gid=1000) (pid 15569)
[2007/04/27 03:30:16, 2] smbd/reply.c:reply_tcon_and_X(711)
  Serving fs as a Dfs root
[2007/04/27 03:30:16, 1] smbd/service.c:close_cnum(1150)
  myclientname (192.168.0.202) closed connection to service fs
[2007/04/27 03:30:16, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [myusername] -> [myusername] -> [myusername] succeeded
[2007/04/27 03:30:16, 1] smbd/service.c:make_connection_snum(950)
  myclientname (192.168.0.202) connect to service fs initially as user myusername (uid=1000, gid=1000) (pid 15571)
[2007/04/27 03:30:16, 2] smbd/reply.c:reply_tcon_and_X(711)
  Serving fs as a Dfs root
[2007/04/27 03:30:16, 1] smbd/service.c:close_cnum(1150)
  myclientname (192.168.0.202) closed connection to service fs
[2007/04/27 03:30:16, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [myusername] -> [myusername] -> [myusername] succeeded
[2007/04/27 03:30:16, 1] smbd/service.c:make_connection_snum(950)
  myclientname (192.168.0.202) connect to service fs initially as user myusername (uid=1000, gid=1000) (pid 15572)
[2007/04/27 03:30:16, 2] smbd/reply.c:reply_tcon_and_X(711)
  Serving fs as a Dfs root
[2007/04/27 03:30:16, 1] smbd/service.c:close_cnum(1150)
  myclientname (192.168.0.202) closed connection to service fs
[2007/04/27 03:30:16, 2] auth/auth.c:check_ntlm_password(309)
  check_ntlm_password:  authentication for user [myusername] -> [myusername] -> [myusername] succeeded
[2007/04/27 03:30:16, 1] smbd/service.c:make_connection_snum(950)
  myclientname (192.168.0.202) connect to service fs initially as user myusername (uid=1000, gid=1000) (pid 15573)
[2007/04/27 03:30:16, 2] smbd/reply.c:reply_tcon_and_X(711)
  Serving fs as a Dfs root
[2007/04/27 03:31:14, 2] smbd/open.c:open_file(352)
  myusername opened file Casts/truthhappens.ogg read=Yes write=No (numopen=2)
[2007/04/27 03:31:14, 2] smbd/close.c:close_normal_file(344)
  myusername closed file Casts/truthhappens.ogg (numopen=1) 
[2007/04/27 03:31:14, 2] smbd/open.c:open_file(352)
  myusername opened file Casts/truthhappens.ogg read=Yes write=No (numopen=2)
[2007/04/27 03:31:15, 2] smbd/open.c:open_file(352)
  myusername opened file Casts/PodsafeforPeace-IfEveryDayWereChristmas.zip read=No write=No (numopen=3)
[2007/04/27 03:31:15, 2] smbd/close.c:close_normal_file(344)
  myusername closed file Casts/PodsafeforPeace-IfEveryDayWereChristmas.zip (numopen=2) 
[2007/04/27 03:31:18, 2] smbd/close.c:close_normal_file(344)
  myusername closed file Casts/truthhappens.ogg (numopen=1) 
[2007/04/27 03:31:18, 2] smbd/open.c:open_file(352)
  myusername opened file Casts/truthhappens.ogg read=Yes write=No (numopen=2)
[2007/04/27 03:31:18, 2] smbd/close.c:close_normal_file(344)
  myusername closed file Casts/truthhappens.ogg (numopen=1) 
[2007/04/27 03:31:18, 2] smbd/open.c:open_file(352)
  myusername opened file Casts/truthhappens.ogg read=Yes write=No (numopen=2)
[2007/04/27 03:32:28, 2] smbd/close.c:close_normal_file(344)
  myusername closed file Casts/truthhappens.ogg (numopen=1) 

```

---

### Post by huygens on 2007-04-27
I did some test here with Samba, and it is working as expected: fine in all cases.
So I would guess that there is a problem in the configuration file of Samba on your computer.
Did you made changes to the standard configuration file (/etc/samba/smb.conf) or followed a guide/howto that has made you modify this file? If yes which modifications were performed? Did you keep the original? If yes, could you restore it temporarily and try to share a folder and perform the transfer using smbclient again (so one the same machine using the loopback interface and not the network).

I have read your logs. But I am not enough knowledgeable to determine whether there is a problem in them or not... I am just surprised by the amount of time a successful connection is logged...

---

### Post by teeks99 on 2007-04-27
There's no substantial changes to my smb.conf file (except the socket options which I've tried all applicable settings on)

diff /etc/samba/smb.conf /etc/samba/smb.conf.original 
```

27c27
<    workgroup = SPRINGFIELD
---
>    workgroup = MSHOME
68c68
<    log level = 2 
---
> 
91c91
<    security = user
---
> ;   security = user
160c160
<    load printers = yes
---
> ;   load printers = yes
190c190
<    socket options = TCP_NODELAY SO_RCVBUF=16384 SO_SNDBUF=16384
---
>    socket options = TCP_NODELAY
213,215c213,215
< [homes]
<    comment = Home Directories
<    browseable = no
---
> ;[homes]
> ;   comment = Home Directories
> ;   browseable = no
220c220
<    valid users = %S
---
> ;   valid users = %S
224c224
<    writable = no
---
> ;   writable = no
300,307d299
< # My base level share
< [fs]
<       comment = file share
<       path = /media/fs
<       browseable = yes
<       read only = no
<       guest ok = no
< 

```

---

### Post by gario on 2007-04-27
This wouldn't be with Windows Vista would it?  There are apparently big problems with SMB interoperability with Vista, even between Vista and XP:

[http://groups.google.com/group/microsoft.public.windows.vista.networking_sharing/browse_thread/thread/dcc0906846bc1716/d96c00ab3b44ed2e%23d96c00ab3b44ed2e](http://groups.google.com/group/microsoft.public.windows.vista.networking_sharing/browse_thread/thread/dcc0906846bc1716/d96c00ab3b44ed2e%23d96c00ab3b44ed2e)

I tried transfering a 3 GB DVD iso between my Linux box and a Vista machine and was getting 200Kbits throughput on a 100 Mbit network!

---

### Post by fyleow on 2007-04-27
This is definitely a bug.  I have the same issue.

Vista desktop to Ubuntu Server goes at 25 MB/s
Ubuntu Server to Vista desktop goes at 8 MB/s

I thought this was a Vista problem at first so I booted up Ubuntu but I got the same problem.

Ubuntu desktop to Ubuntu server goes at 25 MB/s
Ubuntu server to Ubuntu desktop goes at 8 MB/s

Here's what I got using netcat.  One shows the transfer time it takes to transfer a file from the Ubuntu desktop to the Ubuntu server.  The other shows the time to transfer a file from the Ubuntu server to the Ubuntu desktop.

fyleow@ubuntu:~$ time nc 192.168.1.108 8000 -q 0 <temp

real 0m44.871s
user 0m0.052s
sys 0m0.972s

fyleow@ubuntu-server:

real 0m32.653s
user 0m0.028s
sys 0m18.521s

File info:
-rw-r--r-- 1 fyleow fyleow 1346597318 2007-04-07 17:22 temp 

As you can see the times are pretty close together.  One direction shouldn't be relatively quick (25 MB/s) and the other slow (8 MB/s) which is what happens during transfers with Samba.  The file being transferred is about 1.3 gigs and if it takes 32 seconds and 44 seconds the transfer speed should be at least 30 MB/s.

I have tried different socket options in my smb.conf with no success.

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
# SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY

---

### Post by teeks99 on 2007-04-27
My performance is even worse than that.  I get about 100Mbps on the good connection (uploading to the server, or downloading using FTP), and about 6Mbps on the bad connection (downloading using samba).

Gario: No Vista was used in the making of this problem.  I've got Ubuntu 7.04, Fedora Core 5, and WinXP SP2.

---

### Post by jiminycricket on 2007-04-28
> **huygens said:**
> Do you use manual mount point for Samba (with smbfs) or how do you access the Samba shares?
Smbfs is not as maintained as it use to be in the newest kernel, because CIFS is replacing it. Just try to remount your disk with CIFS instead. The options are slightly different though.
To use CIFS, you could look at this thread :-) [http://ubuntuforums.org/showthread.php?t=400413](http://ubuntuforums.org/showthread.php?t=400413)

Have all of you followed his advice to use cifs instead of smbfs?  Also, some good Vista samba tips [here]("http://www.dslreports.com/forum/remark,18218611").

---

### Post by Tulsapoke on 2007-04-29
This is an absolutely awful problem!!  I have all my music and videos on smb shares and now they will not stream and it takes 2hrs to transfer a 700mb file at around 140KB.  I can download off the interweb faster than that!  This is the worst bug I have ever seen with any distro ever.  I will be counting the days looking for a fix to come across for this.

BTW my setup is Feisty on my desktop smb file serving to Feisty laptop and an xbox media center.

---

### Post by huygens on 2007-05-02
Just trying to see where the problem can be.
I'm trying to solve the problem of teeks99, for the others, adapt the following to your own environment.

Could you install the sysstat package (either using Synaptic under the System->Administration menu or using the command line "sudo apt-get install sysstat") on the Linux box
Then run this command in a Terminal (Applications->Accessories menu):
```
iostat -kx 5 | tee -a iostat.log
```
Once you have launched it, perform a transfer: either from Windows and downloading from the linux box where the command has been launch, or from the above linux box and uploading to Windows.
Once the transfer is done, wait 15-20 sec. and stop the command that is still running in the Terminal. To do so press together the keyboard keys once the Terminal windows is active: Ctrl+C.
The command has generated a file named iostat.log. Could you send it here in this thread?

---

### Post by teeks99 on 2007-05-02
Here's the log file (renamed iostat.txt because it needs a .txt extension).  

I didn't complete the file transfer, because it was saying it was going to take half an hour for a 60MB file, if you want more I'd be happy to go finish that, just let me know.

Tom

---

### Post by teeks99 on 2007-05-02
For reference, here's the iostat for the same transfer (same file, same computers) but using FTP instead of Samba.  The file completed in under 10sec.

---

### Post by huygens on 2007-05-04
Hello Tom,

I have read both of your file and I'm puzzled...
In both scenarios that should not work, data should be "read" from your hard drive on Linux. There is no "read" activity (as far as I understood the iostat output) in the log you sent, either via samba or ftp...
There is a bit of activity nonetheless but it is "write" activity only and it is a few kilo bytes only...

I would like to check that the scenario was the one I expected. So let's call things by name.
Let's call the Ubuntu linux computer where you have the problem "ubuntu-desktop". And your windows computer "windows-desktop". Now we are going to upload a file from ubunt-desktop to windows-desktop, and if I understood you right this should be slow when using Samba.
The scenario is as follow:
On ubuntu-desktop, find a big file (> 20 MB) and get ready to upload it to windows-desktop. If you use Nautilus, have it ready so you can start the file transfer in a matter of seconds (e.g. two opened nautilus windows: one where the file to transfer is present, and another with the destination folder on the windows-desktop).
Still on ubuntu-desktop close all other applications (like firefox, evolution, etc.) so that there should be only minimum activities.
When ready, starts the following command on the ubuntu-desktop after havig opened a Terminal:
```
iostat -kx 5 7 | tee -a iostat.txt
```Then, start the file transfer.
If the file transfer is going to take more than a minute, wait for the above command to complete before cancelling the transfer. The above command has been slightly changed so it will be ran 7 times and then stop (so a total of 35 seconds).

---

### Post by teeks99 on 2007-05-05
First, I haven't been logging in interactively to this pc, only via ssh, so there hasn't been firefox or whatever to interfere with all this stuff.

I noticed something interesting this time.  When i did a put from the ubuntu-desktop machine to the windows machine, everything ran fine....its when I did the get, (logged into the windows desktop) copying files from ubuntu-desktop to windows-desktop that I had the problem.  I also did the same transfer from ubuntu-desktop to a fedora machine (lets call it fedora-desktop) using a smbclient get, to verify that its not my windows machine, and it responded similarly, taking many minutes for what should take less than 10 sec.

For the put from ubuntu-desktop to windows desktop:
```

username@ubuntu-desktop:~$ smbclient //windows-desktop/D
Password:
Domain=[windows-desktop] OS=[Windows Server 2003 3790 Service Pack 1] Server=[Windows Server 2003
 5.2]
smb: \> put Pete-Harmonica.avi
putting file Pete-Harmonica.avi as \Pete-Harmonica.avi (18286.5 kb/s) (average 18286.5 kb/
s)

```
As you can see that ran at 18mbps....which is fine. 

For the get initiated on fedora-desktop, getting a file on ubuntu-desktop
```

[username@ fedora-desktop ~]$ smbclient //ubuntu-desktop/username
Password:
Domain=[ubuntu-desktop] OS=[Unix] Server=[Samba 3.0.24]
smb: \> get Pete-Harmonica.avi
getting file \Pete-Harmonica.avi of size 59078656 as Pete-Harmonica.avi (158.1 kb/s) (aver
age 158.1 kb/s)
smb: \>

```
This 150kbps is the same dismal speed that windows seems to get when downloading files from the ubuntu-desktop server. 

Now just to be sure, I tried uploading a file from ubuntu-desktop to fedora-desktop, assuming it would be just as quick as uploading a file from ubuntu-desktop to windows-desktop, I was wrong!  This is just as slow!
```

username@ubuntu-desktop:~$ smbclient //fedora-desktop/fs
Password:
Domain=[fedora-desktop] OS=[Unix] Server=[Samba 3.0.23a-1.fc4.1]
smb: \My Documents\Temp\> put Pete-Harmonica.avi
putting file Pete-Harmonica.avi as \My Documents\Temp\Pete-Harmonica.avi (283.1 kb/s) (ave
rage 283.1 kb/s)
smb: \My Documents\Temp\>

```
Same order of magnitude on the speed....~150.  I kinda wish i could get a smbclient prompt using windows's client, but its integrated into explorer.  

Anyway, I'm happy to gather more data if there's anything I can get.
Tom

---

### Post by jaims on 2007-05-06
hello

Same here; i've tried:

-> not mounting at all (smb://172.16.x.x/shared)
-> doing a mount -t smbfs
-> doing a mount -t cifs

getting files from xp to kubuntu works fine; putting files from kubuntu to winxp extremely slow!

My desktop running kubuntu version edgy eft.

In my laptop i've just installed ubuntu feisty and it's working fine! But just discovered that if I do ssh://172.16.x.x to my desktop running kubuntu, the transfer is also very slow...

Any hints?

Thanx

---

### Post by kaicrr77 on 2007-05-13
I to have noticed slow transfer speeds, while I am getting 1500 kbp/s using smbclient and for the most part this is ok (it's definately better than what some of you are getting for sure). But it's nothing compared to when the server was a Windows box. Using NFS will double the speeds, but using that protocol for home sharing isn't exactly pretty. So I am wondering if there is anything I can do to make smb faster. At the above speed I can listen to mp3's but I am worried that mutiple streams could leave the box useless.

---

### Post by ahelenpo on 2007-05-17
Hello,

I have exactly the same problem. Tried upgrading and downgrading samba with no luck, tweaking the tcp buffers but no luck either. Then I noticed that scp transfers are slow as well :-(.

There's clearly a bug here. Do we know if this has been acknowledged and is being worked on?

Thanks !
   Alex

---

### Post by inque_54 on 2007-06-07
Hello,

I've been researching on this problem too.

Was anybody able to resolve this issue?

---

### Post by Chayak on 2007-06-08
There is a bug report on this in launchpad, if everyone would go to [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/84782]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/84782") and comment on it or file more bug reports we can get this some attention.

---

### Post by Maybelline on 2007-06-08
> **inque_54 said:**
> Hello,

I've been researching on this problem too.

Was anybody able to resolve this issue?

Actually, yes (at least for me).

My speed problems were caused by the gam_server checking my samba share for updates too often.

I added this line to /etc/gamin/gaminrc:
```
fsset cifs poll 60
```
and I haven't had a problem since.

BTW, I had to do this on ALL machines that mount this share.

Hope this helps.

---

### Post by inque_54 on 2007-06-14
Just tried it now and still doesn't work for me 8(

Getting an avg speed of less than 4mbps while transferring 8(

---

### Post by Maybelline on 2007-06-14
> **inque_54 said:**
> Just tried it now and still doesn't work for me 8(

Getting an avg speed of less than 4mbps while transferring 8(

Well, in all honesty, that's the most I expect from mine.  I get about 3.8MB/s using rsync between my share and a local drive.  I get about 5.8MB/s using FTP, but I know that Samba has a lot more overhead than FTP.

---

### Post by chang47 on 2007-06-20
Hello,

I have the exact same problem of very slow transfer rate downloading from my xubuntu pc to my xp pc.  After reading a couple of posts elsewhere mentioning the possible cause being the nic driver, I replaced my xubuntu pc from wired to wireless just to see if this would isolate the cause.  It did!  Instead of 120 min for a 250MB file it is now 5 min.  Still doesn't compare to xp to xp in 2 minutes but much better and acceptible. 

I would suggest looking into that direction for clues.  I guess you need to use the brand specific nic driver for your particular nic card or chipset.  My wired connection was a USB Ethernet adaptor, so Xubuntu might not have the optimal driver for it.  I did not bother to look further as I am happy with the rate I am getting from the wireless connection. 

Hope this helps.

---

### Post by Brazen on 2007-06-20
I've skimmed this thread and I don't think this has been mentioned, but you should get rid of the SO_RCVBUF=8192 SO_SNDBUF=8192 in your socket options.  I know these are reccommended around on the 'net, but this is an old old reccommendation from the 2.4 kernel days and these options will slow things down on the newer 2.6 kernels.

Your socket options should only be:
```
socket options = TCP_NODELAY
```

Make the change, then reboot your server and try your speed test again.

You would also probably have better luck using Dapper.  Dapper is better optimized and tested for servers.

---

### Post by huygens on 2007-06-21
> **Brazen said:**
> Your socket options should only be:
```
socket options = TCP_NODELAY
```

This is also the default installation value it seems. As I did not modify that part of my smb.conf and that's exactly what is set. Maybe that's why I do not see any slow transfer here...

---

### Post by Brazen on 2007-06-21
> **huygens said:**
> This is also the default installation value it seems. As I did not modify that part of my smb.conf and that's exactly what is set. Maybe that's why I do not see any slow transfer here...

In newer packages yeah that is probably the default it puts in the config file, and I think if you leave it completely out of the config file, that is what it defaults to anyway.

---

### Post by teeks99 on 2007-07-20
Well, I fixed the problem, only by using a PCI ethernet card instead of the one built into the motherboard though :-(

For Review:
I have a Realtek RTL8111/8168B PCI Express (Integrated into a Asus P5B P965 Motherboard, Core 2 Duo E6400)
FTP to the good machine gets 100Mbps (over ethernet)
Samba to the same machine over the same link gets about 5Mbps  (1/20th of the speed!)

Good luck to anyone who's still working on this problem....check the hardware!

---

### Post by codmate on 2007-07-22
I'm using sbmbd 3.0.42 and getting great transfer rates  :)

I'm just using user security and mounting samba shares on my Ubuntu box.
It's connecting to a Windows workgroup.

Here's my smb.conf - names have been changed to protect the innocent  ;)

```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MYWGNAME

# server string is the equivalent of the NT Description field
   server string = MyServer

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
security = user
username map = /etc/samba/users.map

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
   comment = Home Directories
   browseable = no
   read only = no
   valid users = theuser

[music]
   comment = Music
   browsable = no
   guest ok = no
   path = /a/path
   read only = no
   valid users = theuser

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

;[printers]
;   comment = All Printers
;   browseable = no
;   path = /var/spool/samba
;   printable = yes
;   public = no
;   writable = no
;   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
;[print$]
;   comment = Printer Drivers
;   path = /var/lib/samba/printers
;   browseable = yes
;   read only = yes
;   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

With this set-up (encrypted passwords are on), you must add users using smbpasswd, as well as them having regular Linux accounts.

---

### Post by Nephi on 2007-07-27
> **teeks99 said:**
> Well, I fixed the problem, only by using a PCI ethernet card instead of the one built into the motherboard though :-(

For Review:
I have a Realtek RTL8111/8168B PCI Express (Integrated into a Asus P5B P965 Motherboard, Core 2 Duo E6400)
FTP to the good machine gets 100Mbps (over ethernet)
Samba to the same machine over the same link gets about 5Mbps  (1/20th of the speed!)

Good luck to anyone who's still working on this problem....check the hardware!

I have the exact same problem with the on-board Realtek RTL8111/8158B Ethernet on my Abit AB9-pro motherboard.  I have tried using the newest R8168B driver from RealTek (ver 8.002.00, released 7/13/07) instead of the kernel's default R8159 driver, but with no change.

I am trying to use my Feisty Ubuntu system as a Samba share to the Windoze XP systems on my network.

Like other reports I've seen, I am able to get full throughput using scp, and I can get that too with Samba **only if** I have multiple transfers going at the same time!  But when a single file is being transfered at at time, I see only inconsistent bursts of traffic with sometimes long delays in between.

If this really is a problem with the Ethernet driver, then it's a bug that's being tickled by Samba.  I've kept the smb.conf file pretty much default, but would be happy to know if there is any parameter I can tweak to fix the problem.

Can someone help me find the solution?  Does smbd support verbose logging?

Thanks!

---

### Post by trashtalk on 2007-07-27
If I smb://192.168.2.12/user to my Mac box I can browse my home folder, but when I copy files to it I get about 80KB/s. (uploading from Kubuntu 7.04 to OS X 10.4.9)

Copying files to a Windows machine  is fine. (uploading and download to and from Windows XP and Kubuntu 7.04)

Browsing the Samba share from OS X and copying the files also works fine. (Downloading from Kubuntu 7.04 to OS X).

I used this tutorial to set up Samba
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Only things I've changed in smb.conf is the workgroup/user info and the directories I'm sharing.

oh, and I'm using a PCI RTL8139C NIC

---

### Post by Nephi on 2007-07-28
> **Nephi said:**
> I have the exact same problem with the on-board Realtek RTL8111/8158B Ethernet on my Abit AB9-pro motherboard.  I have tried using the newest R8168B driver from RealTek (ver 8.002.00, released 7/13/07) instead of the kernel's default R8159 driver, but with no change.

I am trying to use my Feisty Ubuntu system as a Samba share to the Windoze XP systems on my network.

Like other reports I've seen, I am able to get full throughput using scp, and I can get that too with Samba **only if** I have multiple transfers going at the same time!  But when a single file is being transfered at at time, I see only inconsistent bursts of traffic with sometimes long delays in between.

If this really is a problem with the Ethernet driver, then it's a bug that's being tickled by Samba.  I've kept the smb.conf file pretty much default, but would be happy to know if there is any parameter I can tweak to fix the problem.

Can someone help me find the solution?  Does smbd support verbose logging?

Thanks!

If I just keep multiple streams going, it works great, but it slows to a standstill if there is only one.

---

### Post by analogue on 2007-07-29
Ditto. With multiple file transfers over cifs/smbfs, I can get 40Megabytes/sec, but after cancelling all but one, it drops down to 350K - 1.5 Megabytes/sec.

---

### Post by Sadprof on 2007-07-30
Same problem here. Also using RTL8168B on an Asus mobo.
I only get decent speeds with samba when i generate heavy network-traffic (ie. multiple filetransfers, vnc and so on).
Current nic-driver: r8168-8.00.20
Samba updated by ubuntu itself.

---

### Post by zogbench on 2007-07-30
Sorry for the cross posts..

Have you tested the multiple streams out with a couple very large files?  Using 1 GB files I can only get a sustained high transfer rate for the first 120 MB for each file.  After that it slows to a crawl and one of the streams stalls.  The other continues on at about 30KB/s.

This is really frustrating!

---

### Post by zogbench on 2007-07-31
Here's another interesting thing.  When I transfer from Ubuntu to Windows XP and both are set to 1000baseT I get the very slow transfer rate of 30 KB/s.

When I downgrade the Windows XP network connection to 100baseT, it speeds the transfer up to 8 MB/s.

Arrghh!

---

### Post by Mandarine on 2007-08-19
Hi there,

I'm having the same Problem here. Samba 3.0.24 on Ubuntu 7.04 (amd64) access from Win XP.

Upload from WinXP -> Samba : Fast (about 12 Mb/s)
Download from Samba -> XP: Slow (down to 100 kb/s)

When I generate traffic, the speed increases.

In a german forum I read about these Issues only with amd64, with i386 it should work fine. Can anyone confirm that?

Any other hints / suggestions?

Sascha

---

### Post by teeks99 on 2007-08-22
I had the same problem with 64 and 32 bit.

---

### Post by al108 on 2007-08-28
I have similar problem with my Ubbuntu serever using both smbfs and cifs
Win > Server - fine
Server > Win - fine
Ubuntu Desktop > Server - fine
Server > Ubuntu Desktop - problem !!!
Problme also affects Windows under Vbox/VMware.

Works fine Both ways with NFS though. (not under Vbox thogh, I've installed NFS support for Win but it was just as slow as my Ubuntu host with Samba)
Using Realtek 8169 Gigabit Ethernet on my desktop. I think the problem might be driver related.

---

### Post by al108 on 2007-08-28
OK. [COLOR="Green"]Problem solved for me[/COLOR]. :guitar: I've had to reread my old post  [http://ubuntuforums.org/showthread.php?t=143982](http://ubuntuforums.org/showthread.php?t=143982) 

I've replaced my network card yet again with a D-link and it's working fine now.

---

