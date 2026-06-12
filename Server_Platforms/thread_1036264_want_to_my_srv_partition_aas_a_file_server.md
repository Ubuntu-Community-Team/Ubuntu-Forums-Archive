---
title: "want to my /srv partition aas a file server"
date: 2009-01-10
forum: Server Platforms
---

### Post by Heeter on 2009-01-10
Hi all,

I would like to use my /srv partition on my Ubuntu 8.10 Server as a file server for my three Ubuntu desktops and my one Windows desktop.

My goal is to put about ten main folders into the /srv partition, and the desktops will be able to add/edit/remove files from the desktops. 

I have installed samba into the server, but not quite sure on how to proceed from here.

Any help will be greatly appreciated.




Heeter

---

### Post by lykwydchykyn on 2009-01-10
You might want to install webmin, it makes this sort of thing trivial.  But in a nutshell, what you need to do is this:

 - I would recommend creating /srv/samba, to keep things tidy if you decide to add other services later (mkdir /srv/samba)
 - Create your folders under /srv/samba (mkdir /srv/samba/foldername), making them world-writeable. ( chmod 777 foldername).
 - create a samba entry in /etc/samba/smb.conf for /srv/samba, like this:
```

[shares]
path = /srv/samba
writeable = yes
guest ok = yes

```

 - restart samba.  This will give you a share that is world-writeable.  If you want to secure this share with passwords and accounts, that's another matter.

---

### Post by Heeter on 2009-01-10
Thanks bud.

What do I have to do on the desktop end?

Do I need to add the share into the fstab in Ubuntu?

Heeter

---

### Post by lykwydchykyn on 2009-01-10
You could do that, or just mount them in a login script.  I am not familiar with GNOME's facilities for mounting or browsing remote shares, but I'm sure it has something built in (VFS of some kind), so that's an option too.  

Question is, how do you want it to look to the end user?

---

### Post by Heeter on 2009-01-11
Good question.

If I put it into the fstab, I am concerned that I might need to use my server's user/pass. So hopefully I can just create a shortcut on the desktop & user home folder without the need to enter passwords.


Thanks

Heeter

---

