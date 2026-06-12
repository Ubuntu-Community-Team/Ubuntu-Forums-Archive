---
title: "Samba On Ubuntu"
date: 2009-09-16
forum: Server Platforms
---

### Post by raflexras on 2009-09-16
I have just install the desktop version of Ubuntu. I was wondering if this version include the Samba Server packages, and if it doesn't, where can I get it from...
 
Thanks
 
RAS

---

### Post by ChumleyEX on 2009-09-16
Easy enough, you can either go to administration and the package manager, search for samba and install it, or try opening a terminal windows and type

sudo apt-get install samba

---

### Post by Johnsie on 2009-09-16
You can also right click a folder and use the sharing options.

---

### Post by geek-n-out on 2009-09-16
Pretty much all would be the same between desktop and server.  Here is what I would do:

Open terminal

```


sudo su
apt-get update
apt-get upgrade

apt-get install --yes samba


```

Remeber to backup your smb.conf file:

```


cp /etc/samba/smb.conf /etc/samba/smb.conf.bak


```

I like nano cuz I'm a panzy...

```


nano /etc/samba/smb.conf


```

change workgroup to your network workgroup...

```


workgroup = WORKGROUP


```


create a share at the very bottom of your smb.conf file...

```


[share name]
comment = something about the share
path = /path/to/filetoshare
browseable = yes
public = no
writable = yes


```

ctrl-x to save and exit.

Make the directory...

```


mkdir /path/to/filetoshare
chmod 0700 /path/to/filetoshare


```

Restart Samba

```


/etc/init.d/samba restart


```

There you go that should get you going.

:)

---

### Post by raflexras on 2009-09-16
This was easy stuff, I have been using fedora 4, forever and decided to move tou buntu. Thank you all for your help, I'm not used to the fact that ubuntu can be so easy for a linux distribution.
 
Anyway, just wondering.... securing your system is as easy? Again I was using IPtables on fedora to do basic firewall and IP forwarding for my clients PC's.

---

### Post by Iowan on 2009-09-16
It'll end up being IPTables, but UFW and (older) Firestarter are front ends that might make it easier (I haven't used either...).

---

### Post by swerdna on 2009-09-16
This will help: [Opening the UFW Firewall for Samba]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall")

---

### Post by Udayakiran on 2009-09-18
If the problem has been solved, can you please mark it as solved? If not, ignore this post.

---

