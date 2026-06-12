---
title: "VLC 1.1.12-2 in repos"
date: 2011-10-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-10-15
The newest release of VLC (1.1.12-2) is in Precise repos now.

Here:
[https://launchpad.net/ubuntu/precise/+source/vlc/1.1.12-2](https://launchpad.net/ubuntu/precise/+source/vlc/1.1.12-2)

> Changelog
vlc (1.1.12-2) unstable; urgency=low


  * Apply patches from upstream's 1.1 maintenance branch.
    - Turn on XVideo color key automatic painting (fix upstream #4643)
    - Set channel map when using PulseAudio 1.0
    - Translation updates

 -- Benjamin Drung <email address hidden>  Thu, 13 Oct 2011 20:17:03 +0200

---

### Post by mc4man on 2011-10-15
Maybe videolan will get around to finally doing a 1.2 release so that could be used instead of the 1.1.x
Otherwise I'm sure the master ppa will have 12.04 packages before too long.

---

### Post by SpEcIeS on 2011-10-15
Compiled this from source, it seems to run well, and it is stable.

---

### Post by ventrical on 2011-10-15
> **Harry33 said:**
> The newest release of VLC (1.1.12-2) is in Precise repos now.

Here:
[https://launchpad.net/ubuntu/precise/+source/vlc/1.1.12-2](https://launchpad.net/ubuntu/precise/+source/vlc/1.1.12-2)


 I just installed it using synaptic. Worked seamless out of the box!

---

### Post by ranch hand on 2011-10-15
Yup, just got the upgrade today.  Works slick.

---

### Post by pressureman on 2011-10-16
Is the audio sync fixed? I'm wearing out my "J" key by having to press it 6 times at the start of each video I watch. 300ms audio delay is quite noticeable.

---

### Post by ventrical on 2011-10-16
Actually what I did was stick in my pen-drive with *.wmv, 3gp etc files, picked one , dragged it over to the open vlc player screen and tada!! it just started up perfect .. no muss , fuss or anything.

---

### Post by ventrical on 2011-10-16
> **pressureman said:**
> Is the audio sync fixed? I'm wearing out my "J" key by having to press it 6 times at the start of each video I watch. 300ms audio delay is quite noticeable.

The sync is just perfect(err..precise).- almost :)

---

### Post by mc4man on 2011-10-16
> **pressureman said:**
> Is the audio sync fixed? I'm wearing out my "J" key by having to press it 6 times at the start of each video I watch. 300ms audio delay is quite noticeable.
likely improves if not totally fixed - changelog
> vlc (1.1.12-1) unstable; urgency=low

  * New upstream release.
    - Multiple fixes and improved synchronization for PulseAudio support
      (Closes: #601826, LP: #805807).
    - Fix segmentation fault (LP: #803006).
    - Addd GenericName entries to desktop file (Closes: #640911).
    - Do not ignore the --quiet flag (Closes: #531975).
    - Fix vlc runs xdg-screensaver with signal child blocked (Closes: #640245).
    - Fix crashes when trying to play youtube URLs (Closes: #641507).
  * Drop xulrunner-1.9.1.patch (accepted upstream).
  * Refresh 200_osdmenu_paths.patch.
  * Fix typo in vlc.desktop: Name[nn] -> GenericName[nn].

 -- Benjamin Drung <bdrung@debian.org>  Fri, 07 Oct 2011 01:21:06 +0200


---

