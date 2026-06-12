---
title: "USB devs not found."
date: 2010-11-15
forum: Virtualisation
---

### Post by Diametric on 2010-11-15
So, I installed Virtualbox from Oracle this weekend so that I would have USB functionality.  I'm using XP Pro SP3 as the guest OS - and while running the VM, the tool bar at the bottom shows the USB devices I have plugged in (a logitech game controller, thumb drive, external HD) but I can't get the guest OS to "see" them.  Interestingly, I use a wireless mouse and keyboard and there is no issue.  
 
So, as soon as I plug in a USB device Virtualbox populates the USB dev list, but the gues OS has no access.  Can anyone point me in the right direction?
 
Thanks in advance.

---

### Post by Diametric on 2010-11-17
[COLOR=black][FONT=Verdana]So here is a screenshot of what I'm talking about.  See how the USB devices are grayed out and while the system "sees" them, they are not accessible.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]Thanks...[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][/FONT][/COLOR]

---

### Post by Diametric on 2010-11-24
I found the naswer is case anyone is interested.  From a CLI simply type: 
 
 
```
sudo VirtualBox
```
 
 
This allowed my USB devices to work - logitech game controller, External HD, Thumbdrive etc...
 
The interesting thing is that I had to recreate my XP VM - the one I made previously (not as root) wouldn't load.  But...it all worked out in the end as I now have a working XP VM with full USB functionality.

---

### Post by sumithar on 2010-12-25
> **Diametric said:**
> I found the naswer is case anyone is interested.  From a CLI simply type: 
 
 
```
sudo VirtualBox
```
 
 
This allowed my USB devices to work - logitech game controller, External HD, Thumbdrive etc...
 
The interesting thing is that I had to recreate my XP VM - the one I made previously (not as root) wouldn't load.  But...it all worked out in the end as I now have a working XP VM with full USB functionality.

Hi,
How do you mean you had to recreate the XP VM?  Did you have to put the XP install CD back in and reinstall?
Thanks

---

### Post by Dobbin99 on 2011-01-15
Adding my user to the disk group fixed this for me.

    sudo usermod -a -G disk myuser

---

### Post by Dobbin99 on 2011-01-15
Adding my user to the disk group fixed this for me.

    sudo usermod -a -G disk myuser

---

