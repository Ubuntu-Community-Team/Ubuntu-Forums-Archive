---
title: "File Sharing and Permission"
date: 2010-04-17
forum: Server Platforms
---

### Post by imbty on 2010-04-17
Here's the background.

1x Windows Vista laptop (laptop1)
1x Windows 7 laptop (laptop2)
1x Mac laptop (laptop 3)

I am running Ubuntu server with 3 hard drives. I have Webmin installed.

So far, I have the three laptops being able to connect to samba and accessing /home/insert_user_here 

All laptop users have access to my /media/data2 (photographs, videos).

That's all good. At first, I couldn't get other users but laptop 3 to access /media/sdb1, but I fixed that by changing permission to 755 so I guess everyone can access this.

Atm, I want to only allow laptop #3 to connect to /media/sdd1 (be able to read/write/etc.) while laptop 1 and 2 can't even see the files. 

Thanks, guys.

Note: Also, laptop 1 and 2 can't seem to read and write through file share. Any help?

---

### Post by Morbius1 on 2010-04-17
I don't know if this was your intent but I'm going to take your post literally.

What you need is the "hosts allow" option.

For example suppose I have a share that I want to allow read / write access:

[myshare]]
path = /myshare
read only = no
public = yes

With that share definition everyone will be able to read and write to that share.

If I change it to this:

[myshare]]
path = /myshare
read only = no
public = yes
hosts allow = 192.168.0.100

Then only 192.168.0.100 ( which is say ... laptop#3 ) can read and write to that share.

"host allow" can take may forms:

ip address ( hosts allow = 192.168.0.100 )

host names ( hosts allow = laptop#1_machine_name, laptop#2_machine_name )
[COLOR=Blue]*This one's a little tricky - you know how samba is with resolving machine names *[/COLOR]

Range of ip addresses ( hosts allow = 192.168.0. )
[COLOR=Blue]* That's going to be every ip address in the 192.168.0.* range*[/COLOR]

Range of ip addresses except 1:
(hosts allow = 192.168.0. EXCEPT 192.168.0.102 )

"hosts allow" has a cousin named "hosts deny" that might also be useful.

---

