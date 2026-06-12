---
title: "sfxload crashes ubuntu"
date: 2008-08-10
forum: Ubuntu Studio
---

### Post by phil the dill on 2008-08-10
Hi,

I'm new to UbuntuStudio stuff (running Ubuntu 8.04), but I've discovered that sfxload is used to load a soundfont (.sf2) into my SoundBlaster Live's hardware wavetable. I've done it successfully with lots of soundfonts, and been able to play the sounds on my computer from my external midi keyboard. I would prefer to have my soundcard do the processing rather than my cpu, which is why I've been using sfxload.

Unfortunately I've found that attempting to load some soundfonts with sfxload (or asfxload) causes my computer to immediately lock up or reboot. The same soundfonts load without a problem into QSynth and can be played there. The size of the soundfont isn't a factor - I have 128 mb of memory on my soundcard and some of these soundfonts are only 20 mb. The crash happens regardless of what other software is running, whether JACK is started or not, whether my midi keyboard is attached, or any other factor that I've been able to check.

Is this a bug in sfxload, or the soundfont, or Ubuntu? Any ideas for how to fix this? 

(To be honest, I was surprised that Ubuntu could be made to crash this easily - I'm new to Linux and I've always heard that it's very stable. But if simply trying to load a soundfont causes a complete system crash then it appears to be quite fragile. No flames please, I'm just expressing my surprise at a situation that contradicts my expectations.)

---

### Post by Stochastic on 2008-08-11
Nothing's perfect.
If the system is locking up, I'd hedge my bets on it being a bug related directly to the kernel, but originating from sfxload - I'm not terribly educated in kernel matters so take this with a grain of salt.  The RealTime-patched kernel that UbuntuStudio is running is a relatively new kernel in the Ubuntu world (once again I'm no kernel expert), so you may have found a new bug.  It's most likely some misstep by sfxload so the best place to start your research is Launchpad.net at the bug listing for the awesfx package (here: [https://bugs.launchpad.net/ubuntu/+source/awesfx](https://bugs.launchpad.net/ubuntu/+source/awesfx)) and if your problem isn't described accurately by any of the listed bugs; sign up/in and make a new bug.  If it looks like it's a bug specific to UbuntuStudio (i.e. happens in direct combination with the realtime kernel but not the vanilla kernel), then you should post the bug to [UbuntuStudio Launchpad bug listing]("https://bugs.launchpad.net/ubuntustudio-project").

Launchpad is the official bug filing system for Ubuntu, so this is the best place for you to alert developers of the issues you encounter.  Here is a handy doc on how to report a bug in UbuntuStudio: [https://help.ubuntu.com/community/UbuntuStudio/ReportingBugs](https://help.ubuntu.com/community/UbuntuStudio/ReportingBugs)

This issue could also be a soundcard model issue, and I know Creative (the company behind SoundBlaster) hasn't always been the best at allowing open source developers access to its card specs.  But now I'm just speculating.

Anyways, welcome to the world of Linux.  It generally is quite stable around here, but every now and then you'll find a bug that can crash things or annoy your pants off. ;)

---

### Post by phil the dill on 2008-08-11
Stochastic: 

Thanks for the advice. The crash occurs using either the realtime or generic kernel, and I can load and use the soundfont in other midi software in Ubuntu (and in Creative's Soundfont utility in Windows) so I guess that points to a bug in awesfx.

I couldn't find any similar bug at the awesfx launchpad site you referred me to (there were only 4 bug reports in total, making it easy to check) so I've created a bug report for this problem.

---

### Post by Stochastic on 2008-08-11
Well it sounds like its a problem that can be worked around for now.  It's good to hear that a valid bug report has been filed - that's how this bug will eventually get fixed.  The launchpad system can be a bit sluggish sometimes (as a means of resolving bugs) but the only other route is to get onto the software (awesfx in this case) development channels (mailing lists and IRC channels) and complain in person to the developers (though this is not the recommended way to deal with new bugs).

---

