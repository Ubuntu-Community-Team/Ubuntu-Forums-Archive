---
title: "Screen Flickering"
date: 2016-10-07
forum: Ubuntu Development Version
---

### Post by Dawnrazor on 2016-10-07
Hi

I tested aut the new Beta from yesterday.

Now i have extrem Screen flickering wit Nvidia or Intel enabled.

On 16.04 everthing is OK

can somebody confirm this?

Grettings

---

### Post by fthx on 2016-10-07
I don't get any flickering (Intel or Nvidia Quadro M1000M with proprietary drivers, Ub. Gnome).
You should give us some details on your Nvidia GPU.

---

### Post by Dawnrazor on 2016-10-07
HI
My Laptop (Lenovo Z510) has a Die NVIDIA® Geforce® GT 740M and a Intel Grafik (HD Graphics 4600 GPU).
I can switch between them with NVida Prime

---

### Post by nelsoniv on 2016-10-07
I have the same issue with the 4.8 kernels. Seems it&#8217;s upstream.

After a lot of Googling I found a workaround for Intel (i915)

open terminal
gksudo gedit /etc/default/grub
edit line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash&#8221; 
add i915.enable_psr=0 in the quotes e,g.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.enable_psr=0&#8221;
save
sudo update-grub
reboot

---

### Post by Dawnrazor on 2016-10-07
hi nelsoniv

i will check this @home an will give you feedback.

thx

---

### Post by nelsoniv on 2016-10-07
I'm using the Nouveau drivers btw

There's an ongoing bug in the bug tracker that may be related if editing grub doesn't work for you.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1554613]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1554613")

Not sure if it's correct etiquette to link directly on an Ubuntnu forum but if it helps others the Arch Wiki on Intel Graphics explains:

Screen flickering

The following power saving features used by intel iGPUs are known to cause flickering in some instances. A temporary solution is to disable one of them using the appropriate kernel boot parameter option:

    Rc6 sleep modes (see intel#RC6_sleep_modes_(enable_rc6)), can be disabled with i915.enable_rc6=0.

    Panel Self Refresh (PSR) enabled by default since kernel mainline 4.6. To disable this feature use the option i915.enable_psr=0.

---

### Post by Dawnrazor on 2016-10-07
Hi nelsoniv

your first workaraund helped me.

Thank you very much!!!

---

### Post by MikeMecanic on 2016-10-07
Was having the same issue in the launcher area only (Ubuntu Sept28th build).  Switch to Kylin Oct 4[SUP]th[/SUP] build and I don&#8217;t have any bugs.  Intel Graphics(i915).

---

### Post by mistermagio on 2016-10-15
I had the same issue after upgrading to Yakkety Yak, the workaround fixed it. I'm posting because I want to ask what it is we disable to fix it? It may just be placebo effect, but I'm under the impression that my laptop's performance is now slightly more sluggish than it was before. Whether it does have an impact on performances or not, the workaround i.s worth it, just wondering.

Thanks !

---

### Post by nelsoniv on 2016-10-15
"Panel Self Refresh (PSR) enabled by default since kernel mainline 4.6. To disable this feature use the option i915.enable_psr=0"

It's a power saving feature introduced by Intel. Adding the above to grub turns this feature off. You can remove it from grub and see if it helps performance. I've not experienced any speed issues but hopefully there'll be a compatible kernel release soon.

---

### Post by fred.sauze on 2016-10-26
Disabling the psr works for me. Thanks.

---

### Post by zika on 2016-10-27
> **nelsoniv said:**
> I have the same issue with the 4.8 kernels. Seems it&#8217;s upstream.
After a lot of Googling I found a workaround for Intel (i915)
```
[SIZE=6]gksu(do)[/SIZE] gedit /etc/default/grub
```This mistake (explained so many times with its possible consequences) does not want to die. Grub files are not 1s You want to make mistake with/on... ;) Even though that file is root-owned there are feasible scenarios of trouble...

---

### Post by nelsoniv on 2016-10-27
You're right, zika. :oops:

Edited and updated :)

---

