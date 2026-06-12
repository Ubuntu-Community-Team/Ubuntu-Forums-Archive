---
title: "vmWare Server 1.0.6/Ubuntu Host / Sound problem.."
date: 2008-08-05
forum: Virtualisation
---

### Post by dfrandin on 2008-08-05
I posted this on the vmware forums.. Got zero response.. 

I'm running vmware server 1.0.6 on Ubuntu 8.04, works swimmingly except for one major annoyance. A couple of the apps I need the vmware/XP virtual machine for, require sound to be working in vmware/XP guest. Now the rub.. when working on the system, I always have Audacious or Amarok open playing either local MP3s or shoutcast streams.. If I start a vm while doing this, I get a warning from vmware telling me the guests sound will start disconnected.. If I stop the music player then start the vm it usually works ok, and I'm able to restart the music player after the guest vm is up.. This was getting to be an annoyance, so I did a bit of checking and found that it was recommended to switch Ubuntu's sound back to alsa from pulseaudio as alsa "shared" between apps better.. It appears to be vmware that can't share, as I can run other Linux sound apps simulataneously just fine.. Is there a fix for this, or do I have to keep doing the workaround??

Dave

---

