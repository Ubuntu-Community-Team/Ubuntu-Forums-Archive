---
title: "USB Flash drive problems in VMWare"
date: 2008-10-02
forum: Virtualisation
---

### Post by traveler400 on 2008-10-02
I am running ubuntu 8.04 with VMware server running XP.  I have a flash drive that I am trying to access via the XP VM.  When I plug it in Ubuntu finds it no problem.  It also appears in the VM console as a usb drive.  But when I click connect from the console I get:

Remote USB device error: Remote device disconnected: an error occured while sending data.


After that the red X appears over the drive.  Any ideas on what could be causing this?  It seems strange because I am able to connect my iPhone 3G in the VM but the flash drive fails.  Any help would be appreciated, I am a total Ubuntu noob trying to convert...

Thanks,

-A

---

### Post by fjgaude on 2008-10-02
Is there a chance that a driver disk came with the USB drive that is to be installed in Windows? Just a thought...

---

### Post by traveler400 on 2008-10-03
no, that isn't the issue.  the issue is getting it to recognize at all within the windows VM.  It doesn't get to the point where I'd be able to add the driver...

---

### Post by fjgaude on 2008-10-03
You simply load and run the driver program, from a CD or wherever it is stored, while you are in Windows VM, not in the USB Devices menu.

Many folks have found that adding this line to /etc/fstab fixed the issue:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Maybe it would for you.

---

### Post by traveler400 on 2008-10-03
tried it but no go.  I'll keep hunting...thanks for the suggestion.

---

### Post by traveler400 on 2008-10-03
After some more hunting the only other users I see with this issue are in Germany and they don't seem to have found a solution either.  getting desperate...

---

### Post by ready4thebreak on 2008-10-04
I got it! BUY A NEW FLASH DRIVE. lol. But really try out other flash drives are be sure that it's specific to that flash drive. Because they can act really strange sometimes. Apparently it's not the usb hub in VMWare, it's all about the device or maybe just  flash drive support in general, so give another one a try.

---

### Post by douillet on 2008-10-04
Hi,
I had the same problem

I have find this solution

In the file /etc/fstab

You add the following lines

usbfs /proc/bus/usb usbfs auto 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

Good luck

---

### Post by traveler400 on 2008-10-06
PROBLEM SOLVED!!!!

Many thanks...

---

### Post by lionstone on 2009-03-05
Yep this worked for me, too...Thanks!

---

### Post by wh1t3bunny on 2009-03-12
> **douillet said:**
> 

In the file /etc/fstab

You add the following lines

usbfs /proc/bus/usb usbfs auto 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0


Thanks, this worked for me, too!

---

### Post by slyman1973 on 2009-03-18
I believe this fixed my problem too, but it appears that it took having the host computer completely off and connecting the usb drive, booting the host and then all of a sudden VMWARE let me see that device and another that I never unplugged. They both showed up on the devices list on the guest and a little mounting/unmounting on the host and I got it on the guest!! thank you!!!

---

### Post by mjzap on 2009-03-19
I use Virtual Box instead of VMWare and the solution is almost the same except that you have to add a usr for USB access in addition to the fstab lines. In VB, they state that once the guest (Windows etc) OS takes control of the USB drive, it is no longer accessible by the host (Ubuntu).

I would imagine that this result is the same and for the same reasons. (whatever those may be) My guess is it is a data write/read/execute issue since the mouse, keyboard and other standard input devices switch between the guest and host seamless.

---

### Post by ourmartin on 2009-04-09
Sorry, you'll have to explain it to an idiot. How do I add: 

usbfs /proc/bus/usb usbfs auto 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

...or more precisely, where? I added the lines underneath the rest of the text (cd & floppy info) and saved. Made no difference. Where exactly do I put the lines? 

Incidently, VMWare doesn't recognise my CD either... Bugging....

---

### Post by eweibust on 2009-05-04
Well, I too added the two lines mentioned in this post to my /etc/fstab and I'm still not able to connect a usb drive to my Win Vista VM running inside my Ubuntu VMWare Server.

How can I debug this?  Should I be looking for help here or over on the VMWare forums?

Thanks...
Erik

---

### Post by drdave69 on 2009-07-18
> **douillet said:**
> Hi,
I had the same problem

I have find this solution

In the file /etc/fstab

You add the following lines

usbfs /proc/bus/usb usbfs auto 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

Good luck

what is the terminal command to do this?

---

### Post by monicams on 2009-08-29
> **drdave69 said:**
> what is the terminal command to do this?
Hi, if you need to edit the file, once you open the terminal, type:

cd /
gksu gedit /etc/fstab

then add comments (if you wish) and the two lines:

# I included the next lines to fix problem using USBs in VMWare
# following [http://ubuntuforums.org/showthread.php?t=936094](http://ubuntuforums.org/showthread.php?t=936094)

usbfs /proc/bus/usb usbfs auto 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

Then save the file and exit.

---

### Post by XboxModder on 2010-06-09
I've been trying to find my xbox 360 hardrive in virtual box using a data transfer cable and it wont come up. I've tried the solutions posted in this thread but it says that there is no /ect/fstab file. 

Any suggestions?

---

