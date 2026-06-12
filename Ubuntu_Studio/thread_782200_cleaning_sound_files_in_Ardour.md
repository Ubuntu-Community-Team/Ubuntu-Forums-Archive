---
title: "cleaning sound files in Ardour"
date: 2008-05-04
forum: Ubuntu Studio
---

### Post by Dark Horse on 2008-05-04
I Hope this is the right place for this question if not please move it to where it needs to be.
I have ubuntu studio installed and working.I have a collection of albums on vinyl I want to record to CD so they can be played again. I have figured out how to record into Ardour and I think I can burn a CD The Question I Have is what is the best plug ins to clean up these recordings Hiss,crackle,
pops,etc. The albums range from new to pretty rough. I could use some help with the best way to Clean up the resulting files before burning them to CD.
Any help would appreciated.
     Mark:D

---

### Post by alexforcefive on 2008-05-04
You'll want to use a stereo EQ plugin. [This page](http://ardour.org/files/manual/sn-plugins.html) shows you how to add a plugin to your audio track, and you might want to check out [the wikipedia article](http://en.wikipedia.org/wiki/Equalization) on the subject. Basically you'll want to cut out some of the higher frequencies to get rid of all the hissing noises. Try not to go overboard though! Keep checking your original signal by hitting the "bypass" switch on the plugin, to make sure you're not colouring the sound too much

---

### Post by Stochastic on 2008-05-05
No, no, no, don't go eq-ing out those problems.  It will only, at best, get rid of the hiss, and even then it's like using a sledgehammer to open a jar of tomato sauce; the files would be better off without it.

Check out Gnome Wave Cleaner (it's in the repos under the package name gwc) [http://gwc.sourceforge.net/](http://gwc.sourceforge.net/) and post back if you get confused with it, or run into any roadblocks.

---

### Post by Dark Horse on 2008-05-07
Thanks For both suggestions this is a project that has been under discussion since the first RWCD drive turned up locally.  I was looking into Linux as an alternative to Vista when I found Ardour then I discovered Ubuntu Studio and that was the deal maker. Now I have got Hardy up and stable (I Think) So now I have to learn how to use it. So any help or suggestions will much appreciated the ones that work for me will be adopted and passed on to others who are interested. I just down loaded GWC from the repository and I will give It a try asap. 
    Thanks again 
    Mark:)

---

### Post by Dark Horse on 2008-05-20
well I have been playing with the Gnome Wave Cleaner app you suggested still looks the right program but I have yet to get any sound out of it but sound in hardy is flaky any way I have found that some things work one time and not the next time and I don't know what changed or why Or I get something odd like choppy and or twice the speed it should be I have been thinking about moving this computer back to gutsy at least for a while. I like the newer version of Ardour Is there a way to install it in Gutsy through the repository?
   Mark  :)

---

### Post by Stochastic on 2008-05-20
> **Dark Horse said:**
> well I have been playing with the Gnome Wave Cleaner app you suggested still looks the right program but I have yet to get any sound out of it but sound in hardy is flaky any way I have found that some things work one time and not the next time and I don't know what changed or why Or I get something odd like choppy and or twice the speed it should be

Sorry to hear you're having that many troubles with hardy's sound.  GWC was able to give me sound no prob - as long as JACK isn't running.

> **Dark Horse said:**
> I have been thinking about moving this computer back to gutsy at least for a while. I like the newer version of Ardour Is there a way to install it in Gutsy through the repository?

Well yes and no.  The version in Hardy is 2.3.1, gutsy is 2.0.5, and the current release from ardour.org is 2.4.1.  So the easy thing to do would be to go to ardour's website and download 2.4.1 and install it (so yes, you can get the newer ardour).  But to get 2.3.1 you'll need to find it somewhere (source code or executable) other than the ubuntu repos as mixing repos (installing apps from hardy's repo onto a gutsy machine) is bad news (so no to getting 2.3.1 installed easily).

---

### Post by thorgal on 2008-05-20
> **Stochastic said:**
> Sorry to hear you're having that many troubles with hardy's sound.  GWC was able to give me sound no prob - **as long as JACK isn't running**.


run oss2jack at jack start and keep gwc's default setting (/dev/dsp). Works without any problem. That's how I also have youtube, flash crap, etc, working in my jack environment.

---

### Post by Dark Horse on 2008-05-29
> Well yes and no. The version in Hardy is 2.3.1, gutsy is 2.0.5, and the current release from ardour.org is 2.4.1. So the easy thing to do would be to go to ardour's website and download 2.4.1 and install it (so yes, you can get the newer ardour). But to get 2.3.1 you'll need to find it somewhere (source code or executable) other than the ubuntu repos as mixing repos (installing apps from hardy's repo onto a gutsy machine) is bad news (so no to getting 2.3.1 installed easily).

   That's the answer I expected I just wanted to make sure I hadn't missed something along the way I have been thinking about doing that ever since I noticed the version in Gutsy was not the most current version. Is therea tutorial somewhere that will walk me thru the steps to install from source code? I have never tried to do this before I am not real sure about where to start. Do I need to uninstall 2.3.1 Before I install the new version.(If I am going to do this then I will go for the latest stable version available.)
Time to learn something new!. :)


   > run oss2jack at jack start and keep gwc's default setting (/dev/dsp). Works without any problem. That's how I also have youtube, flash crap, etc, working in my jack environment.

That is a good thing to know I will try that soon as I can I will report back later about my success or lack of same. I have tried running Gwc both with and without jack. No success either way so far. :)
    Mark

---

