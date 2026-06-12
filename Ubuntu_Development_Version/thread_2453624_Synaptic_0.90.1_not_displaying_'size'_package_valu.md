---
title: "Synaptic 0.90.1 not displaying 'size' package value"
date: 2020-11-14
forum: Ubuntu Development Version
---

### Post by dino99 on 2020-11-14
Get that error into a terminal:

(synaptic:6482): Pango-WARNING **: 06:06:00.982: Invalid UTF-8 string passed to pango_layout_set_text()

---

### Post by Frogs Hair on 2020-11-14
Can you clarify ? I see the package size when properties are selected in the GUI.

---

### Post by dino99 on 2020-11-14
The 'size' column is displaying some rectangular symbols instead of numerical values as expected. This happen on a gnome-shell on xorg session with US language . Never had that issue before this synaptic upgrade.

---

### Post by lonniehenry-gmail on 2020-11-15
I am seeing this , too.  Gnome shell on xorg with US language and Budgie.

---

### Post by corradoventu on 2020-11-15
Same problem on Ubuntu Gnome standard. I reported a problem on launchpad, please subscribe: 
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1904322](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1904322)

---

### Post by dino99 on 2020-11-15
Hopes someone will post it on Debian too, as the maintainer is there. (mvo@debian.net)
.

---

### Post by Frogs Hair on 2020-11-15
> **corradoventu said:**
> Same problem on Ubuntu Gnome standard. I reported a problem on launchpad, please subscribe: 
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1904322](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1904322)

Thanks for the image. Both categories are missing in my case.

[[img]http://i.imgur.com/hC27QPom.png[/img]](https://imgur.com/hC27QPo)

---

### Post by dino99 on 2020-11-15
Goto Preferences -> columns & fonts: un/check the desired items to get them displayed inside gui list

---

### Post by corradoventu on 2020-11-15
To have Size and Dowload columns you must go to Settings > Preferences > Colums-and-fonts  and select the colums.

---

### Post by Frogs Hair on 2020-11-15
When download is added there are diamond shaped symbols and size is blank.

---

### Post by corradoventu on 2020-11-15
@FrogsHair: you commented: 'Other users affected.' but not subscribed my bug, why? So my bug remains 'new' but not 'confirmed'

---

### Post by Frogs Hair on 2020-11-15
> **corradoventu said:**
> @FrogsHair: you commented: 'Other users affected.' but not subscribed my bug, why? So my bug remains 'new' but not 'confirmed'

Sorry,I forgot to confirm. Done

---

### Post by P-I H on 2020-11-16
I added me to the bug report

---

### Post by dino99 on 2020-11-16
Should be fixed with that new upgrade:

synaptic (0.90.2) unstable; urgency=medium

  [ Heimen Stoffels ]
  * Updated Dutch translation

  [ rezso ]
  * Update autogen.sh

  [ Michael Vogt ]
  * gtk: fix invalid assignment from SizeToStr to intermediate value
    (Closes: 974790, 974725)

 -- Michael Vogt <mvo@debian.org>  Mon, 16 Nov 2020 09:56:34 +0100

Hopes to get a sync soon :D

---

### Post by dino99 on 2020-11-16
0.90.2 is now into 'proposed' and fix that issue.
Closing this thread.

---

