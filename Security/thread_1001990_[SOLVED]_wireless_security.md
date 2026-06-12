---
title: "[SOLVED] wireless security"
date: 2008-12-04
forum: Security
---

### Post by Mr Pockets151 on 2008-12-04
Would it be enough to just use my router as a firewall as opposed to having a firewall installed?

Also is it enough just to use the routers security features for wireless security as opposed to setting up the WPA2 key?

---

### Post by jgoguen on 2008-12-04
> **Mr Pockets151 said:**
> Would it be enough to just use my router as a firewall as opposed to having a firewall installed?
Maybe.  If you aren't running anything that can be accessed publicly (no servers, no P2P, etc.) then a second firewall is probably not needed.  If you do anything that opens a port so any arbitrary person can access your machine, then yes you should use a firewall.  Lucky for you, Ubuntu comes with iptables, a wonderful firewall.  Its use is made simple through _[COLOR=Red][UFW]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw")[/COLOR]_, and you can install the _[COLOR=Red][GUFW]("apt://gufw")[/COLOR]_ package to get a graphical interface to the firewall.

> **Mr Pockets151 said:**
> Also is it enough just to use the routers security features for wireless security as opposed to setting up the WPA2 key?
No.  If you don't enable your wireless security features, than anyone can use your network, see what you're sending across the network, and in general do Bad Things(tm) that could get blamed on you (or whoever pays for the Internet access).  Enabling WPA2 is the way to go here.  I recommend WPA2 with AES (your router may call it CCMP instead).

---

### Post by hyper_ch on 2008-12-04
jgoguen:

I don't get what you mean... if he configures the router's firewall to block everything no matter what you setup on your computer it won't work.

Hence a nice configure router is fine and you can forget about iptables.

---

### Post by jgoguen on 2008-12-04
My thought is for P2P apps that use UPnP to automatically forward ports in the router.  Or if he installs server apps and configures the router to let that traffic through.  Or if it's a laptop and he goes outside his network with P2P/server apps running.  I have used iptables to block IP addresses from connecting to server apps.

I'm perfectly willing to admit that I'm paranoid on that aspect though :)

---

### Post by slowth5 on 2008-12-04
Disable router UPnP .  It's a security nightmare.

---

### Post by Mr Pockets151 on 2008-12-04
Wow...cool responses.  That gives me a lot to go on to start.   Thanks all 3 of you guys.

---

### Post by Vantrax on 2008-12-04
I recommend using WPA2 with a reasonably large key, preferably over 16chars.
Use the option to hide the SSID if you have it, just to avoid the script kiddy next door.

I generally disable PnP and set up port forwarding for anything you must have running like an SSH server, torrents, or SFTP.

As far as a local firewall goes I assume i know whats happening on my machine (and i check regularly to make sure i do) and allow all outbound traffic, but block everything i dont need coming in (and allow SSH, torrents, and SFTP).

If you have specific questions just give us a setup with model numbers and we can look at the options.

---

### Post by Mr Pockets151 on 2008-12-04
Actually, I have WPA2 w/ AES TKIP 16-dig code on my windows
set-up. Ports forward and what not. I'm such a stoney poney, I forgot my damn router password.  I had a wicked one.....anywho, now I'm setting router back to factory preset values.  

I wasn't ready to try and tackle at ubuntu set-up.

Would following the process for another GNOME desktop work just like Ubuntu.  I have MDV 09 set-up through MCC.  I'm ready to give the command line a shot at network set-up.  

That's my main concern is having a proper network w/out the hastle. :popcorn:

---

### Post by jgoguen on 2008-12-05
Ubuntu setup is actually just as easy as Windows, assuming you remember your password :)  I have WPA2/AES on my router at home, it was as simple as click NetworkManager, click my network, enter my password, and start using the network.  The directions for other GNOME desktops will probably work pretty much the same for Ubuntu.  If the directions are for NetworkManager 0.6.x there may be some differences, but nothing major until you start editing network settings after initial configuration.  In any case, if you have problems or questions you can always come back here or hop on IRC and ask away :)

---

### Post by gTinker on 2008-12-06
[QUOTE=Mr Pockets151]Would it be enough to just use my router as a firewall as opposed to having a firewall installed?[/QUOTE]

If the router you mention has a built in firewall, then I agree with hyper_ch (if I understand him correctly), the router's firewall will give you good protection from the Internet if it is setup correctly for the way you use your system. It, however, won't give you protection from other nodes on your local network.

[QUOTE=Mr Pockets151]
Also is it enough just to use the routers security features for wireless security as opposed to setting up the WPA2 key?[/QUOTE]

I agree with the other posters for setup in an urban environment. Security is a process of threat-risk accessment, if for example, you live in a rural setting on acreage and can see that no one is in range of your router, an open WAP would be sufficient (assuming no one with the resources of Homeland Security is interested in your connection). When you are in a location where your radio signals could be intercepted from an apartment next door or a car on the street, you'd be well served to use all security features available. This was a picky point, I just mentioned it for completeness.

---

