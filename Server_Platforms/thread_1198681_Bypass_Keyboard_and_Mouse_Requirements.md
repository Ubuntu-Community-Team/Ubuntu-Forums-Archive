---
title: "Bypass Keyboard and Mouse Requirements"
date: 2009-06-27
forum: Server Platforms
---

### Post by SoulMazer on 2009-06-27
So, I have a dedicated 9.04 server box that hosts my website. I usually just SSH to it from my personal desktop computer. So, when I restart my server, it tells me that I need a keyboard and a mouse. I think it's a big pain to go in my closet and find a keyboard and mouse to plug in for the twenty seconds while it boots, only to unplug them right after.

Is there any possible way to disable the necessity of a keyboard and a mouse?

Thanks in advance.

---

### Post by philcamlin on 2009-06-27
you need it for a server to type...

they are cheap these days  so go get a cheapie and keep it there :) unless you edit a config file that bypasses it but i have no idea

edit: why do you think its a pain its only one if you reboot it every 5 min :D  servers stay on fordays

---

### Post by SoulMazer on 2009-06-27
> you need it for a server to type...
Well, I would prefer to just SSH to my server. I would rather not have two mice, two keyboards, and two monitors on my desk if you know what I mean.

And so is there any way I could edit a config file to change this?

---

### Post by philcamlin on 2009-06-27
umm why dont you plug it in for 30 seconds and then not turn off your pc for like a month?

i cant find any way to disable they keyboard input

---

### Post by bigbearomaha on 2009-06-27
That's called running a server 'headless'.

You can usually open the bios at boot and set it to not look for keyboard or other i/o starting next boot.

Big Bear

---

### Post by TwiceOver on 2009-06-27
Look in your bios settings for "Halt On"  it is probably set to "All Errors".  I usually change this to "All but keyboard"

All of my ubuntu servers are headless, keyboardless and mouseless

---

### Post by SoulMazer on 2009-06-27
Ok thanks guys. Exactly what I wanted. Will try it right now.

EDIT: Found the setting in my BIOS. Problem solved. Thanks everybody.

---

### Post by cariboo on 2009-06-27
Just for anyone else, I usually set the bios to not stop on all errors.

---

