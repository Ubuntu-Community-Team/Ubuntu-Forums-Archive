---
title: "What is the best MP3 player for Ubuntu Studio?"
date: 2009-12-14
forum: Ubuntu Studio
---

### Post by kwabena39 on 2009-12-14
Hi,

I used to use Alsaplayer in regular-old Ubuntu and it worked great...I could play my talk shows while browsing the web.  Hardly ever had to do a re-boot, except when certain updates came in.

But then I got Ubuntu Studio so I could do sound production; since ALSA is gone, Alsaplayer no longer works.  Now, I'm stuck with this Audacious, which means I have to do a hard re-boot because whenever I go to websites while playing my player, the player crashes.  I also noticed that when the player is running, I can't get sound out of Youtube (sometimes I like to pause my player and hear a video.)  It's either-or: either Youtube OR Audacious.

What do you recommend as a good MP3 player, compatible with Artsd, that doesn't crash, doesn't exclude sound playback from other things?

---

### Post by Stochastic on 2009-12-15
ALSA is in Ubuntu Studio, I'm not sure why you thought it was gone.

Which version of Ubuntu Studio are you running?  I find rhythmbox to work fine while playing Youtube vids on my 9.10 install.

---

### Post by kwabena39 on 2009-12-15
Then how come there's no sound out of either Alsaplayer or Audacity?

I'm using the latest Ubuntu Studio via a Generic Kernal of Ubuntu 8.04, AMD-64 bit, because I can't get the X-server on RT kernal to start, or I can only get it to start in Recovery Mode; I can't seem to get my ATI card driver (proprietary) to work right on RT so I only get a black screen while booting up in RT, so I am running it at the highest Generic level (26, I think)

And there is sound on Youtube and other players, but no sound on audacity or alsaplayer.

---

### Post by kwabena39 on 2009-12-15
I figured out what it might be.  I learned that in Ubuntu Studio, everything runs on Jack, so I started the Jack server, and did manage to get some sound out of Alsaplayer by connecting it, although it was scratchy, and still no sound out of Audacity.

Maybe it's my sound card?  Is that an issue?  I mean, I do have a new generic kind of motherboard, and the soundcard came with the motherboard.

Do I have to buy a special soundcard to get everything to work properly?

I tried to force Jack to 16 bit, but still no improvement in Alsaplayer playback.  Ironically enough, Exaille plays normal

---

### Post by thorgal on 2009-12-15
most likely, you are running jack on top of ALSA.

jack has no direct access to your soundcard. It is using a backend driver that communicates with the lower audio level, i.e. ALSA in your case (most likely).

When jack runs, apps that do not understand the jack API, will not be able to connect to the so-called jack graph, so they will be useless as such.

2 options:

1- turn off jackd and you should be fine with the "non jackified" apps

2- in case you want to use jack for some music production work, you need these apps to be able to connect to the jack graph.

alsaplayer comes with a jack module (look up alsaplayer in synaptic) and you should find an 'alsaplayer-jack' package). If you install it, it will then work like this from the terminal:

```

alsaplayer -o jack

``` 

this will trigger alsaplayer to use jack as the audio server.


For audacity, you can look into the preferences. The PortAudio backend it is using has jack support (most likely). So when jack is running and you fire audacity, look into the audio preferences and most likely you will find some jack options.
If not, then I can only think that jack support was not included by default in the compilation of these packages (for U.Studio, that would definitely be wrong when these apps can support jack - I use them in my jack-based studio).

---

### Post by kwabena39 on 2009-12-16
I got Ubuntu Studio and Jack in the first place because I wanted to try and compose music on my computer.  But I just got rid of all the Ubuntu Studio stuff and went back to plain-old Ubuntu, where all my original sound-editing devices and players worked, no problem.

This Jack stuff was just way over my head; it was rickety, always starting and stopping, and I couldn't get it configure right and work on my system with any reliability.  

I did all this originally to get Rosegarden working.  All for Rosegarden, I got into this Ubuntu Studio mess, and got all kinds of stuff like KDE, (which I didn't want)

Is there any simple, no-nonsense program out there to compose some simple music scores, no KDE, no Jack?  How about Noteedit?  Does that require Jack?

---

