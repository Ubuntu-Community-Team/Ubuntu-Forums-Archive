---
title: "installation of gui in ubuntu server edition"
date: 2011-01-05
forum: Server Platforms
---

### Post by ganesh.smart on 2011-01-05
i have installed ubuntu server 10.04 sucessfully. but i'm new to ubuntu so i need graphical user interface(GUI). How can i install gui in ubuntu server 10.04.

---

### Post by david.garceau on 2011-01-05
sudo apt-get install ubuntu-desktop

But you should look into webmin.

[http://www.webmin.com/](http://www.webmin.com/)

---

### Post by d_liebscher on 2011-01-05
Hi,

i think the combination webmin and ubuntu is strongly NOT recommended. Webmin may chang Config files so that they not work. Worst case is a full system crash. btw: this is the reason why webmin was removed from standard ubuntu sources.

If you really need a desktop environment you could use the metapack ubuntu-desktop for gnome (kubuntu-desktop for kde or xubuntu-desktop for xfce)

[PHP]sudo apt-get install ubuntu-desktop[/PHP]regards Daniel

---

### Post by digiplay on 2011-01-20
Is it possible to load and unload the gui interface. I would rather unload it when I'm not using it.

Thanks.

---

### Post by James78 on 2011-01-20
> **d_liebscher said:**
> Hi,

i think the combination webmin and ubuntu is strongly NOT recommended. Webmin may chang Config files so that they not work. Worst case is a full system crash. btw: this is the reason why webmin was removed from standard ubuntu sources.

If you really need a desktop environment you could use the metapack ubuntu-desktop for gnome (kubuntu-desktop for kde or xubuntu-desktop for xfce)

[PHP]sudo apt-get install ubuntu-desktop[/PHP]regards Daniel
Agreed, but there is an alternative way of doing this, which has really good support. I'm hosting an entire server using Webmin and Virtualmin, and it's really great. :D
[http://ubuntuforums.org/showthread.php?t=1197883](http://ubuntuforums.org/showthread.php?t=1197883)

---

### Post by Linux000 on 2011-01-20
What I Do is load up the Default XFCE install, it's not Ubuntu Fancy Graphics, but it does the job, and it's lightweight and doesn't try to take over the system like I've had ubuntu-desktop do. I think the command was ```
sudo apt-get install xfce4
```

---

