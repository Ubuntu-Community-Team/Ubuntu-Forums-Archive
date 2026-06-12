---
title: "Ubuntu studio 10.10 &amp; Delta 1010"
date: 2011-02-06
forum: Ubuntu Studio
---

### Post by Devert on 2011-02-06
Hi, i need some help.

Im new to Ubuntu and i need to get my soundcard to work. I have a M-audio Delta 1010 and running Ubuntu studio 10.10 for AMDx64.

I have been searching around and i really cant get my head around this. I need at least to get the system sound to work. So i can play music and films, and if i can get it to record i'll be happy.

 My card is recognized by the system. ALSA can find it and has loaded it. How to i go on from here??

---

### Post by Devert on 2011-02-06
[SIZE=4]**Update!**[/SIZE]

It seems to work fine with Ardour. I can record and play it back, no problem. So how do i get the system sounds and other aplications to work with my soundcard?

---

### Post by Pablo_F on 2011-02-06
Hi, 

This is a known issue in ubuntu with pulseaudio and the cards that use the snd-ice1712 alsa module, including your interface.

Fyi, pulseaudio is the default audio server, oriented towards desktop use. Jack is a special audio server, oriented to music production, that ardour and other apps need. Pulseaudio has nothing to do with ardour so Sound Preferences (a pulseaudio front-end) is useless when running ardour. 

To solve the problem, see:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442) 

The workaround in comment #30 worked for me.

Cheers, Pablo

---

### Post by Devert on 2011-02-06
[B]Thanks! Fast and accurate reply!
That did the trick, sound works just fine!

For you who want to know what i did, this is the fix posted in comment nr30 in the link:[/B]

 
The reason pulseaudio right now doesn't work with this card is that it expects a front device that has only 2 channels.
A possible fix for this is changing it's definition to:
ICE1712.pcm.front.0 {
        @args [ CARD ]
        @args.CARD {
                type string
        }
        type route
        ttable.0.0 1
        ttable.1.1 1
        slave.pcm {
                type hw
                card $CARD
        }
        slave.format S32_LE
        slave.channels 10
}
in /usr/share/alsa/cards/ICE1712.conf
This is taken from RedHat's and pulseaudio's bugtracker and the alsa list, I can't find the relevant thread/bugs right now though...

**Reboot and it should work fine!**
Thanks to [Florian Zeitz]("https://launchpad.net/%7Eflorian-zeitz") who posted this comment.

---

