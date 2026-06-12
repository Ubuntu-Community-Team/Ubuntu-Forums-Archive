---
title: "Chrome OS on a USB Drive"
date: 2009-12-02
forum: The Cafe
---

### Post by humphreybc on 2009-12-02
Hey guys,

I'm just drafting up a How To install Chrome OS onto a USB Drive using [this image.]("http://chromeos.hexxeh.net/") for my blog, [www.interesting.co.nz](www.interesting.co.nz) 

Has anyone tried out this image and verified that it works and doesn't destroy your computer? The instructions say to run this command:

```

sudo dd if=chromiumos.img of=/dev/X bs=4M

```

Where X is the name of your USB Drive.

As far as I can tell, this is a pretty harmless piece of code - it just writes the image onto the USB Drive. But could someone please verify? I don't want my blog readers wiping their hard drives thanks to me.

Appreciate it.

---

### Post by earthpigg on 2009-12-02
i may give it a shot.

posting so i can find thread later.

---

### Post by humphreybc on 2009-12-02
I'm going to try it out later when I visit the library to download it. We've got shiternet at home, so can't get it here.

My How To will have screenshots for each step etc so if you want to bookmark my blog I should have it posted either tonight or tomorrow.

Cheers

---

### Post by NormanFLinux on 2009-12-02
Try Hexxeh's Google Chrome OS Diet. Its slimmed down yet carries over Ubuntu Karmic's hardware support for Chrome. Its a good way to test it and it will fit a 2GB USB drive.

---

### Post by humphreybc on 2009-12-02
> **NormanFLinux said:**
> Try Hexxeh's Google Chrome OS Diet. Its slimmed down yet carries over Ubuntu Karmic's hardware support for Chrome. Its a good way to test it and it will fit a 2GB USB drive.

Uh yeah that's what I am asking about. So you've tried it and it's safe?

---

### Post by toupeiro on 2009-12-02
[http://ubuntuforums.org/showpost.php?p=8380525&postcount=95](http://ubuntuforums.org/showpost.php?p=8380525&postcount=95)

I can vouch that this process works.  enjoy.

---

### Post by Nerd King on 2009-12-03
Just make it clear that they should be careful what they put in for X. If they put sda for instance it could get messy!

---

### Post by cartisdm on 2009-12-03
I'm confused....I just watched a the video made by the google team about their new OS and I thought this thing wasn't coming out for like 10 months? Did I watch a really old video?

---

### Post by NormanFLinux on 2009-12-03
It boots up but in the current build there is no support for Broadcomm wireless cards. Chrome is essentially the Google browser connected to the Internet. No true desktop to speak of.

---

### Post by Hyper Tails on 2009-12-03
i'll give this a shot

---

### Post by NormanFLinux on 2009-12-03
The final version will be the same. The Google browser plus web apps. Its not meant to be a replacement for a true desktop environment. But when you want to just be in "the cloud" its main advantage is the instant bootup time and fast connection to the Internet because the only thing that loads is the browser on startup.

---

### Post by humphreybc on 2009-12-03
Tutorial is up on my blog. It's for the latest one from Hexxeh, Chrome OS Cherry - released today. The new one adds support for the Broadcomm wireless chipset.

[http://humphreybc.wordpress.com/2009/12/04/how-to-install-chrome-os-on-a-usb-flash-drive/](http://humphreybc.wordpress.com/2009/12/04/how-to-install-chrome-os-on-a-usb-flash-drive/)

---

### Post by NormanFLinux on 2009-12-04
Cool. Most wireless cards today either use Atheros or Broadcomm chipsets and they are both Linux-friendly.

---

### Post by LowSky on 2009-12-04
You know if you tested in a VM you wouldnt have these problems, and your normal data would be safe

---

### Post by NormanFLinux on 2009-12-04
It now connects after waiting five minutes. Its indeed a radical departure from the traditional desktop. There is no software to install and nothing to download. All computing is done from "the cloud" making the traditional desktop redundant.

---

### Post by humphreybc on 2009-12-06
> 
You know if you tested in a VM you wouldnt have these problems, and your normal data would be safe


I'm using a custom kernel so it's a bit of work to load up the kernel module for Vbox or the like. I don't have a use for virtual computers at the moment.

------

Well I tried it out, boots and everything fine but obviously doesn't like my hardware - was as sluggish as anything, unusable.

---

