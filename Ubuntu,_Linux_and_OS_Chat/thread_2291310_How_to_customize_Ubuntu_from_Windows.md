---
title: "How to customize Ubuntu from Windows?"
date: 2015-08-19
forum: Ubuntu, Linux and OS Chat
---

### Post by remmas-sido on 2015-08-19
Hello guys 
I'm using Windows 8 and I'm planning to download Ubuntu Mini Iso to customize it on my taste, are there any tools? like Ubuntu Builder or UCK?

---

### Post by Bucky Ball on 2015-08-19
*Thread moved to **Ubuntu, Linux and OS Chat**.*

? Ubuntu mini.iso installs the Ubuntu base kernel only. You then need to 'sudo apt-get install' whatever else you want need down the line. Windows doesn't come into it.

Please see these links:

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

PS: Ubuntu Builder is for Ubuntu.

---

### Post by buzzingrobot on 2015-08-19
Also, when you do an install with the mini ISO and then add something like "ubuntu-desktop", you get to pretty much the same place as you would by using the standard Ubuntu installation image. Ditto for the other interfaces and desktop environments.

---

### Post by remmas-sido on 2015-08-19
> **Bucky Ball said:**
> *Thread moved to **Ubuntu, Linux and OS Chat**.*

? Ubuntu mini.iso installs the Ubuntu base kernel only. You then need to 'sudo apt-get install' whatever else you want need down the line. Windows doesn't come into it.

Please see these links:

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

PS: Ubuntu Builder is for Ubuntu.
But I can play with the mini iso in Virtual Box and then convert the Virtual Box image to an ISO file?

---

### Post by Bucky Ball on 2015-08-19
Guess so. As buzzingrobot says, avoid installing *buntu-desktop anything as you may as well install which ever flavour desktop you install. 

To do what you are suggesting you'd have to figure how to convert a virtual machine to an .iso, or at least transfer it to hard drive somehow, but I believe it can be done.

Once the mini is installed you need an internet cable. This is normally done using an ethernet cable with the mini. As long as you can get the VM online somehow, you should be good to give it a try. 

If you are not that familiar with the apps and software available in Ubuntu, though, I recommend you run the various flavours as VMs before going to the mini and customising your own. Know what's out there first then throw the bits you like best at the mini rather than trying to test on a mini install. You are at least going to need a window manager or desktop environment (unless you are running a CLI install). Which do you prefer? Best to test in a full system because if you install xfce4, for instance, in a mini install, that's all you have. No apps. Nothing else. Not really a good demo. 

Check them in situ then roll your own. But that my 2c. Up to you, of course. Have fun.

---

