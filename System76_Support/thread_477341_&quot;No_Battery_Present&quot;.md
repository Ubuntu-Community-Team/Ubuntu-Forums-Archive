---
title: "&quot;No Battery Present&quot;"
date: 2007-06-18
forum: System76 Support
---

### Post by IgnacioMiller on 2007-06-18
Hi all,

I was testing out hibernate last night, just to see what would happen. When it resumed the wireless connection was gone and whatnot. I decided that I would save that project for another time and I turned off the laptop and went to bed. This morning I turned it on and none of my 'on battery' conditions were in effect (screen brightness) despite the fact that it was on a battery!

I tried adding the battery manager from gnome (add to panel>Battery monitor) and that told me that there was no battery present, despite the fact that it was not plugged into an AC source at all. I searched the forums and saw that restarting a few times may help. I shut the laptop down, plugged it in, turned it back on, shut it down, unplugged it, and turned it back on again. This time the screen was dimmed as I specified but it still showed "No Battery Present"!

I also tried going into the BIOS to recalibrate the battery but all I got was a choice of boot devices.

Any help would be greatly appreciates!
Dan

---

### Post by thomasaaron on 2007-06-18
What kind of computer do you have?
What Desktop environment are you running?

Does this bug report apply to you?
[https://bugs.launchpad.net/system76/+bug/114932](https://bugs.launchpad.net/system76/+bug/114932)

---

### Post by IgnacioMiller on 2007-06-18
Gazelle Value, the newest version.

I am running the Gnome Desktop Environment.

It does in some ways, except if I am not mistaken his Battery Manager works fine if he restarts and does not suspend/hibernate. Mine refuses to see the battery at all.

Thanks,
Dan

---

### Post by thomasaaron on 2007-06-18
Have you tried turning off your computer, removing the A/C adapter and then removing the battery for a while. Then re-connecting the battery and rebooting?

Also, could you go to System > Administration > System 76 Driver and tell me what model number it reports?

Best,
Tom

---

### Post by IgnacioMiller on 2007-06-18
It is GAzelle Value Model 4 I believe, and I am trying the method you suggested now.

Thanks,
Dan

---

### Post by IgnacioMiller on 2007-06-18
Thanks Tom! Everything works like a charm!

Dan

---

