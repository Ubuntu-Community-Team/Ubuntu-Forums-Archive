---
title: "Transfer files from W7 to Ubuntu Server? (rsync is very slow)"
date: 2011-08-08
forum: Server Platforms
---

### Post by lessblue on 2011-08-08
I recently dove into Linux for the first time with Ubuntu Server (11.04). I had some [difficulty with my install]("http://ubuntuforums.org/showthread.php?t=1817815") on a HP Proliant Microserver, but I'm up and running now.

Right now I have several TBs of media on my Windows 7 machine which I would like to move to my Proliant Ubuntu Server. 

Initially, I tried using rsync first but only with mounted W7 drives. I couldn't figure out the command line for rsync across the network for some reason. So the transfer was between the local Ubuntu Server drive and the locally mounted W7 drive. This however was painfully and abnormally slow and I gave up on it. Figured it was better served after everything was transferred anyway.

I then figured since I could browse Ubuntu from my W7 machine across the network (smb is setup and mostly configured), I would just copy the files over to the Ubuntu Server that way.

Except that I had an error about permissions. So my W7 machine did not have permission to write to the Ubuntu Server drives and I'm not sure how to set those permissions in Ubuntu.

For now, I mounted the W7 drive again and using Webmin did a copy and paste between the mounted W7 drive and the local Ubuntu drive. Much, much faster than rsync but I still feel like it's not as fast as it could be. My router (Netgear WNDR3700) is gigabit and the NICs on my Proliant and W7 machine are also gigabit. 

Any pointers on what I should be looking at? 
Or how I could change permissions on the Ubuntu Server to allow my W7 machine to transfer files to it? Would that be faster than what I'm doing now (mounting the W7 drive first and copying via webmin)?

---

### Post by wojox on 2011-08-08
I've used [WinSCP]("http://winscp.net/eng/index.php") to copy from XP to Ubuntu Server. Worked great.

---

### Post by lessblue on 2011-08-08
> **wojox said:**
> I've used [WinSCP]("http://winscp.net/eng/index.php") to copy from XP to Ubuntu Server. Worked great.

Thank you, I installed it on my W7 machine, connected to the Ubuntu server and tried to copy files over via the WinSCP Explorer interface. This is the error I got from WinSCP:

Permission denied.
Error code: 3
Error message from server: Permission denied
Request code: 14

I had a file permission issue come up in W7 when I tried to copy directly from my W7 machine to the Ubuntu server over the network as well. 

Would someone kindly help me figure out setting permissions on the Ubuntu side to let W7 write to my Ubuntu drives?

---

### Post by lessblue on 2011-08-08
Well, I enabled the root account this time and logged in with WinSCP using root and now am able to copy.

Speed seems very slow though. Transferring a 6.5GB file and it says 35 mins remaining and transferring at about 3,000 KiB/s.

---

### Post by wojox on 2011-08-08
You tried copying them to your /home/<username>/ directory?

---

### Post by lessblue on 2011-08-08
> **wojox said:**
> You tried copying them to your /home/<username>/ directory?

I created a mydata directory at the root partition and within it created folders for each drive-partition in the server. The Ubuntu Servers drives are mounted there.

So I'm copying from my W7 machine to /mydata/hdb1  which is the first partition of the second disk (2TB) in the Ubuntu server.

I tried switching the protocol from SFTP to SCP this time at login and speed is slightly slower now, ~2,700 KiB/s.

There must be a faster way to transfer, everything is gigabit. I just can't figure it out.

---

### Post by garfonzo on 2011-08-09
Are you running over a wired network or a wireless one? 

I have the same setup -- Ubuntu Box with Drives accessible by Windows computers -- and I can transfer a 6.5GB chunk of pictures from my Vista machine to my Ubuntu server at 20-25MB/sec. The kicker is that I have my place wired with a Gigabit switch so everything is fast. 

A wireless N will max out at 300Mb/sec. Keeping in mind that this is the ideal situation, you're more likely to see 150Mb/sec speeds. So, depending on your setup, you might have a bottleneck.

Edit -- sorry, I just noticed your last post says everything is gigabit. Thus, my post is really useless.

---

### Post by lessblue on 2011-08-09
Yeah, everything is gigabit and both computers are directly wired to the Netgear router.

I was expecting speeds at least in the range you mentioned, 20-25 MB/sec.

How are you transferring the files between your windows and ubuntu boxes?

---

### Post by garfonzo on 2011-08-09
> **lessblue said:**
> Yeah, everything is gigabit and both computers are directly wired to the Netgear router.

I was expecting speeds at least in the range you mentioned, 20-25 MB/sec.

How are you transferring the files between your windows and ubuntu boxes?

