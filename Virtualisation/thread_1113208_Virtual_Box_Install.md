---
title: "Virtual Box Install"
date: 2009-04-01
forum: Virtualisation
---

### Post by keygiwawah on 2009-04-01
I'm new to linux and virtual box.  When I install virtual box it asks for the drive has the disk.  Is there a way to install the virtual box without using a disk?

---

### Post by MaindotC on 2009-04-01
You should  be able to download the .deb file from the download.virtualbox.org site.  That installer should not prompt you for anything like a disk location.

---

### Post by keygiwawah on 2009-04-01
Not the actual Virtual box install, It asks for the disk that the operating system is on.

---

### Post by Perryg on 2009-04-01
> **keygiwawah said:**
> Not the actual Virtual box install, It asks for the disk that the operating system is on.

It might help if you provided a little more information.
What is the Host OS,  and the guest OS,  Which version of VBox are you using.

---

### Post by bodhi.zazen on 2009-04-01
You can install from an iso.

for example, download the ubuntu desktop .iso, set the iso as the cd drive, and away you go ;)

---

### Post by itendo on 2009-04-02
i'm willing to bet* you have a ubuntu flavor "Host" and you want to run a [you prior OS] "Guest" machine. before installing, decide on how crucial USB support is; that determines whether you use the Virtual Box flavor OSE (no support, already installed), or PUEL (USB support, search forums for install guide).

anyway, the program wants your Guest OS's install disk. if you want Windows, have your Windows CD, etc.

(*if youre new to linux i doubt you want to ISO five flavors of it quite yet)

---

### Post by keygiwawah on 2009-04-02
I have now installed Mint as the guest OS with Vista as the host OS on the virtual box.  After I installed it I was using it and both the host and guest OS were working fine.  When I restarted my computer now, it tries to boot Mint.

If anyone knows of a way that I could temporarily boot vista by a shortcut key or something that would be great, then I could redo the virtual box.

---

### Post by itendo on 2009-04-02
are you trying to dual boot or run a virtual machine?

---

### Post by bodhi.zazen on 2009-04-02
Or did you install wubi ?

---

### Post by keygiwawah on 2009-04-03
I'm running a virtual machine... The mint is not installed on the computer, it just tries to boot it off of the disk.  If there is no disk in the drive it comes up with like error 17 or something on grub and just sits there.  When i boot mint off of the disk it has an install icon on the desktop, so I dont think it is on a partition.  My vista partition is still there and I can see it on mint, I just don't know how to boot it.

---

### Post by Perryg on 2009-04-03
> **keygiwawah said:**
> I'm running a virtual machine... The mint is not installed on the computer, it just tries to boot it off of the disk.  If there is no disk in the drive it comes up with like error 17 or something on grub and just sits there.  When i boot mint off of the disk it has an install icon on the desktop, so I dont think it is on a partition.  My vista partition is still there and I can see it on mint, I just don't know how to boot it.

It sure sounds like you have installed the mint distro on the primary partition.  Can you post the contents of the grub file here so we can see if there is anyway to get this back?  You can find it under /boot/grub/menu.lst

---

### Post by bodhi.zazen on 2009-04-03
> **Perryg said:**
> It sure sounds like you have installed the mint distro on the primary partition.  Can you post the contents of the grub file here so we can see if there is anyway to get this back?  You can find it under /boot/grub/menu.lst

Actually, boot the live CD and open gparted, post a screen shot, let's look at your partitions.

---

### Post by keygiwawah on 2009-04-03
Ummmm... Sorry stupid question, how do i take a screen shot on mint?

---

### Post by Perryg on 2009-04-03
> **keygiwawah said:**
> Ummmm... Sorry stupid question, how do i take a screen shot on mint?

I see from here and the VBox forums that you are really struggling with this.  My suggestion is to do what Bondi said and then hand write the results here instead of worrying about the screen shot.  Try to be exact in what you send.

---

