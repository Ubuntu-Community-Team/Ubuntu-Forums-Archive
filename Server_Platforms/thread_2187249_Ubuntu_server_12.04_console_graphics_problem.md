---
title: "Ubuntu server 12.04 console graphics problem"
date: 2013-11-11
forum: Server Platforms
---

### Post by raimuucka on 2013-11-11
Hi, 
I have tried installing few times this server from CD, but it always ends the same. When console starts autocratically after installation, you cant understand anything. If you install GUI, then all seams to be OK. when GUI is on. but I do not want it to run with gui. when entering in recovery mode, then text is readable too.
I have a video of how it works:
[http://youtu.be/HuixvFKB3LY](http://youtu.be/HuixvFKB3LY)

[COLOR=#333333]I can connect by SSH to the server and it is OK, but not always comfortable.
Can anyone help me to fix this?[/COLOR]

---

### Post by houstonbofh on 2013-11-11
Your system is wrongly detecting your monitor, and trying to go into an unsupported hires mode.

You can probably fix this by following the instructions here.

[https://wiki.ubuntu.com/FrameBuffer#How_to_disable_the_framebuffer](https://wiki.ubuntu.com/FrameBuffer#How_to_disable_the_framebuffer)

---

### Post by raimuucka on 2013-11-11
> **houstonbofh said:**
> Your system is wrongly detecting your monitor, and trying to go into an unsupported hires mode.

You can probably fix this by following the instructions here.

[https://wiki.ubuntu.com/FrameBuffer#How_to_disable_the_framebuffer](https://wiki.ubuntu.com/FrameBuffer#How_to_disable_the_framebuffer)

Ok, thnx, I'll try it when I'll be at work.  I hope it will work :)

You say unsupported high resolution. Unsupported by monitor or by card? I tested it with really good and new display and it shows the same. So it is not supported by GPU?

---

### Post by raimuucka on 2013-11-12
Yes, this realy helped. I tryed "How to disable the framebuffer" just I didn't write [COLOR=#333333][FONT=Ubuntu Beta]" vga=normal nomodeset" but [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]" vga=791" And it ran like it has to. 
Then I have edited [/FONT][/COLOR]*/boot/grub/grub.cfg.*[COLOR=#333333][FONT=Ubuntu Beta] file ading the same in a row like  described at "[/FONT][/COLOR]Setting different framebuffer resolutions in old versions of GRUB".
Just in my case at the begining of the line there was not "kernel" but "linux". I do not remember in what line, but it was few pages down.

So thank you for your help.

---

### Post by houstonbofh on 2013-11-12
Glad I could help.

---

