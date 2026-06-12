---
title: "Need help mounting Ubuntu Server drives as Windows Network drive"
date: 2010-04-20
forum: Server Platforms
---

### Post by M-ManLA on 2010-04-20
Ok I almost have this figured out. I have been looking on the forums and googling info trying to figure this out for the past two weeks. 

I have setup Ubuntu Server 9.10 in VirtualBox with Samba installed, and I think that I have finally got my Windows 7 OS to see the server (going to run then type \\ubuntuservername) . Now, I just need to map the folder to Windows to use it for a fileserver. I have made a few hard drives (sdb,sdc,sdd, ex. when I type "df" the drives shows up as dev/sdb ), and made a folder directory by using mkdir command. (music, data). But I can not figure out how to get it to where I can map the folder to the client machine. I did use /etc/fstab and added the data as "/dev/sdb /data ext3 defaults 0 0" and dev/sdb /music ext3 defaults 0 0". I also mounted with "sudo mount -a". 

I know I am forgetting a command, so if anyone can help me I will appreciate it.

---

### Post by R.Bucky on 2010-04-20
If I understand your issue, you would need to configure a Samba share and Map Network Drive in Windows with \\servername\sharename

---

### Post by M-ManLA on 2010-04-20
> **R.Bucky said:**
> If I understand your issue, you would need to configure a Samba share and Map Network Drive in Windows with \\servername\sharename
How will I create a Samba Share? Do you have any links or anything?

---

