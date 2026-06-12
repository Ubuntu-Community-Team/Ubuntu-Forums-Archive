---
title: "FL Studio issues"
date: 2012-10-02
forum: Ubuntu Studio
---

### Post by DKA Productions on 2012-10-02
Hi guys I've been a Linux user off and on for the last few years but finally made a complete switch to Ubuntu Studio 12.04 3 weeks ago. One of the problems I'm having is with my audio production software FL Studio. The install went great and all of my plugins, Vst's work in it as well. The issue I'm having is when I try to upload previous songs that I have started when I was using windows. They load fine but the playback goes to hell. Was wondering if anyone else has had this problem or if there is a way around this. 

Thanks in advance

---

### Post by Bufeu on 2012-10-02
Do you run FL Studio through Wine? Ty running it in a VM instead.
If you want a free, Linux alternative to FL Studio, take a look at [LMMS]("http://lmms.sourceforge.net/") or [Jokosher]("http://www.jokosher.org/").
More alternatives here: [http://alternativeto.net/software/fl-studio/?platform=linux](http://alternativeto.net/software/fl-studio/?platform=linux).

---

### Post by DKA Productions on 2012-10-02
Yes i'm running it through wine. I've been seeing a few post on the web on it working but no one goes into depth as to how they did it. Its really bugging me  considering most of these song are almost complete and dont really have time to start using an alternative

---

### Post by Bufeu on 2012-10-02
As i said, try running FL Studios inside a VM instead.

---

### Post by CrocoDuck on 2012-10-02
Hi. Maybe I had a stupid idea/thought... but sometimes those kind of things works. How about loading a session you saved with your "wine-FL"? Does it ruins the playback again? If things go better using "wine-FL" saved sessions, you could load your "windows-FL" sessions, save them again in another place, close "wine-FL", relaunch and reload the new one.

---

### Post by Elfy on 2012-10-02
*Thread moved to **Ubuntu Studio**.*

---

### Post by DKA Productions on 2012-10-02
I took both of your advise. Tried running in VM and still had the same issue. Also tried to create a new song, then saving it and reopening it up. Like I said before the audio playback getst distorted after the first couple of seconds of playback. Been hear a bunch about wineasio and was wondering how to install that.

---

### Post by DKA Productions on 2012-10-02
In other words when I upload the new/old project it makes my CPU jump back and forth. Never had that issue before. Any advise

---

### Post by CrocoDuck on 2012-10-03
Wineasio is a cool tool, I used it with some NI program (Guitar Rig and Bandstand) that I don't need anymore. You can download a wineasio deb from there: [http://sourceforge.net/projects/kxstudio/files/DEBs/repo/](http://sourceforge.net/projects/kxstudio/files/DEBs/repo/) . Here a thread that could help you: [http://ubuntuforums.org/showthread.php?t=2001698](http://ubuntuforums.org/showthread.php?t=2001698)

---

### Post by sgx on 2012-10-04
Hi, try to insure every bitrate and buffer size is uniform
in all the software used. I'm curious how vsts work in FLS,
without a chosen asio driver? What is selected in the
preferences for asio? Wineasio is the linux standard, and shows
as a choice in various windows DAW preferences.

If it does not work, there is a very long FLS thread here to study,
and in the meantime, I would render an FLS track as wav file,
import it into audacity, export from audacity as wav,
then try loading in various DAWs.

If you can load the exported files in reaper, but not back
into FLS, you'll have to weigh your options, and workflow.
Reaper has never posed such an issue, during many happy
years of usage. 
Cheers

---

