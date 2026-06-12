---
title: "XenServer 5.6 FP1 supports Ubuntu!!!  but Desktop not working..."
date: 2011-01-31
forum: Virtualisation
---

### Post by BradenWright on 2011-01-31
So XenServer 5.6 FP1 supports (experimentally) Ubuntu 10.04 (32 & 64 bit)... the cli works great (you can install XenTools, etc).

However I can't get ubuntu-desktop working....  I tried the startx command and I get the following error:

(EE) open /dev/fb0: No such file or directory
(EE) No devices detected.

Fatal server error:
no screens found

I have tried installing framebuffer and I have tried creating an xorg.conf file, seems I don't have a screen (device).  

Any ideas or places to start???

---

### Post by patrick196901 on 2011-05-17
I got the same problem as yours. I have just finished to install Ubuntu 10.10 Server and Ubuntu 10.04 Desktop and for both of them same error message.

:confused:

What to do in order to solve it? Have you already solved your issue?

Regards

Patrick196901

---

### Post by debushau on 2011-05-26
Also looking for a solution for this.

Tried fooled around with a xorg.conf but no luck (does get rid of the fb0 error though once xorg.conf is created). I note that I can vnc into the VM by setting up vncserver on the VM but it only shows a graphical representation of the text console. The "startx" command indicates "no screen found" as noted above. The result is odd since installing Ubuntu (desktop) in HVM mode allows the gui to used (HVM mode is very slow).  The result is the same using 5.6 SP2 and FP1.

---

### Post by coccu on 2011-05-26
Same here :icon_frown:
I have to switch back to HVM mode to get a GUI.   The problem in HVM is that I can't install xen-client on the VM. I guess that's why it was slower!!!!

---

### Post by debushau on 2011-05-27
Xen tools just doesn't install right in HVM mode.

I tried out ESXi and put Ubuntu 10.04 desktop on it. Works just fine as gui and is fairly snappy with VM tools installed. It'll work for my purposes but XenServer was easier to figure out and use. I guess that's one of the reasons why the Ubuntu/Xen template is labelled "experimental".

---

