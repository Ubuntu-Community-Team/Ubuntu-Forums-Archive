---
title: "No HDMI Audio Galago UltrPro"
date: 2013-10-08
forum: System76 Support
---

### Post by 4CP8X4x on 2013-10-08
I have no audio through HDMI and no HDMI shows up in sound outputs.

---

### Post by isantop on 2013-10-08
Try restarting your computer and see if that makes it show up.

---

### Post by 4CP8X4x on 2013-10-08
So I just restarted after the last update and now my fans are erratic and my keyboard isnt registering most of the keys at all.....? Im on 13.10

---

### Post by 4CP8X4x on 2013-10-08
So I just booted the previous kernel and the fans are working right, but the keyboard is still wonky, Im using an external now.

---

### Post by 4CP8X4x on 2013-10-08
Please help, this was really going very good - best computer Ive ever had - I dont understand whats going on. Some keys work fine, others dont work at all, and some register as other keys? Help would be VERY appreciated.

---

### Post by 4CP8X4x on 2013-10-08
So never mind I guess, all of a sudden its working fine, thanks anyway. 

EDIT: Still have the original problem of no HDMI audio though.

---

### Post by raphael-estrada on 2013-10-09
When HDMI shows up in "sound settings" (which unfortunately doesn't seem to be the case for you), I found you sometimes have to select the laptop audio once then re-select HDMI for it to work. Sometimes after suspending it seems to confuse the output every now and then.

---

### Post by isantop on 2013-10-09
Give it one more reboot, and make sure that the HDMI is connected throughout the reboot. It should detect the HDMI audio and list it in the output list.

---

### Post by 4CP8X4x on 2013-10-09
It detected it and is displayed in sound output but there is still no actual audio coming through despite it being selected.

---

### Post by isantop on 2013-10-09
Can you take a screenshot of the output window? This sounds a bit like a problem on the receiver's end.

---

### Post by raphael-estrada on 2013-10-10
> **4CP8X4x said:**
> It detected it and is displayed in sound output but there is still no actual audio coming through despite it being selected.

Try de-selecting and then re-selecting HDMI in the sound settings window. Sometimes I have to wiggle around the volume level for it to pick up. For some reason Ubuntu occasionally confuses the audio devices from that menu from what I can tell.

---

### Post by raphael-estrada on 2013-10-19
ok i'm having this problem too. galago with ubuntu 13.10.

after changing the optio  of my hdmi from stereo to surround (was just messing around) it stopped working - for that tv! it will work after some fiddling on another.

i can select hdmi output but no audio will play on the tv (no tv is not muted).

how can i reset the audio to how it was with vanilla 13.10?

fwiw, here's the setting that seems to have permanently broken my hdmi audio (on apparently just the tv connected at the time!)
[http://imagebin.org/274095](http://imagebin.org/274095)
[IMG]http://imagebin.org/index.php?mode=image&id=274095[/IMG]

---

### Post by raphael-estrada on 2013-10-19
for whatever messed up reason, i fixed my problem by choosing a "different" stereo profile using pulse audio volume controller in the configuration tab. details see here
[http://imagebin.org/274099](http://imagebin.org/274099)

---

### Post by raphael-estrada on 2013-10-19
scratch that, only worked once. seriously, how can this be so random?? i see the meters for the hdmi output moving in pulse audio volume controller, but don't hear anything. it worked until i switched that profile the first time. it works on the same hdmi cable and tv connection when i use a bluray player.

what can possibly be wrong here?

---

### Post by raphael-estrada on 2013-10-19
it looks like even though volumes are up high everywhere and the meters are moving i have to turn the tv volume up to max to hear very quiet sound... once or twice a "sudo alsa force-reload" with reboot will fix it. but it will go back to broken short after (like reconnecting the tv). what else governs the hdmi audio output volume?

this is ridiculously frustrating! :-(

---

