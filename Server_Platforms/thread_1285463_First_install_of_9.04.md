---
title: "First install of 9.04"
date: 2009-10-07
forum: Server Platforms
---

### Post by J0hnnyBr@v0 on 2009-10-07
This is the first time I have installed Ubuntu Server.  I wanted to install a desktop so I ran aptitude install x-window-system ubuntu-desktop

I rebooted and logged in and issued the command startx, but it gave me an X11 error.  Do I have to sudo startx?

Thanks in advance

---

### Post by Cowzor on 2009-10-08
The whole idea behind the server edition is that you DON'T have a desktop. This saves on diskspace, performance and adds security. Also, normally when you run a server it's just sitting there doing it's thing and there is no need to even have a desktop.

If you really prefer having a desktop, you're better off just installing the regular non-server edition and use that. It's not like you can't just the desktop version as a server, it's just that the server edition is optimized for being a server.

I hope you understand what I mean :)

---

### Post by J0hnnyBr@v0 on 2009-10-08
I totally understand what you mean...but how do you install VirtualBox and guest OS's without a GUI?  I know they have command line....but how do you configure a Virtual WinXP wihtout a GUI?

Thanks,
Eric

---

### Post by BQAggie2006 on 2009-10-08
The VirtualBox manual covers command line administration pretty thoroughly. It is located at [http://www.virtualbox.org](http://www.virtualbox.org) on the Downloads page. Also, you can run VirtualBox just as well on the desktop edition as you can on the server edition.

A note on your installation, you didn't need to explicitly state the x-window-system during the install, the ubuntu-desktop metapackage will install everything needed for a functional desktop.

---

### Post by J0hnnyBr@v0 on 2009-10-08
Also, I found this link....wish I had found it yesterday!!

This explains everything from start to finish....
[http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-3.0-on-a-headless-ubuntu-9.04-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-3.0-on-a-headless-ubuntu-9.04-server)

Now that its built....can I remove the gnome desktop without hosing everything up?

Thanks,
Eric

---

### Post by BQAggie2006 on 2009-10-08
Yes, just run the following commands
```

sudo apt-get purge ubuntu-desktop x-window-system
sudo apt-get autoremove

```

---

### Post by J0hnnyBr@v0 on 2009-10-08
I booted up hit ctrl+Alt+F5 and logged in and ran those commands...it did something...but still boots to the GDM.

Thanks,
Eric

---

