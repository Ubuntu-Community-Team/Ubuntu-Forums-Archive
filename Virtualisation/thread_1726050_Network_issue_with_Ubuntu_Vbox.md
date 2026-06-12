---
title: "Network issue with Ubuntu Vbox"
date: 2011-04-10
forum: Virtualisation
---

### Post by jlego on 2011-04-10
I am trying to set up a LAMP VM using VirtualBox & Ubuntu Server 10.10. My host operating system is Windows 7 64-bit. 
I only want to use it for web development and for it to be accessible only on my local network. (basically a test server that I can build the sites on with AMP and then transfer to a live web host)
I have successfully installed and booted the system using Vbox, but I seem to have some error in my network config.
I've been looking at several guides:

[http://jamielesouef.com/linux/installing-ubuntu-server-lampsshftpwebmin-and-phpmyadmin-for-a-newbie/]("http://jamielesouef.com/linux/installing-ubuntu-server-lampsshftpwebmin-and-phpmyadmin-for-a-newbie/")
[http://www.lukeweaverwebdeveloper.com/install-your-own-virtual-lamp-server/]("http://www.lukeweaverwebdeveloper.com/install-your-own-virtual-lamp-server/")
[http://blog.quibb.org/2010/02/setting-up-a-virtualbox-lamp-server/]("http://blog.quibb.org/2010/02/setting-up-a-virtualbox-lamp-server/")
[http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html]("http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html")

Whenever I go to install the additional packages like Webmin, it gives me and error that "cannot resolve hostname." This seems to have something to do with my network settings whenever I change the interface to static IP, and I assume that the VM cannot access the internet using the static IP settings. I am using Vbox 4.0 and have changed the network settings though the Vbox GUI to a bridged adapter, but it does not work.

The LAMP server has loaded correctly as I see a message when booting that Apache is running. I can also access the default Apache page in a browser.
Other (potentially) useful information:


Host OS: Windows 7 64-bit
Virtulization Software: VirtualBox 4.0
Guest OS: Ubuntu Server 10.10

I am using a DSL modem connected to a Belkin wireless router, but my host machine has a hard wired ethernet connection (although it does have a Lynksys wireless card)

---

### Post by CharlesA on 2011-04-10
Does it allow you to install other software besides webmin?

If you can access the default apache test page, then the networking is working fine.

---

