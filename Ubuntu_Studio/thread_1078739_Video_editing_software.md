---
title: "Video editing software"
date: 2009-02-23
forum: Ubuntu Studio
---

### Post by justin10ec on 2009-02-23
Okay guys. This will keep me on Ubuntu or send me back to Vista right here. I need a good, easy to use video production software.

I need to be able to do the following:
[LIST]
[*]Import video (multiple formats)
[*]Make text appear on the screen
[*]Make transitions
[*]Export to formats that are compatable with YouTube
[*]Add background music
[*]Record the screen (I don't care if I would need an different program, if I do, please suggest a few).
[/LIST]

If there is anything that nears Vegas Pro or Camtasia Studio. I would prefer something similar. I love Ubuntu, so I am willing to settle for less, but it's important that I can do the above.

THANKS!!!!!

---

### Post by lukeiamyourfather on 2009-02-23
This might be of interest for the screen recording:

[http://www.linux.com/articles/38221](http://www.linux.com/articles/38221)

Recording VNC sessions works pretty good but would require another machine (or virtual machine). Cheers!

---

### Post by ouija on 2009-02-24
I too am looking for a good video editing program for linux, but have yet to find one.  I tried Cinelerra awhile ago but only for a short period as I found it a little more complicated than something like Vegas.   Are they any others out there of interest?

---

### Post by af20001 on 2009-02-24
Have you tried [Kdenlive]("http://www.kdenlive.org/users/j-b-m/kdenlive-072-released")?

---

### Post by ouija on 2009-02-24
Does that only work with KDE or will in run under Gnome as well?

Update: Nevermind, just going to install and see for myself :)

---

### Post by cotcot on 2009-02-24
Screen  capturing : [[COLOR="Red"]recordmydesktop[/COLOR]]("http://ubuntuforums.org/showthread.php?t=294605"); [[COLOR="Red"]istanbul[/COLOR]]("http://live.gnome.org/Istanbul").

---

### Post by justin10ec on 2009-02-24
> **af20001 said:**
> Have you tried [Kdenlive]("http://www.kdenlive.org/users/j-b-m/kdenlive-072-released")?

I just installed, but it's crashing when it starts (I think because I choose the wrong setting at startup)?

---

### Post by jag32266 on 2009-02-24
> **justin10ec said:**
> Okay guys. This will keep me on Ubuntu 

I need to be able to do the following:
[LIST]
[*]Import video (multiple formats)

!

Hey,

I'm just now downloading this Ubuntu Studio and don't know it's capabilities- thought you might give it a shot,,,

hth

[http://ubuntustudio.org/home](http://ubuntustudio.org/home)

Ubuntu Studio. A multimedia creation flavor of Ubuntu.

Ubuntu Studio is aimed at the GNU/Linux audio, video and graphic enthusiast as well as professional.

We provide a suite of the best open-source applications available for multimedia creation. Completely free to use, modify and redistribute. Your only limitation is your imagination. 

Video-PiTiVi, Kino, Cinepaint are included for video creation. We hope to provide a creative environment to people as well as give a spotlight to some amazing open-source applications.

Graphics-Graphic design and modeling applications including The GIMP, Inkscape and Blender. Along with plugins like dcraw to help with RAW camera files and wacom-tools for people with Wacom drawing tablets.

Audio-Our aim is to assemble suites of applications aimed at creative people. Suites including the best open-source applications available.

For instance, Ardour 2 - A multitrack recorder/editor geared toward people familiar with Pro-Tools.

---

### Post by kelvin spratt on 2009-02-24
Do you remember when you 1st tried Sony Vegas and thought what the #### i'll never learn this well Cinelerra is just the same

---

### Post by ouija on 2009-02-24
I *do* remember saying that regarding Vegas and how far I've come :p

However, I never really gave Cinelerra a chance... But I do like the looks of kdenlive, so I'm currently in the painstakingly long process of building and installing it piece by piece... (had issue with choppy sound when installing from the repository so hopefully this fixes that, which I read somewhere that it should)

I will post my results later and let you know how it went..

---

### Post by ouija on 2009-02-25
I installed kdenlive and am still having issues with stuttering audio during playback.  Rendering works great, and I love the layout of the application (very vegas-like!) so I would love to get it working 100%.   I tried changing the output settings within kdenlive preferences, but only Automatic or ALSA has sound that works, and both are choppy on playback.  

From my understanding, PulseAudio is the major player within Ubuntu Intrepid, however when I select this specifically there is no audio outputted at all.

I installed the pulse audio mixer and volume control, and noticed when I have the PulseAudio Playback Volume Meter loaded there is no output coming through as well (even when I set the preferences back to Automatic and the sound is working (but remember, choppy!) so I am curious as to how I can configure kdenlive to use PulseAudio, and is this maybe an issue related to the fact that kdenlive is running under Ubuntu Intrepid (and not Kubuntu)?  Is there a way to configre kde based applications to use pulse audio under Ubuntu/Gnome?

Any help would be greatly appreciated!!  Getting Kdenlive to work is basically the very last thing I'm looking for in a MICROSOFT-FREE computing environment!

Thanks!

---

### Post by ouija on 2009-02-25
Fixed my sound issues; Audio "stuttering" or "choppiness" is now completely gone.  I did this with help found at the kdenlive forum: [http://www.kdenlive.org/forum/kdenlive-under-ubuntu-intrepid-amd64-bit-and-gnome-choppy-audio-stuttering-problems#comment-2636](http://www.kdenlive.org/forum/kdenlive-under-ubuntu-intrepid-amd64-bit-and-gnome-choppy-audio-stuttering-problems#comment-2636)

Basically, Kdenlive uses SDL for sound, and Ubuntu Intrepid relies on PulseAudio.

Providing you are still using the Pulseaudio package within your Ubuntu setup; If not, install the "pulseaudio" package to follow these instructions.

Then you'll simply need to install the "pulseaudio-esound-compat" package and the "libsdl1.2debian-esd" package.

Then, open up the Terminal and enter the following: 
> $ export SDL_AUDIODRIVER=esd

Then try testing the sound using the command: 
> $ inigo myvideo.mpg

You should hopefully hear sound.  Then fire up Kdenlive and reconfigure your settings to use the proper output. I found that simply using the defalt settings within Kdenlive worked fine;  I had actaully erased my settings file (found under "~/.kde/share/config/kdenliverc") and then launched the Kdenlive program again to reconfigure.

And voila! Stuttering sound is a thing of the past!

Hope this is helpful for anyone else experiencing the same issue. :)

---

### Post by cotcot on 2009-02-25
> **ouija said:**
> I *do* remember saying that regarding Vegas and how far I've come :p

However, I never really gave Cinelerra a chance... But I do like the looks of kdenlive, so I'm currently in the painstakingly long process of building and installing it piece by piece... (had issue with choppy sound when installing from the repository so hopefully this fixes that, which I read somewhere that it should)

I will post my results later and let you know how it went..

Compile it yourself or use the [[COLOR="Red"]building wizard[/COLOR]]("http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/builder-wizard") from the kdenlive site

---

