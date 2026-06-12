---
title: "Wireless on Server 8.10"
date: 2009-01-01
forum: Server Platforms
---

### Post by wmgries on 2009-01-01
I set up my installation of the Ubuntu server OS on my computer with an ethernet connection from my Windows machine because I anticipated that to get my wifi PCI card set up I would have to do a lot of downloading and configuring with ndiswrapper.  To aid the process, I installed the ubuntu-desktop metapackage and the gnome interface automatically recognized my wireless card and connected to my network (something that it doesn't do in the Desktop 8.10 version of Ubuntu).  But I can only utilize that connection when I have the desktop loaded; I have it configured so it only loads when I type 'startx' at the command prompt.  Since I am planning on using this server without a monitor in a remote portion of my house, I kind of need to work with the GUI.

Is there anyway to configure the non-Desktop portion of the server to use my wireless connection?

---

### Post by cariboo on 2009-01-01
It shouldn't make any difference if you have /etc/network/interfaces setup with auto wlan0 or whatever you wireless interface. Networking should start automatically whether your are running a desktop or a server.

```
auto lo
iface lo inet loopback

# Primary Network Interface
auto eth0
iface eth0 inet dhcp

# Wireless interface
auto wlan0
iface wlan0 inet dhcp
```

The above would be an example of /etc/network/interfaces

Jim

---

### Post by wmgries on 2009-01-01
Hmm, the wlan0 entry was not in the /etc/network/interfaces file.  When I added it and tried to restart the networking service with sudo /etc/init.d/networking restart, it seem to try and use the card, but couldn't get DHCP settings... it didn't connect to my network.  Do I need to specify which wireless network to connect to and the key?

By the way, the GNOME network manager always asks me for permission to start when I start the GUI.  Are the managers separate?

---

### Post by wmgries on 2009-01-03
Anything?

---

### Post by wmgries on 2009-01-03
Ok, I have finally figure it out.  I need to further configure my /etc/network/interfaces file with the wireless-essid and wireless-key options.

The only further issue is that this seems to have broken the "ubuntu-desktop" meta package I installed, but not that everything is basically configured I'm not too worried about it.  It would be nice to have working later on though if I ever need to make changes.

---

### Post by likebikes on 2009-01-24
Hi I'm new to this server networking lark and am trying to set up a wireless server so i can install it down the shed! i have managed to set up a full 8.04 ubuntu desktop with samba over ssh and the wireless works great.However, i would like to build a pure ubuntu server edition and configure via ssh and putty.However, i dont know how to set up wirelss in terminal. could someone point me in the direction of what files i need to copy on my existing full ubuntu desktop server so i can transfer the wireless config details into my new ubuntu 8.04 server build via terminal.

cheers

---

### Post by Iowan on 2009-01-24
The */etc/network/interfaces* file is the primary file you'll need. [This]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") help page may be useful for general WiFi setup.

---

### Post by likebikes on 2009-01-29
Cheers Iowan i'll give it a go

---

### Post by volkswagner on 2009-02-02
> **Iowan said:**
> The */etc/network/interfaces* file is the primary file you'll need. [This]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") help page may be useful for general WiFi setup.

Where did the thanks button go?

Thanks Iowan, I followed the command line section.  It worked a treat.  I was testing a Linksys card on an old laptop.  I was running Xubuntu 8.04 live CD and the network manager kept stalling on getting the WEP Key.

Now I can move onto the Ubuntu Server install.

---

