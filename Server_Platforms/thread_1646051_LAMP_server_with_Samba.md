---
title: "LAMP server with Samba"
date: 2010-12-15
forum: Server Platforms
---

### Post by ryanrobinson on 2010-12-15
OS: Ubuntu 10.4

Hi guys,

I have recently setup a LAMP server for my web development test platform.

However, I need the /var/www folder to be accessible by the other computers on my LAN. I need this to be done as I want all of my website files to be available for every PC on my network. I want to be able to map a network drive to the www root so I can create and modify the files of my websites.

Does anyone know how to do this using Samba?

---

### Post by arrrghhh on 2010-12-15
Sure, [see this post](http://ubuntuforums.org/showpost.php?p=10225297&postcount=2).

SWAT will help you setup samba, in addition to installing all the necessary stuff.  Enjoy!

---

### Post by SeijiSensei on 2010-12-15
One tip I'll mention is to use the "force user" and "force group" directives if you're going to be sharing /var/www.  In /etc/samba/smb.conf, I'd define the share like this:

```

[website]
path = /var/www
browseable = yes
read only = no
force user = www-data
force group = www-data
create mode = 0664
directory mode = 0755

```

Then no matter what user connects to the site, the files will always be owned by the www-data user and group that the Apache server runs as.  Otherwise you can end up with permission problems.

---

### Post by ryanrobinson on 2010-12-15
I added that to the Samba file and I wasn't able to create a new file or folder from my Windows box. 

Is there a way I can create a samba user that can create files and folders in the www folder and be able to run PHP files?

I just need the var/www folder to be mappable so I can create my PHP/MySQL websites and store them onto my server so I can access them from any other computer.

---

### Post by ryanrobinson on 2010-12-15
Regarding the SWAT install.

I did install it but how do I access the web interface?

---

### Post by arrrghhh on 2010-12-15
> **ryanrobinson said:**
> Regarding the SWAT install.

I did install it but how do I access the web interface?

Please see the [Swat Ubuntu Community Doc](https://help.ubuntu.com/community/Swat) for help with it.

---

### Post by SeijiSensei on 2010-12-15
> **ryanrobinson said:**
> I added that to the Samba file and I wasn't able to create a new file or folder from my Windows box. 

Is there a way I can create a samba user that can create files and folders in the www folder and be able to run PHP files?

I just need the var/www folder to be mappable so I can create my PHP/MySQL websites and store them onto my server so I can access them from any other computer.

Did you create a Samba user as well and log in to the share?

Another option is to add "guest ok = yes" to the share's configuration, but that's not very secure.

---

