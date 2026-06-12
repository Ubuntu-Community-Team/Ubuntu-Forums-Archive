---
title: "How can I see shutdown text?"
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by drumour on 2012-03-24
I have removed "quiet" and "splash" from kernel boot line but I still get a plain purple screen when I boot and shutdown. I would like to see the system messages, particularily at shutdown.

---

### Post by lucazade on 2012-03-24
> **drumour said:**
> I have removed "quiet" and "splash" from kernel boot line but I still get a plain purple screen when I boot and shutdown. I would like to see the system messages, particularily at shutdown.

try to press ESC when you see the splashscreen

---

### Post by dino99 on 2012-03-24
have the same issue since a few days now, total black screen with both cases (quiet splash" removed too)

---

### Post by zika on 2012-03-24
> **drumour said:**
> I have removed "quiet" and "splash" from kernel boot line but I still get a plain purple screen when I boot and shutdown. I would like to see the system messages, particularily at shutdown.
Turn plymouth off?
I would try with plymouth-splash first. I do turn all of plymouth off often..
In /etc/init for all plymouth* create corresponding .override files with one line: manual.
```
:/etc/init$ echo 'manual' | sudo tee /etc/init/plymouth.override
:/etc/init$ echo 'manual' | sudo tee /etc/init/plymouth-stop.override
:/etc/init$ echo 'manual' | sudo tee /etc/init/plymouth-splash.override 
:/etc/init$ echo 'manual' | sudo tee /etc/init/plymouth-upstart-bridge.conf.override
:/etc/init$ echo 'manual' | sudo tee /etc/init/plymouth-log.conf.override

```
To undo simply remove .override files that were made...

---

### Post by dino99 on 2012-03-24
> **lucazade said:**
> try to press ESC when you see the splashscreen

damn, have forgotten that, will try next time :) thanks

---

### Post by lucazade on 2012-03-24
> **dino99 said:**
> have the same issue since a few days now, total black screen with both cases (quiet splash" removed too)

then remove also the gfxpayload entry in grub and vt.handoff from kernel params.

If not enough move the plymouth init script (/etc/init/plymouth.conf) avoiding it to start.

---

### Post by drumour on 2012-03-24
When a disk is being checked for errors I can switch between text and splash by pressing the up arrow, but before and after disk checking its a plain purple screen and Esc or up arrow has no effect.

Thanks for plymouth info, from posts elsewhere there seems to be a lot of dependencies on Plymouth so I am loathe to muck about with it, will try temporarily renaming /etc/init/plymouth.conf and give it a shot...

---

### Post by drumour on 2012-03-24
Please Do Not Rename /etc/init/plymouth.conf. When I did I still got a plain purple screen and then text but it stopped after some init scripts and I had to Ctrl-Alt-Del to get the system to resume booting. 

However I am seeing shutdown text now. I think though this was more a result of stripping quit, splash and vt.handoff from kernel params.

Thanks

---

### Post by lucazade on 2012-03-24
> **drumour said:**
> Please Do Not Rename /etc/init/plymouth.conf.

you probably have done  something wrong.. moving that script to somewhere else doesn't break anything.
please mark thread as solved.

---

### Post by zika on 2012-03-24
> **drumour said:**
> Please Do Not Rename /etc/init/plymouth.conf. When I did I still got a plain purple screen and then text but it stopped after some init scripts and I had to Ctrl-Alt-Del to get the system to resume booting. 

However I am seeing shutdown text now. I think though this was more a result of stripping quit, splash and vt.handoff from kernel params.

Thanks
Did You try what I've suggested to You in [http://ubuntuforums.org/showpost.php?p=11789876&postcount=4](http://ubuntuforums.org/showpost.php?p=11789876&postcount=4) ? ... It works on dozen of machines I (kind of) take care of... ;)
That is a documented and &#8222;proper&#8220; way of preventing services from starting automagically...

Update: I forgot: try un-comment-ing ```
GRUB_TERMINAL=console
``` in */etc/default/grub* followed with ```
sudo update-grub
```...

---

