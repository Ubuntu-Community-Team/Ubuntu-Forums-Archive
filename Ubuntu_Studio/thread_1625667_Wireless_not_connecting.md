---
title: "Wireless not connecting"
date: 2010-11-19
forum: Ubuntu Studio
---

### Post by guest5 on 2010-11-19
I first want to say thanks in advance to all the helpful folks here.  If this has been asked and answered, could someone please provide a good link for me.  I am a noob - sorry.

I just installed studio 10.10 on my friends desktop - not any problems at all.  So I decided to try it again on my laptop.  The install went well, however I cannot connect to my wireless network.  

I navigated to system/administration/network and turned on the wireless option, entering my ssid and passowrd - no option to actually connect to it; I believe the following to be the issues:

1.  Upon startup, Ubuntu has a popup message saying something about network discovery not being turned on.  I don't know how to turn it on.  So I first went to read the documentation on "To connect to a wireless network"

2.  There is no Network Manager icon in the system notification area

---

### Post by cchhrriiss121212 on 2010-11-19
You should just need to install a network manager, Studio does not come with one. If you have a wired connection handy, plug it in and search for gnome-network-manager in synaptic. The nm-applet should show up next time you boot.

If you have no wired connection, all the files are included on the studio image but you must install them in the right order. They are deb files so just click on them to install.

---

### Post by guest5 on 2010-11-19
thank you.  I installed gnome-network-manager in synaptic, but there is still no applet for me to play with.  What can I try next please ?

Edit in:

I noticed that both networks, wireless as well as the other one, well, the entire tab which they used to reside in has disappeared from the menu items in administration / network ? ? ? ?

---

### Post by guest5 on 2010-11-19
OK, the place to find this connection interface (might be called something else, don't know) was not in administration / tools any longer, but now it exists under system/preferences/network connections. 

Thank you very much.

---

### Post by cariocakev on 2010-11-24
I too, cannot get a wireless connection.

I have enabled the broadcom driver, installed the Network manager all according to the instructions found on the Ubuntu Studio support site.

I have used the System > Preferences > Network Connections dialogs to enter SSID and WPA password.

But the machine does not find a network.

Is there an element of software still missing to enable wireless connections? It was seamless in Xubuntu so I never sleuthed out the mechanics of it.

Running on a Macbook Pro 6,2.

Thanks!

---

### Post by den2042 on 2010-12-05
First of all you have to make sure that the only entry in your /etc/network/interfaces file is

auto lo
iface lo inet loopback 


You can change the contents of this file by typing in terminal

gksudo gedit /etc/network/interfaces

This will allow you to view and edit the /etc/network/interfaces. You will have to delete some lines.
Now REBOOT
Might help sometimes
[http://www.geteasypeasy.com/forums/viewtopic.php?f=12&t=2890](http://www.geteasypeasy.com/forums/viewtopic.php?f=12&t=2890)

HOWEVER
It might be another issue 
Try to play with encripting and encoding in your home WLAN. Might help as well.

---

### Post by hueygunner on 2010-12-14
I followed your link.  It was somewhat helpful.  I'm in the root and I'm running terminal.  I typed pon dsl-provider and I'm getting a bunch of gibberish in the terminal box now.  I tried <CTRL + c> to stop it but... It finally stopped by itself.

---

