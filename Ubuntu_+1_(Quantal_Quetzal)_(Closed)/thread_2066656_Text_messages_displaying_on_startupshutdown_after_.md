---
title: "Text messages displaying on startup/shutdown after latest updates"
date: 2012-10-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by alphacrucis2 on 2012-10-05
After the latest round of updates I get text messages displaying on startup and shutdown. It does boot ok to the GUI login though. Possibly Plymouth has got a bit broken. Also autohide in unity has stopped working. The latter happened to me in 12.04 after an nvidia update from xswat ppa. After upgrading to 12.10 that problem went away but is now back again.

---

### Post by dino99 on 2012-10-05
check /etc/default/grub about "quiet splash" settings

---

### Post by alphacrucis2 on 2012-10-05
> **dino99 said:**
> check /etc/default/grub about "quiet splash" settings

Currently 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

I presume that is correct

---

### Post by macstevejb on 2012-10-05
I believe this is the result of an nVidia update that hit the repositories yesterday (v304.51) On my machine this also gives rise to a lack of graphics during boot and shutdown.

So anyone with an nVidia graphics card will be experiencing the same problem. (This does not occur on my intel graphics-based laptop).

No doubt this will be fixed soon, after all, this IS still a development version.

Regards

---

### Post by gspe on 2012-10-05
> **macstevejb said:**
> I believe this is the result of an nVidia update that hit the repositories yesterday (v304.51) On my machine this also gives rise to a lack of graphics during boot and shutdown.

So anyone with an nVidia graphics card will be experiencing the same problem. (This does not occur on my intel graphics-based laptop).

No doubt this will be fixed soon, after all, this IS still a development version.

Regards

Affect my system too after i did an update this mornig

---

### Post by stinkeye on 2012-10-05
Same problem here with new nvidia drivers.
Can bring back plymouth with the old fixes.
IE.
```
gksudo gedit /etc/default/grub
```
and add the line
```
GRUB_GFXPAYLOAD_LINUX="[COLOR="Magenta"]1680x1050[/COLOR]"
```
Using [COLOR="magenta"]your native resolution[/COLOR].
Then
```
sudo update-grub
```


and for plymouth only showing briefly
```
gksudo gedit /etc/initramfs-tools/conf.d/splash
```
and add this line
```
FRAMEBUFFER=y
```
save the file.

Then
```
sudo update-initramfs -u
```

---

### Post by funicorn on 2012-10-05
check if you have dkms installed.

---

### Post by Harry33 on 2012-10-05
This issue is due to the nvidia-current_304.51 update from yesterday.
To solve it, download the same correctly built driver from xorg-edgers and all is well again.

---

### Post by Frogs Hair on 2012-10-05
Seeing the  same with Nouveau but just received another kernel Update. I'll see what happens at restart. I did not see this Nvidia  Current.

---

### Post by macstevejb on 2012-10-05
How does using the xorg-edgers ppa help here? This is the beta version of what will become 12.10 later in the month. Shouldn't have to install bleeding edge stuff from a non-official source.

I'd rather this problem be thrashed out and corrected during development from official sources and if not, revert to a previous more stable nVidia driver.

Just my 2p

Regards,

---

### Post by Frogs Hair on 2012-10-05
Back to normal after kernel update and I also returned to Nvidia current.

---

### Post by serdotlinecho on 2012-10-05
When i'm using 12.04 with NVIDIA Corporation G98 [GeForce 8400 GS], the ubuntu plymouth looks terrible. This workaround(answer no.2)help me to get the normal ubuntu plymouth.

[http://askubuntu.com/questions/6033/enabling-nvidia-driver-messes-up-splash-screen](http://askubuntu.com/questions/6033/enabling-nvidia-driver-messes-up-splash-screen)

The config settings persists after upgrading to ubuntu 12.10(partial upgrade), though. :)

---

