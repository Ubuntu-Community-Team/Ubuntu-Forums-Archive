---
title: "[SOLVED] The Most Basic Samba Server"
date: 2008-10-13
forum: Server Platforms
---

### Post by wordie on 2008-10-13
I would (very much) like to have a file server at home where I can store my music, video and pictures, safely backed up. I use MythTv on separate box, so the video section is quite large (500Gb). I recently lost 160GB worth to a hard drive failure...

I've got a 1GHz Athlon with 512MB Ram and a 160GB WDC IDE Drive, plus 2x500GB USB Drives for the main backup. At the moment I have 8.04 installed, but have yet to get Samba working properly.

My smb.conf file is below, niftily adapted from [this link:]("http://www.linux.com/articles/58593")

[INDENT]
# Global parameters
[global]
       workgroup = 110A
       netbios name = SAMBA
       server string = Samba Server %v
       map to guest = Bad User
       log file = /var/log/samba/log.%m
       max log size = 50
       socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
       preferred master = No
       local master = No
       dns proxy = No
       security = User

# Share
[FileServer]
       path = /storage/share
       valid users = mythtv
       read only = No
       create mask = 0777
       directory mask = 0777
[/INDENT]

I then added a single samba user - mythtv (the user name and password are a fixed requirement of using MythTV) to match the one I already use this to log onto Windows.

Anyway, when I browse to Network Places, I can see the share and the folders internally, but I can't write to them.

Any thoughts on this would be much appreciated.

Cheers

Nick

---

### Post by Iowan on 2008-10-13
Try adding a "write list = mythtv" line to the [FileServer] share. Or, you could check ownership of that directory - and **chown**  to mythtv.

---

### Post by lykwydchykyn on 2008-10-13
My guess is that your user does not have write access at the filesystem level.  This is the #1 thing that trips people up about Samba -- both samba and filesystem permissions apply, and the most restrictive wins out.  This is true both on Linux servers and Windows servers.  

Check this:
```

ls -l /storage/share

```

And paste the output here if you're not sure.

---

### Post by wordie on 2008-10-14
nick@ubserver:~$ ls -l /storage
total 4
drwxr-xr-x 3 root root 4096 2008-10-14 09:00 share
nick@ubserver:~$

It looks like the group and users only have read and execute access. Is that right?

So I've done this

nick@ubserver:/storage$ sudo chown mythtv:mythtv /storage/share
nick@ubserver:/storage$ ls -l /storage
total 4
drwxr-xr-x 3 mythtv mythtv 4096 2008-10-14 09:00 share
nick@ubserver:/storage$

But still no access. Do I need to restart/logout of Windows as well as samba?

---

### Post by lykwydchykyn on 2008-10-14
Is your security mode set to 'user' or "share"?  You want it set to "user" in this case.

---

### Post by wordie on 2008-10-14
Actually, it's now working. I restarted my windows machine and it now seems to let me read and write.

Once I've realised what made the difference I'll mark the thread Solved. I'll also try logging in as a different person and see what effect that has.

Thank you all for your help.

Cheers
Nick

---

### Post by wordie on 2008-10-14
Ok

I retried this and got it to work on my other PC - the MythTV machine

[root@mypc using FC8]# nano /etc/samba/smb.conf

#Global parameters
[global]
       workgroup = 110A
       netbios name = MYTHAMBA
       server string = Samba Server %v
       map to guest = Bad User
       log file = /var/log/samba/log.%m
       max log size = 50
       socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
       preferred master = No
       local master = No
       dns proxy = No
       security = User

# Share
[MythShare]
       path = /storage/mythshare
       valid users = mythtv
        write list = mythtv


[root@mypc using FC8]# smbpasswd -a mythtv
New SMB password:
Retype new SMB password:
startsmbfilepwent_internal: file /var/lib/samba/private/smbpasswd did not exist. File successfully created.
Added user mythtv.
[root@mypc using FC8]# testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[MythShare]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = 110A
        netbios name = MYTHAMBA
        server string = Samba Server %v
        map to guest = Bad User
        log file = /var/log/samba/log.%m
        max log size = 50
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        preferred master = No
        local master = No
        dns proxy = No

[MythShare]
        path = /storage/mythshare
        valid users = mythtv
        write list = mythtv
[root@mypc using FC8]# mkdir /storage/mythshare
[root@mypc using FC8]# chmod 0777 /storage/mythshare    
[root@mypc using FC8]# chown mythtv /storage/mythshare
[root@mypc using FC8]# service smb restart

oops - this should be  # /etc/init.d/samba restart !the one above is FC8 speak!

Shutting down SMB services:                                [  OK  ]
Starting SMB services:                                     [  OK  ]
[root@mypc using FC8]# exit

Then log out of your windows box and log back in using the user and password specified. In my case my windows user is mythtv.

Then go to Windows Explorer and type \\the.ipa.ddr.ess. of your server (e.g. 192.168.1.100) and hit enter.

Hey Presto! Map the drive and you are done!

---

### Post by Iowan on 2008-10-14
If you're feeling brave, try commenting out the "write list = mythtv" line, restart samba (/etc/init.d/samba restart) and see if you still have write access. If not, uncomment the line - if so, leave the line commented - or delete it.

---

