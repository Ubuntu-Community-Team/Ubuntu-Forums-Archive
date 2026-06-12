---
title: "Why use UNR ?"
date: 2009-11-29
forum: Ubuntu Moblin Remix
---

### Post by blkjack26 on 2009-11-29
I really need to know if there is a real advantage to using UNR. I have installed UNR on a new compaq mini 110 and cannot get the broadcom drivers to work. I know there is a fix but it requires a wired connection that i don't have. But Jaunjty works fine out the box for me. Should i scrap the UNR and just use Jaunty?

---

### Post by ugm6hr on 2009-11-29
UNR is available for 9.04 and 9.10.

I believe not including Broadcom proprietary drivers for download was a deliberate omission by Canonical (although it is reported as a bug).

The NBR is basically a front-end for Ubuntu.  No reason to use it unless you like the interface.

---

### Post by gfe on 2009-12-01
Are there any "under the hood" differences, like things that make the Remix work with the processor more efficiently or anything? I'll be getting a netbook later this month, and while the UNR interface doesn't appeal to me, if there's more efficiency (and thus better battery life or speed) I might want to install it.

---

### Post by ugm6hr on 2009-12-02
> **gfe said:**
> Are there any "under the hood" differences, like things that make the Remix work with the processor more efficiently or anything? I'll be getting a netbook later this month, and while the UNR interface doesn't appeal to me, if there's more efficiency (and thus better battery life or speed) I might want to install it.

No.

The lpia version has been dropped.  UNR is a standard i386 build.

In fact, the Netbook Interface runs on top of Gnome, so is actually heavier in terms of RAM use.

---

### Post by gfe on 2009-12-02
That's good information to have. Thanks!

---

### Post by shkaff on 2009-12-03
If the NBR is just a front-end for Ubuntu on top of Gnome, can it be easy turned off and on?

---

### Post by ugm6hr on 2009-12-03
> **shkaff said:**
> If the NBR is just a front-end for Ubuntu on top of Gnome, can it be easy turned off and on?

Sort of... but I think the "switcher" is currently broken.

It used to rearrange my panels every time in Hardy, so I ditched it.

---

### Post by shkaff on 2009-12-04
Could you please hint which tool / applet / script is used for that.
I would like to give it a try with it and make a conclusion regarding its feasibility.

---

### Post by Aearenda on 2009-12-04
The point about UNR for me is that it is optimised to make best use of a small screen (1024x600 in my case) by maximising most windows, and merging the title bar and panel. The Netbook Launcher also makes menu navigation easy for those who can't read small writing, and replaces the traditional desktop. I don't think there are any hidden differences.

BTW, there was a UNR for Jaunty too. The UI was a bit different.

---

### Post by gabz8472 on 2009-12-08
I'm on an MSI Wind, started out with the basic installation of Jaunty then added the NBR UI. I kind of liked the BNR UI  as it maximizes the visual areas of the screen. Other than this, there really isn't much difference between the NBR and the classic UI. Its just better for option for small screens. I haven't tried Karmic, but I usually wait a few months before I move to the new version, this gives the ubuntu guys a chance to clean up the issues that usually crop up. All in all, whether you choose to go with the jaunty or karmic, you might benefit from the NBR UI on a small screen. I also use a 14' laptop, and i havent seen the need to use the NBR on it.

---

### Post by ugm6hr on 2009-12-09
> **shkaff said:**
> Could you please hint which tool / applet / script is used for that.
I would like to give it a try with it and make a conclusion regarding its feasibility.

Just search for netbook-launcher in Synaptic; I think it includes maximus etc as dependencies.

```
sudo apt-get install netbook-launcher
```

---

### Post by shkaff on 2009-12-11
thanks, i managed to find netbook-launcher as well as maximus installed and configured for auto-loading

after disabling both of them i got an empty desktop with no ability to do anything with it... not much impressive

probably i could tune something else and enable context menu, shortcut creation, etc but i realized that UNR is really cool and turned everything back

---

### Post by SnappyU on 2009-12-17
For your sanity, stay off karmic for now.  I tried it on my MSI Wind u100+ and it had couple of issues such as flashing screen (brightness going yoyo) and broken USB

> **gabz8472 said:**
> I'm on an MSI Wind, started out with the basic installation of Jaunty then added the NBR UI. I kind of liked the BNR UI  as it maximizes the visual areas of the screen. Other than this, there really isn't much difference between the NBR and the classic UI. Its just better for option for small screens. I haven't tried Karmic, but I usually wait a few months before I move to the new version, this gives the ubuntu guys a chance to clean up the issues that usually crop up. All in all, whether you choose to go with the jaunty or karmic, you might benefit from the NBR UI on a small screen. I also use a 14' laptop, and i havent seen the need to use the NBR on it.

---

### Post by Sven6210 on 2009-12-18
I am running UNR based on Ubuntu 9.10 Karmix Koala on my EeePC 900a (Atom CPU, 2 GB RAM, 8 GB SSD) and it works very well. I only needed to make 2 patches for WiFi and the microphone, apart from that everything worked out of the box. On Ubuntu 9.04 Jaunty  I needed to do more patches.

I personally like the UNR user interface very much, especially the new one from Karmic (9.10). It improved a lot compared to Jaunty (9.04). I even started with the Beta in beginning of October and since the early beta phase I was rather impressed about the stability.

However I do admit that I installed the UNR only on the netbook due to the fact that it optimises the screen utilization. On my Desktop with a 19' screen I also use the standard Desktop release and I am very happy with that one as well. Due to my netbook I moved from Windows XP to Unbuntu 9.10 on my Desktop. Currently I only have one remaining EeeBox - which is a kind of media center connected to the TV - with Windows XP. And I am considering when to install Ubuntu there as well. The main reason I did not yet try is that I have a Logitech DiNovo keyboard (wireless) with bluetooth. I am not sure how difficult it will be to get it running with Ubuntu...

---

### Post by brian mcgee on 2009-12-24
> **Sven6210 said:**
>  And I am considering when to install Ubuntu there as well. The main reason I did not yet try is that I have a Logitech DiNovo keyboard (wireless) with bluetooth. I am not sure how difficult it will be to get it running with Ubuntu...

I have a diNovo Edge that you simply plug in and it works with Ubuntu 9.10. Nothing to do. Worst case you might have to configure it through Bluetooth Prefs. We also have the older DiNovo at the office, and it works great with Debian Lenny. My advice is test it out on another Ubuntu machine or use a LiveCD.  :)

---