### Post by Dark Horse on 2008-06-01
GWC is still not working for me (No sound ) Probably something simple that I am missing.  I have been working on installing a later version of ardour But I am kind of stumped about what to do next. this is the result of the last scons command I think I still need something but I am not sure where to look for it.
scons: Reading SConscript files ...
Checking for pkg-config version >= 0.8.0... yes
Checking for gthread-2.0... yes
Checking for lrdf... yes
Checking for libgnomecanvas-2.0... yes
Checking for gtk+-2.0... yes
Checking for jack... yes
Checking for samplerate... yes
Checking for glib-2.0... yes
Checking for libxml-2.0... yes
Checking for raptor... yes
Checking for fftw3f...yes
Checking for fftw3...yes
Checking for C header file fftw3.h... yes
FREESOUND support is not enabled.  Build with 'scons FREESOUND=1' to enable.
LV2 support is not enabled.  Build with 'scons LV2=1' to enable.
Congratulations, you have a functioning C++ compiler.
system triple: x86_64-unknown-linux-gnu

*******************************
detected DIST_TARGET = x86_64
*******************************

Checking for C header file fftw3.h... yes
Checking for usb_interrupt_write() in C library usb... no
Checking for C header file linux/input.h... yes
Checking for FLAC__seekable_stream_decoder_init() in C++ library FLAC... no
Checking for C++ header file boost/shared_ptr.hpp... no
Boost header files do not appear to be installed.
mark@ubuntustudio2:~/Desktop/ardour-2.4.1$ 
I am just lost any help about where to look for these last items and what do I need to do to finish this install. :confused:

Mark

---

### Post by Stochastic on 2008-06-01
> Checking for C++ header file boost/shared_ptr.hpp... no
Boost header files do not appear to be installed.

This seems to be where things stopped for the compiler.  I did a search of ```
apt-cache search boost | grep dev
``` and it turned up the package libboost-dev.  I'd put money on that being the required library you're missing.  Also, you may want to install libflac++-dev to get flac support.

---

### Post by Dark Horse on 2008-06-01
Yes it was there when I went looking for it. (when I got the right name 
right now I am up to : scons: done building targets.
I think I am ready to install? let me search the ardour website In case I missed something. Ithink the command is : scons-install ?
Mark

---

### Post by Dark Horse on 2008-06-01
It's installed and playing in the back ground as I type this.! :)  I found a tutorial at: [http://groups.google.com/group/studiob/web/building-ardour-on-linux](http://groups.google.com/group/studiob/web/building-ardour-on-linux)
would have been easier if I had found this sooner but I learned some things I probably wouldn't have other wise. when ardour starts I get a message about memory  Being locked Should I do something about that or can I safely ignore it?  I still have'nt gotten any sound from G.W.C. I think I might have a file  
mismatch some times I get a no recognized file message then G W C appears to load anyway the display shows the waveforms and the cursor travels over them like it was playing but no sound.
   Mark

---

### Post by thorgal on 2008-06-02
so you have not tried yet oss2jack ?
Because I have jackd running 100% of the time in my studio PC, that was the only way to get weird or deprecated apps to scream something in my speakers JUST because they use /dev/dsp and not jack natively. But if you really want to try oss2jack, I prefer warning you : it is tough to get up and running (kernel module to be compiled, etc).

---

### Post by Dark Horse on 2008-06-04
> so you have not tried yet oss2jack ?
Because I have jackd running 100% of the time in my studio PC, that was the only way to get weird or deprecated apps to scream something in my speakers JUST because they use /dev/dsp and not jack natively. But if you really want to try oss2jack, I prefer warning you : it is tough to get up and running (kernel module to be compiled, etc).

No I hav'nt I thought you were suggesting some changes in settings for jack I just googled oss2jack and it looks interesting I would like to give it a try When I get back to where I can Unfortunatly after I got ardour 2.4.1 running in gutsy sunday after about an hour the computer froze and I had to reset to get out of it I dont know what happened but I cant boot either hardy or gutsy on that system I have come to the conclusion that I will have to wipe the drive and reinstall.the only good thing is that I did not lose anything important. Ubuntu sha not been stable for me so I think that that I am going to try a different distro and see if it makes a differance. I noticed in another thread that you were running debian wich is one of three that I keep comming back to and probably the most user friendly of the bunch. I would like to hear any suggestions you might have on the subject.If you think it Should be handled off the forum you can email me directly at 
[email]ka5rzz@gmail.com[/email] :(  :)
   Mark

---

### Post by baltho on 2008-07-01
Hi all: I have the same problem as dark horse, all's well but no sound from GWC. With or without jack, I can cat a file straight down the throat of /dev/dsp (as the same user - it's not permissions) no problem. lsmod shows a ton of OSS modules, no problems there.
Everything except GWC works. The cursor scrolls as if it's playing, but there's no activity on the level meters at the bottom of the GWC screen.
Colour me baffled, people! Any thoughts?

---

### Post by baltho on 2008-07-11
Woohoo! It worked! I have no idea why, but I installed a vanilla Debian, added the usual jack, rosegarden, rezound, and still no sound from gwc. Then I went back to reloading my music library, installed amarok (as you do) and included the recommended packages (several of those, forget which ones, sorry...) and all of a sudden gwc is making noises! I have amarok but not jack running at the moment, just btw.

---

### Post by Dark Horse on 2008-07-29
Baltho,
 I am glad you found an answer that works. I am still having problems with random freezes so I have not been using studio very much lately. Although that problem seems to be getting better lately It is not gone but doesn't happen as often as it did month or so ago. I can start Amarok or Banshee and they will play maybe 5 minuets or less before it freezes.
Good luck.  :-k 
  Mark

---

