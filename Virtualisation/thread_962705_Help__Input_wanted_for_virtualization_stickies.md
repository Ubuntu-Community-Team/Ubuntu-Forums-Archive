---
title: "Help : Input wanted for virtualization stickies"
date: 2008-10-29
forum: Virtualisation
---

### Post by bodhi.zazen on 2008-10-29
With the release of Intrepid, I would like to update the How to VMWare sticky and add one for VirtualBox and possibly one for KVM as well. (OpenVZ anyone ?)

Anyone wanting to help or offer suggestions, feel free to either post here or PM me (otherwise I will do my best with both 32 and 64 bit versions).

_Please no flaming or "fan boys", each package has advantages and disadvantages_

---

### Post by 080729jk on 2008-10-30
&#12289;[**&#32593;&#31449;&#25512;&#24191;**](http://www.jingke.org/)[**&#32593;&#31449;&#20248;&#21270;**](http://www.jingke.org/)[**&#34394;&#25311;&#20027;&#26426;**](http://www.jingke.org/xunizhuji.htm)[**&#32593;&#31449;&#20248;&#21270;**](http://www.jingke.org/wangzhanyouhua.htm)&#25628;&#32034;&#24341;&#25806;&#20248;&#21270;&#35786;&#26029;&#24037;&#20855;&#12289;&#24120;&#29992;&#32593;&#31449;&#25512;&#24191;&#26041;&#27861;&#12289;[url=http://www.jingke.org/]**&#32593;&#31449;&#25512;&#24191;**[/url

---

### Post by Dyffo on 2008-10-31
Have just upgraded to 8.10 , have reinstalled V Box , I cannot for the life of me remember how to set up the USB ports, I might have a problem with Guest additions as well. From memory we had a sticky on this .

---

### Post by philetus on 2008-11-03
This works for me

1. Go to System-Administration-Users&Groups, unlock the groups and go down to vbox users, click on it and add yourself.Remember the group: number (mine=125).
2. Do sudo gedit /etc/fstab and add the line:
none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0

being XXX the group ID of your user when you look under System-Administration-Users&Groups for the group vboxusers.

3. Enable USB
In a terminal type:
sudo gedit /etc/init.d/mountdevsubfs.sh

You need to look for this section:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

And delete all the # shown, it should look exactly like this.

(I didn't have this section so I just added  the following:

#Magic to make /proc/bus/usb work

mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

4. In your virtual OS, see if you need to install the USB controller.

---

### Post by Dyffo on 2008-11-04
All done - thanks - works fine

---

### Post by bodhi.zazen on 2008-11-04
Just a (brief) update for the community.

I am working my way through some of the options.

I worked through qemu last night. It does not appear xen or openvz are available the in 8.10 (it appears xen will be DomainU only, ie guests not host). The openvz kernel is not yet in the intrepid repo.

That leaves Virtualbox and a tips section, ie USB devices and networking.

Once that is done I will consolidate all the stickies.

---

### Post by philetus on 2008-11-05
You may have seen my post here:
[http://ubuntuforums.org/showthread.php?t=971002](http://ubuntuforums.org/showthread.php?t=971002)

Which is similar to these:
[http://forums.virtualbox.org/viewtopic.php?t=10744](http://forums.virtualbox.org/viewtopic.php?t=10744)
[http://forums.virtualbox.org/viewtopic.php?t=8563](http://forums.virtualbox.org/viewtopic.php?t=8563)

I had a question mark in my virtual W2k device manager for a "PCI device",but I figured it was my PCIe vidio card, which you don't use in VB so I disabled it.

This morning, on a whim, I deleted it and now my problem is gone.
I will probably have to delete it again when I reboot the Virtual W2k, but that isn't very often if I'm not forced to.

---

### Post by bodhi.zazen on 2008-11-07
OK, I got a start on a "Mega thread" and took down the other stickies.

I will finish when I can , then I will open the mega thread for comments and take this "suggestions" thread down as well.

Again, if anyone has any suggestions or would like to help please send me a PM.

If there is a link I overlooked, I apologize, please send me a PM and I will add it in.

---

### Post by bodhi.zazen on 2008-11-12
OK, I am almost finished. Any final comments ? Suggestions ?

I have not received much in the way of offers to help, so, in the absence of team work you will be stuck with me, and all my biases, and mistakes. And I can only keep things just so up to date. I do not have an installation of windows XP for example, let alone Vista or OSX.

So please, anyone who has any suggestions, consider offering assistance.

---

### Post by Dyffo on 2008-11-14
Sorry can't help. I have V.Box on 8.10 all working fine, am running X.P on V.Box.again all fine I did have an issue trying to record on the cd/dvd drive, this has been resolved by V.B. they confirm that the record facility is not yet available. I also have  a problem in trying to set up network sharing of files and printers, this I also believe is not yet possible.If I can be of any help - which I doubt - just point me in the direction required.

---

