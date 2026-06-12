---
title: "Alternative to MythTV"
date: 2006-09-14
forum: The Cafe
---

### Post by Beamerboy on 2006-09-14
I was wondering if there are any alternatives to MythTV, it seems to be way above what I needfrom a PVR.  All I basically want to do is record live tv from my tuner. What I don't need:

1.  I don't need my computer to change the channel or schedule things for recording, I have a seperate Satellite box similar to the US TIVO (called Sky+ in the UK) for that.

2.  I don't need to pause/rewind my shows.

3.  I don't need it to make my coffee.

There are one or two shows I always watch (like New Yankee Workshop) and all I want to do is record them as I watch them so I can refer back to them at a later time if needed.

I have my card working under TVTime (but Ican't see any recording features in this application) so I just need something that will capture the current stream to file.

Any help and advice appreciated, I am gonna see if VLC will do what I need and will update the thread accordingly (if it does).

Beamerboy

---

### Post by Jussi Kukkonen on 2006-09-14
I guess you could just use xine or mplayer (source *dvb://* if your tuner is a dvb tuner) and save the output to file... A really low-tech solution would be using something like dvbstream.

---

### Post by Sarisar on 2006-09-14
OK possibly a dumb question, but myth TV is basically sky+, so if you have a sky+ box you don't need it.  Both are PVRs.

(Disclaimer:  I have cable not sky!)

---

### Post by Beamerboy on 2006-09-14
> **Sarisar said:**
> OK possibly a dumb question, but myth TV is basically sky+, so if you have a sky+ box you don't need it.  Both are PVRs.

(Disclaimer:  I have cable not sky!)

Actually there are a lot of differences.  Firstly Sky+ has 2 inputs from the dish allowing you to watch one channel whilst recording another, MythTV doesn't (at least not for satelite TV, you can enable multi channel if you have multiple cards and are using terrestrial or dvb).  Secondly my Sky+ box is in the lounge, my desktop is in my office in the basement.  I have sky multiroom in the basement allowing me to watch something other than what is being watched in the lounged, I wanted Sky+ in the basement as well but we also have Sky multiroom in the bedroom and the dishes that Sky issued up until very very recently only had 4 outputs, to have Sky+ in the basement I would need an 8 output dish (which are starting to become the norm but would cost me a lot of money to change our existing dish.)

Furthermore, moving the recordings from the Sky+ box to my pc is a royal pain in the ***.  By having a PVR on the sky box in the office, I can record the programs I like to keep for future reference.  I watch a lot of Home Improvement and Carpentry shows, so they are a very handy reference resource to keep hold for my own projects in the future.

---

### Post by mtron on 2006-09-14
some suggestions:

*gdvb: a mplayer java - gtk gui that extends mplayer with a dvb channel list, ect.

*kaffeine 0.8.2 (not in repos) comes with full dvb support (gui similar to progdvb from the windows world), and is able to handle plugins ;)

*minimal vdr

*kaxtv

check it out

cheers mtron

---

