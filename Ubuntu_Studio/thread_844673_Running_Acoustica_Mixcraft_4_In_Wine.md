---
title: "Running Acoustica Mixcraft 4 In Wine"
date: 2008-06-29
forum: Ubuntu Studio
---

### Post by aberk421 on 2008-06-29
Has anyone attempted to run Acoustica Mixcraft 4 in Wine?  It installs and opens for me without any problems, and even plays the included sample songs without any audible problems, but the controls and volume indicators all respond with a 2-3 second delay.

I'm running a Pentium 4 3.0 Ghz machine with 1GB RAM and using Wine 1.0 with the default Windows XP settings.  I have also toggled all of the video settings in winecfg and experienced no noticeable improvement.  I'm wondering if anyone with a faster system has seen an increase in peformance.  The fully functional trial version, which I am experimenting with, is available at [http://acoustica.com/mixcraft/](http://acoustica.com/mixcraft/).

I should add that I'm looking for a Garageband replacement for Ubuntu.  I have read a number of other postings and have tried a number of apps (Ardour, Jokosher, Rosegarden, Traverso).  I like bits and pieces of each of these apps (Joskosher being the closest to Garageband), but without simple VST support, adding a quick keyboard part to a song becomes a tedious task.  Having said that, any suggestions for other free/open-source DAW apps are greatly appreciated.

Thanks!

---

### Post by Stochastic on 2008-06-30
> **aberk421 said:**
> without simple VST support, adding a quick keyboard part to a song becomes a tedious task

VST support can be installed for most linux DAWs, but is a touch of work.  The issue stems from Steinberg's license on the VST SDK, which prevents it from being installed by default.  Take a look at the bottom of this page for more info on getting VST support: [http://linux-sound.org/plugins.html](http://linux-sound.org/plugins.html)  Here is an old how to I wrote on getting VST to work through fst on feisty: [http://ubuntuforums.org/showthread.php?t=557466](http://ubuntuforums.org/showthread.php?t=557466)

But even without VST support, adding a keyboard part to your songs really shouldn't be tedious; open a soft synth, hook up a midi keyboard (or virtual keyboard), hit record, and play away - insert sequencer instead of keyboard at your own discretion.

As for acoustica mixcraft in wine, I can't say I've ever needed wine for audio applications, so I can't offer any advice.

---

### Post by aberk421 on 2008-07-07
> **Stochastic said:**
> 

But even without VST support, adding a keyboard part to your songs really shouldn't be tedious; open a soft synth, hook up a midi keyboard (or virtual keyboard), hit record, and play away - insert sequencer instead of keyboard at your own discretion.

As for acoustica mixcraft in wine, I can't say I've ever needed wine for audio applications, so I can't offer any advice.

Thanks for your suggestions.  You encouraged me to keep searching for a suitable FOSS solution.  I ended up using a soft synth, as you suggested, by using the qsynth, fluidsynth, and jack setup with the free Hammersound SondFonts mentioned on this posting: [http://ubuntuforums.org/archive/index.php/t-485225.html](http://ubuntuforums.org/archive/index.php/t-485225.html).

After the initial setup, using a USB Midi Keyboard is a breeze--and the number of free instruments available is impressive.

---

### Post by Adavur on 2009-07-02
I've just installed Mixcraft through Wine. Worked quite nice, but a bit slowly though...

Do any of you know if there's any alternative to Mixcraft in Linux? Mixcraft is the Windows-alternative to GarageBand, but what about Linux?

---

### Post by sgx on 2009-07-02
> **Adavur said:**
> I've just installed Mixcraft through Wine. Worked quite nice, but a bit slowly though...

Do any of you know if there's any alternative to Mixcraft in Linux? Mixcraft is the Windows-alternative to GarageBand, but what about Linux?
Reaper is far and away the best audio app for linux. Version 2.56 is the one I use, but newer versions are worth testing  if you have modern hardware. You will need wineasio, and an hour or two to click menus and widgets, and vsts, and some blanck CDs to hold your new songs.
Cheers

---

