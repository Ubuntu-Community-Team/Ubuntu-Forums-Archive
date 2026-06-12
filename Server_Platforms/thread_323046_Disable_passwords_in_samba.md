---
title: "Disable passwords in samba"
date: 2006-12-21
forum: Server Platforms
---

### Post by Dansaycool on 2006-12-21
Hi, i've just configured a very basic samba server sharing a folder /home/samba, it works and everything but each time ypu have to log on to the folder in able to view/edit it, how do you simply disable the user + password box from appearing on my XP home machines?

many thanks 
dan

---

### Post by Brazen on 2006-12-21
Is the username and password the same on your windows box and samba box?  I believe even the case of the username must be the same.

I'm thinking you also have to have the workgroup parameter set in Samba to the same workgroup as your Windows machine.

---

### Post by Dansaycool on 2006-12-21
on all of my XP machines i dont use passwords, and i'm pretty sure i've set the workgroup correctly becuase I can already log on to the shared folder from my XP machines i just have to type in a user and password each time which is the thing i'm trying to disable?
I've heard of a public folder in Samba? is that what i need do you think?

thanks 
dan

---

### Post by dannyboy79 on 2006-12-21
well, when you're on windows xp, are you using pro? if so, did you turn off simple file sharing? if so, then you need to edit the permissions for the folders you want to be able to access without a password. or are you talking about accesss ubuntu shares without a username and password. I would strongly suggest against this though!!!

---

### Post by Dansaycool on 2006-12-21
im using XP home, and ye I want to access a ubuntu share from my XP machines without any passwords, why do you not recommend doing this? lol

---

### Post by dannyboy79 on 2006-12-21
well, if you run any services that allow internet traffic to your machine, ssh or ftp or http then if that person breaks in, then they'll be able to access your machines that don't have passwords to access them. do you want to be able to write to these locations or just read from them? if just read from them, then add guest = ok to your share within your smb.conf. this will allow guest access, read only, which the guest account doesn't require a password. otherwise, don't know what else to tell ya. what about using security = share instead of user within your smb.conf? do a man smb.conf and read about the security option. that'll get ya going. the man pages are a wealth of info, as soon as I found out about them I started being able to figure things out on my own. it felts great to be more independent from having to wait for anyone to respond. which sometimes takes awhile but don't get me wrong, this forum is pretty active.

---

### Post by speedman on 2006-12-21
> **Dansaycool said:**
> im using XP home, and ye I want to access a ubuntu share from my XP machines without any passwords

Edit /etc/samba/smb.conf and create a wide open share like this:

=====

[landisk]
    comment = LAN Disk
    path = /media/landisk
    read only = no
    available = yes
    browseable = yes
    public = yes
    writable = yes
    force create mode = 777
    force directory mode = 777

=====

Change the share name [landisk], the comment and the path to suit your system.

HTH


SM

---

### Post by Brazen on 2006-12-21
> **Dansaycool said:**
> im using XP home, and ye I want to access a ubuntu share from my XP machines without any passwords, why do you not recommend doing this? lol
It's not reccommended because it's terribly insecure.  You can try adding this to your share configuration: "guest ok = yes"  This will allow guest access (no password).  I'm not sure how it acts in practice though, because I would never do such a thing.

---

