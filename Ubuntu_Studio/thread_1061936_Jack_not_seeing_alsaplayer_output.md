---
title: "Jack not seeing alsaplayer output"
date: 2009-02-06
forum: Ubuntu Studio
---

### Post by Graham C Williams on 2009-02-06
Hello all.
I'm new to this forum and new to Linux/Ubuntu/The wonders of the Terminal/GNOME. I'm not at all new to computers and operating systems. Over the last week (and with a lot of help from this forum, so 'Many Thanks') I've put 8.10 onto a small touch screen Panel PC. Set-up Jack and Ardour and got the system talking (correctly) to a Aureon5.1USB MKII. 
I would like to get alsaplayer to work via Jack. 
I suspect that alsaplayer as downloaded via Add/Remove is in some way set to Alsa only output as the Jack Input refuses to recognise the alsa player as a source. I have no problems with jack seeing the Aureon or seeing the on-board sound system. (Just to clarify, The panel PC has an internal sound system that works well and the USB sound card.)

How can I solve this problem - Any suggestions please?
Thanks in advance
Graham.

---

### Post by thorgal on 2009-02-06
```

sudo apt-get install alsaplayer-jack

```

---

### Post by Graham C Williams on 2009-02-07
Wow. Thanks for the prompt reply.
Unfortunately the suggested did not work; the Alsaplayer and Jack resolutely refuse to see each other. 
Not to worry! I tried GNOME MPLAYER instead; that worked well (after a bit of fiddling!). It's a shame because in my opinion Alsaplayer seems to be a smoother app, GNOME MPlayer appears a little clunky in comparison but it works and that is all that was needed for my purposes.

For the record.
By running 3 instances of GNOME MPLAYER through JACK you generate 3 Independent stereo outputs from the Aureon5.1USB MKII. Lovely!;)

Many Thanks
Graham.

---

### Post by thorgal on 2009-02-07
hi Graham,

I might have been fast at replying but I certainly wasn't exhaustive ... the real tip is the following:
alsaplayer has different output drivers. Jack can be used. If you search alsaplayer in your package manager, e.g. synaptic, you'll see that these output drivers are modular, some don't get installed by default. My suggestion was to install the alsaplayer jack output driver.

Once you have done that, you need to tell alsaplayer to explicitely use this output driver:

```

alsaplayer -o jack some_file

```


if you type 
```

alsaplayer --help

```
there's a section about output drivers with the -o option. It will list what you have (apt)installed.

I hope you will make it work as you hoped.

---

### Post by Graham C Williams on 2009-02-07
OK. I'll give that a go. It'll be tomorrow now but I'll let you know how I get on.

Graham.

---

### Post by Graham C Williams on 2009-02-09
Magic. It works! I put your line:

Code:

alsaplayer -o jack some_file

into the start-up command section of the menu list and now I can call-up 3 instances of the Alsaplayer. They instantly appear in Jack. The result is 3 separate stereo streams of audio. The connection is stable and the programe runs well. I can change playlists or songs etc in any of the alsaplayers without disturbing the connections to or inside jack. This is exactly what is wanted.

Would it be possible to write a script that would start up-to 3 instances of Alsaplayer and jack then make the connections within jack, so that the first alsaplayer went to outputs 1 and 2, the second to 3 & 4 etc.? I guess it must be possible, Ardour does something like that when it starts and you put in the initial values?

Thanks for all your help
Graham

---

### Post by thorgal on 2009-02-09
Ciao Graham,

Glad you have it working as you want.

For what you are asking, sure, it is possible :)
Once again, the command line help is your friend:

```

alsaplayer -o jack -d system:playback_1,system:playback_2 &
alsaplayer -o jack -d system:playback_3,system:playback_4 &

```

provided that you have 4 ouputs, listed by jackd as system:playback_x
alsaplayer is all too ignored in general. It's one of the greatest audio players, doing reverse playing as well (useful sometimes ;) )

---

