---
title: "Audacity-Recording and Playback Issues"
date: 2008-04-22
forum: Ubuntu Studio
---

### Post by indiekid97 on 2008-04-22
Hello and thanks in advance for anyone who responds :]

I've used audacity on windows for as long as i can remember for some basic songwriting/recording, and had great success.
however, on ubuntu its another story...
I'm not a complete newbie to linux, ive run various distros for over 2 years now but ive seem to come across a head scratcher
:confused:

After opening Audacity, it will record from my mic input only once and then upon playback attempt it reports
```
Error while opening sound device. Please check the output device settings and the project sample rate
```
This occurs during simple playback also, say opening an OGG file. 
Also, after the initial record, the error will be displayed when Audacity is asked to record again

any help?

---

### Post by indiekid97 on 2008-04-23
bump

---

### Post by lolwhites on 2008-04-23
Am having similar issue but in my case it won't record at all. When I try to record, I get the same error message, unless I select "ALSA: HDA Intel: STAC92xx Analog (hw:0,0) as the input device, in which case I don't get the message, but it still doesn't record off the mike.
I had hoped it's sort itself out when I upgraded to Hardy, but it hasn't made any difference.

---

### Post by thirdspace on 2008-04-23
audacity under ubuntu has been kind of unreliable for me too. One of its problems is it gets tangled up in multi-thread sound device access deadlocks. For recording music, you might find that learning to use jack (qjackctl) and ardour is worth the time it will take. Or, using jack to connect audacity to the sound device might work better than the "direct" route and isn't much harder. Jack usually at least gives a real error report when something goes wrong, instead of a generic "something went wrong".

---

### Post by BenniP on 2008-04-25
For me, Audacity works on the condition that no other program (ie music player) is opened at startup.

However, I can first start Audacity, then the music player when I need it, close the music player and Audacity output works again.

---

### Post by lolwhites on 2008-05-11
When I select ALSA: HDA Intel: STAC92xx Digital (hw:0,1) as my output device, it appears to play but no sound comes our of the speakers (yes, I have checked the volume controls). Therwise I get the same error message as indiekid97 when I try to play back.

Ardour won't open mp3 or Ogg files to edit, which I can do in Audacity in Windows.

---

### Post by Matokias on 2008-05-12
Hi all!.

I've had the same inconvenience while using Audacity in my laptop, with a "ALSA: HDA NVIDIA Conexant Digital" Device... this setting would not work either for recording or for playback.

I simply set the Device to DEFAULT... and that did the trick!!!...

It's working perfectly fine, for editing, multiple tracks and ev'thing.


Hope this helps!.

Cheers!

---

### Post by lolwhites on 2008-05-12
Doesn't work for me I'm afraid. However, I tried some other audio editors and found similar issues: Jokosher crashed when I tried to play an Ogg I'd imported, and when I started Rosegarden I got this:

> Rosegarden could not connect to the JACK audio server. This probably means the JACK server is not running.

n.b. I got this even after starting JACK Control beforehand.

Does this shed any light on things?

Edit: AHA! I got it to work - here's what I did:

1) I installed JACK Control from Add/Remove.
2) I started Jack Control, clicked in Setup.
3) On the "Misc" tab, I checked *Start JACK audio server on application startup*, clicked OK
4) In Audacity, I selected *JACK Audio Connection Kit: system* as the output device
Now it plays back! Woohoo!

---

