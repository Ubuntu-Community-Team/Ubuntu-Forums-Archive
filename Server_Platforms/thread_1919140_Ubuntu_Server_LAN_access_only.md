---
title: "Ubuntu Server LAN access only"
date: 2012-02-02
forum: Server Platforms
---

### Post by Jnetty99 on 2012-02-02
I setup a Ubuntu Server with LAMP on our local work network. 

Is there a way to continue to have the local network access to it, but make sure the server has no outside internet connection? 

I just don't want it to communicate back to the real world. Anything i can change on the network settings on the server?

---

### Post by wyliecoyoteuk on 2012-02-02
Simple,just don't give it a gateway.

---

### Post by Jnetty99 on 2012-02-02
> **wyliecoyoteuk said:**
> Simple,just don't give it a gateway.

I remove the gateway by running this command

```
sudo route del default gw 172.24.0.1
```

This stopped communication, but when I restart the server the gateway comes back when I guess it gets the IP address from the DHCP Server. 

Do I have to setup a static ip address?

---

### Post by drdos2006 on 2012-02-02
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb

Install with :
sudo dpkg -i webmin_1.570_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to [https://server_IP:10000](https://server_IP:10000) to edit files, create shares, startup daemons etc..

regards

---

### Post by jonobr on 2012-02-02
Hello


IMO servers should always have static IP addresses.

If you bite the bullet now and change it, its solves this problem also by not defining a gateway address.

---

### Post by codmate on 2012-02-03
Another approach would be to use IPtables.

The directive
> -m iprange --src-range 192.168.1.2-192.168.1.150
limits connections to the ip range specified.

---

### Post by Jnetty99 on 2012-02-03
> **codmate said:**
> Another approach would be to use IPtables.

The directive

limits connections to the ip range specified.

Thanks i will check it out. going to test it on VM Virtual Box first before moving it over to a physical machine.

---

