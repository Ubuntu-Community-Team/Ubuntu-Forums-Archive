---
title: "Installing X Window"
date: 2008-11-29
forum: Server Platforms
---

### Post by chmod007 on 2008-11-29
Dear Penguins,

I am about to install Ubuntu Server Edition 8.10 for my local area network. Where I need to use. FTP, Web Application Server (PHP, MySQL), File Server, Mail Server for Local Users etc. But, I also want to install X Window on Server Edition. Is it possible doing so? and if yes how?

Because, I am going to use same as for other different purpose. Please guide me through. 

Most important thing in this is. I want to maintain a log of what users do when they logon to the file server. What they copy to their machines and where. Its very important to me.

Regards,
Sending KILL Signal.....

---

### Post by Philio on 2008-11-29
You can install the GUI on server edition via:

```
sudo apt-get install ubuntu-desktop
```

This will install GNOME desktop.

If you want KDE instead you can use:

```
sudo apt-get install kubuntu-desktop
```

---

### Post by chmod007 on 2008-11-30
Hey Very thanks for help.

---

