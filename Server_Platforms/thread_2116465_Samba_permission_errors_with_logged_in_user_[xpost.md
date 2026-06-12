---
title: "Samba permission errors with logged in user [xpost]"
date: 2013-02-15
forum: Server Platforms
---

### Post by deflin39 on 2013-02-15
I've setup a samba server and successfully integrated it with the unix accounts on the box. I am using Samba-3.6.3 on Ubuntu 12.04.

I've setup three shares: share, myuser, and private. The myuser share is simply my home directory. The other two shares point to directories under /srv/samba.

When not logged in I can read and write to the share group. When I login under myuser account I can read and write to myuser share (just my home directory). I can read but not write to share. I cannot read or write to private.

This happens whether I use a Mac remote connecting or Nautilus on the same computer hosting Samba. 

**File system listing for the community shares:**
```
myuser@burns:/srv/samba$ ls -la
total 16
drwxr-xr-x 4 nobody   nogroup  4096 Feb  9 13:35 .
drwxr-xr-x 3 root     root     4096 Feb  9 11:43 ..
drwxr-xr-x 2 nobody   nogroup  4096 Feb  9 14:44 private
drwxr-xr-x 9 nobody   nogroup  4096 Feb  9 14:33 share
File system listing myuser directory:
```


```
myuser@burns:/home$ ls -la
total 12
drwxr-xr-x  3 root     root     4096 Jul 28  2012 .
drwxr-xr-x 24 root     root     4096 Jan 18 18:17 ..
drwxr-xr-x 68 myuser   myuser   4096 Feb  9 14:42 myuser

```

**Relevant /etc/samba/smb.conf sections**
```

[share]
	comment = Raw File Server Share
	path = /srv/samba/share
;	browseable = yes
	guest ok = yes
	writeable = yes
	create mask = 0755

[private]
	comment = private
	path = /srv/samba/private
;	browseable = yes
	valid users = myuser
	writeable = yes
	create mask = 0755
        read only = no

[myuser]
        comment = myuser home
        path = /home/myuser
;       browseable = yes
        valid users = myuser
        writeable = yes
        create mask = 0755
        read only = no
```

**Relevant output from testparm**
```
[share]
	comment = Raw File Server Share
	path = /srv/samba/share
	read only = No
	create mask = 0755
	guest ok = Yes

[private]
	comment = private
	path = /srv/samba/private
	valid users = myuser
	read only = No
	create mask = 0755

[myuser]
	comment = myuser home
	path = /home/myuser
	valid users = myuser
	read only = No
	create mask = 0755
```

I do not see any information in the log files that has been helpful to me at least. As a test I tried giving full permissions to my user for the /private directory but that still didn't help (and isn't what I want anyway). Anyone have ideas or links to point me in the correct direction? Any additional information I can provide? Thanks in advance.

