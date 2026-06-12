---
title: "MuseScore (Playback help, anyone?)"
date: 2009-08-05
forum: Ubuntu Studio
---

### Post by Wataru8675 on 2009-08-05
This is the best-fitting forum I could find for this thread, sorry if it's a little out of place...

Is anyone good with the program MuseScore?  I installed it the other day and it works fine except for that I can't get my scores to play.  The buttons at the top of the screen (play, rewind, etc.) are there, but when I click them, nothing happens.  And F11 (the shortcut for the Play Panel) doesn't do anything; neither does going to Display > Play Panel.  I've tried downloading a new SoundFont, but to no avail.

I've already tried the forums at musescore.com, but I couldn't get an answer there either.

---

### Post by dawiba on 2009-08-05
I use Musescore via Jack in Ubuntustudio.

Open and start Jack Control.

Open Musescore and select Edit -> Preferences and then select the General tab. I've attached a screenshot of mine for you to try the settings.

Then go to the I/O tab.

I've attached a screenshot of my settings for you to try these as well.

If you're using Ubuntustudio, you shouldn't have to download additional soundfonts (I didn't).

Once you've applied the settings, try playing your scores or else the Mussorgsky file that came with Musescore.

Hope this helps.

---

### Post by Wataru8675 on 2009-08-06
Under my I/O tab, I can't select anything under JACK Audio Server; both dropdown boxes are greyed out, even though I've checked the box next to it.  My JACK program is open and I hit Start.  Also, my ALSA has values for the Sample Rate and Period (48,000 and 1,024 respectively).

In another tutorial on this, it said to uncheck "Realtime" in the setup menu of JACK, so unless that did something goofy, all of the rest of my JACK settings are default.  Haven't changed anything 'cause I don't quite get what it's supposed to be used for...

---

### Post by dawiba on 2009-08-06
Under your I/O tab, what *do* you have selected? Can you attach a screenshot?

Are you trying to use an external soundcard or your computers speakers?

On it's own, whether or not you use realtime shouldn't stop you from playing back your score.

---

### Post by Wataru8675 on 2009-08-06
Yeah, I'll upload a screenshot right now.  I'm just trying to play it out of my plain ol' laptop speakers.  I really didn't think trying to get it to play would be this big of a hassle. @_@

Everything looks just like how you had yours...

EDIT:  Note that my soundfont is one I downloaded thinking that the problem was related to that.  Should I set it back to default?  I can't fathom it'd matter, but...

RE-EDIT:  I noticed that my ALSA box wasn't checked, so I fixed that and rebooted MuseScore, but still no luck...

---

### Post by dawiba on 2009-08-07
In your Musescore I/O, you need to specify Jack outputs for 'Left Port' and Right Port'. I've attached a screenshot.

I normally run Musecscore while running Jack, using Realtime, going through a Firewire interface. Just to be sure, I changed to alsa in Jack (in order to use the onboard sound) and disabled realtime to try to match the way you are trying to run Musescore. I was able to play through my laptop speakers this way. I've attached a screenshot of the Jack settings for this. Hopefully this will work for you.

Your soundfont should be fine so long as Musescore is looking in the right place. If in doubt, resetting to defaults shouldn't hurt.

Remember, most settings you change in Musescore will mean you have to close the program and restart it in order for the changes to take effect.

---

### Post by Wataru8675 on 2009-08-07
That's the thing...I CAN'T specify left/right ports.  They're both greyed out.  Nothing drops down in the box when I click on it and I can't type anything in.

My JACK settings are identical to yours.

---

### Post by dawiba on 2009-08-07
I tried again using the same settings myself and everything worked fine.

Just to be sure, are you starting jack before you launch Musescore?

Jack needs to be started before launching Musescore using these settings in the app preferences that I attached to my posts. Without Jack running, my Musescore outputs are greyed out, but with Jack running, I get to use system playback 1 and 2.

I've attached a screenshot of Jack started to show you what I mean.

---

### Post by Wataru8675 on 2009-08-08
Well, good news is I was able to specify the left and right ports in the MuseScore settings for JACK.

The bad news is, now that I've got it all set up...I CAN'T OPEN A [beep]ING SCORE TO [beep]ING TEST IT THE [beep] OUT!! [beeeeep]!!!!!!!!!!  Whenever I go to Open or hit Ctrl+O, the box comes up, but there's nothing in it...this is SOOOOOO frustrating. T______T  I'll post something of substance if I finally get this kink worked out......

---

### Post by Wataru8675 on 2009-08-08
I just put a bunch of random notes into a new score and the sound works perfectly now.  Thanks for your help!  Now I just need to figure out how to open my OLD [beep]ING SCORES!!!! DDDDD<

---

### Post by dawiba on 2009-08-08
Glad to have been able to help.

Good luck with your scores!

---

