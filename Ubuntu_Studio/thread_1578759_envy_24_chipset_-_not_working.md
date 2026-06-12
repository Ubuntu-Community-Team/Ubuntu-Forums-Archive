---
title: "envy 24 chipset - not working ?"
date: 2010-09-20
forum: Ubuntu Studio
---

### Post by its_jon on 2010-09-20
Help :confused: :P Please

just installed a fresh Ubuntu Studio.

My Envy24 chipset is recognised and the Envy24 control also installed.

PulseAudio Volume Meter bouncing away fine ! ..... but no actual output.

Where do I start ?

Its as if everything is working except the final output to the speakers.

---

### Post by Pablo_F on 2010-09-21
See: 
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)

Comment #30 solved the problem for me and more people.

Cheers! Pablo

---

### Post by its_jon on 2010-09-21
Thanks.... I tried that..

Logged out and back in... still no sound.

I notice that when I enter the Pulse Audio Applets My card shows up as 

ICE1712 [ENVY24] Multi Channel I/O Controller Digital Surround 4.0 (IEC958 )

What's the (IEC958 ) ?

(IEC958 ) appears in all the pulse profile choices and yet not in /usr/share/alsa/cards/ICE1712.conf.

?

---

### Post by Pablo_F on 2010-09-21
Afaik, IEC958 is S/PDIF but I am not an expert. It is digital I/O. I have never used it.

I have a m-audio 2496, based on that chip, module used by it is snd-ICE1712. I use jack so I don't care much about pulseaudio but I might need pulseaudio so I don't want to completely forget about it. 

I launch pavucontrol, configuration tab. I only see different **digital** I/O Stereo/Surround combinations. I apply comment #30. This is my file now:

 cat /usr/share/alsa/cards/ICE1712.conf


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
					interfa#
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
ce PCM
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

I reboot the computer. I launch pavucontrol. Configuration tab. Now, I see, between others, Analog Stereo output. I choose that. I can rise the volume in the Output Devices tab.

I launch,for example:

mplayer -ao pulse some-music.ogg

In the Playback TAB of Pavucontrol I see the audio stream of mplayer that I can route to ICE1712.

I hear it!

HTH, Pablo

---

### Post by its_jon on 2010-09-22
:guitar:
[B]
Thanks SO Much ![/B]

You made a Scotsman dance :)

[IMG]http://1.bp.blogspot.com/_af2tMq2AjDc/SXwNuVtRfTI/AAAAAAAABYs/i-sHigrIJwg/s400/Burns+scotsman_on_a_horse.jpg[/IMG]

thank you
thank you
thank you
thank you
thank you
thank you

Arrrrrrrr....... 24/96 :-({|=

---

