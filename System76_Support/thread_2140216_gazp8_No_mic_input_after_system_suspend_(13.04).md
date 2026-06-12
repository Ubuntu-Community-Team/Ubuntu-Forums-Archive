---
title: "gazp8 No mic input after system suspend (13.04)"
date: 2013-04-29
forum: System76 Support
---

### Post by tonyr2k8 on 2013-04-29
After taking the laptop out of suspend, the internal mic input does not work. 
My current fix requires me to plug in an external mic into the input port, then remove it, after that the internal mic will work again.

Using the 3.2.7 driver. Issue was not present when using 12.04.2 or 12.10.

---

### Post by usind on 2013-06-17
This is just a workaround but might help. 

Open a terminal (ctrl+alt+t) and type:
 sudo alsa force-reload

---

### Post by KlipperKyle on 2013-06-22
Try checking your microphone with pavucontrol.

```

sudo apt-get install pavucontrol
pavucontrol

```

pavucontrol is the Pulse Audio control panel. Your microphone might just be disabled.

---

### Post by rorschachwalter on 2013-07-19
Did you file a support ticket on this?

This problem is repeated in the GazP9. Very bad form.

---

### Post by screaminj3sus on 2013-07-31
> **rorschachwalter said:**
> Did you file a support ticket on this?

This problem is repeated in the GazP9. Very bad form.

according to the OP it worked fine in 12.04.2 and 12.10, so it sounds like an upstream kernel driver regression.

Have you guys tried the latest alsa drivers to see if its been fixed upstream yet? [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by vaughnhannon on 2013-08-20
> **KlipperKyle said:**
> Try checking your microphone with pavucontrol.

```

sudo apt-get install pavucontrol
pavucontrol

```

pavucontrol is the Pulse Audio control panel. Your microphone might just be disabled.


I'm also on a gazp8 and this worked for me.  Too bad we need a workaround tho.

V

---

### Post by rjwiii on 2013-08-28
I just got my gazp9 a few days ago and had this issue. Close the lid & the mic stops working. Here's my version of the work around:


[LIST]
[*]Open lid.
[*]Install pavucontrol as above.
[*]Launch pavucontrol.
[*]Click on the "Input Devices" tab.
[*]Switch from "Internal Microphone" to "Microphone" from the "Port" dropdown.
[*]Switch back.
[*]Mic should now Work.
[/LIST]

Hope this helps.

rjwiii

---

### Post by tonyr2k8 on 2013-08-31
Thanks for all of the help. It's working good for me.

---

### Post by Willynux on 2013-09-11
I also have a similarproblem on my gazp9 except that I don't need to suspend the computer for the mic not to work.
I also use the workaround you mention, exactly the same steps but it's not consistent after reboot, I have to do it all over again...
I was not expecting to babysit my ubuntu on a system76 computer. All threads I've read go to more or less the same solutions. And none have worked completely yet. :confused:

---

