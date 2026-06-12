---
title: "Which firewall to use?"
date: 2009-08-04
forum: Security
---

### Post by dragon84 on 2009-08-04
i'm currently looking for a easy and secure to use firewall for ubuntu. at the moment i'm using firestarter which is really good but it seems to be blocking my ISP's iptv ports. i tried enabling the ports but i can only get a few minutes of view time before it stops playing. on [http://linuxappfinder.com/internetandnetworking/firewalls](http://linuxappfinder.com/internetandnetworking/firewalls) i can see that Linux-Firewall.org and firestarter and pretty much the top ranked ones. can anyone tell me if "Linux-Firewall.org"  is a safe/reliable/top notch firewall to use.

btw whenever i try to unistall firestarter using the add/remove or "sudo apt-get remove --purge firestarter" it doesnt seem to completely remove the program. when i reinstall firestarter i can still view the firewall's previous logs.

born with windows i have gotten used to windows+firewall+antivirus whenever i install windows. still, i'm still planning to use firewall and antivirus for linux but is it really required as a home user?

many thanks

---

### Post by NormanFLinux on 2009-08-05
Ubuntu is secure by design. If you want a firewall, install gufaw as a graphical front-end to ufaw iptables. You can set it and forget about anything harming the computer. Windows needs security software to keep viruses and malware at bay. Neither Linux or Mac OSX users have to worry about them.

---

### Post by sasho_zl on 2009-08-05
I recommend that you check this thread first - [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
About the firewall - Linux has built in firewall called Netfilter. All the software like firestarter (who btw is not supported since 2004)  is only for configuring that firewall. There are many tools that allow you to configure your firewall - some with graphical user interface and some from the command line. I would recommend to you first to learn about "iptables" which is very strong tool. You can see tutorial here - [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)
If you want to configure your firewall quick and easy through graphical interface - gufw is for you and you can install it from Synaptic.
Another choice is the Shorewall firewall which I am currently using. You can get the latest version by installing those two files - [http://packages.debian.org/testing/net/shorewall-common](http://packages.debian.org/testing/net/shorewall-common)  and  [http://packages.debian.org/testing/net/shorewall-perl](http://packages.debian.org/testing/net/shorewall-perl)
This is the latest version. After you install them, the only thing you need to do is to copy the contents of         /usr/share/doc/shorewall-common/examples/one-interface into the /etc/shorewall directory. After that change to value to 1 in the startup entry in /etc/default/shorewall and you are ready to go! Only type sudo shorewall start in the terminal and forget about it! :popcorn:
Page - [http://www.shorewall.net/](http://www.shorewall.net/)

Cheers! I hope I was useful!

---

### Post by dragon84 on 2009-08-05
thanks:P heaps guys

---

