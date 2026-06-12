---
title: "More usb woes with Virtual Box"
date: 2008-05-25
forum: Virtualisation
---

### Post by Azalar on 2008-05-25
I am trying to get USB working in Virtual Box following a zillion guides that I have found here on the forums and around the net but still no joy.
The steps I have taken so far include..

Adding myself to the vboxusers groups, the group id was 25

Editing the mountdevsubfs.sh file and uncommenting the 4 lines that always get mentioned in the guides.

Adding the line..
none /proc/bus/usb usbfs devgid=25,devmode=664 0 0
in my fstab file

Allowing access to the usb bus with..
sudo chown -R root:vboxusers /proc/bus/usb

And finally editing the mountkernfs.sh file and adding..
domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev,devgid=25,devmode=664

When I plug in any usb device Linux immediately grabs it for its own use
So like if I plugin a usb stick it will auto mount and view the files.
But when I go in virtual box it isn't seeing these.
I'm out of things to try, does anyone know anything else I can try?

Thanks

---

### Post by BobLand on 2008-05-26
If you plug the device into the computer then go to the virtualbox settings, select USB.  On the right hand panel are usb icons.  Select the second from top.  This should set the device automatically.

This worked for me after having similar problems with my printer.

However, while vbox now sees my printer connected to the usb port, and xp sees it also, I can't get xp to print.  Hopefully, you will have better luck.


bobland

---

### Post by ddixonr on 2008-05-26
I had the same problems you are having, went to (I'm sure) the same guides and tutorial sites, and nothing seemed to fix this problem.

After hours of troubleshooting, I realized that there are TWO versions of virtualbox. One has usb support, and the other does not. If you cannot see any settings for usb on the left side of the settings menu, then you have the wrong version. 

I am surprised that not more people are talking about this.

---

### Post by CameO73 on 2008-05-26
Oh, and don't forget to enable USB for your virtual machine. Select the virtual machine -> Settings -> USB -> Enable USB & Enable USB 2.0 Controller.

Btw, the latest and greatest VirtualBox can be found at [http://virtualbox.org/wiki/Downloads](http://virtualbox.org/wiki/Downloads). The one in Synaptic is slightly outdated.

---

### Post by kxmas on 2008-05-26
I found that the suggested fstab entry didn't have enough options.  This one sets the bus permissions and the device permissions.  It also worked for me, while the other one didn't.

gid=46 is plugdev on my system

```
none                   /proc/bus/usb   usbfs   devgid=46,devmode=664,busgid=46,busmode=775 0 0
```

---

### Post by CameO73 on 2008-05-27
Well, all I needed were the steps [in this guide](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html). The line in /etc/fstab looks simply like this:
```
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0
```
(where 124 = groud id for vboxusers)

---

### Post by Azalar on 2008-05-30
The guide you mentioned is excellent and it all works well now.
The problem in my case is I started by installing the very latest version, ie the Sun download, now that they own the product.
The one in the guide is slightly older when it was owned by Innotek.
So I guess there is some problem with the Sun version and USB on Hardy.

---

### Post by theZoid on 2008-05-31
Here is another guide I put together myself...same stuff, different place :D  [http://linuxchronicles.wordpress.com/](http://linuxchronicles.wordpress.com/)

---

### Post by dm6257 on 2008-06-01
Thanks.  I have been struggling with USB on VirtualBox since the Hardy upgrade.  My USB devices were recognized but grayed out.  When I created the usbuser group and modified the permissions as you describe, it now works.  (I have no idea what I did,  just that it works!)

---

### Post by sawk on 2008-12-01
Hi, I had the same problem after upgrading from vbox 1.6 to 2.0.4, after tring everything suggested above, i found that i added previously in /etc/fstab/   

none /proc/bus/usb usbfs devgid=120,devmode=664 0 0

needed changing to 

none /proc/bus/usb usbfs devgid=126,devmode=664 0 0

because after checkin system - users and groups - vboxusers 

had changed to 126

---

