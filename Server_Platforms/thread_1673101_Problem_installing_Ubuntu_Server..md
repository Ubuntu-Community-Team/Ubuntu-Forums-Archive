---
title: "Problem installing Ubuntu Server."
date: 2011-01-21
forum: Server Platforms
---

### Post by Ranger_Joe on 2011-01-21
Hello everyone,
I'm pretty new to Ubuntu and DEFINITELY new to servers. I'm installing Ubuntu Server on my first home server. I've already hit a hiccup 2 minutes in.

I am being prompted to enter my IP address. I have no idea where to find that. Please help!

---

### Post by wongo888 on 2011-01-22
If you are running this from home behind a consumer grade router, just use a free IP that is not being handed out by your local DHCP server. You would have to configure your router's DHCP server to not use up the whole subnet.

If you are running this on a VPS or elsewhere out on the Internets then your IP would be assigned to you from your ISP. Check with them.

---

### Post by Ranger_Joe on 2011-01-22
Wongo,
I am using it at home behind a consumer grade router. How do I go about finding a free IP? Sorry for insane level of confusion.

---

### Post by wongo888 on 2011-01-22
You can configure your DHCP server to only manage a limited range of IPs. That will free up the non-DHCP IPs for use as static IPs. Exactly how you would do that depends on your router.

Example:

192.168.0.0 network
255.255.255.0 subnet mask
192.168.0.1 gateway and dhcp server IP
192.168.0.2 - 192.168.0.99 range for static assignment
192.168.0.100 - 192.168.0.254 range for DHCP

Then configure your static IP, say...192.168.0.10 or 192.168.0.18 or anything in range 2 - 99.

---

### Post by Ranger_Joe on 2011-01-22
Ok, I'm sorry I still don't exactly understand how to do this or why I should. Here's what I was going to do:

1. Go to whatismyipaddress.com
2. Enter that IP address during the server install

Is this an acceptable way to do it?

---

### Post by wongo888 on 2011-01-22
Just checking, but are you actually stuck in the server install section with the grey dialogs? Did your machine not find a DHCP server during installation? Or have you logged into the machine and are configuring the interfaces?

Take a look at this...

[http://www.ubuntugeek.com/step-by-step-ubuntu-10-04-lucid-lynx-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-10-04-lucid-lynx-lamp-server-setup.html)

---

### Post by drdos2006 on 2011-01-22
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by Ranger_Joe on 2011-01-22
Ok guys, I figured it out. The only reason it was prompting me to input my IP address is because I didn't have the server connected to the internet via ethernet. It was looking for some manual info, because it couldn't detect it automatically. 

I think I have this one figured out... at least for the purposes of installation. I may need to revisit this soon.

---

