---
title: "Wild Dog - plugging in headphones does not mute speakers"
date: 2011-06-25
forum: System76 Support
---

### Post by ccrs8 on 2011-06-25
I have a Wild Dog Performance ( wilp8 ) running Ubuntu 11.04, and plugging in my headphones to the jack on the top of the computer case does not automatically mute my speakers.

I have run in to this problem a year or two ago on a Dell computer with earlier versions of Ubuntu, and the the solution was to enable jack sense by adding a line at the bottom of /etc/modprobe.d/alsa-base.conf that says:

options snd-hda-intel model=xxxxx

where 'xxxxx' is a particular value specific to the computer.  Once you add that line and reload alsa, you can go in to alsamixer and enable headphone jack sense by following these instructions:
[http://ubuntuguide.net/fix-sound-still-coming-from-speakers-after-plug-in-headphones-on-ubuntu-10-04](http://ubuntuguide.net/fix-sound-still-coming-from-speakers-after-plug-in-headphones-on-ubuntu-10-04)

Anyway, I can't figure out what to enter for 'xxxxx' for my Wild Dog Performance ( wilp8 ) computer to get the headphone jack sense option enabled in alsamixer.  Using 'auto' does not work, so I'll need a specific value.  Alsamixer reports my audio card as:
HDA Intel PCH
Realtek ALC892

The headphone jack does work, as I can manually send output to it using the sound preferences, and when I plug my headphones in I get sound out of them.  I just need jack sense to work.

Any ideas?

---

### Post by isantop on 2011-06-27
This is actually a known problem, and we believe it's a quirck of the sound system in desktop machines. Essentially, the sound system can't tell the difference between a set of speakers and the headphones. I'll look into it a little, but since this is expected, I'm not sure what all we can do. Is there a headphone jack on the speakers you can plug into?

---

### Post by halibaitor on 2011-06-27
This might be as simple as the manufacturer using the wrong jack for the audio.  It might not be a switching jack.

Manufacturers sometimes do goofy things, like Acer putting out laptops and netbooks with mono sound instead of the stereo that everybody expects.

---

### Post by juaninse on 2011-11-19
I have encountered this problem with every version of ubuntu, and on computers (desktop) on which Windows correctly mutes the speakers when performing the same action. Clearly,it is possible to differentiate between the ports, but it is left to the software to do the muting.

---

### Post by ccrs8 on 2012-04-14
FYI, I just plugged in my headphones for the first time since doing a clean install of Xubuntu 11.10 (I started this thread while on Ubuntu 11.04) and I'm happy to say that the speakers now automatically mute when I plug in my headphones.  Nothing except the OS has changed.  Same headphones, same exact PC hardware, same headphone port.  So I'm not sure exactly what solved it, but something changed between Ubuntu 11.04 and Xubuntu 11.10 that fixed the problem.

---

### Post by isantop on 2012-04-16
There were some known issues with the headphone mute and 11.04 (all flavors). So my guess is that it's simply the updated versions in 11.10.

---

