---
title: "Problem with file permissions/ownership of a public Samba share"
date: 2007-04-28
forum: Server Platforms
---

### Post by quirks on 2007-04-28
Hey folks!

I have created a public Samba share in a mixed Windows/Ubuntu network, which may be used to freely move files between two PCs. Everything works nicely so far: everyone in the network can access the share and insert/modify/delete files on it. I have told Samba to create files with the permissions rw-rw-rw- and the owner nobody and the group nogroup. This way, anybody may access the files in the public share, which is quite comfortable to use.

My problem is that when somebody puts a file on the share via SMB, the owner is nobody/nogroup - as mentioned above - and when someone else copies the file into his/her profile to "fetch" it, this owner is retained. But then you can't change the permissions of the file, because you are not the owner of it and you can only change the owner when you are an adminstrator (i.e. you can sudo, which is only allowed for a few users).

How can I achieve that one has full control over the file after copying it into his/her own profile while keeping the transfer of files from one machine to the other simple? (I should mention, that I am currently trying to introduce Ubuntu to the rest of my family, so the solution should be SIMPLE. That is, I can't tell them to run some geekish shell commands after copying. This would tremendously decrease the acceptance of Linux. Ideally it should be a drag'n'drop job.)

Any help is very much appreciated!

---

### Post by misconfiguration on 2007-04-30
Show your config file? If you want everyone to browse/write you need to specify that.

#example
; pub
[pub]
; example smb config / pub
   comment = Shared DIR
   browseable = yes
   writable = yes
   path = /path/to/your/share/dir
   public = yes

I myself like to employ strict rules for ppl on my network, I allow everyone to read but only I can write, I have a custom folder setup for uploading then I distribute the files accordingly. You could also set it up where everyone has their own username//login and they can have access to their "home" dirs remotely.

---

### Post by Deb.Early on 2008-03-11
> **quirks said:**
> 
My problem is that when somebody puts a file on the share via SMB, the owner is nobody/nogroup - as mentioned above - and when someone else copies the file into his/her profile to "fetch" it, this owner is retained. But then you can't change the permissions of the file, because you are not the owner of it and you can only change the owner when you are an adminstrator (i.e. you can sudo, which is only allowed for a few users).

Hi there! Did you ever get this resolved? Because I may have what boils down to the same problem with WinXP machines using an Ubuntu desktop's share, despite a section in the Ubuntu machine's smb.conf that looks like the one "misconfiguration" posted. 

The scenario goes as follows: 

```
dearly@Mercury:~/Public$ ls -l
total 4
-rw-rw-rw- 1 dearly dearly  523 2008-03-10 22:12 Questions.txt
dearly@Mercury:~/Public$
```
Somebody on a WinXP machine edits/saves "Questions.txt", then...
```
dearly@Mercury:~/Public$ ls -l
total 4
-rwxr--r-- 1 nobody nogroup 523 2008-03-11 17:14 Questions.txt
dearly@Mercury:~/Public$ 
```

Now the person using the Ubuntu machine can't do anything other than read the file.

Anyone kind enough to help, here's my smb.conf file (Gutsy desktop install, native filesystem):
```
[global]
workgroup = EPSILON
netbios name = Mercury
server string = ""
map to guest = Bad User
passdb backend = tdbsam
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
dns proxy = No
panic action = /usr/share/samba/panic-action %d
socket options = IPTOS_LOWDELAY TCP_NODELAY
invalid users = root
name resolve order = bcast host lmhosts wins
printing = cups
printcap name = cups
cups options = raw
use client driver = yes
browseable = true
wins support = no

[Public]
path = /home/dearly/Public
available = yes
browsable = yes
public = yes
writable = yes
```

I was a computer professional for 30 years before I retired, but Linux was always my oldest son's thing and I feel like Bozo the Clown with a shotgun, here...  :redface:

---

