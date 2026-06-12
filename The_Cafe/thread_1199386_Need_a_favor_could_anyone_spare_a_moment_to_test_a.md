---
title: "Need a favor: could anyone spare a moment to test a new program?"
date: 2009-06-28
forum: The Cafe
---

### Post by nobodysbusiness on 2009-06-28
I've just recently posted a new free-software utility for Ubuntu called "[Caffeine for Linux]("http://pragmattica.wordpress.com/2009/06/27/caffeine-not-just-for-beverages-anymore/")". The blog post contains instructions on installing and running the program, and I've tested it using a 9.04 live CD.

Still, I'm a little worried that the instructions might not work or might be confusing, so I'd feel calmer if someone else gave it a try before I posted the link to reddit or anything. So if you're familiar with Caffeine for Mac OS X, and would like to have something similar for Linux, and you have a little time to kill, would you be willing to try the instructions from the link above and let me know what happens?

Thanks for your help!

---

### Post by Blood//Stain//Child on 2009-06-28
Why don't you just disable sleep mode?

---

### Post by MaxIBoy on 2009-06-28
Well, it runs without any errors, and the icon changes when I click on it. I'll post back later to tell you if it actually works.

---

### Post by swoll1980 on 2009-06-28
> **Blood//Stain//Child said:**
> Why don't you just disable sleep mode?

Because he likes sleep mode, and it would be really annoying to keep disabling it every time he wants to watch a movie. :roll: This app solves a problem that almost all users have. I will follow this, and install it when it's ready for the masses.

---

### Post by FuturePilot on 2009-06-28
Wow, awesome. Just the other day I was wishing there was something that would do exactly this as there are certain times I don't want my computer to suspend. I will definitely try this out.

---

### Post by Bodsda on 2009-06-29
Hi, I love the idea, but I have an error.

I use fluxbox WM, and when I click the cup, this pops up

"Error: couldn't find bus to allow inhibiting of the screen saver.

Please visit the web-site listed in the 'About' dialog of this application and check for a newer version of the software."

Regards,

Bodsda

---

### Post by doorknob60 on 2009-06-29
> **Bodsda said:**
> Hi, I love the idea, but I have an error.

I use fluxbox WM, and when I click the cup, this pops up

"Error: couldn't find bus to allow inhibiting of the screen saver.

Please visit the web-site listed in the 'About' dialog of this application and check for a newer version of the software."

Regards,

Bodsda

