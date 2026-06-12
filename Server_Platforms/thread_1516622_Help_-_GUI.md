---
title: "Help - GUI"
date: 2010-06-24
forum: Server Platforms
---

### Post by imlens on 2010-06-24
Hi all, I'm new at linux and just install linux server ed. 10.04 downloaded from ubuntu website. I'm confuse with dos prompt 
Well I try to use 

#** sudo apt-get update**

#[B] sudo apt-get install build-dep gnome-shell

[/B]And there are no package at all when I try to install it regarding many website. Am I making mistake during Installation Linux? I just want GUI like gnome or something

Please help

Regards,
Nababan

---

### Post by jbrown96 on 2010-06-24
Why don't you just download the desktop edition?

---

### Post by sikander3786 on 2010-06-24
Download the desktop edition of Lucid as mentioned above and install it.

Server edition is not for beginners as it has no gui.

Desktop edition will have almost all the gui-tools including the desktop to configure and maintain your pc just like WIN****.

HTH.

---

### Post by imlens on 2010-06-24
> **sikander3786 said:**
> Download the desktop edition of Lucid as mentioned above and install it.

Server edition is not for beginners as it has no gui.

Desktop edition will have almost all the gui-tools including the desktop to configure and maintain your pc just like WIN****.

HTH.

Hi thanks for your help I really appreciate it. But I need Linux to run at my server it must be able to manage more than 100 user.
Well I really like Microsoft Server but my Director ask me to change to Linux.
So I need a GUI to learn more faster and simple

---

### Post by koenn on 2010-06-24
> **imlens said:**
> Hi all, I'm new at linux and just install linux server ed. 10.04 downloaded from ubuntu website. I'm confuse with dos prompt 
Well I try to use 

#** sudo apt-get update**

#[B] sudo apt-get install build-dep gnome-shell

[/B]And there are no package at all when I try to install it regarding many website. Am I making mistake during Installation Linux? I just want GUI like gnome or something

Please help

Regards,
Nababan

For a GUI, ```
sudo apt-get install ubuntu-desktop
```
not that it's going to help much if you don 't know what you're doing, but at least you'll have a point and click environment. 

for servers with GUI, consider RedHat, Suse, or Canonical's Landscape, a.o.


also, consider getting professional support from Canonical.

and get yourself some training. Unless you have extraordinary learning and 'think on your feet' skills, maintaining a 100 user environment that you are not at all familiar with without any preparation, is not going to end well.

if nothing else, do some reading
[https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

### Post by dragos2 on 2010-06-24
Install these and your ready to go:
```

apt-get install xorg-core gnome-core gdm ubuntu-artwork

```
Then reboot.

Edit: xorg-core was replaced by xserver-xorg-core.

---

### Post by OneMixDJ on 2010-06-24
I have Ubuntu Server 8.10 as a file server.

I've gone this road before in the past and overall it just didn't work for me.

Instead of directly installing a desktop GUI on the machine, I installed Webmin which gives me a web GUI interface accessible from my primary desktop or any machine on my network via https. 

ISPConfig also provides similar administration access, but Webmin was good enough for my needs so I stuck with Webmin.


Here's how I did mine.

Since my server was already up and running for a while, I just followed Step 2 to prep the machine and install:

[http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html]("http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html")

After that, I just access my server via URL using a browser:

[https://your-server-ip:10000/](https://your-server-ip:10000/) 


This gives me login prompt below:

[IMG]http://www.ubuntugeek.com/images/web/1.png[/IMG]



After logging in, you get a GUI interface similar to this:

[IMG]http://www.ubuntugeek.com/images/web/2.png[/IMG]



Works great! 

I can configure anything I have on the server.
\\:D/

Hope this helps. ;)

---

