---
title: "Hardware/USB-Soundcard for recording guitar?"
date: 2008-10-02
forum: Ubuntu Studio
---

### Post by mrtenl on 2008-10-02
Hey, I'm a guitarist, and i really would like to record some music using my computer, and i was wondering what hardware i need? I have a acoustic guitar, and a Boss ME-50 effects box. I have tried using a mini-jack cable, to connect my effect-box to the mic input of my computer, but the sound quality is very bad, lots of clipping.
I think i need some kind of USB-soundcard, or a preamp? Have tried searching the forums, and googling, but it is a bit confusing, i have no previous experience with music recording.
I would like to be able to add effects to the guitar while playing, listen to it through my headphones, and record at the same time.
:guitar:

---

### Post by cb951303 on 2008-10-02
use the line out from your boss 50 to the line in on your sound card
the quality problem is probably originated form your sound card (I assume its a onboard one?)
other than a quality sound card you don't need a preamp or DI box etc.. since me-50 is a preamp and have a line out output.

---

### Post by Bungo Pony on 2008-10-02
> I would like to be able to add effects to the guitar while playing, listen to it through my headphones, and record at the same time.

As previously mentioned, use the LINE IN on your sound card, not the Mic jack. Not sure how your effects box works, but you may have to reduce the output level to prevent distortion. Pulse Audio has VU meters that will tell you what your input volume is at.

You can also install a piece of software that puts effects on your guitar. It's called "Creox" and it's in the repos (I personally haven't tried it yet)

---

### Post by mrtenl on 2008-10-03
I'm using a laptop (HP 530) and have only got a mic-in, no line-in.

---

### Post by cb951303 on 2008-10-03
> **mrtenl said:**
> I'm using a laptop (HP 530) and have only got a mic-in, no line-in.

you may buy a USB sound card.

cheapest solution that works in linux out of the box: [http://pro-audio.musiciansfriend.com/product/Behringer-UCONTROL-UCA202-USBAudio-Interface?sku=702540](http://pro-audio.musiciansfriend.com/product/Behringer-UCONTROL-UCA202-USBAudio-Interface?sku=702540)

it only supports 16bit resolution and 44k sampling frequency but i tried it and latency is acceptable with jack (17ms)

---

### Post by thorgal on 2008-10-03
or if you have a lot of money, a PCMCIA RME cardbus connected to a multiface II. Latency can be < 2ms in a well tuned system. It can do 96kHz, 24bit.

---

### Post by mrtenl on 2008-10-03
I just ordered the Behringer U-CONTROL UCA202, the Multiface 2 was a bit out of my price range :P
I was wondering about the latency you are talking about. Is 17ms much? Will it be a noticable delay when I'm playing? I have also noticed some talk about realtime kernels? Will i have to recompile my kernel to reduce the latency?

---

### Post by cb951303 on 2008-10-03
I've got the 17 ms without realtime kernel but I believe realtime kernel will reduce it. 17 ms isn't that much. at first you feel the difference while playing but after 10 secs it's just like playing through an amp. you get used to it...

---

### Post by cb951303 on 2008-10-03
oops it seems like I remember it wrong. It's 11.6 ms afterall. look at the second post: [http://ubuntuforums.org/showthread.php?t=806730&highlight=jack](http://ubuntuforums.org/showthread.php?t=806730&highlight=jack)

it was achieved with a behringer uca202

---

### Post by thorgal on 2008-10-03
if you add the ubuntustudio package repositories in your list of repos (package manager like synaptic makes it easy), you can install a realtime kernel next to your non rt kernel (I believe the meta package is called linux-rt but I am not using ubuntu so you will have to google a bit if it's not that). Give it a try and see if you can reduce latency. You will need to set up the file /etc/security/limits.conf: tune it either for your login user or add yourself to the audio unix group and tune the file for the whole group. mine looks like this at the end of the file :


@audio - rtprio 99
@audio - memlock unlimited
@audio - nice -19

you can replace '@audio' by 'username' (your login name without @, which is for a unix group). Then you reboot.

---

### Post by mrtenl on 2008-10-06
Thanks for the help, I'm looking forward to the soundcard arrives, I might have a few more questions then :)

---