### Post by R.Bucky on 2010-04-20
You will need to install the Samba package using the apt-get and then read this ([https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")). It is fairly simple if you just want a read/write all access type of folder. A sample configuration might look like this in your /etc/samba/smb.conf.
[SHARE-NAME]
	writeable = yes
	public = yes
	path = /YOUR-FOLDER
        create mode = 777
        directory mode = 777
        allow hosts = 10.1.10.122, 10.1.10.30, 10.1.10.29, 10.1.10.62, 10.1.10.81

---

### Post by M-ManLA on 2010-04-20
> **R.Bucky said:**
> You will need to install the Samba package using the apt-get and then read this ([https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")). It is fairly simple if you just want a read/write all access type of folder. A sample configuration might look like this in your /etc/samba/smb.conf.
[SHARE-NAME]
	writeable = yes
	public = yes
	path = /YOUR-FOLDER
        create mode = 777
        directory mode = 777
        allow hosts = 10.1.10.122, 10.1.10.30, 10.1.10.29, 10.1.10.62, 10.1.10.81
Wow that is a lot of stuff. Still a little confused

put it in, but no luck. Maybe I'll reinstall it and start fresh again and see if it works.

---

### Post by M-ManLA on 2010-04-20
Ok see this is what I am getting 



[http://www.m-manla.com/media/pics/windowsubuntup1](http://www.m-manla.com/media/pics/windowsubuntup1)



It comes up when I go to "Run" then type in \\ubuntuserver, but there is no drives or no folders that I can share.

---

### Post by R.Bucky on 2010-04-20
Are you sure that the samba server is started? Start the server with **sudo /etc/init.d/samba start**. Next, see your samba shares with **sudo smbtree**. It will list all of your shares. Also, make sure that your samba share folder has the appropriate permissions.

---

### Post by Jive Turkey on 2010-04-20
Your share directive in smb.conf should look more like this:```

[music]
  comment = Music Folder
  writable = yes
  guest ok = yes
  path = /deb/sdb/music
```

Assuming you have a folder you want to share at /deb/sdb/music that anyone on your network can write in.

The ";" and "#" characters denote comments and those lines are ignored by samba.

another helpful command is "testparm" it will sometimes help you identify errors in your smb.conf

I have a similar situation as you do and my share directive looks like this```
[Music]
	comment = Music
	path = /moo/Music
	read only = No
	guest ok = Yes

``` where i have a partition mounted at /moo and a directory inside named Music.

---

### Post by M-ManLA on 2010-04-21
> **R.Bucky said:**
> Are you sure that the samba server is started? Start the server with **sudo /etc/init.d/samba start**. Next, see your samba shares with **sudo smbtree**. It will list all of your shares. Also, make sure that your samba share folder has the appropriate permissions.

> **Jive Turkey said:**
> Your share directive in smb.conf should look more like this:```

[music]
  comment = Music Folder
  writable = yes
  guest ok = yes
  path = /deb/sdb/music
```Assuming you have a folder you want to share at /deb/sdb/music that anyone on your network can write in.

The ";" and "#" characters denote comments and those lines are ignored by samba.

another helpful command is "testparm" it will sometimes help you identify errors in your smb.conf

I have a similar situation as you do and my share directive looks like this```
[Music]
    comment = Music
    path = /moo/Music
    read only = No
    guest ok = Yes

``` where i have a partition mounted at /moo and a directory inside named Music.


OK Guys. I'm SOOOO Close now I can taste it. The folders now show up, I can even map the files now, but When I click on them in windows it says;

"Windows cannot access \\ubuntuserver\MUSIC

Check the spelling of the name. Otherwise, there might be a problem with your network. to try to identify and resolve network problems, click Diagnose"

[http://www.m-manla.com/media/pics/ubuntuserverp2]("http://www.m-manla.com/media/pics/windowsubuntup2")

So I guess I have to set some kind of permission or something. Is there one more thing I'm missing?

---

### Post by R.Bucky on 2010-04-21
Try temporarily disabling your firewall on each machine to diagnose potential port blocking issues. Samba uses 137: udp and tcp, 138: udp and tcp, and 139: udp and tcp. The command for disabling the Linux firewall is **sudo /etc/init.d/ufw disable**. You are almost there.

---

### Post by tumandro on 2010-04-21
Are the permissions and user.group for the folder correct? Do a ls -l on it. Also, check the logs for samba after you try to connect and see what error it spits out. I believe they're in /var/log/samba/nmbd.log.

---

### Post by M-ManLA on 2010-04-22
> **R.Bucky said:**
> Try temporarily disabling your firewall on each machine to diagnose potential port blocking issues. Samba uses 137: udp and tcp, 138: udp and tcp, and 139: udp and tcp. The command for disabling the Linux firewall is **sudo /etc/init.d/ufw disable**. You are almost there.

I'll check it out. 

> **tumandro said:**
> Are the permissions and user.group for the folder correct? Do a ls -l on it. Also, check the logs for samba after you try to connect and see what error it spits out. I believe they're in /var/log/samba/nmbd.log.


I think that might be the problem. Will try it tomorrow nite after work.

---

### Post by 3L33T on 2010-04-27
ANY updates to this?   You've received some very good suggestions here :P

---

### Post by Morbius1 on 2010-04-27
I'm still trying to figure your how he did this:
> I did use /etc/fstab and added the data as "/dev/sdb /data ext3 defaults 0 0" and dev/sdb /music ext3 defaults 0 0". I also mounted with "sudo mount -a"You can't mount sdb. You can mount sdb1. 

So let's say that was just a typo and let's say what he really meant was this:
> /dev/sdb1 /music ext3 defaults 0 0So that's going to mount sdb1 to /music with owner=root and permissions set to 0755.

Now he's created a share. Let's say he did the last one he was offered in this thread:
```
[Music]
    comment = Music
    path = /music
    read only = No
    guest ok = Yes
```No matter how hard samba tries the remote guest will never be able to write to that share. Not unless he's done some chmod'ing somewhere along the line.

---

### Post by LiLoather on 2011-01-23
Bump:

Google led me here, and it was disappointing when the thread died unresolved as this is what I'm trying to do.

What I'd like to achieve is something along the lines of a Google drive - where the drive appears in Windows Explorer and is accessible just like any other drive after a simple log-in.

Can anyone point me at a good How-To?

---

### Post by Morbius1 on 2011-01-24
@LiLoather,

We don't know what version of Ubuntu you are using.
We don't know what version of Windows you are using.
We don't know where it is you need help. On the Linux end setting up a share. Or on the Windows end "mapping" a network drive.

---

