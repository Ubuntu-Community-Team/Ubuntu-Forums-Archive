---
title: "Setting up FTP server without root access"
date: 2008-11-05
forum: Server Platforms
---

### Post by shjr on 2008-11-05
Is there a way to setup proper FTP server without root access (ideal would be vsftpd). I'v followed many guides for different clients, but i cannot add users or groups with 'only' admin access. Note that i'am a newbie with linux. I'v only picked ubuntu over windows on this server, becouse it was free. Only thing i need is proper and secured FTP server.

---

### Post by lykwydchykyn on 2008-11-05
Do yourself a favor:
 - install proftpd
 - install webmin from [www.webmin.com](www.webmin.com)
 - use webmin's nice proftpd config interface to set up your ftp server.

Why would vsftpd be ideal, just out of curiosity?

---

### Post by baudday on 2008-11-05
There's nothing wrong with vsftpd.

---

### Post by lykwydchykyn on 2008-11-05
> **baudday said:**
> There's nothing wrong with vsftpd.

Darn tootin' there's not a thing wrong with it.  But it doesn't have a webmin interface, whereas proftpd does.  In my estimation, apart from a few scenarios one handles better than the other, they're equivalent in any other sense.  So why not use the one with a nice web interface when you're struggling?

I'm just curious why the OP thinks it would be ideal.  There are a lot of ftp servers available, most of them are great, just have their own unique little features.

---

### Post by baudday on 2008-11-05
Actually I found a webmin interface for vsftpd that I used when I still used ftp.

---

### Post by lykwydchykyn on 2008-11-05
Ok, well there you go.  Third party one?

---

### Post by baudday on 2008-11-05
[http://www.debianadmin.com/webmin-installation-and-configuration-in-debian-and-ubuntu-linux.html](http://www.debianadmin.com/webmin-installation-and-configuration-in-debian-and-ubuntu-linux.html) to install webmin

[http://articles.techrepublic.com.com/5100-10878_11-6182594.html](http://articles.techrepublic.com.com/5100-10878_11-6182594.html) to install vsftpd module for webmin

You can add users using webmin

---

### Post by baudday on 2008-11-05
> **lykwydchykyn said:**
> Ok, well there you go.  Third party one?

Yeah I'm pretty sure

---

### Post by shjr on 2008-11-07
Honestly, becouse the UI is very laggy and annoying, especially on linux (my first time, so kinda struggling with everything).

I installed GPROFTPD UI, seems like it's working great, except, i missing SSL transfer settings.

---

### Post by shjr on 2008-11-12
I tried to follow a guide for setting up SSL, but then i realized i cannot change the config files of proftpd, just becouse i dont have root access for this server. Is there a way to trick this?

---

### Post by lykwydchykyn on 2008-11-12
Why don't you have root access?  Is it not your server?

---

### Post by cariboo on 2008-11-12
In Ubuntu the root user is disabled, use sudo before any commands eg:

```
sudo chmod -R 777 somefile
```

the above command will ask for your user password and will not be echoed back. I see that you are trying to use gproftpd, so you must be using a gui of some sort. For graphical applications press Alt-F2 and type, for instance if you want to use the file manager as root:

```
gksu nautilus
```

You can find how to enable root if you look hard enough, but it is against forum policy to instruct how to do it here.

Jim

---

### Post by shjr on 2008-11-24
> **lykwydchykyn said:**
> Why don't you have root access?  Is it not your server?

I ordered dedicated server from OVH company. Other companies usually provide also root access, that's why i'am a bit surprised.

---

### Post by any.linux12 on 2008-11-24
I have one FTP-server mounted in startup

just do like this 

create a folder wherever you want (for ex. Desktop/FTP)
create a a bash file like this

#!/bin/sh

sudo mkdir -p /home/username/Desktop/FTP
chmod 744 /home/username/Desktop/FTP
curlftpfs USERNAME:PASSWORD@example.com /home/username/Desktop/FTP

works with me. 
and if you know german you can also go here
[http://www.exanto.de/sftp-und-ftp-unter-linux-mounten.html](http://www.exanto.de/sftp-und-ftp-unter-linux-mounten.html)

and you can also put your script in the startup easily.
goto system>preferences>sessions and add the script

Hope it helps

---

### Post by any.linux12 on 2008-11-24
After try it tell me the result please

---

