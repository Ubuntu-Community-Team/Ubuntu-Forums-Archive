---
title: "Simple MP3 editor required"
date: 2008-10-11
forum: Ubuntu Studio
---

### Post by DoctorBeaver on 2008-10-11
I want to extract portions from MP3 tracks and save them as separate files. Is there a simple program that I can use?

I've got Audacity but it won't play anything - I get a device & sample rate error.

---

### Post by eye208 on 2008-10-11
mp3splt is a program to split MP3 files without sacrificing quality by re-encoding them.

[http://mp3splt.sourceforge.net/](http://mp3splt.sourceforge.net/)

The command line version is in Ubuntu's repository, but you probably want the GUI version as well. The download section has .deb files for Ubuntu.

---

### Post by DoctorBeaver on 2008-10-11
Thanks, I'll give it a go.

---

### Post by simtaalo on 2008-10-11
i'd recommend sweep, worked with my onboard soundcard without any need to setup, its in the repo's or if you really want the latest version goto [http://www.metadecks.org/software/sweep/](http://www.metadecks.org/software/sweep/)

---

### Post by tgalati4 on 2008-10-11
Sox is another music file pocket knife.  Audacity is the defacto tool for this kind of task.  When you run audacity in a terminal, what errors come up?  What version of Ubuntu?

---

### Post by DoctorBeaver on 2008-10-12
Tgalati4 - I don't run Audacity in a terminal. I run it from the Applications -> Sound & Video -> Audio Production menu.

I load an MP3 for editing and when I try to play it I get the message:-

**Error while opening sound device. Please check the output device settings and the project sample rate.**

I've checked the sound card and set the Audacity Preferences to it. My sample rate is set to 44100.

---

### Post by DoctorBeaver on 2008-10-12
Simtaloo - thank you, I'll try it.

---

### Post by eye208 on 2008-10-12
Note that Audacity, Sweep and others will re-encode after editing. This will degrade audio quality because compression artifacts add up. If all you want to do is cut MP3 files, mp3splt is the best option because it works in a lossless fashion.

---

### Post by Bungo Pony on 2008-10-12
You can also get wavbreaker which I believe is in the repos:

[http://wavbreaker.sourceforge.net/](http://wavbreaker.sourceforge.net/)

---

### Post by DoctorBeaver on 2008-10-13
Bungo - wavbreaker doesn't do MP3s

---

