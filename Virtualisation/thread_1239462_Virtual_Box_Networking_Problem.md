---
title: "Virtual Box Networking Problem"
date: 2009-08-13
forum: Virtualisation
---

### Post by tyke on 2009-08-13
Hey all.

Having a spot of bother with networking in Virtual Box. I'm using Virtual Box 2.2.4, running XP as the guest OS. For some reason, it will not start the Network Adapter. I've tried all five virtual adapters offered, and they all have the same problem. The device manager in XP just gives a yellow exclamation mark and this error:

```
This device cannot start. (Code 10)
```

I RTFM on the[ [COLOR="Red"]Virtual Box website[/COLOR]]("http://download.virtualbox.org/virtualbox/3.0.4/UserManual.pdf") (Warning, PDF), and it suggests running the virtual card in NAT mode, which is what I've done, but I also tried it in not attatched mode. No difference, same error message. 

The vboxnetflt module is loaded, I checked. 

I have no doubt I'm missing something blindingly obvious, but I'm totally stumped. Any help would be greatly appreciated.

---

### Post by kestrel1 on 2009-08-13
Have you installed vbox guest additions?
I would also suggest that you get the latest version of Vbox, I think it is on V3.0.4 now

---

### Post by jocampo on 2009-08-13
Did you try this (exact order) 

1. Remove adapter
2. Reboot and log in into XP vm (with no adapter at all)
3. Shutdown
4. Add adapter again
5. Restart, login and check

For some reason (don't ask me why) sometimes when playing with NICs on XP virtual machines, if I restart and login after change, XP gets crazy and does not recognize NIC drivers. Doing "2" someway cleans the registry. You won't loss anything trying

BTW, are you using NAT or Bridged network? try last one and let us know. Also, be sure you installed VBox additions ...

---

### Post by tyke on 2009-08-13
Thanks for the replies.

> **jocampo said:**
> Did you try this (exact order) 

1. Remove adapter
2. Reboot and log in into XP vm (with no adapter at all)
3. Shutdown
4. Add adapter again
5. Restart, login and check


Tried this, made no difference. Still gives the same error.

> **jocampo said:**
> 
BTW, are you using NAT or Bridged network? try last one and let us know. Also, be sure you installed VBox additions ...

Tried as both NAT and bridged network. Both give exactly the same error, the adapter cannot start. VBox additions is installed.

Anyone have any other ideas?

---

### Post by tyke on 2009-08-13
I have also upgraded to the latest Virtual Box version in the repositories, still receiving the same error message in the device manager.

---

### Post by kestrel1 on 2009-08-13
> **tyke said:**
> I have also upgraded to the latest Virtual Box version in the repositories, still receiving the same error message in the device manager.
What version is in the repo's? I prefer to use the download from Sun [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by jocampo on 2009-08-13
Can you please post the exact error?

---

### Post by tyke on 2009-08-13
> **jocampo said:**
> Can you please post the exact error?

Well, it's not an error message as such. Under the Device Manager in the windows System Properties, the VMware Accelerated AMD PCNet Adapter has a yellow exclemation mark next to it, indicating there is some kind of problem. 

If you select the device and open its properties window, the Device Status box reads:

```
This device cannot start. (Code 10)

Click Troubleshoot to start the troubleshooter for this device.
```

Obviously, this leaves me with no network connections available. Which is something of a problem, since Virtual Box is effectively useless to me without a net connection.  Oh, and the trouble-shooter is worse than useless.

I really hope someone can shed some light on this for me. I desperately want to ditch my window partition and do away with re-booting. 

BTW, I really appreciate the suggestions so far.

---

### Post by jocampo on 2009-08-13
This is a really weird situation, 'cause to me, looks like a driver problem. The issue here is that this is a "fake" machine. I suggest this ... download the driver for VirtualBox NIC (don't remember which one, maybe Intel or AMD, but is something like that) Make an iso (maybe you should included several drivers in that ISO, just in case) Mount that ISO as CD and when VirtualMachine boot again, use that as a new driver. Of course, you will have to uninstall the device using Device Manager, etc...but later, setup and install the one that is suitable for your NIC.

Kind of force workaround but obviously, Windows is not recognizing the fake driver VirtualBox is providing.

---

### Post by kestrel1 on 2009-08-13
What nic do you have?

---

### Post by tyke on 2009-08-13
OK, I'm going to give jocampo's idea with the drivers try, but that can wait till tomorrow, since it's 23:30 where I am, and I have work in the morning. Will let you know how I get on.

And kestrel1, the PC is using a belkin wireless card, RTxxx chipset.

---

### Post by tyke on 2009-08-14
OK, everything works now. Just in case anyone else hits the same problem, here's what I did.

Reinstalling the drivers for the default Network card, the AMD PCNet, made no difference, it still refused to start. The Intel PRO/1000 card however did start once I'd reinstalled the drivers, and it appears to be working just fine. 

I've no idea why the default virtual NIC refused to play nice, but I'm content to live in ignorance now I have a net connection.

If anyone else has problems with the default networking, switch to the Intel desktop card and re-install the drivers.

Thanks for all the help to everyone, and thanks to jocampo for the fix.

---

### Post by jocampo on 2009-08-14
> **tyke said:**
> OK, everything works now. Just in case anyone else hits the same problem, here's what I did.

Reinstalling the drivers for the default Network card, the AMD PCNet, made no difference, it still refused to start. The Intel PRO/1000 card however did start once I'd reinstalled the drivers, and it appears to be working just fine. 

I've no idea why the default virtual NIC refused to play nice, but I'm content to live in ignorance now I have a net connection.

If anyone else has problems with the default networking, switch to the Intel desktop card and re-install the drivers.

Thanks for all the help to everyone, and thanks to jocampo for the fix.

Awesome man! :-) ... please mark it as SOLVED! en enjoy your virtualization environment ...

---

### Post by veroxii on 2010-02-04
> **tyke said:**
> 
Reinstalling the drivers for the default Network card, the AMD PCNet, made no difference, it still refused to start. The Intel PRO/1000 card however did start once I'd reinstalled the drivers, and it appears to be working just fine. 


+1

I had the same issue and the same fix. My issue started though because I was trying to run a VMWare image in Virtualbox. It's all working fine now after changing the adaptor to "Intel PRO/1000 T Server (NAT)"

Cheers,
-V

---

