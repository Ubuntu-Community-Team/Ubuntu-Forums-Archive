---
title: "Samba users able to browse folders they don't have permission to browse"
date: 2011-02-11
forum: Server Platforms
---

### Post by iiz on 2011-02-11
I've set up smbd 3.4.7 on 10.04x64 LTS server. I've set up a couple shares and i'm having problems blocking access to certain directories using native file permissions. There is one directory that has folders for each sales rep to store their current list of quoted clients, i only want sales people to be able to browse the directories owned by themselves. Everything seems to be set up correctly in terms of user groups and permissions on the filesystem.

Below is marina, a sales rep, and brian, a super user of sorts.
id marina:
```
uid=1011(marina) gid=1006(office) groups=1006(office),1005(sales)
```

id nick:
```
uid=1000(brian) gid=1006(office) groups=1006(office),118(admin),1001(full),1002(processing),1003(management),1004(it),1005(sales)
```

Below is the directory with all the sales reps folders.

ls -la:
```
total 60
drwxrwxr-x 15 root    it         4096 2011-02-10 20:06 .
drwxr-x---  9 root    office     4096 2010-11-19 12:40 ..
drwxrwx--- 13 katya   full       4096 2010-12-07 12:36 Katya
drwxrwx--- 18 lana    full       4096 2011-02-08 17:09 Lana
drwxrwx--- 23 marina  full       4096 2011-02-10 18:09 Marina
drwxrwx---  4 mike    full       4096 2011-02-01 12:42 Mike

```

With this setup marina only be able to browse her folder, but she can browse all folders and has full write access to all folders. This leads me to believe something is up with the smbd.conf file, which is below.

```
[global]
	workgroup = COMTREAD
	null passwords = no
	server string = Root Server
	dns proxy = no
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	security = user
	encrypt passwords = true
	passdb backend = tdbsam
	obey pam restrictions = yes
	unix password sync = no
	map to guest = never

##################################
## Default settings for all shares
guest ok = no
invalid users = root
create mask = 0760
directory mask = 7770
force create mode = 0760
force create directory = 0770
force group = comtread
force user = root
writable = yes

[ftp-root]
	comment = Server Root
	path=/mnt/raid/shares/ftp-root
	browseable = yes
	inherit permissions = yes

[database]
	comment = Database
	path=/mnt/raid/shares/database
	browseable = yes

[db2]
	comment = Secondary Database
	path = /mnt/raid/shares/DB2
	browseable = no
	
[www]
	comment = HTTP
	path=/mnt/raid/www
	browseable = no
	force user = www-data
	force group = www-data
```

In this case the *valid users* directive would not work cause I am not making a share for each user. I had this on other shares like the db2 share. My windows box lagged heavily when I tried to access that share with an invalid user.

If anyone knows how to deny users the ability to modify permissions I would also like to do that.

Thank you!

---

### Post by elico on 2011-02-11
the problem is your global options:
and i will hilight it : "force user = root" and "writable = yes"

```
## Default settings for all shares
guest ok = no
invalid users = root
create mask = 0760
directory mask = 7770
force create mode = 0760
force create directory = 0770
force group = comtread
force user = root
writable = yes
```the users login  as their users but the samba is forcing the writable and the root user that will make them able to do what ever they want.

dont force any group and users and use these settings instead.
```
## Default settings for all shares
 guest ok = no
 invalid users = root
#create mask = 0760
#directory mask = 7770
#force create mode = 0760
#force create directory = 0770
#force group = comtread
#force user = root
#writable = yes
writable = no


```also a much more simple way will be to setup a share like using %u paramater and an example is:
(i dont now the full path of the user storage direcotry
```
#============================ Share Definitions ==============================
[agent_data]
   comment = Home Directory for %S
#   path = /home/%u
   path = /mnt/raid/shares/%u
   force user = %u
   browseable = no
   writable = yes
   valid users = %u 
# This test share works perfectly.. Only allows those users listed. All
other
```

---

### Post by iiz on 2011-02-11
Thank you for the reply. Removing force user and force group did the trick. For some reason i was under the impression that was forcing directory and file ownership/group.

Handled the file and directory preservation using chmod u+s

Thanks again.

---

### Post by elico on 2011-02-12
happy it helped you.

---

