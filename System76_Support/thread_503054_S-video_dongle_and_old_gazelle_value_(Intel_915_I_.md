---
title: "S-video dongle and old gazelle value (Intel 915 I believe)"
date: 2007-07-17
forum: System76 Support
---

### Post by newlinux on 2007-07-17
I have a vga->s-video dongle that I would like to use with this laptop. Can anyone give me some pointers on how to get it to work or if it can work in linux (are there some standard changes to xorg.conf that one makes?)

Thanks.

---

### Post by thomasaaron on 2007-07-17
I'm not sure, but I would guess that you could just plug and play it.
Then you could just turn your VGA port on and off via the appropriate FN-F* combination.

---

### Post by newlinux on 2007-07-17
Thank you for your response. I tried that and did not get any output. Tried restarting X as well. I figured there must be more I am supposed to do.

---

### Post by newlinux on 2007-07-17
I guess an important question for me before I try more things is does this model support TV-out. I know not all do... I was pretty sure this one does though. Any help is appreciated on how to get this to work. If it is supposed to just work, maybe something is wrong with my cable.

---

### Post by thomasaaron on 2007-07-18
Yes, The Gazelle Value does support TV out.
Incidentally, there is an s-video port on the Gazelle. It is right beside the VGA out.

Back to the dongle.
Try hooking everything up and rebooting the computer. When the Intel splash screen comes up, press the Fn-F* key until your LCD goes blank. Then, as the computer boots up, you should see your output on the TV.

If this does not work, there may be refresh-rate problems in your xorg.conf file.
Try commenting those lines out and see what happens.
(Save a backup of xorg.conf first.)

---