[https://help.ubuntu.com/12.04/server...ileserver.html](https://help.ubuntu.com/12.04/server...ileserver.html)
[https://help.ubuntu.com/12.04/server...-security.html](https://help.ubuntu.com/12.04/server...-security.html)
[http://ubuntuforums.org/showthread.php?t=2114312](http://ubuntuforums.org/showthread.php?t=2114312)

---

### Post by brent1975 on 2013-02-15
aren't you missing the ```
write list = user1, user2
``` for each one of your shares you want users to write to?

Mine looks like this

```

[www]
        path = /var/www
        username = brent
        write list = brent

[Brent]
        path = /home/brent
        valid users = brent
        write list = brent

[Jessica]
        path = /home/jessica
        valid users = brent, jessica
        write list = brent, jessica
[movies]
        path = /home/movies
        valid users = brent, jessica
        write list = brent, jessica
```

---

### Post by deflin39 on 2013-02-16
*write list* has no effect on any of the shares. What really puzzles me is why I can write to guest when I'm not authenticated as a user but not when I'm authenticated.

---

### Post by Morbius1 on 2013-02-16
[COLOR=Blue]**NOTE**: Would somebody please remove that Samba Howto in help.ubuntu.com.[/COLOR]

> drwxr-xr-x 9 nobody   nogroup  4096 Feb  9 14:33 shareOnly one person getting write access to that share and it's nobody. That’s fine if you never ever authenticate anyone but the minute you do he's no longer nobody. Change the share definition to this:
> [share]
    comment = Raw File Server Share
    path = /srv/samba/share
;    browseable = yes
    guest ok = yes
    writeable = yes
[COLOR=Blue]**    force user = nobody**[/COLOR]
    create mask = 0755
Then restart samba:
```
sudo service smbd restart
```

---

### Post by Morbius1 on 2013-02-16
Sorry, missed the thing about [private]:
> drwxr-xr-x 2 nobody   nogroup  4096 Feb  9 14:44 privateYou've got 2 choices here:

** You can do the "force user" thing again:
> [private]
    comment = private
    path = /srv/samba/private
;    browseable = yes
    valid users = myuser
    writeable = yes
[COLOR=Blue]**    force user = nobody**[/COLOR]
    create mask = 0755
        read only = no** Or keep the share just like it is and simply change ownership of the target to "myuser":
```
sudo chown myuser /srv/samba/private
```

---

### Post by deflin39 on 2013-02-16
Thanks for the input. *force user = nobody* worked for the guest share. For the private share it did not. Even though it's not what I want I went ahead and tried to change ownership of the /srv/samba/private folder to my user and I was still not able to write or read from it (I have a single file in the directly with nobody/nogroup ownership).

**testparm:**
```
[private]
	comment = private
	path = /srv/samba/private
	valid users = myuser
	write list = myuser
	force user = nobody
	read only = No
	create mask = 0755
```

[B]Directory listing:
[/B]```
myuser@burns:/srv/samba$ ls -la
total 16
drwxr-xr-x 4 nobody nogroup 4096 Feb  9 13:35 .
drwxr-xr-x 3 root   root    4096 Feb  9 11:43 ..
drwxr-xr-x 2 nobody nogroup 4096 Feb  9 16:28 private
drwxr-xr-x 3 nobody nogroup 4096 Feb 16 15:42 share
```

---

### Post by Morbius1 on 2013-02-16
> Even though it's not what I want I went ahead and tried to change  ownership of the /srv/samba/private folder to my user and I was still  not able to write or read from it (I have a single file in the directly  with nobody/nogroup ownership).Define read / write. You cannot read ( access ) or write ( add to ) the contents of the private folder. Or you cannot read / edit the contents of the file within that folder.

Post the output of this please:
```
ls -al /srv/samba/private
```

---

### Post by deflin39 on 2013-02-16
If I am not logged in I cannot access private. If I am logged in then I can access private but 1) cannot see any files 2) cannot create any files. (**access directory**: On my mac I can enter the folder but nothing appears. On my linux box using nautilus I cannot even access the directory).

```
myuser@burns:/srv/samba/private$ ls -la /srv/samba/private/
total 12
drwxr-xr-x 2 nobody   nogroup  4096 Feb 16 16:47 .
drwxr-xr-x 4 nobody   nogroup  4096 Feb  9 13:35 ..
-rw-r--r-- 1 myuser   myuser      0 Feb 16 16:47 bar.txt
-rw-r--r-- 1 nobody   nogroup     5 Feb  9 16:28 foo.txt
```

---

### Post by deflin39 on 2013-02-16
In case the output of smbclient helps any:

```
myuser@burns:/srv/samba/private$ smbclient //burns/private
Enter myuser's password: 
Domain=[SPRINGFIELD] OS=[Unix] Server=[Samba 3.6.3]
smb: \> ls
NT_STATUS_ACCESS_DENIED listing \*
```

I'll start googling NT_STATUS_ACCESS_DENIED.

---

### Post by Morbius1 on 2013-02-16
You've added too many lines to your share definition:
> [private]
    comment = private
    path = /srv/samba/private
    [COLOR=Blue]valid users = myuser
    write list = myuser
    force user = nobody[/COLOR]
    read only = No
    create mask = 0755You can have a "valid user" and a "force user" together becase the two happen at differnt times. But you cannot have a "write list" and a "force user" together since at that point everyone is "nodody" so no one can write. Get rid of the "write list".

This should have nothing to do with reading it I'm just working my up.

---

### Post by deflin39 on 2013-02-16
Removed "write list", explanation makes sense thanks.

The problem ended up being apparmor. Ugh. I updated it when I created /share but not when I went back and added /private.

dmesg provided the details: 
```
[605072.939116] type=1400 audit(1361055644.660:824): apparmor="DENIED" operation="open" parent=3966 profile="/usr/sbin/smbd" name="/srv/samba/private/" pid=4487 comm="smbd" requested_mask="r" denied_mask="r" fsuid=65534 ouid=65534
[605083.332343] type=1400 audit(1361055655.056:825): apparmor="DENIED" operation="open" parent=3966 profile="/usr/sbin/smbd" name="/srv/samba/private/" pid=4494 comm="smbd" requested_mask="r" denied_mask="r" fsuid=65534 ouid=65534
```

Thank you Morbius1 and brent1975 for taking the time to respond to my post.

---

