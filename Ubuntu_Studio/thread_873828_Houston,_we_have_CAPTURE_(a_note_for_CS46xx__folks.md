---
title: "Houston, we have CAPTURE (a note for CS46xx  folks)"
date: 2008-07-29
forum: Ubuntu Studio
---

### Post by Abstract Zzzxyz on 2008-07-29
Mission complete, i CAN record.

Okay, I thought my soundcard was a Cirrus Login CS46-something, and the driver is CS46xx - fine. I tried everything, rt-kernel, you name it. Then, after sniffing around s'more (and by s'more, i mean obsessively), I found out my chipset 4297, is also called AC97. 

This morning, on an Ubuntu Sound Troubleshooting page I've read a hundred times ([https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)), I saw a little thing toward the bottom, listed under 'Misc Tips and Tricks' which said:
webbca01 figured out how to get AC'97 work with the help of the second last post here and this post. Basically, if you have an intel8x0 module, you can get AC'97 working by sudo nano /etc/modprobe.d/alsa-base and adding this as the last line: "options snd-intel8x0 ac97_quirk=3"

That did the trick. I've only tried to record in Traverso (w/alsa - not Jack), so I'm guessing both Jack and Ardour will be all right too. Tada! 

Whew.

---