My Ubuntu server has Samba running with 3 shares. All the shares are mounted at /mydata like you mentioned. I have a user created on my server with my name, Garfonzo. Then, on my Vista box, I use the same username and password (Garfonzo). That way I avoid dealing with multiple users and whatever. I know it isn't ideal, but it is my house and it was easy to not deal with multiple users for Samba. 

I have the server and the house WinXP computers all on the same WorkGroup. This is important. I've noticed that a Win7 computer can still see all the computers on the LAN even if the Win7 computer is not on the same Workgroup. So, slap the all computers on the network on the same workgroup. 

On my Vista box, I open up "Network Places" and view all computers on the Workgroup. When my server pops up, I double click it and see that the shares are there, looking like network drives. Then I map these network drives to drive letters on my Vista box. That way I have easy access to all my server data. When I want to transfer stuff to the server, I just drag and drop from the Vista box over to the mapped network drive. Although I have used WinSCP in other scenarios, I don't use it at home. Drag-n-drop works fine. 

Some things you may want to try:
[LIST]
[*]Put server and Win7 machine on same workgroup (edit smb.conf WORKGROUP area)
[*]Use the exact same username and password on the Win7 machine as the server. Log into that user name account on the Win7 machine and try to connect to the server.
[/LIST]

---

### Post by lessblue on 2011-08-09
> **garfonzo said:**
> My Ubuntu server has Samba running with 3 shares. All the shares are mounted at /mydata like you mentioned. I have a user created on my server with my name, Garfonzo. Then, on my Vista box, I use the same username and password (Garfonzo). That way I avoid dealing with multiple users and whatever. I know it isn't ideal, but it is my house and it was easy to not deal with multiple users for Samba. 

I have the server and the house WinXP computers all on the same WorkGroup. This is important. I've noticed that a Win7 computer can still see all the computers on the LAN even if the Win7 computer is not on the same Workgroup. So, slap the all computers on the network on the same workgroup. 

On my Vista box, I open up "Network Places" and view all computers on the Workgroup. When my server pops up, I double click it and see that the shares are there, looking like network drives. Then I map these network drives to drive letters on my Vista box. That way I have easy access to all my server data. When I want to transfer stuff to the server, I just drag and drop from the Vista box over to the mapped network drive. Although I have used WinSCP in other scenarios, I don't use it at home. Drag-n-drop works fine. 

Some things you may want to try:
[LIST]
[*]Put server and Win7 machine on same workgroup (edit smb.conf WORKGROUP area)
[*]Use the exact same username and password on the Win7 machine as the server. Log into that user name account on the Win7 machine and try to connect to the server.
[/LIST]

My setup is pretty much exactly the same. I did edit the smb.conf file to match the workgroup. I use the same username and password on all my computers at home to make networking easier.

The problem I have is drag and drop doesn't work because I don't have the permissions set it seems on my Ubuntu box to allow my W7 machine to write to it. If I can figure this out it would probably fix my transfer speed problem.

---

### Post by garfonzo on 2011-08-09
> **lessblue said:**
> My setup is pretty much exactly the same. I did edit the smb.conf file to match the workgroup. I use the same username and password on all my computers at home to make networking easier.

The problem I have is drag and drop doesn't work because I don't have the permissions set it seems on my Ubuntu box to allow my W7 machine to write to it. If I can figure this out it would probably fix my transfer speed problem.

I just looked at my shared directories on the server. I have those folders' permissions set to full read/write/exe access.

Maybe do a ```
chmod /mydata -R 777
``` on your shared directories. Maybe that is the reason you can't access the files from Win7? Do you have another computer with Vista or WinXP that you could use to try to access the server? Maybe it is a Win7 issue. If you could verify that you are having the same permissions issue on all computers, then you know that it is a server setup thing. However, if you can access the shares from WinXP or Vista, then it is a Win7 issue. This might help narrow down the problem.

---

### Post by dtfinch on 2011-08-09
Using a network share defeats the entire purpose of using rsync. You really need it running on the Windows server for it to work right.

I have the cwRsync port installed on our Windows servers, which hosts rsync as a service. In your rsyncd.conf, you'd set your paths in the cygwin fashion (so something like "C:\data" would become exactly "/cygdrive/c/data").

You'll also want to use the -t and --modify-window options. Windows has different file time resolution, so without a modify window rsync will think most files have changed when they haven't. --modify-window=5 is probably good enough.

---

### Post by lessblue on 2011-08-09
> **garfonzo said:**
> I just looked at my shared directories on the server. I have those folders' permissions set to full read/write/exe access.

Maybe do a ```
chmod /mydata -R 777
``` on your shared directories. Maybe that is the reason you can't access the files from Win7? Do you have another computer with Vista or WinXP that you could use to try to access the server? Maybe it is a Win7 issue. If you could verify that you are having the same permissions issue on all computers, then you know that it is a server setup thing. However, if you can access the shares from WinXP or Vista, then it is a Win7 issue. This might help narrow down the problem.

