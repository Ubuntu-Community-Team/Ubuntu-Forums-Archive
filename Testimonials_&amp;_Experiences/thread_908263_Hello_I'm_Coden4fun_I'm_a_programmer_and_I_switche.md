---
title: "Hello I'm Coden4fun I'm a programmer and I switched to Ubuntu"
date: 2008-09-02
forum: Testimonials &amp; Experiences
---

### Post by coden4fun on 2008-09-02
Hi, I'm announcing to the world that a .Net Developer has switched to Unix FOR GOOD!

And since I've switched to Unix in one day I would like to tell the usual Ubuntu developers/users what I have done in my spare time to run Ubuntu.

I downloaded and installed Ubuntu (with Ease)

I downloaded Pulse and got my Eclipse profile back in Unix form (with Ease)

I downloaded Pidgin, and other apps I couldn't live without through the Synaptic Pack Manager (with Ease)

However, when I installed and started using RealPlayer (wasn't easy, nor satisfied).

Now I know I have downloaded the mp3 codecs through realplayer, but I can't find the realplayer music library, so I can't sort, search, or organize my music collection, nor can I use Banshee, or Rhythmbox(cough coough lame way of imitation iTunes cough cough) to playback mp3 files, so I have a catch 22.

All music is .mp3 I tried a shell run to convert all mp3 to .ogg, but that was an Epic fail as I'm a first time Ubuntu user, and anytime I run RealPlayer11 I must run in terminal before it pulls up the GUI, and I can only open one file at a time.

RealPlayer is also in the launch menu under Sound and Video, however, when I try to pull it up I get an error "Fail to execute child process"

So... what is one like me to do to solve my mp3 problem?

I don't care what player I use long, or what codec I use long as I can listen to my music.

Thanks,

---

### Post by Joeb454 on 2008-09-02
Moved to Testimonials & Experiences :)

---

### Post by forger on 2008-09-02
Here's a list of all my codec-related packages:
```
sudo apt-get install lame vorbis-tools flac ffmpeg liblame0 gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse libdvdread3 gstreamer0.10-x gstreamer0.10-fluendo-mp3
```
You can then play your mp3 in rhythmbox or banshee (Applications > Sound & Video)

---

### Post by Teamgeist on 2008-09-03
Easier would have been ```
sudo apt-get install ubuntu-restricted-extras
``` with this you also get MS-fonts, the flash plug-in, etc

Here is the official description:

[I]Paket: ubuntu-restricted-extras
Zustand: Installiert
Automatisch installiert: ja
Version: 15.2
Priorität: optional
Bereich: multiverse/metapackages
Verwalter: Michael Vogt <michael.vogt@ubuntu.com>
Unkomprimierte Größe: 32,8k
Empfiehlt: flashplugin-nonfree, gstreamer0.10-ffmpeg, gstreamer0.10-plugins-bad,
           gstreamer0.10-plugins-bad-multiverse, gstreamer0.10-plugins-ugly,
           gstreamer0.10-plugins-ugly-multiverse, icedtea-gcjwebplugin,
           libdvdread3, liblame0, msttcorefonts, sun-java6-jre, unrar

Beschreibung: Commonly used restricted packages

 This package depends on some commonly used packages in the Ubuntu multiverse
 repository. 
 
 Installing this package will pull in support for MP3 playback and decoding,
 support for various other audio formats (gstreamer plugins), Microsoft fonts,
 Java runtime environment, Flash plugin, LAME (to create compressed audio
 files), and DVD playback. 
 
 Please note that packages from multiverse are restricted by copyright or legal
 issues in some countries. See [http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing) for more
 information.[/I]

So you should install that package anyway. You can also do so with the Synaptic-Package-Manager under System--> Administration.

Also you should take a look at [www.medibuntu.org](www.medibuntu.org) for encrypted DVD-Playback.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
and ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```


So have fun.

---

### Post by ronnielsen1 on 2008-09-03
> However, when I installed and started using RealPlayer (wasn't easy, nor satisfied).
I've never got this one to work. AmaroK works great - a little resource hungry. (I'm used to Kde)
Welcome to Linux. It only gets better

---

### Post by 3rdalbum on 2008-09-03
> **coden4fun said:**
> Hi, I'm announcing to the world that a .Net Developer has switched to Unix FOR GOOD!

Congratulations! I hate to sound picky, but Linux is not Unix - just ask any Unix fan :-D

If you haven't done so already, you want to learn Python - it's quicker to write and debug than C# and is more "native" to Linux, especially to Ubuntu.

---

### Post by coden4fun on 2008-09-04
Thanks for all the help, and I'm currently downloading and will install Amarok.

---

### Post by Crafty Kisses on 2008-09-05
Hey coden4fun! 

Sounds like after you install those packages you'll be on your way, and hopefully your stay with Ubuntu will be a good one!

---

