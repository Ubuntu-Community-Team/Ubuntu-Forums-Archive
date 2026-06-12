---
title: "Xubuntu control"
date: 2006-10-03
forum: Repositories &amp; Backports
---

### Post by tedux on 2006-10-03
Hello again, I have tried ubuntu, and kubuntu, and xubuntu. k was real slugish, on my laptop U froz from time to time. So I am using X. I have used it in work related jobs. runs my laptop just fine. (inspiron 1000) 
Xfce control center is just a little lite. But works. I have to shutdown and reboot if I change domain DHCP, to catch the new IP address, DNS, and domain host. Ubuntu had a place for me to add DNS and domains to a search list. I don't seem to be able to fined it in Xunbuntu. 

Has anyone found something in repository that will help with dropping and renewing IP address, that works with xubuntu. so a person don,t have to reboot, when changing domain host DHCP. 

I did a search for renewing IP address, results seem to go unresoved, alot of good advise. But didn't work for me.

---

### Post by sawjew on 2006-10-03
I use netapplet in Xubuntu for switching networks along with wifi-radar for switching wireless networks.  I only use 2 different networks though and I never seem to have any problems. 

I don't know if this will help or not but I have never had any problems, netapplet just logs on to whatever network you are connected to automatically once it's configured.

---

### Post by tedux on 2006-10-03
I just have what was installed with xunbuntu, and if I reboot it will log on to any network. but if I pull the lan cable out and plug it into a diffrent network, It will connect but I can not browse becouse (I think) it don't let go of the dns and domain, I don't even recall see any were what ip address I have. I don't know commands to use terminal. 

Is that netapplet GUI or terminal, and can I get it from repo??

---

### Post by sawjew on 2006-10-03
Netapplet is in the repositories.  You can get it by ```
sudo apt-get install netapplet
``` or using synaptic.

You start netapplet by going to Applications>Network>Network Selector

Netapplet shows an icon in your system tray.  If you click on the icon it drops down a menu showing all your available network connections.  At the bottom of the menu it has 'Connection Information' and 'Configure Network Settings'.  Connection Information will show you the details of your current IP address, Subnet Mask, etc.  Configure Network Settings will open the Networking configuration window which is available from Applications>System>Networking.

You should be able to just click on your nework connection on the menu (usually eth0) and netapplet will connect to it, if it hasn't done so automatically.  You can check if your connection has changed by checking the IP address under "Connection Information".  You may have to use the 'Disconnect' in the netapplet menu first and then connect by clicking on your connection.  If this doesn't work you should be able to use the Configure Network Settings item to set up your new network and then netapplet should remember it and automatically connect next time you use that network.

To make netapplet come on automatically at boot go to Applications>Settings>Autostarted Applications and add 'netapplet' as the command.  You can name it whatever suits you but I used "Network Selector' the same as in the menu.

I hope this helps you out.

PS. next time it would be a good idea to post something like this in the support forums under networking.  I only found your post because I was looking for unanswered posts.

---