I get that too using Openbox. My X Server just defaults to go to blank screen every 10 (I think it's 10) minutes, nothing else set to control it like xscreensaver or anything. Sounds pretty useful though, I'll try to remember and keep an eye on this.

---

### Post by magmon on 2009-06-29
Seems to work. A quick note to people using 8.10 or lower, when following the guide, go to sessions instead of startup applications.

---

### Post by sisco311 on 2009-06-29
> **doorknob60 said:**
> I get that too using Openbox. My X Server just defaults to go to blank screen every 10 (I think it's 10) minutes, nothing else set to control it like xscreensaver or anything. Sounds pretty useful though, I'll try to remember and keep an eye on this.

the default blank time is 10 minutes([man 5 xorg.conf]("http://linux.die.net/man/5/xorg.conf")) when [DPMS]("http://en.wikipedia.org/wiki/VESA_Display_Power_Management_Signaling") (VESA Display Power Management Signaling) is enabled.

you can control the DPMS settings with the xset command:
```

#!/bin/bash

ICON_ON="/path/to/icon/on.png"
ICON_OFF="/path/to/icon/off.png"


if [ "$(xset q | grep "DPMS is" | awk '{print $3}')" == "Disabled" ]; then
  xset +dpms
  notify-send -i $ICON_ON "DPMS ON"
else
  xset -dpms
  notify-send -i $ICON_OFF "DPMS OFF"
fi

```

---

### Post by Nevon on 2009-06-29
I posted a comment on the blog post with two new icons. Those two default ones are way pixelated. 

Here you can see them in action, so to speak.

[img]http://i43.tinypic.com/25tg9s1.png[/img]

[img]http://i40.tinypic.com/2czspvq.png[/img]

---

### Post by Islington on 2009-06-29
this is very much needed and wanted. trying it out now. It really sucks when playing a game and the monitor tries to nap.

edit: reddited: [http://www.reddit.com/r/linux/comments/8wm7q/caffeine_for_linux_stop_sleep_mode_interupting/](http://www.reddit.com/r/linux/comments/8wm7q/caffeine_for_linux_stop_sleep_mode_interupting/)

---

### Post by nobodysbusiness on 2009-06-29
@Bodsda and doorknob60: I think that the program works reasonably well under Gnome, but I know for sure that it's broken under KDE and I didn't test fluxbox or openbox. Still, if people are using other window-managers, then I have no problem with installing them and figuring out how to make Caffeine work properly. In fact, it might be nice to get some more exposure to other window managers. I've been using Gnome for so long...

@Nevon: Thanks again for the icons! I'll get those incorporated ASAP.

Everyone else: Thanks for your support and encouragement. It really helps my motivation to know that there are people out there rooting for me.

---

### Post by RiceMonster on 2009-06-29
I like the idea of this. I've got Fedora 11 running GNOME on my laptop, so I'll try it out when I get home tonight. I've got Xfce on Arch Linux on my desktop, but I don't have it set to sleep automatically, so I won't be able to test it there, unfortunatly.

---

### Post by argie on 2009-06-29
So far the Power Manager Inhibit Applet has worked fine for me. Have you tried using that?

---

### Post by nobodysbusiness on 2009-06-29
@Islington: Thanks for posting this to Reddit! It's up to 3 points and is #6 on the linux.reddit.com list.

@argie: Yes, I've tried the inhibit applet, and it didn't quite do the trick. Here's the experiment that I attempted:
[LIST]
[*]set the screensaver to activate after 1 minute
[*]set sleep mode to activate after 2 minutes
[*]wait a while
[/LIST]
In my experiment, after one minute, the screensaver did activate. I may have been doing something wrong though. Does this happen for anyone else?

---

### Post by nobodysbusiness on 2009-06-29
@RiceMonster: So you use Xfce on your desktop, huh? That's another WM that I haven't tested, so I would imagine that it probably doesn't work. I'll add it to the list of WM's to support, though. Other posters have already mentioned Fluxbox and OpenBox.

---

### Post by Dawei87 on 2009-06-29
this is great! the inhibit always worked well enough for me in gnome, but for non-gnome users this is great! i do use gnome, but i have been trying to get rid of the gnome panel and this is the one applet i couldnt live without

EDIT: well i just tested it, but it doesnt seem to work for me. my screensaver still works and it still goes into sleep. i followed the instructions and have the icon in the notification area, is there something else i can do or did i do something wrong?

---

### Post by nobodysbusiness on 2009-06-30
@Dawei87: Let's see, if it's not working, there could be any number of causes. Are you still using Ubuntu 8.10? You mentioned that you were using Gnome, right? I tested Caffeine with Ubuntu 9.04 and it worked, but there certainly could be problems with an earlier version of Ubuntu...

I have an Ubuntu 8.04 box at home; perhaps I should upgrade that to 8.10 and see what happens. Another idea: maybe you could quit the applet, open a terminal and run "opt/caffeine/caffeine.py" and then see what kind of messages are printed to the terminal when you click the icon to fill it with coffee. Do you see any errors?

---

### Post by Dawei87 on 2009-06-30
> **nobodysbusiness said:**
> @Dawei87: Let's see, if it's not working, there could be any number of causes. Are you still using Ubuntu 8.10? You mentioned that you were using Gnome, right? I tested Caffeine with Ubuntu 9.04 and it worked, but there certainly could be problems with an earlier version of Ubuntu...

I have an Ubuntu 8.04 box at home; perhaps I should upgrade that to 8.10 and see what happens. Another idea: maybe you could quit the applet, open a terminal and run "opt/caffeine/caffeine.py" and then see what kind of messages are printed to the terminal when you click the icon to fill it with coffee. Do you see any errors?

yea, i should have mentioned im on 8.10. ill try and run it through the terminal and ill post back what i find. im not at my linux box now so it will be a minute...

EDIT: ok. i did what you said and it appears to run, this is what the terminal says when i click the applet:

david ~  $  .caffeine/caffeine-0.1/caffeine.py
Caffiene is now preventing powersaving modes and screensaver activation
Caffiene is now dormant; powersaving is re-enabled
Caffiene is now preventing powersaving modes and screensaver activation
Caffiene is now dormant; powersaving is re-enabled

but it still goes into sleep when it is active. im really looking forward to using this, but maybe i just have to wait to upgrade.

---

