---
title: "binding pci devices directly to vfio-pci instead of stubbing first"
date: 2015-12-29
forum: Virtualisation
---

### Post by KillerKelvUK on 2015-12-29
Read somewhere recently that as of kernel 4.1 its possible to bind passthrough devices directly to the vfio driver instead of pci-stubbing them first.  Tried it and works a treat, first impressions are that I get a better overall result as previously my dvb card would hang the guest unless the host was cold booted, since switch the guests boot every time with no hangs etc.

Anyway it was a simple transition to create a new 'local.conf' file in /etc/modprobe.d/.  The contents of the file for me is...

```

cat /etc/modprobe.d/local.conf 
#e159:0001: OpenVox FXO/FXS Card
#1ade:3038: DVBSky Card
#10de:11c8: nVIDIA GTX 650 (video) card
#10de:0e0b: nVIDIA GTX 650 (audio) card


options vfio-pci ids=10de:11c8,10de:0e0b,1ade:3038,e159:0001

```

The problem is the vfio binding occurs later in the boot process than the pci-stub binding, as a result the OpenVox and GTX 650 audio device are grabbed by their legitimate modules first so the vfio binding fails.  I can *fix* this by blacklisting the modules namely snd_hda_intel and netjet which gets my passthrough all working again, however I lose host audio as snd_hda_intel is used by other devices not intended for passthrough.  Again I can easily fix this by issuing a 'sudo modprobe snd_hda_intel' post boot but I was wondering if there is a better/more elegant way of doing this?

---

### Post by heiko_s on 2015-12-30
Thanks for the update. Check out this blog post: [http://vfio.blogspot.co.il/2015/05/vfio-gpu-how-to-series-part-3-host.html]("http://vfio.blogspot.co.il/2015/05/vfio-gpu-how-to-series-part-3-host.html").

I haven't tried that script yet, but it should solve your issue with the late binding. Unfortunately I'm not yet at kernel 4.1, and don't plan to install that on my production system. Maybe in a year or two it will trickle down into LTS.

---

### Post by KillerKelvUK on 2015-12-30
> **heiko_s said:**
> Thanks for the update. Check out this blog post: [http://vfio.blogspot.co.il/2015/05/vfio-gpu-how-to-series-part-3-host.html](http://vfio.blogspot.co.il/2015/05/vfio-gpu-how-to-series-part-3-host.html).

I haven't tried that script yet, but it should solve your issue with the late binding. Unfortunately I'm not yet at kernel 4.1, and don't plan to install that on my production system. Maybe in a year or two it will trickle down into LTS.

Thanks for that...the tl;dr from the blog is to add '[FONT=Arial]rd.driver.pre=vfio-pci' into the grub defaults line which apparently prioritises the vfio-pci module load; this would address my problem however it looks like its a Fedora specific kernel parameter as it hasn't worked for me.  I've looked through [/FONT][https://www.kernel.org/doc/Documentation/kernel-parameters.txt](https://www.kernel.org/doc/Documentation/kernel-parameters.txt) to see if I can spot any alternatives that would work with Ubuntu but no dice so far.

---

### Post by KillerKelvUK on 2015-12-30
Found it...kinda...

/etc/initramfs-tools/modules; I must have edited this in the past (way back) and added in the pci-stub module so I updated it by adding the vfio-pci module and unblacklisted those needed and it work...except for the nouveau module which grabbed my video device (GTX 650) still, so just blacklisted that again = no more manual reloading for sound.

Prob understand this as much as I want to so thanks for the assit heiko_s.

---

### Post by heiko_s on 2015-12-30
:-) You are welcome. Sorry for the confusion, but yes, you got it. Nouveau can be very insistent.

---

### Post by heiko_s on 2016-01-06
I have a 3.19 kernel and am using the script mentioned above in the vfio.blogspot... link. It works like a charm.

---

