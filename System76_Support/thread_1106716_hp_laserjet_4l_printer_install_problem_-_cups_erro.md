---
title: "hp laserjet 4l printer install problem - cups error"
date: 2009-03-26
forum: System76 Support
---

### Post by elphaba on 2009-03-26
Have done some troubleshooting with CUPS.  Found message below n the CUPS log which I access by going to [http://localhost:631/admin/log/error_log](http://localhost:631/admin/log/error_log)  
 
"cupsdAuthorize: Local authentication certificate not found!"

Anyone know how I can fix this. I'm thinking I will be able to print once I can get rid of this error. 

I'm running system76 pangolin laptop
Ubuntu 8.10
using ppd file downloaded from linuxprinting.org
using usb to parallel port adaptor (which works fine without a driver on an xp laptop)

There are suspicious errors showing in dmesg about "inode permission" but thought I would start with cups error log first.

Any thoughts?

---

### Post by thomasaaron on 2009-03-26
That error message seems to be fairly prevalent. Here's one that might help...

[https://lists.ubuntu.com/archives/ubuntu-users/2007-February/106384.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-February/106384.html)

So, you might try going to Applications > Add/Remove Software and downloading the HPLIP Toolbox.

---

### Post by formol on 2009-03-26
for HPLIP, I suggest to go directly on the hplip website and go get the most recent version.  I solved a printer with my HP printer that way.

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by elphaba on 2009-03-28
Thanks for the tips. I've got the HPLIP installed but before I proceed, I need to restore the original /etc/cups/cupsd.conf file. Idiot that I am, I made some changes trying to fix the printer problem and didn't save a backup copy of the original. The changes I made are preventing me from adding a printer.

So...I found "cups configuration" in the add/remove list under applications.
Thought I would remove cups and then re-install.  Well, system won't let me. Says I need to use the Synaptic package manager. What's that? is that the original Debian "apt-get" utility?

If anyone has a new Pangolin ubuntu 8.10 and if they could post their /etc/cups/cupsd.conf file, that would probably be the simplest method.

Or is there another way around this problem?

---

### Post by formol on 2009-03-28
to use Synaptic, go to System - Administration - Synaptic Package Manager.

then search for HPLIP

EDIT : CUPS i mean

---

### Post by elphaba on 2009-03-28
Thanks formol but in the meantime, I found /etc/cups/cupsd.conf.default which was a "clean" version of the config file I needed.  In case anyone else doesn't know, I guess others have this on their system as well in case they happen to be idiots too and not backup their cups config file before making changes.
  Anyway, I got back my privileges to manage the printers. I started over. Looks like the HPLIP added all the HP drivers. I was able to choose one for the printer I have even though it is rather old.  I setup the queue and printed a test page and still nothing.  
  Perhaps I have the "device URI" incorrect. I guessed and used
[http://www.localhost/ipp/](http://www.localhost/ipp/) (I think) or something like that.
  since this printer is on a usb port, I'm thinking I might should have
entered something in the form of usb://localhost  
  Anyway, I've ordered a new printer and chose one that is supposed to work with ubuntu - a Brother wireless laserjet mono printer so I'm hoping this headache will soon be behind me.  But I hate that I couldn't get this working with ubuntu.  Looks like some of the stuff they say about drivers on linux causing more problems than drivers on windows may still have some truth. Oh well, I still prefer not having the old Microsoft logo on my computer.
  Thanks to Thomas and Formol for your help.

---

### Post by formol on 2009-03-28
what is the model of your HP? most of them work.

---

### Post by jdb on 2009-03-28
To manage printers in CUPs browse to

[http://localhost:631/](http://localhost:631/)

jdb

---

