---
title: "Installing ebox add on erros"
date: 2009-12-17
forum: Server Platforms
---

### Post by twin-08 on 2009-12-17
Sorry guys but I have another noob problem I installed ebox fine and its working however when I try to install add on packages I get an error.

[IMG]http://img17.imageshack.us/img17/5986/screenshotzr.png[/IMG]

Also guys, how do I edit the samba user name and password as when I try to connect to it on my windows based pc I get asked for an user and pass.

Thanks, twin-08

---

### Post by cj13579 on 2009-12-17
Edit your samba shares using the following in your smb.conf:

```

[share]
    path = /path/to/dir
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = user
    force group = user
```

replacing "user" with a user e.g. john

Then restart samba:

```
sudo /etc/init.d/samba restart
```

You should now be able to login with the username and password of the user you selected.

Also, I would go for Webmin over eebox. A great tutorial: [http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html](http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html)

---

### Post by MikeyPooh on 2009-12-17
Hi , I Have Never Been Able To Get ebox-all to work i have always had to do each module by itself,
 
Just a FYI

Mike

---

### Post by ibeeby on 2010-07-31
Bad day today - installed 10.04 LTS and added ebox - bare bones ebox worked fine (but doesn't do much) so added a set of modules (office) and then now all I get is a 403 error for the control page and a note saying that there is also a 500 error.

Any ideas - why has ebox eaten itself?

Regards

Ian

---

