---
title: "Altec Lansing USB Speakers (XT1) and Daru2"
date: 2008-01-14
forum: System76 Support
---

### Post by imhavoc on 2008-01-14
I was happy to see NewEgg.com put the Altec Lansing XT1 USB speakers on sale last week, so I placed the order knowing that problems were likely with the Daru2 and Gutsy (Kubuntu 7.10).

Well, the speakers are here, and I am having the expected trouble with them.

The good new is that:
 - The speakers are recognized by the system
 - the bottoms on the side of the speaker work correctly (vol up, vol down, "power" button mutes sound)
 - I can force mplayer's output to the speakers with: 'mplayer -ao alsa:device=hw=1.0 path/to/file.mp3'

Unfortunately, I can't get KDE to send output to the speakers. Also, when I send the output from mplayer to the XT1s, I have no control over the volume. (Woohoo!)

thoughts? suggestions? comments?

---

### Post by thomasaaron on 2008-01-15
I'm not all that familiar with KDE, but in Gnome, if you go to System > Prefs > Sound you can select which devices do what. You could choose to use the USB sound device for multimedia output, etc... Then at the bottom of the GUI, you could select which device your volume buttons control (i.e. your USB device).

There must be an equivalent control panel in KDE, but I'm not sure what it is. Maybe some of our KDE customers can help out.

---

### Post by imhavoc on 2008-01-16
I tried messing with under Gnome as well as KDE4. it's just ... messed up.

I've read that it works with other distros, but I also know that there have been enough googfy things with the Daru2 sound that I thought I'd throw it out here first.

"Maybe it'll work with Hardy" :-D

(I know that Gutsy sure fixed a world of issue for me. We'll see.)

No big. The speakers were on sale, and I can still run the headphone out to the Aux-in on the speakers if I really want to use them.

Thanks!

---

### Post by thomasaaron on 2008-01-17
Well, if you're happy, we're happy. But I'd be REALLY surprised if it can't be made to work.

If your interested in pursuing it, plug in the speakers and post some screenshots of your sound control settings.

Also, I would need to know if you just downloaded the kde desktop, of if you did a fresh install of Kubuntu? (I'm wondering, I guess, if ALSA is compiled with the USB tag. Do USB headphones work? There shouldn't be much of a difference.)

Best,
Tom

---

### Post by imhavoc on 2008-01-19
This is a complete install of Kubuntu 7.10.

I think I've used my USB headset with this install on this machine. I'm not sure, but I can certainly test it easily enough. I'll do that.

I'm also hoping to have enough time this weekend to plug the speakers into the desktop in the office and see how it responds to them.

With that information, I should have some idea about what's going on.

---

### Post by OOOOPS on 2008-02-08
anyone ever get this to work?

---

### Post by imhavoc on 2008-02-09
I can play files to the speakers with a command like this:

mplayer -ao alsa:noblock:device=hw=2.0 path/to/file.mp3

I can then control the volume with **(you'll want to turn the volume down before you start playing a file, so do this first)**:

alsamixer -c 2

**NOW**, this is for the onboard card being card 0, my bluetooth headset being card 1 and the USB speakers being card 2, **SO**, if your USB speakers are card 1, you'll use "hw=1.0" instead of "hw=2.0"

I hope this helps. If I'm confusing everyone, I'll try again.

I'm listening to a podcast while typing this through my bluetooth headset.

---

### Post by imhavoc on 2008-02-09
A note on my and consoles:

I always have a console open. I actually always have 5 consoles open. KDE's konsole is always open on my desktop with 5 tabs open, so I do a lot of things from the command line. I actually prefer to listen to my podcasts through Mplayer's command line interface instead of any of the graphical players I've ever messed with.

So, while playing mead through a text interface may be strange, it's where I live most of the time, so it doesn't bother me to do command line things like I described above.

---

### Post by imhavoc on 2008-02-09
At the risk of rambling....

It just occurred to me that I could stop and restart Kmix (I'm a Kubuntu/KDE user). Kmix does not connect to the Altec Lansing controls until it has been restarted after the speakers are connected.

If you want to control the USB speakers with the volume slider of Kmix and the keyboard shotcut keys, you'll need to right-click on the kmix icon, "Select Master Channel", and change it to the Altec Lansing speakers, and select the PCM channel. (one of the Bass channels is selected by default.)

Once that's done, you have normal control of the volume of the speakers. The volume and "power" button on the speaker also work in this context. (The "power" button will actually mute the output from the PC, which is kind of cool.)

I hope this helps Gnome users and users of other desktops along.

I would still love to figure out how to get Amarok to play to the USB speakers.

---

