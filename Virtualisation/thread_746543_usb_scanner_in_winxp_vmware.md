---
title: "usb scanner in winxp vmware"
date: 2008-04-05
forum: Virtualisation
---

### Post by StOoZ on 2008-04-05
I used to have a scanner in windows, when I used it as my only OS.
now I use windows only in VMware, I have the USB enabled in vmware server.

is there anyway to use my umax astra 5600 (bad ,crappy scanner..doesn't work under linux) ???
I have the windows drivers, they installed perfectly, but windows doesnt recognize the scanner.

---

### Post by fjgaude on 2008-04-05
Have you clicked on the Removable Devices in VM and seen your scanner there?

That has to be done each time you boot Ubuntu and go into vmware.

---

### Post by StOoZ on 2008-04-05
u mean the little vmware logo where to clock is in the vm'ed windows?

---

### Post by fjgaude on 2008-04-05
I mean the VM tab menu, then click on Removable Devices, then click on USB Devices, and there you should see your scanner. Click on it. Then see if you can find it in Windows.

This is the same menu you used to Install VMware Tools.

Let us know how you are doing.

---

### Post by StOoZ on 2008-04-06
well, it doesnt shows up there... :(

---

### Post by fjgaude on 2008-04-06
There's your answer... Try adding this line to your /etc/fstab file as the last line:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Do this with this:

```
gksudo gedit /etc/fstab
```

Then reboot and see if you can find the USB scanner in Devices.

Let us know how you are dong.

---

### Post by StOoZ on 2008-04-07
well it worked, now it sees the device, what does this command exactly do?

there is another problem, but it has anything to do with configuration (I guess...), when I install the driver, during the installation process , I get a BSOD )-:

---

### Post by fjgaude on 2008-04-07
> **StOoZ said:**
> well it worked, now it sees the device, what does this command exactly do?

there is another problem, but it has anything to do with configuration (I guess...), when I install the driver, during the installation process , I get a BSOD )-:

I'm not sure but it seems to solve a "race" issue when the bootup process occurs. It is needed for many setups, but not for all.

I don't understand, the driver for the scanner doesn't load, produces BSOD? I don't know what to say about that. It is the correct disk for this scanner, eh?

---

### Post by StOoZ on 2008-04-07
well on a native winxp (dont remeber the SP version) this driver worked flawlessly.
now when I try it on the vm'ed version of Winxp pro SP3 It produces a BSOD on the installation process , Sad.
I'll give it another try, and maybe install it on a different XP version (SP) , it might work or not...
this is the BSOD im getting:
[http://msdn2.microsoft.com/en-us/library/ms797153.aspx]("http://msdn2.microsoft.com/en-us/library/ms797153.aspx")

---

### Post by fjgaude on 2008-04-07
I have no idea, other than the driver doesn't like the USB support built-in vmware server. I have an old scanner that is not Linux supported but it works perfectly in server, in all that I've used, 1.0.3 through 1.0.5.

Good luck!

---

### Post by StOoZ on 2008-04-07
thats what you get when you want to save some bucks ... umax scanners :(:mad:

---

### Post by fjgaude on 2008-04-07
Just thought of something, that SP3. Pray where did you get that?

---

### Post by StOoZ on 2008-04-07
its already SP3, I might try a different version of windows, say win me? or 98?
I need that scanner to work, and I dont want to dual book ,even though I have a dual booted system (xp and ubuntu)

---

### Post by fjgaude on 2008-04-07
Yes, but how did you get SP3. AFAIK it's not out, not officially.

---

### Post by StOoZ on 2008-04-07
Well, my windows xp sp3 is genuine , the SP3, is a beta /not final whatever, but the latest available sp3.

---

### Post by fjgaude on 2008-04-07
I think there's a good chance that the SP3 is the problem. Can you install a WinXP SP2? That is what I run.

Seems there's always something that stops things from perfectly working, eh?

---

### Post by StOoZ on 2008-04-07
first of all, thanks for your help , it is much appreciated.
and yes, there is always a problem :(
but you know, as a new user to linux (only two months) , I like when such things happen, thats the only way to really learn stuff.
I will install SP2 and also both Win2000 & Win2003, and then give it a try.

---

### Post by fjgaude on 2008-04-07
Let us know how things work out... you know, we all are learning day-by-day.

---

### Post by StOoZ on 2008-04-08
Well problem is solved, win2000 advanced server did the job.
Now , I'll try doing the same on windows XP SP2 clean install

---

### Post by fjgaude on 2008-04-08
I thought that SP3 might have something to do with the problem... SP2 should be okay.

---

