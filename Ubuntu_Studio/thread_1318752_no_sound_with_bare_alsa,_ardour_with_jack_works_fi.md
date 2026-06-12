---
title: "no sound with bare alsa, ardour with jack works fine"
date: 2009-11-07
forum: Ubuntu Studio
---

### Post by tomas vtipil on 2009-11-07
hi,
running ubuntu studio karmic with rt kernel (2.6.31-9-rt), amd64 machine, m-audio delta1010lt soundcard. 
experiencing strange problems with audio. i have no sound via alsa from the "consumer" sound apps (movie player, alsaplayer, vlc, flash videos with firefox...). funny is that the "professional" stuff works - jack apps like ardour, muse or zynaddsubfx work normally, i'm able to run renoise (via jack or just clean alsa - both ok). (traditionally unreliable) audacity gives mixed results - with alsa it works slowly and with crackles, but cannot connect to jack.

any ideas?

thanks, t.

---

### Post by tomas vtipil on 2009-11-09
er, nobody any clue?

---

### Post by VertexPusher on 2009-11-10
Do you have more than one audio interface? Enter
```
aplay -l
```
in a terminal to get a list.

By default, ALSA selects card 0 as the default device for all applications. The problem is that card 0 is not always the same physical device. The card numbers may change between sessions, i.e. sometimes the sound goes where you would not expect it.

You can fix this by selecting the default device by name instead of number. There are tools to do this, e.g. asoundconf.

---

### Post by AutoStatic on 2009-11-10
Did you configure/modify anything on your system? Did you uninstall or disable anything?

---

### Post by tomas vtipil on 2009-11-30
VertexPusher: thanks, but this is probably not the case. i have just delta1010lt (hw0), onboard soundcard is disabled in bios.

AutoStatic: i just uninstalelled jack and compiled jackdmp from source instead to take advantage of multiple cpu cores. it works like charm. the problem is alsa seems to refuse working WITHOUT jack, which is strange because, as far as i understand, jack calls alsa. some apps like renoise can also handle it and work normally with alsa, but most of simplier sound apps like mplayer suck. actually, there are no error messages, crackles, whatever, just silence. i wander if this is some tricky setting in alsamixer - but i think i've tried everything...
tomas

---

### Post by tomas vtipil on 2009-11-30
VertexPusher: ok, i tried it anyway: i disconected all my midi gear and everything that might look like a soundcard, checked if the onboard card is really disabled (it is), installed asoundconf (it was sorta tricky, had to use the jaunty (non-gtk) .bin to make it work), and did

```

asoundconf is-active
asoundconf set-default-card M1010LT

```no results. 

???
t.

---

### Post by wegface on 2009-12-02
Same trouble here on ice1712 soundcard- pulseaudio doesnt play nice with it at all- jack alone does... :-S

---

### Post by RaumTrug on 2009-12-08
you might try to disable pulse (temporarily) to let the apps interface with the pure alsa driver (I do this a lot, because pulse sucks in terms of latency, quality & cpu for most apps):

create a text file "~/.pulse/client.conf" with just "autospawn = 0" as contents (i.e. run "gedit ~/.pulse/client.conf", enter the text and save...)
you might have to restart/relogin the pc, not sure

then enter "pulseaudio -k" in a terminal. the volume control applet in the taskbar should disappear after a few seconds.

now run any alsa app: it will now get direct access to the soundcard alsa driver, and not try to use pulse as intermediate step.

also, mind that no mixing will happen, so you can only run 1 audio app at any time

to restart pulse just enter "pulseaudio -D" in the terminal, and it will reload and the volume control in tray will reappear!

this is very useful for using music progs without jack (milkytracker is the main reason why I do this, it just has crapped, erratic sound with pulse). you can create quicklaunch buttons in the tray that kill/restart pulse with one click!! just keep some alsa mixer in hand to rule the levels, as the tray thing will disappear!

that pulse doesn't work with your card could be fixed with this with just a little hassle: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/52](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/52)

---

### Post by VertexPusher on 2009-12-08
Why not just remove PulseAudio and get rid of all those problems at once?

---

### Post by DerickX on 2009-12-09
It's a pulseaudio bug in ubuntu. It can be fixed for sure, see above. I wouldn't remove pulseaudio.

---

### Post by tomas vtipil on 2009-12-16
thanks so much, this link
[https://bugs.launchpad.net/ubuntu/+s...42/comments/52]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/52")
helped!

i just tried youtube vids and audacity, both working fine now. thank you again!
t.

---

