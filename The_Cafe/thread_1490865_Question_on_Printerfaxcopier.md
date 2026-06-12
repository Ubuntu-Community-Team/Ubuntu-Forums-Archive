---
title: "Question on Printer/fax/copier"
date: 2010-05-22
forum: The Cafe
---

### Post by sports fan Matt on 2010-05-22
What are ya'll's opinions on this printer/copier/scanner combo?

-will I need to dual boot
-is it easy or a pain to set up?

---

### Post by pwnst*r on 2010-05-22
I'm not a fan of combos unless you are on an EXTREME budget.  Combos, from my experience, do not produce results as good as their separate counterparts.  Also, if something breaks on it, you may be out 3 devices, and not just one.

---

### Post by sports fan Matt on 2010-05-22
True but it was a gift so I can't look it in the mouth :)

---

### Post by pwnst*r on 2010-05-22
Oh, you asked for opinions.  They don't matter because you already have one - and free at that.

---

### Post by sports fan Matt on 2010-05-22
Very true.

---

### Post by YuiDaoren on 2010-05-22
> **sox fan Matt said:**
> What are ya'll's opinions on this printer/copier/scanner combo?

-will I need to dual boot
-is it easy or a pain to set up?
It's not in the openprinting database, and I've never tried that model, but:

HP has fair Linux support. It'll probably work, even if you can't get at all the fiddly features.

Best way to know is just to plug the booger in.

---

### Post by sports fan Matt on 2010-05-22
True, I was just seeing if ya'll had heard of it/worked with it.

---

### Post by retro89 on 2010-05-22
I bought this printer and it works great! Im running 9.10 and had to get hplip driver from hp website.I think 10.04 already has these drivers. I used X-Sane with no issues.Only drawback is it dont fit much paper in the tray and ink cartridges are small and ink doesnot last long but im going to get bulk ink and refill it.

---

### Post by stuart.reinke on 2010-05-22
i have one too. l'm very happy with it. I had to get the latest hplip version from hp as the older one in the repos didn't  have support.

---

### Post by Linuxforall on 2010-05-22
Get HP, even the cheapest one is recognized by Ubuntu and runs out of the box, scan works, printer works its total bliss compared to my high end Canon which is nothing but a brick in Linux.

---

### Post by gletob on 2010-05-22
They've got the software great, now if they could just get them to work longer than a year after the end of the warranty....

On a side note my current HP printer hates windows 7 for some reason, have to boot into Ubuntu to print stuff.

---

### Post by sports fan Matt on 2010-05-27
Can anyone tell me how to install the drivers?

---

### Post by FuturePilot on 2010-05-27
Make sure you have hplip-gui, hpijs, hpijs-ppds, and hplip-cups installed. Plug it in and then open HPLIP Toolbox and follow the steps to add a new device.

---

### Post by mihai.ile on 2010-05-27
If you have ubuntu it already comes with those,just plug it in. Ubuntu 10.04 comes with drivers for F2400 series. I do not know if 2430 will work. Someone with this printer and ubuntu 10.04 could confirm if you still need the driver. Best thing is to plug the printer and wait to get installed automatically.

---

### Post by sports fan Matt on 2010-05-27
Ok, I followed the steps but then when I select "Network/Ethernet/Wireless" and click ok, the prompt is " no devices found".

The printer is currently on top of my kitchen counter, and I think this maybe the issue, since it can't access the computer.  I guess I need  possible new ethernet cord to hook into the printer to get it working, or if anyone has anymore suggestions feel free to submit.

---

### Post by FuturePilot on 2010-05-27
If it's wireless it needs to be connected to the network before you can see it. You may have to use the 1 time USB connection option so you can set it up for the network if you can't configure the network directly on the printer itself.

---

### Post by sports fan Matt on 2010-05-27
I don't beleive it's wireless, but I just ran into this error.  cupsd: Child exited on signal 15!

Thanks one and all for assisting--I haven't the slightest idea how to set up a printer

---

### Post by sports fan Matt on 2010-05-27
using this guide: im getting somewhere. [http://www.freesoftwaremagazine.com/articles/printing_ubuntu](http://www.freesoftwaremagazine.com/articles/printing_ubuntu)

---

### Post by sports fan Matt on 2010-05-27
The printer is recognized and installed.

---

