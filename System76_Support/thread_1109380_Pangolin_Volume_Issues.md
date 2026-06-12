---
title: "Pangolin Volume Issues"
date: 2009-03-28
forum: System76 Support
---

### Post by christophermluna on 2009-03-28
Hey there,

I've got a Pangolin Performance, panp4 running Ibex.

I've had a recent strange audio problem.  Sometimes, the volume totally cuts out.  At first, I thought that it only happened after muting.  I.e., I would mute the laptop, and then turn the volume back up, only to have it stay silent, but now I'm not sure.  I think it just happened without me muting.

In any case, it's pretty frustrating.  A restart fixes the problem, but I'm wondering if there's anything I can do to troubleshoot it?

Thanks in advance!
~Luna

---

### Post by thomasaaron on 2009-03-28
Please provide a little more detail about what you are doing? What app are you running when it died?

Also, are you running more than one app that need the sound card? If so, you may be running into a conflict.

---

### Post by christophermluna on 2009-03-29
Hey there, Thomas

I will pay close attention the next time it happens.  So far, it has been hard to isolate, because it doesn't seem to be just one app.

The most common occurrence would be running Firefox, and sometimes VLC at the same time.

I know that there have been times that I've muted the computer through the keyboard (Fn+F5) until the volume is totally down, surfed the web for a while, and then wanted to play a video on YouTube or something, so I turned the volume back up with the keyboard; the computer still wouldn't produce sound.  To be sure it wasn't a problem with Firefox, I have then opened other applications and tried to play sound.  I have tried to play music with Amarok, tried to play videos with VLC, etc.  But once the volume is in this state, the only thing that seems to bring it back is a reboot.

I am only sure that it has happened while using Firefox.  I will pay more attention and let you know if it happens with other apps.  But since I am muting the computer with the keyboard, I don't know if it has to do with the apps.

I should also note that I'm getting a "beep" that wasn't there before when I shut down.  It's like a system beep or something, totally unrelated to the volume level, that happens when I'm on the black screen before the Ubuntu logo and scroll bar show up on shutdown.

~Luna

---

### Post by thomasaaron on 2009-03-29
Sounds like conflicting apps is probably the issue. See if you can figure out how to reliably re-produce the problem. I've tried a few things with no luck.

As or the beep, see this thread...
[http://ubuntuforums.org/showthread.php?t=1093128&highlight=system+beep](http://ubuntuforums.org/showthread.php?t=1093128&highlight=system+beep)

---

### Post by christophermluna on 2009-03-30
It's driving me a little batty, but I am having a hell of a time trying reliably reproduce this.

Last time it happened when I hibernated by closing the lid and came back by opening it.

The time before that, it just stopped working between two different mkv files I watched with VLC.

I will keep experimenting.  The one thing I am fairly confident of is that it's not a hardware problem (at least not with the speakers).  Although the system beep is annoying, the fact that the laptop beeps at me every time I restart assures me that the speakers are working before the reboot.

~Luna

---

### Post by christophermluna on 2009-04-01
Okay, well I have something.

On a fresh restart, I got sound for the loading of the OS-- the drums and buzzing default OS load sound.

Then, I started Firefox, Skype and Pidgin.  In the case of the latter two, I only logged in.  I didn't make any calls or do any chatting.

The first thing I did on Firefox, was look up a movie trailer, which was played with a Flash movie player, I think.  No sound, and the embedded player was not muted.

Just to test, I opened up VLC and played a movie file.  No sound.

I hope that this narrows it down somewhat.  I am running Firefox version 3.0.8.  I don't know how to check the version of my embedded Flash player.

Let me know if there's something I can do to narrow it down from here.

~Luna

---

### Post by thomasaaron on 2009-04-01
Run these commands...

sudo apt-get --purge remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

See if that fixes it.

Your set-up is pretty much what I use every day, though, and I don't experience the problem.

What is the link of the movie trailer. I'm guessing it wasn't on youtube. It could be that there is something amiss with their site.

---

### Post by christophermluna on 2009-04-01
It was YouTube.  I wonder if it might be something off with the Flash plugin, still.  I'm reinstalling and will update you on whether the problem recurrs.

Either way, the problem has definitely occured when I wasn't using YouTube.

~Luna

---

