---
title: "How well willl ubuntu adapt to a new monitor?"
date: 2006-03-09
forum: The Cafe
---

### Post by Rotarychainsaw on 2006-03-09
I have a Dell 2005 in the mail and I know Windows can detect stuff like that on boot up. But I'm Dual booting and have using dapper constantly for the past few weeks. So I'm wondering if Dapper will find this on boot up, or if I'm going to have to edit xorg.conf before hooking it up. Also I will be switching from vga port to DVI on thhis card.

---

### Post by poofyhairguy on 2006-03-09
[QUOTE=Rotarychainsaw]I have a Dell 2005 in the mail and I know Windows can detect stuff like that on boot up. But I'm Dual booting and have using dapper constantly for the past few weeks. So I'm wondering if Dapper will find this on boot up, or if I'm going to have to edit xorg.conf before hooking it up. Also I will be switching from vga port to DVI on thhis card.[/QUOTE]

If the new monitor has different specs (resolution, refresh rate, etc.) then you have to use the magical command:

> sudo dpkg-reconfigure xserver-xorg 

To reconfigure it. It should be easy to answer even the hardest questions (pick a higher difficulty level for the monitor than the base level) because you will have the information in some book that came with the monitor (or on the box).

Do this with you old monitor RIGHT BEFORE you plan to turn the computer off and plug the new monitor in. If you forget to do that, you will have to use the recovery mode.

The VGA DVI should be no big deal, but that might be because I have an Nvidia card.

---

### Post by John.Michael.Kane on 2006-03-09
You should be good to go.. however have a look at this since your switching to dvi [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

---

### Post by Rotarychainsaw on 2006-03-09
Oh I forgot to mention, this is a nvidia 6800, so Hopefully everything will go well.

---

### Post by poofyhairguy on 2006-03-09
[QUOTE=Rotarychainsaw]Oh I forgot to mention, this is a nvidia 6800, so Hopefully everything will go well.[/QUOTE]

Be sure the Nvidia drivers are installed, and when you have the option pick the "nvidia" driver. 

I love Nvidia.

---

### Post by Rotarychainsaw on 2006-03-09
Yeah, Nvidia is win. The reason I haven't used windows in the past few weeks is because of XGL haha. can't wait for the mailman, hope there is no backlight bleeding (although I'm sure there will be)

---

### Post by Rotarychainsaw on 2006-03-14
bump

should be here today. Just seeing if anyone wants to jump in with anything. we all agree that dpkg reconfigure is a must, right?

---

### Post by zAo on 2006-03-14
[QUOTE=Rotarychainsaw]bump

should be here today. Just seeing if anyone wants to jump in with anything. we all agree that dpkg reconfigure is a must, right?[/QUOTE]
Yes. On a 2005FPW here.

---

### Post by Rotarychainsaw on 2006-03-14
hey zAo,
any problems with usplash? I figured text mode widescreen might be weird. like I pass the kernel vga=790 or something, I wonder if there are widescreen codes?

---

### Post by John.Michael.Kane on 2006-03-14
Rotarychainsaw you should be good to go after you run said comand. I'm sure if you have any issues you will let us know, and enjoy  the wide view...

---

### Post by egon spengler on 2006-03-15
My monitor broke last week. I dug out an old spare as a temp and it needed to be reconfigured, the replacement came yesterday and worked straight away. I redid xorg.conf just to be certain but nothing other than monitor identifier changed

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Should auto re-write xorg.conf for you if you can't be bothered to sit through the questions

---

### Post by kayas80 on 2006-03-15
Why can't Ubuntu manually detect refresh rates etc when connecting a new monitor? It would be so helpful if it did.

---

### Post by LordBug on 2006-03-15
That's not a limitation of Ubuntu, but of Xorg.

---

### Post by kayas80 on 2006-03-15
[quote=LordBug]That's not a limitation of Ubuntu, but of Xorg.[/quote]

I hope it's something xorg will fix in the future.

---