Thank you garfonzo, i"m going to look into that.

> **dtfinch said:**
> Using a network share defeats the entire purpose of using rsync. You really need it running on the Windows server for it to work right.

I have the cwRsync port installed on our Windows servers, which hosts rsync as a service. In your rsyncd.conf, you'd set your paths in the cygwin fashion (so something like "C:\data" would become exactly "/cygdrive/c/data").

You'll also want to use the -t and --modify-window options. Windows has different file time resolution, so without a modify window rsync will think most files have changed when they haven't. --modify-window=5 is probably good enough.

Absolutely, I was trying it out to do the initial transfer via rsync just to get a feel for it and get my hands a little dirty. Then noticed it was horribly slow. I probably did not configure W7 for rsync correctly. Looked into DeltaCopy and cwrsync but dropped it for now because I don't plan on rsync'ing between W7 and Ubuntu in the end. 

Meaning right now I just need to transfer the files from my W7 machine to my new Ubuntu server. Afterwards, I plan on taking that W7 drive, format it to ext3 and install it on another Proliant Ubuntu Server (backup server, I have two HP Proliant Microserver's). This is where I plan to use rsync: sync the primary Proliant Ubuntu Server to the backup Proliant Server.

This initial transfer of files from W7 -> HP Ubuntu Server would be easier if I can figure out how to get my primary Ubuntu Server to allow my W7 box to write to it.

---

### Post by YesWeCan on 2011-08-09
You may wish to consider NFS. Windows can mount an NFS share: [http://technet.microsoft.com/en-us/library/cc754350.aspx](http://technet.microsoft.com/en-us/library/cc754350.aspx)
I haven't tried this from Windows myself but I read from another member that it is a fast method for data transfer.

---

### Post by lessblue on 2011-08-09
> **YesWeCan said:**
> You may wish to consider NFS. Windows can mount an NFS share: [http://technet.microsoft.com/en-us/library/cc754350.aspx](http://technet.microsoft.com/en-us/library/cc754350.aspx)
I haven't tried this from Windows myself but I read from another member that it is a fast method for data transfer.

Thank you for your help in the other thread, I used tune2fs in the end to free up the space. 

Going to read up on that link regarding NFS.

Though I do wonder if there is an option/setting I missed in Ubuntu that would allow W7 to write as well as read an Ubuntu partition.

---

### Post by YesWeCan on 2011-08-09
> **lessblue said:**
> Thank you for your help in the other thread, I used tune2fs in the end to free up the space. 

Going to read up on that link regarding NFS.

Though I do wonder if there is an option/setting I missed in Ubuntu that would allow W7 to write as well as read an Ubuntu partition.
It has been quite some time since I set up Samba shares on my Ubuntu 10.04 server. Configuring Samba seems to drain the life-force from my body. If it is of any help this is the essence of the smb.conf file I use:

```
[global]
workgroup = Home
netbios name = Tofu
security = user
interfaces = 127.0.0.1 eth0
bind interfaces only = yes
hosts allow = 192.168.1.0/24
hosts deny = #none
encrypt passwords = true
smb passwd file = /etc/smbpasswd
local master = no
dns proxy = no
smb ports = 139

[Share]
path = /srv/Share
browsable = yes
guest ok = no
read only = no
create mask = 0755

[homes]
   comment = Home Directories
   browseable = no
```

Personally, if I were trying to do what you are I would either use a Windows SSH client (like filezilla) for ease or enable NFS on the server and mount it on the Windows client for speed. As I say I have never used NFS for this but only heard it recommended. Obviously, between linux machines NFS is very good.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by lessblue on 2011-08-10
Thank you again YesWeCan for posting that smb file. It has prompted me to look deeper into Samba configuration via webmin and via editing the smb.conf file.

On the issue of permissions, this link has helped tremendously:

[http://www.zzee.com/solutions/unix-permissions.shtml](http://www.zzee.com/solutions/unix-permissions.shtml)

I now understand permission and their textual and numerical representations.

By textual representations I mean the 10 digit representation when running the command $ ls -l  (i.e. drwxr-xr-x).

By numeric I mean chmod usage (i.e. 777, 744, 755, etc...).

As a result, I see that I can't write because the drives are only have read/execute permission (no write) so I'm working on changing that in the Samba Server share creation settings. Hopefully that let's me simply transfer over the network. Do want to read further on setting up a more secure server with permissions.

---

### Post by lessblue on 2011-08-11
After learning about permissions, I ran through the Samba Server configuration on Webmin again and sorted it out.

I can now transfer files from my W7 machine to the Ubuntu server data drives.

Thanks to all those who helped.

**Edit: Just a final update, now that I can write from W7 to the Ubuntu drives, windows is showing transfer speeds in the 60-65 MB/s range. Much better.

---

