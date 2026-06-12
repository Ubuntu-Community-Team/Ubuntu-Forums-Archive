---
title: "So Ubuntu 22.04 has a built-in screen recorder but it doesn't record audio"
date: 2023-12-06
forum: Ubuntu, Linux and OS Chat
---

### Post by SpaceManJack on 2023-12-06
Yeah the built in screen recorder in 22.04 only records the screen, it doesn't record the sound. I mean if it doesn't record sound then it's absolutely worthless to me! Are the developers really that lazy? Why would it not record sound? You know how frustrating it is to record something and then realize it has no sound? I guess that's what happens when you get a free product that you didn't pay for, beggars can't be choosers. Shame on them!

---

### Post by TheFu on 2023-12-06
> **scott130 said:**
> Yeah the built in screen recorder in 22.04 only records the screen, it doesn't record the sound. I mean if it doesn't record sound then it's absolutely worthless to me! Are the developers really that lazy? Why would it not record sound? You know how frustrating it is to record something and then realize it has no sound? I guess that's what happens when you get a free product that you didn't pay for, beggars can't be choosers. Shame on them!

Sorry that your expectations were different from everyone else's.  I don't have a fix for that, however.  Many times, people specifically do not want to record audio.  It is relatively easy to record audio at the same time using any number of other tools, like **audacity** or ffmpeg.  You'll need to sync the audio and video.  Remember those TV/Movie clapper bars at the start and end of every scene?  A/V sync is why they did that.  I mux TV recordings of my favorite sports team with the radio announcers play-by-play.  Getting the sync correct can take a bit, but usually there's a cannon at kickoff, so I have that point of reference.  Then I use mkvtoolkit to offset the audio, usually 30 seconds. A 30 second delay seems to be common.

[https://ubuntuhandbook.org/index.php/2022/05/record-desktop-with-sound-ubuntu-2204/](https://ubuntuhandbook.org/index.php/2022/05/record-desktop-with-sound-ubuntu-2204/)

I've been using SimpleScreenRecorder for 5+ yrs. It is exactly what it claims to be.  A simple, screen, recorder.  Of course, it doesn't work with Wayland, just X11, so YMMV.  I only use it when no other method works.

---

### Post by monkeybrain20122 on 2023-12-06
I find kazam the best. [https://github.com/henrywoo/kazam/issues](https://github.com/henrywoo/kazam/issues) . It works on Ubuntu22.04 after some tweaking and no need to install.

---

### Post by SpaceManJack on 2023-12-17
> **TheFu said:**
> Sorry that your expectations were different from everyone else's.  I don't have a fix for that, however.  Many times, people specifically do not want to record audio.  It is relatively easy to record audio at the same time using any number of other tools, like **audacity** or ffmpeg.  You'll need to sync the audio and video.  Remember those TV/Movie clapper bars at the start and end of every scene?  A/V sync is why they did that.  I mux TV recordings of my favorite sports team with the radio announcers play-by-play.  Getting the sync correct can take a bit, but usually there's a cannon at kickoff, so I have that point of reference.  Then I use mkvtoolkit to offset the audio, usually 30 seconds. A 30 second delay seems to be common.

[https://ubuntuhandbook.org/index.php/2022/05/record-desktop-with-sound-ubuntu-2204/](https://ubuntuhandbook.org/index.php/2022/05/record-desktop-with-sound-ubuntu-2204/)

I've been using SimpleScreenRecorder for 5+ yrs. It is exactly what it claims to be.  A simple, screen, recorder.  Of course, it doesn't work with Wayland, just X11, so YMMV.  I only use it when no other method works.

You seriously think it was ok for the developers to not include sound in the built-in screen recorder with 22.04LTS?????

---

### Post by TheFu on 2023-12-17
> **scott130 said:**
> You seriously think it was ok for the developers to not include sound in the built-in screen recorder with 22.04LTS?????

Yep.  Audio is very, very, different from video. It is a completely different skill-set.  The video guys were more concerned about supporting Wayland video than 3 different, popular, audio engines.  I suppose time ran out on them.  A working "something" is better than a non-working "nothing".  

Canonical isn't the Gnome project.  They don't control what Gnome does or doesn't do.  Both teams have their own timelines to meet.  Canonical releases happen in April and October. We count on this. Business customers, who are PAYING, count on this.

Canonical has decided that the Gnome and Wayland projects are their way forward.  If you disagree, feel free to chose X/Windows and all the tools there that will do what you need, like SimpleScreenRecorder.  22.04 still supports X/Windows as the display manager.  You have a workaround - so do I.  Wayland breaks many of my workflows. That's life. 

If I cared THAT much, I could learn and code a solution.  For the next few releases at least, I cannot use Wayland.  I've been waiting since 2017 for them to fix a bug/feature they don't consider as important as I do. I have doubts that it will ever be fixed. 

My last desktop upgrade happened last March. I stopped using Ubuntu desktops then and moved to Linux Mint to avoid snaps and Wayland.  My servers are still mostly Ubuntu, with a few debian installs.

We have a choice. If a distro doesn't fit your needs, there are 50 others.  Mint isn't perfect either.  I'm still not happy with systemd being forced onto the world.  If I cared THAT much, I'd have switched to a distro that doesn't use systemd, like perhaps MXLinux.  Perhaps next year.  That's just desktops. For servers, I find Ubuntu to be the best mix of stable, yet new, software.  Debian is sometimes TOO new or TOO old. Sigh.  

People are always changing things.  I miss Ubuntu 10.04 - perhaps the best OS ever created. It did everything expected, like a good Linux distro should. No surprises.

---

