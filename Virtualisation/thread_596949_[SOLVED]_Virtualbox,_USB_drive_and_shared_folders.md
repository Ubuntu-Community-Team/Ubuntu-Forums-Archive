---
title: "[SOLVED] Virtualbox, USB drive and shared folders"
date: 2007-10-30
forum: Virtualisation
---

### Post by lsutiger on 2007-10-30
Hi all! I installed VB and having a few problems.
With the USB, when I click on settings, I get the following error:
```
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}

 
```

I am not totally sure what this means, but in the end it means it doesn't work.

Next I have a shared folder called Programs in VB and Downloads in Ubuntu. It is listed in the shared folders. When I am in windows and use :
net use f: \\vboxsrv\Programs

I get an error 53 - network path can not be found. When I try in network places, nothing is listed, when in the network computers, I see my maching (linux-1501) and the VM, but I can not access the linux-1501, username and password do not work. When I map network drive \\vboxsrv\Programs I get the same error as net use of course.

What I want to do is access a folder on my machine from the VM and use my usb drive also.
Thanx for any input!

---

### Post by paul.matthijsse on 2007-10-30
hello,

not sure about the USB part of your question, but under Settings of your VM (or in the right pane of VirtualBox) there's a option to enable USB and what USB device exactly. Did you do that?

To see your shared folder(s), yoe need to mount the drive they are on, like:
# mount -t vboxsf [-o OPTIONS] sharename mountpoint

More about this in the very well written help-file of VirtualBox (F1). :-)

Paul.

---

### Post by kcy29581 on 2007-11-01
More info for you guys:

[http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)

Basically, in the file /etc/init.d/mountdevsubfs.sh you need to edit the lines:

```
#
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

```
to look like this (removing four #'s):

```
#
     # Magic to make /proc/bus/usb work
     #
     mkdir -p /dev/bus/usb/.usbfs
     domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
     ln -s .usbfs/devices /dev/bus/usb/devices
     mount --rbind /dev/bus/usb /proc/bus/usb
 
```

---

### Post by notwen on 2007-11-01
> **kcy29581 said:**
> More info for you guys:

[http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)

Basically, in the file /etc/init.d/mountdevsubfs.sh you need to edit the lines:

```
#
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

```
to look like this (removing four #'s):

```
#
     # Magic to make /proc/bus/usb work
     #
     mkdir -p /dev/bus/usb/.usbfs
     domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
     ln -s .usbfs/devices /dev/bus/usb/devices
     mount --rbind /dev/bus/usb /proc/bus/usb
 
```

Thanks for the link.  I'll be sure to try my VirtualBox images USB capabilities once I get home.

---

### Post by lsutiger on 2007-11-01
Originally Posted by kcy29581  View Post
More info for you guys:

[http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)

Basically, in the file /etc/init.d/mountdevsubfs.sh you need to edit the lines:

Code:

#
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

to look like this (removing four #'s):

Code:

#
     # Magic to make /proc/bus/usb work
     #
     mkdir -p /dev/bus/usb/.usbfs
     domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
     ln -s .usbfs/devices /dev/bus/usb/devices
     mount --rbind /dev/bus/usb /proc/bus/usb


I have done that already. I can see the usb tree under device manager in my XP vm but when I attach my usb drive I see nothing

---

### Post by kcy29581 on 2007-11-02
lsutiger, sorry, but I forgot the extra steps! My test pc was upgraded to 7.10, and I did these steps back in 7.04...

Just follow the steps on the Virtualbox wiki:

[http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04](http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04)

I know it say 7.04, but the steps apply to 7.10 as well.

After this, once you have Windows running in Virtualbox, you can right-click on the USB icon in the bottom-right corner and select what USB device you want to activate. I usually ensure that any storage devices are unmounted in Ubuntu first, otherwise data loss may occur.

Good luck!

---

### Post by lsutiger on 2007-11-02
Thanx for the reply kcy29581, but I did that also.
You say > After this, once you have Windows running in Virtualbox, you can right-click on the USB icon in the bottom-right corner and select what USB device you want to activate
But all I see there is the Guest Additions. When I right click on it, notta.
I wonder what I am jacking up here...
I double checked all the work and all of it is ok.

hmmm.....

---

### Post by kcy29581 on 2007-11-03
lsutiger, this is what I mean (and see):

The USB icon I mentioned is the one circled in red in the following screenshot:

[IMG]http://i17.photobucket.com/albums/b87/kcy29581/Ubuntu/VirtualboxUSBscreenshot1.png[/IMG]

Then, when I right-click the screenshot, I see this, and just click on the USB device name I want to be enabled:

_[IMG]http://i17.photobucket.com/albums/b87/kcy29581/Ubuntu/VirtualboxUSBscreenshot2.png[/IMG]_

What do you see with regards to this USB icon?

---

### Post by lsutiger on 2007-11-03
Geez, I feel like a box of rocks! I was running in seamless mode and therefore did not see the menubar from VB. 
Thanx a bunch! got it working!

---

### Post by kcy29581 on 2007-11-03
> **lsutiger said:**
> Geez, I feel like a box of rocks! I was running in seamless mode and therefore did not see the menubar from VB. 
Thanx a bunch! got it working!

No problem, mate! :)

---

### Post by Green_Star on 2007-11-11
I am trying to connect my bluetooth usb device, i get the same error when ever i start VB.

Even after booting VB if i try the way how kcy29581 showed in his screeshots, this is disconnecting bluetooth usb from ubuntu (i can see that bluetooth icon dissappered on ubuntu panel) and after 3-4seconds, that icon comes again on ubuntu panel and VB popsup the same error. I badly need that bluetooth working for my VB. 

thanks in advance.

---

### Post by lsutiger on 2007-11-11
Hmmm... I had that problem when I connected a backup ide laptop drive via usb adapter. It went away in Gutsy (7.10)

---

### Post by Green_Star on 2007-11-12
I can find so many help articles and post regarding USB file system but not about USB devices like phones, scanners, printers etc....

---

### Post by riokerr on 2007-11-13
I tried the examples that kcy29581  and lsutinger said in the previoius posts by editing the files : 
/etc/udev/rules.d/40-permissions.rules &
/etc/init.d/mountdevsubfs.sh 

I can get my windoze guest to recognise the usb devices with one very annoying consequence... The usb devices in gutsy disappear when windoze mounts them.  I have a usb hard disk, a card reader and both times windoze mounts either one of them they disappear from linux host.  Is there anyway to fix that?

Thanks in advance!

---

### Post by mate84 on 2007-11-23
Hi!
I installed virtualbox. I used this how to ( [http://ubuntuforums.org/showthread.php?t=603661](http://ubuntuforums.org/showthread.php?t=603661) ) and there I read USB supported!

---

### Post by Portable_Jim on 2007-12-16
> **kcy29581 said:**
> More info for you guys:

[http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)

Basically, in the file /etc/init.d/mountdevsubfs.sh you need to edit the lines:

```
#
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

```to look like this (removing four #'s):

```
#
     # Magic to make /proc/bus/usb work
     #
     mkdir -p /dev/bus/usb/.usbfs
     domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
     ln -s .usbfs/devices /dev/bus/usb/devices
     mount --rbind /dev/bus/usb /proc/bus/usb
 
```
May seem like a simple thing, but you may have to restart to get this to work, If you do not want to restart issue
```
$ sudo /etc/init.d/mountdevsubfs.sh stop
$ sudo /etc/init.d/mountdevsubfs.sh start
```you can then start up Virtualbox

I am using the Linux Format article on Virtualbox (LXF97 page 98-101), however they miss out this problem.

---

