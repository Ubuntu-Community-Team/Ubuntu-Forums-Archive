---
title: "Can't Enable Desktop Effects?"
date: 2011-05-08
forum: Virtualisation
---

### Post by Jasonix on 2011-05-08
Well, I'm using VirtualBox to virtually run Ubuntu 10.10. First, I enabled 3d Acceleration in VirtualBox. Then, I have installed the ubuntu additions by putting the disc file on my desktop and double clicking it, and running the automatic prompt(it asks if I want to run it like this). I installed, rebooted, and tried to enable advanced desktop graphics. It said scanning for drivers, then, it said it could not enable the desktop effects.
Any suggestions?

P.S:Installing Ubuntu is something I do not want to do, so do not post that as a solution.

---

### Post by Dedoimedo on 2011-05-08
Did you try running the guest addons installation from command line?
Dedoimedo

---

### Post by Jasonix on 2011-05-08
> **Dedoimedo said:**
> Did you try running the guest addons installation from command line?
Dedoimedo

It does run from command line...I click on vboxadditions disc, then brings up some files, and I click autorun.sh(I'm pretty sure that's what it's called). Btw, I have an asus eah 5770(it has radeon hd 5770). Also, when running compiz-check, it says no rendering method or something related to rendering...

---

### Post by Jasonix on 2011-05-09
Bump. Any suggestions?

---

### Post by wilee-nilee on 2011-05-09
> **Jasonix said:**
> Bump. Any suggestions?

Virtual machines have their own drivers, sometimes they are not totally compatible with all the effects.

You could do a full install on a thumb though, and have the bling. 

I did not suggest a install on your computer, so don't yell at me for a usable option.;)

---

### Post by Jasonix on 2011-05-10
> **wilee-nilee said:**
> Virtual machines have their own drivers, sometimes they are not totally compatible with all the effects.

You could do a full install on a thumb though, and have the bling. 

I did not suggest a install on your computer, so don't yell at me for a usable option.;)

No, this is my newer computer. The other I haven't done anything to, yet. Anyway, people can use the guest addition drivers to run the desktop effects...

---

### Post by SecretCode on 2011-05-10
How much video memory did you allocate? Try 64MB.

What version of Virtualbox ... and what is your host OS?

---

### Post by Jasonix on 2011-05-10
> **SecretCode said:**
> How much video memory did you allocate? Try 64MB.

What version of Virtualbox ... and what is your host OS?

I have 128mb video memory there, and 4.0.6 version(latest version). Windows 7 64 bit host and ubuntu 10.10 64 bit guest. However, I get an error when starting up the guest os or adding it to virtualbox. The guest os is actually on my father's account on the newer computer, and I'm not sure if it works, but when I try to add the guest os to virtualbox on my account, it has an error code. VBOX_E_INVALID_OBJECT_STATE (0x80BB0007) is part of the code. I'll post the whole thing later.

(I don't have access to the newer computer right now).

Newer Computer Specs: Amd Phenom II x6, asus eah5770(radeon hd 5770), g skill 2x2gb ddr 3 1600.
Thanks in advance!

---

### Post by SecretCode on 2011-05-10
In your Ubuntu guest, do you have build-essential and linux-headers-generic installed? I can't recall if they are installed by default in 10.10. And without them, guest additions may not completely install.

In a terminal
```
sudo apt-get install build-essential linux-headers-generic
```
If they're already installed this will do nothing

Then reinstall the guest additions - but this time from a terminal.
```
/media/VB
*press tab - it will autocomplete the path - something like*
/media/VBOXADDITIONS406.iso/
*then type*
/media/VBOXADDITIONS406.iso/autorun.sh
```

---

### Post by Jasonix on 2011-05-10
> **SecretCode said:**
> In your Ubuntu guest, do you have build-essential and linux-headers-generic installed? I can't recall if they are installed by default in 10.10. And without them, guest additions may not completely install.

In a terminal
```
sudo apt-get install build-essential linux-headers-generic
```If they're already installed this will do nothing

Then reinstall the guest additions - but this time from a terminal.
```
/media/VB
*press tab - it will autocomplete the path - something like*
/media/VBOXADDITIONS406.iso/
*then type*
/media/VBOXADDITIONS406.iso/autorun.sh
```

Thanks, but I get an error code when adding ubuntu (the existing guest os on my other computer account) to virtualbox on my computer account, and when starting it up. The code is VBOX_E_INVALID_OBJECT_STATE (0x80BB0007){d2de270c-1d4b-4c9e-843f-bbb9b47269ff}. Any suggestions?

---

### Post by Jasonix on 2011-05-10
I didn't install linux headers first, only dkms and build-essential. I hope it will work to install linux headers, but I need help to fix the error code.

---

### Post by SecretCode on 2011-05-11
> **Jasonix said:**
> Thanks, but I get an error code when adding ubuntu (the existing guest os on my other computer account) to virtualbox on my computer account, and when starting it up. The code is VBOX_E_INVALID_OBJECT_STATE (0x80BB0007){d2de270c-1d4b-4c9e-843f-bbb9b47269ff}. Any suggestions?

I'm not clear what's going on here ... are you moving a VM image from a different computer? Which computer accounts are you referring to?

Invalid object state sounds like you have a saved state (which can't be used on another computer if for example you have a different CPU). You would need to click "discard" - the effect of this on the guest is like powering off without shutting down & you have to reboot the guest.

---

### Post by Perryg on 2011-05-11
Are you installing the guest additions (on the guest)?  Sounds like you are trying to install them on the host and this will cause all kinds of issues.

---

### Post by Jasonix on 2011-05-11
> **Perryg said:**
> Are you installing the guest additions (on the guest)?  Sounds like you are trying to install them on the host and this will cause all kinds of issues.

I'm installing it on the guest.

---

### Post by Jasonix on 2011-05-11
> **SecretCode said:**
> I'm not clear what's going on here ... are you moving a VM image from a different computer? Which computer accounts are you referring to?

Invalid object state sounds like you have a saved state (which can't be used on another computer if for example you have a different CPU). You would need to click "discard" - the effect of this on the guest is like powering off without shutting down & you have to reboot the guest.

It's on the same computer, just adding it to virtualbox on another computer account. I don't have access to the virtual guest os on MY account. When clicking add in virtualbox I get this error(I post wrong code before sorry)
  VBOX_E_OBJECT_NOT_FOUND (0x80BB0001)
   IVirtualBox {d2de270c-1d4b-4c9e-843f-bbb9b47269ff}

It also says could not find an open hard disk with uuid.

---

### Post by Jasonix on 2011-05-11
Update: I have successfully launched ubuntu 64 bit guest, but now the screen is small, even when it is maximized. I launched it by making a new virtualmachine, then deleting it, and then adding back the old one. But, the screen is small, and it is having monitor issues. My monitor is an acer e211h( this is what windows 7 reports). Thank You.

I have posted a picture of my small screen of guest os.

Edit: Nevermind, I just had to switch to scale mode. Anyway, back to business. Anyone else got fixes to enable desktop effects?

---

### Post by SecretCode on 2011-05-12
Make sure that "auto-resize guest display" is ticked under the Machine menu.

If it is and it's still not working, then guest additions is not properly installed. Go back to earlier posts.

---

### Post by Jasonix on 2011-05-12
> **SecretCode said:**
> Make sure that "auto-resize guest display" is ticked under the Machine menu.

If it is and it's still not working, then guest additions is not properly installed. Go back to earlier posts.

It still doesn't work with that. I have reinstalled guest additions using command line many times. Are there are packages I should install before installing guest additions? Like linux-headers, but that didn't work. Could you guys research some more packages I should install? Also, some people had to uninstall all traces of ati or nvidia. I use ati. I have an asus eah5770, which has a radeon hd 5770. What packages should I uninstall?

Thanks in advance!

---

### Post by SecretCode on 2011-05-13
I don't what else to suggest, **except reinstall guest additions in a terminal window and post the entire output here**. That may point out something.

---

### Post by Jasonix on 2011-05-17
I still can't enable desktop effects with update 4.0.8 virtualbox. Anyway, should I open a terminal from accessories(I've always done this) or open command line by using ctrl-alt-f2?

---

