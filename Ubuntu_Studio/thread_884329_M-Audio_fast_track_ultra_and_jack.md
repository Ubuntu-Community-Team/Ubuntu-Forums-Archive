---
title: "M-Audio fast track ultra and jack"
date: 2008-08-08
forum: Ubuntu Studio
---

### Post by Miesco on 2008-08-08
I plugged my fast track ultra in, see the sound cards but jack is giving errors, any help would be appreciated.

root@ubuntu:/home/shawn# cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 19
 1 [Ultra          ]: USB-Audio - Fast Track Ultra
                      M-Audio Fast Track Ultra at usb-0000:00:1d.7-3, high speed
 2 [K88            ]: USB-Audio - Keystation Pro 88
                      Evolution Electronics Ltd. Keystation Pro 88 at usb-0000:00:1d.0-2, full speed

So, when I use hw:1 for jack i get this: 
21:15:47.142 Startup script...
21:15:47.145 artsshell -q terminate
21:15:47.563 Startup script terminated with exit status=256.
21:15:47.564 JACK is starting...
21:15:47.564 /usr/bin/jackd -R -dalsa -dhw:1 -r44100 -p1024 -n2 -s
21:15:47.582 JACK was started with PID=22377.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1|hw:1|1024|2|44100|0|0|nomon|swmeter|soft-mode|32bit
control device hw:1
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
21:15:47.605 JACK was stopped successfully.
21:15:47.605 Post-shutdown script...
21:15:47.605 killall jackd
jackd: no process killed
21:15:48.012 Post-shutdown script terminated with exit status=256.
21:15:49.805 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by jazzman on 2008-08-09
First turn off any other audio. I had Amarok going when I tried just a second ago...whoops!

Second, open qjackctl and click on SET UP. Change FRAMES/PERIOD to 256, then change PERIODS/BUFFER to 2. This is a good starting point.

Here's a link to an article that explains JACK fairly thoroughly. 

