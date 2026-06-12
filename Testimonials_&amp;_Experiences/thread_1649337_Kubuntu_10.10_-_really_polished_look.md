---
title: "Kubuntu 10.10 - really polished look"
date: 2010-12-20
forum: Testimonials &amp; Experiences
---

### Post by mastablasta on 2010-12-20
What i hated trying it before was the main menu - it just too me too long to search for what i wanted to find. Ok it has a search function but i dont' really like to always type for programms. sometimes i just like to move the mouse arround... I found GNOME Ubuntu menu more intuitive, so i went with it.  But now i read on how to switch the K menu to the classic style. So i just had to give it another try. this time 10.10...
 
I went with USB this time so it's faster. And i must say i am impressed. Using classic menu style i can find everything i need very fast (must be because it looks like Windows :-) ). I played arround with it and tried a few things. This was only live session of course, so many things i couldn't try. such as how wine programmes would perform or flash... so this is just at first glance and what i noticed the most.
 
the plus:
- nice and clean default theme (polished look)
- more space for running programmes (no second bar)
- more settings for screen by default as well as special effects
- interesting browser
- system settings are easier to search through
the minus:
- there seems to be only one theme available
- the default email programme is not so integrated as Evolution. I understand there is a calendar application, but i am not sure how good this integrates with emails or also how good is Evolution in KDE. Anyone knows this?
- notification about closing virtual terminals is realyl a bit silly if you ask me. perhaps it should be made option for those that need it. for most ordinary users i doubt it is necessary. 
 
What forgot to check was the memorry use compared to GNOME. i have 1.3 GB ram and cheapest Celeron i could fine. Graphics card uses opensource drivers, so i am sure plenty of eye candy would be handled by processor. i also couldn't enable certain desktop effects. not really sure why might be the drivers or the fact i was using live session.
 
what puzzles me most still is that both GNOME and KDE lunch quite normally using live session, while the installed GNOME doesn't show any startup dots (plymouth is it?). it only shows a cursor for a while and then switched to login screen. i remember it used to work in 9.10. the funny thing is it all works on on shutdown.

---

### Post by ventrical on 2010-12-20
Thanks mastablasta.

 I had some of the same experiences with kubuntu. It was almost like windows 7 :) but even better.:) The things jumping around ..hehe.. I was laughing so hard. I'll try to set the classic menu the next time.

ps.. I'm not laughing at Kubuntu.. just the way the desktop seems to have a mind of it's own:)

---

### Post by andymorton on 2010-12-20
> **mastablasta said:**
> What i hated trying it before was the main menu - it just too me too long to search for what i wanted to find. Ok it has a search function but i dont' really like to always type for programms. sometimes i just like to move the mouse arround... I found GNOME Ubuntu menu more intuitive, so i went with it.  But now i read on how to switch the K menu to the classic style. So i just had to give it another try. this time 10.10...
 
I went with USB this time so it's faster. And i must say i am impressed. Using classic menu style i can find everything i need very fast (must be because it looks like Windows :-) ). I played arround with it and tried a few things. This was only live session of course, so many things i couldn't try. such as how wine programmes would perform or flash... so this is just at first glance and what i noticed the most.
 
the plus:
- nice and clean default theme (polished look)
- more space for running programmes (no second bar)
- more settings for screen by default as well as special effects
- interesting browser
- system settings are easier to search through
the minus:
- there seems to be only one theme available
- the default email programme is not so integrated as Evolution. I understand there is a calendar application, but i am not sure how good this integrates with emails or also how good is Evolution in KDE. Anyone knows this?
- notification about closing virtual terminals is realyl a bit silly if you ask me. perhaps it should be made option for those that need it. for most ordinary users i doubt it is necessary. 
 
What forgot to check was the memorry use compared to GNOME. i have 1.3 GB ram and cheapest Celeron i could fine. Graphics card uses opensource drivers, so i am sure plenty of eye candy would be handled by processor. i also couldn't enable certain desktop effects. not really sure why might be the drivers or the fact i was using live session.
 
what puzzles me most still is that both GNOME and KDE lunch quite normally using live session, while the installed GNOME doesn't show any startup dots (plymouth is it?). it only shows a cursor for a while and then switched to login screen. i remember it used to work in 9.10. the funny thing is it all works on on shutdown.

Hi

To make the plymouth theme show on start-up enter the following into the terminal:

sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u

andy

---

### Post by mastablasta on 2010-12-21
What will this command do? Does it update kernel? because if so then sound will stop working again :-(

---

### Post by ventrical on 2010-12-21
I think he adressing the 'startup dots' part of your question.

At the opening screen before log-in.

UBUNTU
  .  .  .  .

Is that not what you were referring to?

---

### Post by mastablasta on 2010-12-22
sure.
 
But initframs i checked online it says it will do some kernel update.... and last kernel update overwrote my sound driver (eventhough i have locked packages to 1.0.23). oh well never mind i will just try it. i have all files backed up on another disk &DVD's anyway...

---

