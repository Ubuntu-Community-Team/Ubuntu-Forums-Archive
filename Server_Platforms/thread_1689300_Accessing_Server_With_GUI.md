---
title: "Accessing Server With GUI"
date: 2011-02-16
forum: Server Platforms
---

### Post by Orange Worker on 2011-02-16
Hello,

I had Ubuntu Server installed on my server which used to be in a data center. I have since pulled it out of the data center. How can I access the server with a GUI interface?

I used to be able to access it with a GUI when I had it at the data center, but I can't remember how I was doing it.

The software I've listed below is installed on the server, but when I turn the server on, I only get a blank screen.

-LAMP
-PEAR
-Webmim
-FTP Server
-SSH

Thanks,
-H

---

### Post by James78 on 2011-02-16
When you say GUI, do you mean a Desktop GUI (e.g. Gnome or KDE) or a Web GUI?

If you mean Desktop GUI, then you could install "gnome-desktop". If you don't want all the extra packages, you could install "gnome-core" instead, then install only what you want.

If you mean web GUI, then to access Webmin, you go to the machines IP/domain name, with port 10000 (unless it's been changed).

---

### Post by volkswagner on 2011-02-16
I'm not sure how you accessed it with a GUI, perhaps it was Webmin, or your provider had a control panel allowing you access to your server's ip address.

Most likely the server is setup with a static ip address.  You may want to reconfigure that for your local LAN first.

Since you have a blank screen you may also have video issues.

I would start by booting the machine with a live cd.  Mount the local drive and look for /etc/networking/interfaces file.  You will want to edit the settings for you local LAN.  If you get networking up and running you can access your server by it's new ip address you assign.  This will allow you to use Webmin, ftp, ssh.

If you are able to access the machine via ip, you may not need a monitor connected at all.

---

### Post by James78 on 2011-02-16
> **volkswagner said:**
> I'm not sure how you accessed it with a GUI, perhaps it was Webmin, or your provider had a control panel allowing you access to your server's ip address.

Most likely the server is setup with a static ip address.  You may want to reconfigure that for your local LAN first.

**Since you have a blank screen you may also have video issues.**

I would start by booting the machine with a live cd.  Mount the local drive and look for /etc/networking/interfaces file.  You will want to edit the settings for you local LAN.  If you get networking up and running you can access your server by it's new ip address you assign.  This will allow you to use Webmin, ftp, ssh.

**If you are able to access the machine via ip, you may not need a monitor connected at all.**
1. And if worst comes to worst, they bought a machine without any onboard video card.
2. Always a plus.

---

### Post by Orange Worker on 2011-02-16
Thanks for the quick responses. I was using Webmim to access the server at the data center from my home, but I'm not sure how to set it up so I can do it like that again. Sorry I didn't mention that earlier. Either way, I'm assuming that I will need two internet connections to access the server that way again, is that correct?

Thanks,
-H

---

### Post by James78 on 2011-02-16
From the top of my head, the way to solve the problem might be.

1. Change the connection from the old static IP to a new static IP.
2. Access Webmin at <ip>:10000

Webmin should automatically start itself up, so you just need to make sure the server actually has it's networking working. If it still doesn't, make sure that Webmin isn't tied to a specific IP in the config (you'll have to go config file hunting!)

---

### Post by Orange Worker on 2011-02-16
Would it be easier to access it with FTP? I don't necessarily need the GUI, just need to access the files. Would this scenario listed below be possible?

1. Connect server to an internet connection

2. From another computer/internet connection, launch Filezilla.
-Host should be the IP of the server (how can I get the current IP address from the server,
is their any code that I can use to display it?)
-I'm assuming the user/pass would be the same that it's always been cause I never changed it.

---

### Post by weblizist on 2011-02-16
It all depends on where your workstation logically is placed related to the new home of the server. Is it on the same sub-net? Do you know the new IP address of the server ... you might want to run "fping" from a different server on the same subnet to find new'n'active IP's.

I'm also confused about the black screen? Are you able to connect a keyboard and monitor to the server? ... does the screen remains black, even if you hit <enter> or <ALT>+F1(F2)...F7?

---

### Post by James78 on 2011-02-16
If the server is successfully connecting to the internet, and you have a router, you would see it in your routers DHCP list, otherwise the internet most likely isn't working yet for that server; check /etc/network/interfaces to see if it lists any static IP, then you can just change all the settings to your own to fix it.

You could also use netdiscover to find the IP (again, only works if it successfully connected)

---

### Post by Orange Worker on 2011-02-16
I don't believe the server is successfully connecting to the internet cause when i plug the ethernet cable into it and try to use my laptop (wireless), it doesn't work.


What would I need to type as line code to access what you mentioned? Or is that What I need to type in?

/etc/network/interfaces

---

### Post by Orange Worker on 2011-02-16
This is what I see when I turn on the server and it settles in:



fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 145604/4685824 files, 16652514/18730240 blocks



I can't type anything though. I do have a monitor, mouse and keyboard.

---

### Post by James78 on 2011-02-16
I forgot to tell you that you should probably use a LiveCD to get at that file. Just open the file and post the contents in a [CODE] tag (unless you know how to edit the file yourself).

So if that's what you see, everything works graphics wise at least. A LiveCD should work then. I don't know why it's getting stuck there though. Do you plan on re-installing eventually? All you want are the files right? If so, you can just use a LiveCD to get at the systems contents, then re-install or whatever after. Would save a bunch of time trying to fix a system you're just going to tear down right after anyways.

---

### Post by Orange Worker on 2011-02-16
James,

Yes, I'm planning on wiping out the server and selling it anyway, so no need to try and fix.

I will take your advice and try using a live CD, but I don't have one. I had a developer install everything for me. Could you tell me which version of the software I need to download? ...then I'll burn a copy.

Thanks,
-H

---

### Post by spynappels on 2011-02-17
Any Desktop version CD will work as a live CD, I'd suggest using 10.04 32bit which can be downloaded directly from Ubuntu.com, or as a bittorrent.

---

### Post by Orange Worker on 2011-02-17
Okay, I will download the version you recommend. Could you give me a heads up on what I need to do to access the files once the CD is running?

---

### Post by volkswagner on 2011-02-17
Once you boot the live CD, navigate to >places and look for your hard drive.  You can also mount a usb drive to copy to, are if your network card is up and running, you may be able to copy data to a network drive/machine.

It is hard for us to determine where your information is but I'd first check your home directory and www directory.

```
/home/user
/var/www/
```

---

### Post by Orange Worker on 2011-02-17
Okay, great. My data is going to be here, I know that for sure.


/var/www/
I'll get back to you once I burn the CD and make an attempt at getting my data.

Thanks,
-H

---

### Post by Orange Worker on 2011-02-17
Burning Ubuntu Desktop 10.04 worked!! I was able to access my files, so I copied everything on a USB drive. Thanks to everyone for your help. :D

-H

---

### Post by Orange Worker on 2011-02-17
I don't see the "prefix" option so I can mark this thread as solved. :confused:

---

### Post by James78 on 2011-02-17
Top of the thread, "Thread Tools", click on it to expand it, then click "Marked as solved"

---

