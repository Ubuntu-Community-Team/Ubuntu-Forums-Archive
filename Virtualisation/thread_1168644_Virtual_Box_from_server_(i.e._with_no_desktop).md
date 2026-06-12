---
title: "Virtual Box from server (i.e. with no desktop)"
date: 2009-05-24
forum: Virtualisation
---

### Post by bodycorp on 2009-05-24
Hi can I virtualise (e.g. XP using e.g. VirtualBox) from an Ubuntu server (e.g. Jaunty) with no visual desktop running on the host machine ? i.e. with no gnome/gdm nor kde running on the host server?  I want to cut out the processing overhead of the graphical desktop on the host . Thanks Colin

---

### Post by Cheesemill on 2009-05-24
I'm not sure if it can be done with VirtualBox, but I do it all the time at work with an 8.04 minimal CLI server install and VMware Server.

Cheesemill

---

### Post by balloooza on 2009-05-24
```
VBoxHeadless
```

Use the capitolization!!

Two ways to do it:
ONE: 
```
VboxManage createvm --name xp
```
then 
```
VBoxManage modifyvm (figure out the options you need)
```

then 
```
VBoxHeadless -s xp
```

then use annother machine (windows or ubuntu) and connect to the server using RDP that is right RDP!!! use the ip of the HOST

and setup windows

TWO: (this is if you have no other machine connected in the SERVERS network)
1. Install the server, use an x environment temorarily (startx) on the host
> sudo apt-get install tsclient fvwm

then run
```
startx
```

now open an xterm (or whatever the terminal is) and type
```
tsclient
```

THen connect to localhost, and install the desktop, and you are done!!

---

### Post by veloce on 2009-05-25
I haven't tried it with vbox but use vmware server that way.  They are windows vms so I rdp to them from a Ubuntu Desktop.

---

### Post by bodycorp on 2009-06-03
Balooza,

Thanks for your reply and advice to try VBoxHeadless.

I am now working each day programming on a Windows XP virtualised (Headless as per your suggestion)under Ubuntu 9.04. This is a very convenient work arrangement for me. 

While it is working well, performance is a bit problematical (though still workable) .. The dual AMD core AMD (and INTEL on the second machine) processors are reporting quite often 100% load on at leat one processor and very high also on the other. The cause of part of the processor load  is that I have to leave gdm running on the host machine .. even though it is not being used most of the time. If I go to Ubuntu 9.04, System, Adminisration, services .. and deselect "graphical login manager gdm" (or leave it deselected for boot) then of course Gnome desktop ceases and the machine shows just the Linux command line interface ... and the virtual xp machine which is running imediately crashes and closes itself i.e. no gdm / Gnome then no virtual XP PC. The result is the same whether I run the virtual machine Headless or not.

If you have a suggestion on how to configure so that gdm can be closed (or never installed and just ubuntu server installed )  but a virtual windows machine till able to run , then that would be an improvement and would reduce the load on the machine as the monitor is showing that the gnome desktop and XOrg are chewing up a noticeable slice of the processors capacity i.e. around 15 %.

Many thanks again for the initial info which was very helpful.

---

### Post by bodhi.zazen on 2009-06-03
Just to throw out options, if you have the hardware, KVM comes with a VNC server "built in", so no need to install a VNC server on the guest.

---

