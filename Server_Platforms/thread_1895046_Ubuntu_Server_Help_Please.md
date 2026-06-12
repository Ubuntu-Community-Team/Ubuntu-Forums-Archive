---
title: "Ubuntu Server Help Please"
date: 2011-12-13
forum: Server Platforms
---

### Post by Jennifer29 on 2011-12-13
I really need some help setting up a file server it a 5 year old pc.Here is what i have done so fat I installed the server OS on a spare pc and selected samba then I installed openssh no problems so far.The problems I am having is I am the only one in the house and i do not have a router.

I am wanting to set this server up off line so I don't need Internet going to it.So my question is how can i make a direct connection from my PC to the server?I have a network to usb cable and a parallel to parallel cable.

Will any of these work or do I need to get something else it doesn't have to be that fast and how do I set it up?

Thanks

---

### Post by drdos2006 on 2011-12-14
I would say that you need an ethernet cable first.
Second, 

Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb
###  	web site is here: http://sourceforge.net/projects/webadmin/files/webmin/1.550/webmin_1.550_all.deb
Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by Jennifer29 on 2011-12-14
OK i have a Ethernet cable how would i connect the two pc's together?I want to connect them directly.

---

### Post by ephmanjmm on 2011-12-14
You will need (most likely) a hub or a switch, or a crossover ethernet cable.  I would stay away from hubs.  A small switch (10/100) can be had for very low cost but RadioShack (and others) sell crossover cables.
If it were me, I would buy a wireless router with a built in switch.  Don't configure the default gateway on the server to limit internet access.  This would allow for more options down the road and given the cost of wireless routers now, it would not be that much more that buying a crossover cable.
Of course, if you have the tools, you could make a crossover cable for about 3 dollars.

---

### Post by Iowan on 2011-12-14
Some of the newer NIC's will auto-configure - but the 5 year old machine probably doesn't have one.

---

### Post by arrrghhh on 2011-12-14
> **Iowan said:**
> Some of the newer NIC's will auto-configure - but the 5 year old machine probably doesn't have one.

Indeed, crossover cables should not be necessary any longer.  If it doesn't work, then get a crossover cable :D.

But as was previously stated, you should just buy a wireless router with a built-in switch.  They're less than $50 depending on brand/features.

---

