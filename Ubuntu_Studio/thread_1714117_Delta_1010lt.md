---
title: "Delta 1010lt"
date: 2011-03-24
forum: Ubuntu Studio
---

### Post by heavyhanded on 2011-03-24
Hi, I've got a fresh install of Ubuntu 10.10 (not studio) and a delta 1010lt card that's not giving any sound.  I'd like to get ardour up and running and am wondering what the current fix is for this.  I've search around a bit and found a lot of mostly outdated forum posts.  

I do have an onboard VIA sound card on the asus mobo but I'd prefer to use the delta exclusively as it's nicely patched in to my patch bay and don't really want to screw around with other I/O if I can avoid it.  

From what I can gather there is some kind of conflict with pulse audio?  I'm not too familiar with pulse audio since I haven't used linux in a while and it used to be all alsa mixer from what I remember.  

Every thing else on this install is finally running great but I'm 
really wanting to see how the linux DAW world is coming along.  Help?

Is there a possible conflict with the onboard sound?
Should I just get rid of the onboard sound drivers all together?

---

### Post by ailo.at on 2011-03-25
M-Audio Delta cards use the chip ice1712. The card is well supported by alsa, but is not presenting a standard set of outputs for pulseaudio, which is why you get no desktop sound. However, this can be fixed.

Getting Ardour + jack to run should be no problem. ice1712 cards work fine with jack without fixes.

Here is a fix that should resolve the pulseaudio problem: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/30](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/30)

I haven't tried those fixes for a while, since I don't use pulseaudio with that card. I have two ice1712 cards, and both work fine.

---

### Post by heavyhanded on 2011-03-25
Thanks, that fix worked. 

I had found that fix before and thought I tried it but I must have forgot to write the change :S

---

### Post by heavyhanded on 2011-03-25
Actually, although ardour is working properly now, I still don't have ubuntu's main audio working with jack.  ardour is the only program I can get sound out of.  I'll keep looking for a solution.

---

### Post by cchhrriiss121212 on 2011-03-25
Jack is not supposed to work with regular apps (system sounds, Firefox etc), it is for audio work only (Ardour, Hydrogen etc). You can modify jack to do that, but I would not recommend it.

---

### Post by zettberlin on 2011-03-25
> **cchhrriiss121212 said:**
> Jack is not supposed to work with regular apps (system sounds, Firefox etc), it is for audio work only (Ardour, Hydrogen etc). You can modify jack to do that, but I would not recommend it.

Dont be too apodictic ;-)

Just listening to OGG-files and watching DVDs with VLC via jack is perfectly OK.

---

### Post by cchhrriiss121212 on 2011-03-25
^Yes, VLC is easy to use with jack as it has a jack-plugin package in the repos. Most other software does not, and requires you to route pulse or ALSA through jack, which is quite complex and hit-and-miss for many users.

---

### Post by Pablo_F on 2011-03-26
There is a surprisingly high number of apps that can be "jackified", including the flash player and ubuntu's default multimedia players.

---

### Post by ailo.at on 2011-03-26
> **heavyhanded said:**
> Actually, although ardour is working properly now, I still don't have ubuntu's main audio working with jack.  ardour is the only program I can get sound out of.  I'll keep looking for a solution.

As mentioned already, you don't need jack for Desktop sound. When you don't use jack, pulseaudio is in use. 
The fix I mentioned should fix the Desktop sound problem (pulseaudio). If it hasn't, you might want to have another look at that.
Did you keep the original file found in /usr/share/alsa/cards/ICE1712.conf? If not, here is the edited version. I only added two lines to the original:
```

#
# Configuration for the ICE1712 (Envy24) chip
#

# default with dmix & dsnoop
ICE1712.pcm.default {
    @args [ CARD ]
    @args.CARD {
        type string
    }
    type asym
    playback.pcm {
        type plug
        slave.pcm {
            @func concat
            strings [ "dmix:" $CARD ",FORMAT=S32_LE" ]
        }
    }
    capture.pcm {
        type plug
        slave.pcm {
            @func concat
            strings [ "dsnoop:" $CARD ",FORMAT=S32_LE" ]
        }
    }
}

<confdir:pcm/front.conf>

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

<confdir:pcm/surround40.conf>

ICE1712.pcm.surround40.0 {
    @args [ CARD ]
    @args.CARD {
        type string
    }
    type route
    ttable.0.0 1
    ttable.1.1 1
    ttable.2.2 1
    ttable.3.3 1
    slave.pcm {
        type hw
        card $CARD
    }
}    

<confdir:pcm/surround41.conf>
<confdir:pcm/surround50.conf>
<confdir:pcm/surround51.conf>

ICE1712.pcm.surround51.0 {
    @args [ CARD ]
    @args.CARD {
        type string
    }
    type route
    ttable.0.0 1
    ttable.1.1 1
    ttable.2.2 1
    ttable.3.3 1
    ttable.4.4 1
    ttable.5.5 1
    slave.pcm {
        type hw
        card $CARD
    }
}

<confdir:pcm/iec958.conf>

ICE1712.pcm.iec958.0 {
    @args [ CARD AES0 AES1 AES2 AES3 ]
    @args.CARD {
        type string
    }
    @args.AES0 {
        type integer
    }
    @args.AES1 {
        type integer
    }
    @args.AES2 {
        type integer
    }
    @args.AES3 {
        type integer
    }
    type asym
    playback.pcm {
        type hooks
        slave.pcm {
            type route
            ttable.0.8 1
            ttable.1.9 1
            slave.pcm {
                type hw
                card $CARD
            }
            slave.format S32_LE
            slave.channels 10
        }
        hooks.0 {
            type ctl_elems
            hook_args [
                {
                    interface PCM
                    name "IEC958 Playback PCM Stream"
                    lock true
                    preserve true
                    value [ $AES0 $AES1 $AES2 $AES3 ]
                }
            ]
        }
    }
    capture.pcm {
        type route
        ttable.0.8 1
        ttable.1.9 1
        slave.pcm {
            type hw
            card $CARD
        }
        slave.format S32_LE
        slave.channels 12
    }
}

```

---

