---
title: "Vsftpd"
date: 2008-08-23
forum: Server Platforms
---

### Post by Drezard on 2008-08-23
Im trying to set up vsftpd so my friends can use my server as well but, I don't want them touching all of the files in my filesystem. Im setting up the user accounts like this 

```

useradd -d /var/public/ -p password -s /bin/false friendsname 

```

How do I make it so they can ONLY access /var/public and nothing else? I'm using a basic vsftpd set up with these settings changed: 

> 
anonymous_enable = NO (changed from YES to NO)
local_enable = YES (uncommented)
write_enable = YES (uncommented)


Just going to be using it for allowing them to upload and download games and other files. 

Thanks, Daniel

---

### Post by inphektion on 2008-08-23
Add:
local_root=/var/public

edit: oh, didn't notice you are making /var/public thier home dir?
then i guess you could just set
chroot_local_user=YES

consider using virtual users though, I hate the idea of using system accounts solely for ftp access.

---

### Post by hux on 2008-08-28
++ on the virtual users recommendation. It's pretty easy to set up and it's *much* more secure.

---

