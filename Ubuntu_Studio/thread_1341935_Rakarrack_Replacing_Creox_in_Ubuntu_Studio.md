---
title: "Rakarrack Replacing Creox in Ubuntu Studio"
date: 2009-11-30
forum: Ubuntu Studio
---

### Post by Scott L on 2009-11-30
The Ubuntu Studio developers are considering replacing Creox with Rakarrack as a default application in Ubuntu Studio.

Creox has not had any development in years while Rakarrack continues development through this year.

Let's hear your opinion.

---

### Post by dawiba on 2009-11-30
It gets my vote

---

### Post by transmogrifox on 2009-11-30
I just joined the rakarrack team recently.  Of course it is good news that there is consideration to include rakarrack in Ubuntu Studio.    

For those wondering what's going on:
Rakarrack is still under active development, and a version 0.4.0 does not appear to be far off.  We would appreciate help from those who like to compile from CVS in the way of beta testing, and even submitting some of your own presets.  Of course, bug fixes and code are welcome.  

Here are some of the highlights I see that rakarrack users can look forward to using in the next release:
--More MIDI support

--New distortion from ZynAddSubfx.  This is an fft based distortion.  I have spent only a small amount of time reviewing this code, but it looks like it adds harmonic distortion in the frequency domain, then inverse transforms the signal to the time domain -- that tidbit for those who have a technical bent.  In more practical terms, it has promise for generating truly harmonic distortion without the typical non-musical side-effects of traditional clipping.  For even the less technical, "it's different and you gotta try it".

--There is a new phaser effect, "Analog Phaser", based upon basic building blocks found in analog phaser circuits.  It combines features of many different circuits, but the primary inspirations were the MXR Phase 90, and Ibanez AP7 as well as a Ross OTA phaser, just to name a few.  You can download some audio samples recorded from the alpha version on my blog, rakahack.blogspot.com.  I will be posting some more from a more current build, which adds the hyper-sine modulation wave form, which sounds much more natural (IMHO).

--Reverb will likely see an update as I was recently informed by one of the project members from ZynAddSubFX that Paul Nasca has made improvements to the reverb since what has been integrated into Rakarrack.

--Reverse delay.  A prototype is running on my development machine right now, and just needs some minor finessing before committing to CVS.

--Compressor re-write:  strange things were happening around the compression threshold in the original code.  Along with compressor re-write, some features were added: adjustable knee for more flexibility.  In all truth, the adjustable knee is subtle for guitarists, but it seems to be a really nice feature when rakarrack is used with Hydrogen or recorded drums/percussion.  Another feature was further development on the Auto function. Auto is not quite true to the traditional interpretation as it does not invoke limiting.  This check box enables automatic make-up gain calculation.  Otherwise, the compressor acts as a limiter about the threshold. 

For those who like to compile from source, you can get early (albeit possibly buggy or quirky) snapshots of any of my work from my blog mentioned earlier as I post code and audio samples.  I have not yet posted the reverse delay, but will probably upload it in the next day or two.

---

### Post by Scott L on 2009-11-30
transmogrifox,

Thanks for the great update!

---

### Post by kayosiii on 2009-12-01
This is a good idea, Creox has been broken for higher samplerates for me for years now.

Rakarrack at least works. I might say for me at least that I enjoy using it.

---

### Post by babarosa on 2009-12-01
Hello ScottL and transmogrifox,

I do not know Creox, and I am no UbuntuStudio user, but I am using Rakarrack  a lot on voice recordings - not as a guitar effects rack, please forgive me ;-)
I like especially the reverb and delay effects very much.
To my mind Rakarrack would be a valuable addendum to any multimedia distribution.

Thank you very much for this fine application.

Greetings,
Michael

---

### Post by sgx on 2009-12-01
> **transmogrifox said:**
> I just joined the rakarrack team recently.  Of course it is good news that there is consideration to include rakarrack in Ubuntu Studio.

snip
    

Thanks for working on this great software, it is one of the highlights of the linux world! I don't really need or want to use the commercial amp-sims any more, even though they are excellent products. I use rakarrack with hydrogen, Reaper output, zynaddsubfx, and guitars of course. I would rather see more stability, and uniform default levels in the presets, before new fx, it tends to disappear when jackd is stopped, and at times when other apps are connected or removed from jackd. But that may be old bugs, since I have a V3 vintage. If a V4 .deb, or rpm should appear, I can test a lot.

