---
title: "Nouveau driver compiz tearing"
date: 2012-04-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by open.source on 2012-04-17
Hi. I'm happily using 12.04 fully updated, there is one problem though. On the nouveau driver there is tearing in compiz unity despite sync to vblank being enabled. I heard there is some option that you have to add to xorg.conf to make nouveau support sync to vblank but I don't have an xorg.conf file.

The option I found is:
[FONT=monospace]
[/FONT]Option "GLXVBlank" "true"

Can someone please help me.

---

### Post by t1497f35 on 2012-04-17
I don't know, but one should also specify the videocard one's using since Nouveau behaves very differently with different cards.

---

### Post by mc4man on 2012-04-17
I don't use nouveau (nvidia) but there was some work done via this bug

Don't obviously know where it stands after 'fix released' as far as any settings or xorg changes needed other than after a new install there is tearing with nouveau without anything additional done

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/880707](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/880707)

So you **will** want to read thru to get a sense

An xorg edit was mentioned as was enabling an option in  ccsm > workarounds, maybe not together

xorg for nouveau (nvidia card

>  * nouveau: If you are using the "nouveau" driver for NVIDIA chips you will
    need to enable sync-to-vblank support in the driver options because
    nouveau has it disabled by default. You can do this by editing
    /etc/X11/xorg.conf and adding:
      ```
 
Section "Device"
  Identifier "My Graphics"
  Option "GLXVBlank" "on"
EndSection
```
    Then log out and in again for it to take effect.



---

### Post by open.source on 2012-04-17
Thank You for your help. I would enable the xorg option but I don't have an xorg.conf file. It would be great if someone could walk me through creating an xorg.conf as I am unsure of how to proceed.

---

