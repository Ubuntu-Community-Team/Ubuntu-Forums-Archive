---
title: "[SOLVED] FLAC audio in Windows...?"
date: 2008-02-03
forum: Windows
---

### Post by gobbles414 on 2008-02-03
Hi all,

In Ubuntu 7.10, I am able to play FLAC audio files and  convert them "on-the-fly" for use with my iPod using the Banshee Music Player. Is there a similar program for Windows?

**BACKGROUND (IF YOU CARE)**
My fiancée had an Apple iBook, which recently died a very horrible death. She is going to use my Ubuntu-based laptop for a few months while she saves some money for her own new laptop. Meanwhile, I will be using my Windows Vista desktop computer. I cannot install Ubuntu on my desktop because its shard graphics hardware is not very well supported in Linux, due to a lack of support from the hardware manufacturer.

Thank you all in advance! :)

---

### Post by cozmicharlie on 2008-02-04
There are a number of decoders that can convert flac.  You did not mention what format you are using in your ipod so I will assume you convert the flac files to mp3.  In Ubuntu you have many options.  Make sure you have the gstreamer plug ins, flac codecs and the mp3 codecs installed.  Then you can use a number of programs. I personally use SoundKonverter (yes it is a kde program but it works fine in Ubuntu) for decoding/encoding, Exfalso (for tagging) and gtkpod for managing my ipod.  All of these are in Synaptic (the Ubuntu package manager) so they are easy to install.  PACPL is probably the best encoder/decoder I have used but it is a command line program and coming from Windows, you may want to stick with programs that have a gui interface until you get more experience in Ubuntu.  Amarok is an excellent program that is integrated with SoundKonver.  This thread has a lot of good info and should help [http://ubuntuforums.org/showthread.php?t=103071&highlight=gstreamer/](http://ubuntuforums.org/showthread.php?t=103071&highlight=gstreamer/)

---

### Post by tbroderick on 2008-02-04
> **gobbles414 said:**
>  Is there a similar program for Windows?


foobar2000 or you could use any number of audio converters like dBpoweramp.  The people behind dBpoweramp also make Sveta Portable Audio which does what you want.

---

### Post by gobbles414 on 2008-02-04
Hi cozmicharlie,

Thanks for your reply. **But I already know how to use my FLAC files and my iPod in Ubuntu!** I use the Banshee Music Player for both of these tasks. Banshee is a native Linux program.

**What are my options for managing my FLAC files and my iPod from a single Windows music program?** I would like to avoid converting my FLAC files to another format if possible, because I am only going to be using Windows for a few months. After those few months have passed, I will be able to switch back to Ubuntu again. Please re-read the background details in my original post for more information.

PS: There are some conversations taking place on the internet about porting Banshee to Windows. But I do not think that Banshee for Windows is even an "alpha build" yet.

---

### Post by gobbles414 on 2008-02-04
Hi tbroderick,

Thank you so much. If it works, foobar2000 is EXACTLY the program that I will need. I will install it later today or sometime tomorrow. Then, I will report back. Thanks again. :)

---

### Post by gobbles414 on 2008-02-09
Hi all,

Sorry for the delay in my report...

Foobar2000 is working very well. I had to download a plugin for my iPod from [here]("http://yuo.be/ipod.php"). And on the advice of the Foobar2000 website, I did not download the Apple Lossless plugin for Foobar2000. Instead, I used dBpoweramp to convert all of my Apple Lossless files to the FLAC format. Incidentally, dBpoweramp is apparently compatible with Linux through Wine!

My only question at this time regarding Foobar2000 is, how do I get the genre column to appear? It is not in the list of available columns; but I see that there is a way to create customized columns.

---

### Post by gobbles414 on 2008-03-23
> **gobbles414 said:**
> Hi all,

Sorry for the delay in my report...

Foobar2000 is working very well. I had to download a plugin for my iPod from [here]("http://yuo.be/ipod.php"). And on the advice of the Foobar2000 website, I did not download the Apple Lossless plugin for Foobar2000. Instead, I used dBpoweramp to convert all of my Apple Lossless files to the FLAC format. Incidentally, dBpoweramp is apparently compatible with Linux through Wine!

My only question at this time regarding Foobar2000 is, how do I get the genre column to appear? It is not in the list of available columns; but I see that there is a way to create customized columns.

I was able to get the genre column to appear by going *File => Preferences => Display => Default User Interface => Playlist View => Custom Columns*. I used the name *Genre* and the pattern *%genre%*.

---

