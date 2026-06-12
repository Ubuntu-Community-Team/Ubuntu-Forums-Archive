---
title: "Samba no write priv?"
date: 2009-11-17
forum: Server Platforms
---

### Post by TironN on 2009-11-17
Hey guys, I just set up samba and I have got a share that I connect to fine but I have no write only read.
So here is what i have in my config:

[Pub]
    force create mode = 755
    writeable = yes
    path = /public
    force directory mode = 755


What else do I need (or not need) to get this going?

Thanks, Fergus

---

### Post by capscrew on 2009-11-17
> **TironN said:**
> Hey guys, I just set up samba and I have got a share that I connect to fine but I have no write only read.
So here is what i have in my config:

[Pub]
    force create mode = 755
    writeable = yes
    path = /public
    force directory mode = 755


What else do I need (or not need) to get this going?

Thanks, Fergus

Have you added yourself to the Samba users database?```
 smbpasswd -a <youruser_name>
```

---

### Post by uberamd on 2009-11-17
If you set the local permissions on the server folder to 777 can you write? I usually start there and work backwards with Samba permissions problems.

---

### Post by dca on 2009-11-17
You should be able to add:
 
read only = no
 
into the other stanzas in smb.conf file...
 
then:
 
/etc/init.d/samba restart
 
then:
 
sudo smbpasswd -a <username> ###to add user
sudo smbpasswd -e <username> ###to enable the user

---

### Post by dca on 2009-11-17
Here's my Public share in smb.conf: 
 
[I][Public]
comment = Home share
path = /home/Public
guest ok = no
writable = yes
browseable = no
valid users = dca[/I]

---

### Post by gufran777 on 2009-12-26
What are the permissions and the ownership of the directory being shared?

For a public writable service, the directory should have the same permissions as the /tmp directory, 
sudo chmod a=rwxt <directory> will fix the problem.  

However, the share is in /media/ which makes me wonder what kind of filesystem is on it and whether this is a removable drive.
we can bring you wholesale prices on [Isuzu Power Steering Rack](http://www.powersteeringpros.com/Isuzu_Power_Steering_Rack.htm) through our national chain of warehouses

If the user has an account in samba, you should use the "smbpasswd" program to add the user & password to samba's /etc/samba/smbpasswd file, which serves a similar function as Linux's /etc/passwd & /etc/shadow files. Ideally you want to keep the usernames & passwords identical for Linux & Windows users.

If this is a public share that any user can access, make sure to use the "map to guest = bad user" option in the share definition or the [global] definition. This will give unknown users the username of nobody.
____________________________________________________________
[Find Contractors]("http://www.homeimprovementcorner.com/contractors_by_state.php")
[home painting colorado]("http://www.homepaintingcolorado.com")

---