I would keep creox in the studio too, it is actually a good companion to rakarrack, and its gui is handy for certain practices.

Cheers

---

### Post by Drunky on 2009-12-01
> **sgx said:**
> Thanks for working on this great software, it is one of the highlights of the linux world! I don't really need or want to use the commercial amp-sims any more, even though they are excellent products. I use rakarrack with hydrogen, Reaper output, zynaddsubfx, and guitars of course. I would rather see more stability, and uniform default levels in the presets, before new fx, it tends to disappear when jackd is stopped, and at times when other apps are connected or removed from jackd. But that may be old bugs, since I have a V3 vintage. If a V4 .deb, or rpm should appear, I can test a lot.

I would keep creox in the studio too, it is actually a good companion to rakarrack, and its gui is handy for certain practices.

Cheers

The plan as it currently stands is that Rakarrack would be included in the default installation of Ubuntu Studio.

Creox would still be in the repositories and easily available as an "apt-get install", but just not installed during the Ubuntu Studio installation.

A .deb file for Rakarrack will not be available until after a sync with Debian later in the development cycle.

---

### Post by transmogrifox on 2009-12-01
> **Drunky said:**
> The plan as it currently stands is that Rakarrack would be included in the default installation of Ubuntu Studio.

Creox would still be in the repositories and easily available as an "apt-get install", but just not installed during the Ubuntu Studio installation.

A .deb file for Rakarrack will not be available until after a sync with Debian later in the development cycle.

That reminds me of some of the misunderstandings some users had about the GIMP being removed from default install of Ubuntu.  Thanks for clarifying, as I'm sure it may have been a question in the mind of U-studio's users whether Creox would be available in the repositories.  :)

 @barbarosa -- Rakarrack is tested by, and presets are aimed at, guitarists, but is also a very good engine for vocals and other instruments.  Most of the DSP effects come from the ZynAddSubFX synthesizer, and there is nothing that filters the out the low end by default.  It can be used with Bass, synth, trumpet...any instrument.  


@ sgx "I would rather see more stability, and uniform default levels in the presets, before new fx"
I agree.  I have been working on the DSP side of things, and will be putting some time into reviewing volume control between FX, as well as presets.  I actually got started working on the project because of this reason, and the main violator in all the presets was the compressor, so I dug into the source to figure out why, found the problem and fixed it.  Then I started to dream about the possibilities, and now there is an analog phaser emulator and reverse delay. ;)

The area of bugs and uniform default levels in presets is where you users can help.  Please visit the rakarrack sourceforge project page and leave comments in the forum, or bug trackers when you have a crash, or find an effect misbehaving.  It may be a little more effort to report what all was running, what you were doing, copying jackd log messages, and maybe an strace on rakarrack, but it will help us track down bugs.  Of course, this advice goes for any open source program you enjoy using.  The developers can be helped a lot by good bug reports.  The next step is to notify the Ubuntu package maintainer(s) so they can get an update into the repositories when a bug has been fixed.

You may submit presets, or just say  "preset xx is too loud and/or clips by default" or something like that. :)  Presets are really easy to fix.

I personally have not experienced any unexpected crashes, but I have been compiling most recent code base from CVS, so as mentioned above, they may be old bugs that have been fixed since 0.3.0.

---

### Post by kayosiii on 2009-12-02
> **babarosa said:**
> I do not know Creox, and I am no UbuntuStudio user, but I am using Rakarrack  a lot on voice recordings - not as a guitar effects rack, please forgive me ;-)


It also works great on the output of Hydrogen :)

---

### Post by AutoStatic on 2009-12-02
Ah, good to know :)
I've never used Creox and I like Rakarrack so I wouldn't mind .

---

### Post by l0wender on 2010-02-05
I also think that Rakarrack is a nice program, fully deserving to be in the UbuntuStudio repository. In fact, I was surprised it is still not there. Yesterday I had to compile it for my 64-bit Ubuntu installation. I am a software developer so it was not difficult for me to pinpoint the necessary library dependencies but I think we should not require musicians to compile stuff for themselves ;)

Thanks for this great app, BTW.

---