[http://linux-sound.org/knowing-jack.html](http://linux-sound.org/knowing-jack.html)

Good Luck

Jazzman

---

### Post by Miesco on 2008-08-10
Do you have the fast track ultra?  Is it even possible to use it on linux?

---

### Post by rosegarden78 on 2008-08-15
I have an M-Audio Fast Track Pro.  After a week collecting research I managed to get it working just fine.  Why don't you take a look at this article?  [http://ubuntuforums.org/showthread.php?t=769822](http://ubuntuforums.org/showthread.php?t=769822)

---

### Post by weegreenblobbie on 2009-05-05
I have tried to configure my fast track pro for 24 bit recording.  Following the info posted at

[http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro](http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro)

I have tried to configure the snd_usb_audio kernel module to enable 96000 Hz 24 bit mono recording.

My /etc/modprobe.d/sound.conf looks like this:

options    snd_usb_audio    vid=0x763 pid=0x2012 device_setup=0xD index=5 enable=1

However using arecord fails for 24 bit recording:

// Big Endian

$ arecord -c 1 -t raw -r 96000 -f S24_3BE -D hw:5,1 test.raw
Recording raw data 'test.raw' : Signed 24 bit Big Endian in 3bytes, Rate 96000 Hz, Mono
arecord: set_params:961: Sample format non available

// Little Endian

$ arecord -c 1 -t raw -r 96000 -f S24_3LE -D hw:5,1 test.raw
Recording raw data 'test.raw' : Signed 24 bit Little Endian in 3bytes, Rate 96000 Hz, Mono
arecord: set_params:961: Sample format non available

Has anybody successfully recorded at 24 bits? If so, how about 96000 Hz, 24 bits?

Does anybody know how to confirm that my snd_usb_audio options are being used when the module loads?

Thanks!
-Nick

---

### Post by salvoinzk on 2010-01-15
> **Miesco said:**
> I plugged my fast track ultra in, see the sound cards but jack is giving errors, any help would be appreciated.

root@ubuntu:/home/shawn# cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 19
 1 [Ultra          ]: USB-Audio - Fast Track Ultra
                      M-Audio Fast Track Ultra at usb-0000:00:1d.7-3, high speed
 2 [K88            ]: USB-Audio - Keystation Pro 88
                      Evolution Electronics Ltd. Keystation Pro 88 at usb-0000:00:1d.0-2, full speed

So, when I use hw:1 for jack i get this: 
21:15:47.142 Startup script...
21:15:47.145 artsshell -q terminate
21:15:47.563 Startup script terminated with exit status=256.
21:15:47.564 JACK is starting...
21:15:47.564 /usr/bin/jackd -R -dalsa -dhw:1 -r44100 -p1024 -n2 -s
21:15:47.582 JACK was started with PID=22377.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1|hw:1|1024|2|44100|0|0|nomon|swmeter|soft-mode|32bit
control device hw:1
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
21:15:47.605 JACK was stopped successfully.
21:15:47.605 Post-shutdown script...
21:15:47.605 killall jackd
jackd: no process killed
21:15:48.012 Post-shutdown script terminated with exit status=256.
21:15:49.805 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.



Hi Miesco, and hi you all

Try to download the ALSA driver from here:

[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

(the following files : alsa-driver-1.0.22.1.tar.bz2 ; alsa-lib-1.0.22 ; alsa-utils-1.0.22 should be enough)


unpackage the zipped files in /usr/src/ should be good
then apply the patch to "usbaudio.c" and "usbquirks.h" files inside /alsa-driver-1.0.22.1/sound/usb folder.


--- linux/sound/usb/usbaudio.c
+++ linux/sound/usb/usbaudio.c
@@ -2235,6 +2235,10 @@ static void init_substream(struct snd_us
                case USB_ID(0x041e, 0x3f0a): /* E-Mu Tracker Pre */
                        subs->ops.retire_sync = retire_playback_sync_urb_hs_emu;
                        break;
+               case USB_ID(0x0763, 0x2080): /* M-Audio Fast Track Ultra */
+                       subs->ops.prepare_sync = prepare_playback_sync_urb;
+                       subs->ops.retire_sync = retire_playback_sync_urb;
+                       break;
                }
        }
        snd_pcm_set_ops(as->pcm, stream,
@@ -2786,6 +2790,7 @@ static int parse_audio_endpoints(struct
                        break;
                case USB_ID(0x041e, 0x3020): /* Creative SB Audigy 2 NX */
                case USB_ID(0x0763, 0x2003): /* M-Audio Audiophile USB */
+               case USB_ID(0x0763, 0x2080): /* M-Audio Fast Track Ultra */
                        /* doesn't set the sample rate attribute, but supports it */
                        fp->attributes |= EP_CS_ATTR_SAMPLE_RATE;
                        break;
--- linux/sound/usb/usbquirks.h
+++ linux/sound/usb/usbquirks.h
@@ -1864,6 +1864,33 @@
                }
        }
},
+{
+       USB_DEVICE_VENDOR_SPEC(0x0763, 0x2080),
+       .driver_info = (unsigned long) & (const struct snd_usb_audio_quirk) {
+               /* .vendor_name = "M-Audio", */
+               /* .product_name = "Fast Track Ultra", */
+               .ifnum = QUIRK_ANY_INTERFACE,
+               .type = QUIRK_COMPOSITE,
+               .data = & (const struct snd_usb_audio_quirk[]) {
+                       {
+                               .ifnum = 0,
+                               .type = QUIRK_IGNORE_INTERFACE
+                       },
+                       {
+                               .ifnum = 1,
+                               .type = QUIRK_AUDIO_STANDARD_INTERFACE
+                       },
+                       {
+                               .ifnum = 2,
+                               .type = QUIRK_AUDIO_STANDARD_INTERFACE
+                       },
+                       /* interface 3 (MIDI) is standard compliant */
+                       {
+                               .ifnum = -1
+                       }
+               }
+       }
+},

/* Casio devices */
{



And then try to compile the sound-driver only (not the whole kernel)

I found a totorial for compiling the alsa driver here:

[http://forum.masterdrive.it/blogs/master85/ubuntu-9-10-compilare-alsa-driver-55/](http://forum.masterdrive.it/blogs/master85/ubuntu-9-10-compilare-alsa-driver-55/)

It's in italian language but if you need I can translate it.

I'll be honest I failed trying to patching the driver ..... so good luck!


ps: here is a tutorial, in english language, for upgrading (/compiling) the ALSA driver (remember, do it after paching the driver!):
[http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/)

and here, too:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)



Hope this help, and please let us know your progress
Salvo

ps: if you want, try to go to this forum, too:
[http://www.linuxmusicians.com/viewtopic.php?f=6&t=1581&p=8085](http://www.linuxmusicians.com/viewtopic.php?f=6&t=1581&p=8085)

---

### Post by salvoinzk on 2010-01-20
Hi you all

it seems that a french guy was able to make work the Fast Track Ultra (= FTU)

I don't understand the french language but, it seems, he applied the previous patch to the kernel and then recompiled it again, and now the FTU works.

here is the link:
[http://www.linuxmao.org/tikiwiki/tik...parentId=16414]("http://www.linuxmao.org/tikiwiki/tiki-view_forum_thread.php?topics_offset=1&forumId=2&comments_parentId=16414")

hope this help !


ps: here the english translation of the above site:
[http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fwww.linuxmao.org%2Ftikiwiki%2Ftiki-view_forum_thread.php%3Ftopics_offset%3D1%26forumId%3D2%26comments_parentId%3D16414&sl=auto&tl=en](http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fwww.linuxmao.org%2Ftikiwiki%2Ftiki-view_forum_thread.php%3Ftopics_offset%3D1%26forumId%3D2%26comments_parentId%3D16414&sl=auto&tl=en)

bye

---

