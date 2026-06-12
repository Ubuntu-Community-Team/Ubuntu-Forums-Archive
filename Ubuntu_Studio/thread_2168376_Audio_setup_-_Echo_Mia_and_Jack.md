---
title: "Audio setup - Echo Mia and Jack?"
date: 2013-08-17
forum: Ubuntu Studio
---

### Post by Steve_Ragnar on 2013-08-17
Can anybody help me please? I was so hoping for a good straightforward experience with Studio - you know, get straight in to making music and working with the sounds...BUT I can't even get the ******ed thing to play a ******ed CD, let alone get going with Ardour and Hydrogen etc. I've been trying on and off for two weeks and am just about ready to go back to XP - if this doesn't work, I shall just, a bit sadly, forget about Ubuntu. All that stuff with Terminal is really off-putting. Terminal indeed.

I have Ubuntu Studio 12.04 installed, Athlon XP 3000+, 1.5 GB RAM, masses of HD space and an Echo MIA Midi card. I get the Jack dbus won't run error (amongst others), tried the killall -9jack routine  and still get absolutely nowhere. I can see the Echo mixer, tried 'select control', the card shows as Mia in hw:0 on Jack set up page. 

I've been all over the forums and elsewhere online and still can't get it sorted. Keep getting the throw it out the window urge. Such a maddening dumb waste of time. And yes, this is the first time I have tried Ubuntu or Linux in any form.

---

### Post by jejeman on 2013-08-17
It took me couple of years to switch to Ubuntu, specially for audio work. So...
You should read this to understand a little bit what is going on
[http://tuxradar.com/content/how-it-works-linux-audio-explained](http://tuxradar.com/content/how-it-works-linux-audio-explained)
Give
```
aplay -l
arecord -l
```

---

### Post by Steve_Ragnar on 2013-08-22
Thanks for your reply, jejeman, and an informative link.
Well, I've tried, but I'm not going to spend any more time on Ubuntu. I wish it had worked for me - it seemed promising, but I'm not a programmer and I have no intention of grappling with the terminal and learning something that just looks totally inscrutable and opaque. I want to be making music and learning my way through musical problems - I get a high off doing that, I get nothing from trying to grapple with software and hardware problems like this.

---

### Post by cub on 2013-08-24
Too bad you didn't ask earlier, instead of being frustrated in two weeks, and we might have been able to help before you gave up. Maybe you come back? If not earlier, so try out the next LTS in April 2014.

---

### Post by pumrel on 2013-09-14
I have got a similar problem so I thought I would continue with this thread. I am trying to get Guitar Rig 3/4 (in wine) to work with my Echo Audio io card but I am quite struggling. It seems that the card is supported well. The output works fine, I can hear the metronome in Guitar Rig, I can play music through the card and so on. If I plug my guitar to the card I can see in Echomixer that it is catching the signal but the input is not fed into Guitar Rig. I can't figure out what is wrong.

I played a bit with wineasio and installed the lowlatency kernel as well but with no success. It's a dead end for me.

---

### Post by jejeman on 2013-09-15
First, does it work tih linux applications? Both JACK and non-JACK ones?

---

