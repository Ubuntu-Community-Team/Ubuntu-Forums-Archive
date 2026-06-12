---
title: "No desktop after install"
date: 2009-03-18
forum: Ubuntu Studio
---

### Post by mdharp on 2009-03-18
How do I get a desktop on Ubuntu Studio 8.04.1 ???
5th attempt (yes, that is five over many days) at installing Ubuntu Studio. 
Still no desktop, only getting text which asks for username, then password (entered & OK) then sits there waiting for me to type something in. All media programs & Ubuntu Studio desktop install options were done at install.
Dual boot system that runs great with WinXP & Hardy 8.04, but can't get Mackie Onyx firewire soundcard to run on Hardy with Ardour, jack or Reaper.
Tried Ffado FW driver install, but copy & paste install instructions for command line didn't work. 
Studio was recommended to get FW Onyx audio "in".

Tried amd64 iso for my AMD 64 x2 system, & i386 version for better compatibility. 25 + hours of downloads - (*%#!^)
Tried all recovery mode &/or repair options - still nothing.(*%&^@#$!!)

Then tried command line startx, response = not installed, then followed prompt > sudo apt-get xinit, which started a download, then reboot > log on > command startx, again nothing, now installed but no response.
Then tried Cntrl>Alt>F7 to bring up graphic display -
nothing again [^&*%$#^&%#!!!]:(

Ubuntu Studio web page links to here for support - so how about some support from the guys at Ubuntu Studio ???

My system = amd x2 64 (939 chipsets) +3800 cpu, 4GB RAM DDR400, Gigabyte NVidia Grfx card, Gigabyte MoBo GA-K8N-ProSLI

---

### Post by Stochastic on 2009-03-18
Hmm, sounds like you should [file a bug on launchpad.net against UbuntuStudio]("https://launchpad.net/ubuntustudio-project/+filebug") describing your inability to get past the graphic login.  That's the best way to get the issue fixed.

But as a quick fix, you really don't need to install UbuntuStudio via a new iso install, it is essentially just a bunch of metapackages that are installed over the base Ubuntu.  So, if you already have a successful Hardy install you can just install the UbuntuStudio metapackages.  For a list of them do ```
apt-cache search ubuntustudio
```  One of the main items is the linux-rt kernel that is inside the ubuntustudio-audio package.  That should fix up whatever "ubuntustudio install" issues you were having.

I have a gut feeling however, that your audio card issues won't be solved by having UbuntuStudio rather than Ubuntu.  I'll gladly help you along with getting ffado running, but not in this thread.  Please start a new thread with that as the subject (so others know what's inside) and link to it here.  I should make a note that ffado is not officially supported by ubuntustudio on any release earlier than Jaunty (coming in April) but I have managed to get it working.

---

### Post by mdharp on 2009-03-18
First, thanks for responding, & for your offer of assistance.
I was hoping Ffado would be in the current studio version 8.04.1.
I have had some more feedback about getting Ffado to install first, which looks more detailed than installer notes in Ffado tar package. Then install jack after, so it sees Ffado driver for Onyx FW mixer, then Ardour, Reaper (via LinReaper maybe) in Wine which I had working quite well with midi - vst/i etc, except for no audio input.

Would it work to allow Hardy the upgrade option from iso CD ??
Cheers

---

### Post by Stochastic on 2009-03-18
> **mdharp said:**
> Would it work to allow Hardy the upgrade option from iso CD ??
Cheers

Quite possibly, but I've never tried that method.

If you're worried about downloading times, you could add the CD as a repository then install the packages you want.

Oh, and Hardy does have freebob drivers that are supported and are the earlier version of the ffado drivers (but I'm not sure if freebob supports the Onyx).

---

### Post by mdharp on 2009-03-18
Freebob was on Hardy, but couldn't see Onyx, hence need for Ffado.
Got more info from 
[http://osdir.com/ml/ubuntu-studio-users/2009-01/msg00089.html](http://osdir.com/ml/ubuntu-studio-users/2009-01/msg00089.html)
Cheers

---

