---
title: "M-audio Fast Track ULTRA Problems! Solution?!"
date: 2009-12-09
forum: Ubuntu Studio
---

### Post by Jurica on 2009-12-09
Hi!
I'm linux ubuntu user for quite some time and I have it on all of my comps except my main computer. I'm a professional musician and I use my computers for recording and sound synthesis. I'm using "Fast track ultra " sound card and it sure has a few problems under linux. First of all I googled around and found out that "Fast track pro" works under linux and "fast track ultra" doesn't.
The problem with "FTU" is that Audio inputs/outputs do not work at all. I can only use it as a MIDI device. And when I start JACK with this device it just wont start. I tried blacklisting my onboard sound card and problem still remains. I see that many people have this problems, but googleling around I found this forum, where this guy posted a kernel patch that he received from ALSA. 
So I'm wondering...How to patch a kernel with this file and is it safe. 
Here is the link to forum:

[http://www.linuxmusicians.com/viewtopic.php?f=6&t=1581&p=8085](http://www.linuxmusicians.com/viewtopic.php?f=6&t=1581&p=8085)

And here is the patch file that he got from ALSA:
[COLOR=Blue]
The MIDI interface is class compliant, and this is what's shown by Jack.
The audio interfaces are marked as vendor specific, so the driver needs
to be changed to support them.

Please try recompiling your kernel with the patch below.

Some M-Audio devices use big-endian samples, so beware of speaker-
killing noise.

It's possible that playback synchronization doesn't work completely.

Please check what happens when you try to play and record with different
sample rates.


HTH
Clemens

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
 {[/COLOR]

I would appreciate any help!
Has anyone tried this. And can anyone make a .deb file or something out of this?
If someone could make it i would like to test it!
Best to you all
JJ

---

### Post by DerickX on 2009-12-09
What version of Ubuntu do you use?

What about buying another soundcard? :)
That might safe you having trouble...

I think if possible it's better to buy a full supported pci or firewire card

---

### Post by Jurica on 2009-12-09
Hi, thank you for your reply!
I'm using Ubuntu studio 9.10 (Karmic) with RT and Ubuntu Studio 9.10,
on two different computers and the problem keeps repeating.
And new sound card...hmmm...Idk. I'm very pleased with this one.
I'm using it on windows Xp for now just for recording. Good thing is that
device is very mobile and it has  8 inputs which come handy when I
record a live drumkit or a small band. Plus, Croatian pay checks are
pretty lame and small so new sound card is something to save for :( 
Best
J

---

### Post by DerickX on 2009-12-09
Sell it! :P

More info on supported (usb) cards: 
[http://wiki.linuxmusicians.com/doku.php?id=hardware&DokuWiki=524266daad7393d7106d66d92bd1fd33](http://wiki.linuxmusicians.com/doku.php?id=hardware&DokuWiki=524266daad7393d7106d66d92bd1fd33)

---

### Post by salvoinzk on 2010-01-15
> **Jurica said:**
> Hi!
I'm linux ubuntu user for quite some time and I have it on all of my comps except my main computer. I'm a professional musician and I use my computers for recording and sound synthesis. I'm using "Fast track ultra " sound card and it sure has a few problems under linux. First of all I googled around and found out that "Fast track pro" works under linux and "fast track ultra" doesn't.
The problem with "FTU" is that Audio inputs/outputs do not work at all. I can only use it as a MIDI device. And when I start JACK with this device it just wont start. I tried blacklisting my onboard sound card and problem still remains. I see that many people have this problems, but googleling around I found this forum, where this guy posted a kernel patch that he received from ALSA. 
So I'm wondering...How to patch a kernel with this file and is it safe. 
Here is the link to forum:

[http://www.linuxmusicians.com/viewtopic.php?f=6&t=1581&p=8085](http://www.linuxmusicians.com/viewtopic.php?f=6&t=1581&p=8085)

And here is the patch file that he got from ALSA:
[COLOR=Blue]
The MIDI interface is class compliant, and this is what's shown by Jack.
The audio interfaces are marked as vendor specific, so the driver needs
to be changed to support them.

Please try recompiling your kernel with the patch below.

Some M-Audio devices use big-endian samples, so beware of speaker-
killing noise.

It's possible that playback synchronization doesn't work completely.

Please check what happens when you try to play and record with different
sample rates.


HTH
Clemens

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
 {[/COLOR]

I would appreciate any help!
Has anyone tried this. And can anyone make a .deb file or something out of this?
If someone could make it i would like to test it!
Best to you all
JJ



Hi Jurica and hi you all.

I know the forum that you are talking about.

Well, right some days ago I have posted 2 messages, go there and read them.

About the patch, maybe, you don't need to compile the whole kernel, but it should be enough to apply it only to the ALSA driver and then compile only the sound-driver.

Go to the following link for some help for compiling the driver:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

(of course before apply the patch).


Anyway if you go to the "LinuxMusicians" forum you'll find my posts.

[http://www.linuxmusicians.com/viewtopic.php?f=6&t=1581&p=8085](http://www.linuxmusicians.com/viewtopic.php?f=6&t=1581&p=8085)



Hope this help, and please let us know your progress
Salvo

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

