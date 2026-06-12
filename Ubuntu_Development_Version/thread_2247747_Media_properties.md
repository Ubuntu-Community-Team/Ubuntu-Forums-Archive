---
title: "Media properties"
date: 2014-10-10
forum: Ubuntu Development Version
---

### Post by P-I H on 2014-10-10
Media properties present different in Ubuntu 14.04 and Utopic.
The left picture is from Ubuntu 14.04 and the right from Utopic
Nautilus sometimes crashes when checking permissions.
Totem doesn't play the video.
Kodi (XBMC) plays the video with sound only.

---

### Post by grahammechanical on 2014-10-10
Double check questions.

Is this media file an example for display purposes or does this happen with all media files of that type? Is 14.04 accessing the same physical file and not a copy somewhere else on the disk? If an application in XBMC is not playing the file correctly and applications in both 14.04 and 14.10 refuse to play the file then the file and not the OS becomes the suspect.

Can you confirm that Totem in 14.04 will play this video and other videos? Can you confirm that Nautilus in 14.04 does not crash when checking permissions on this file. Any chance of making another copy of that file and seeing if that copy plays correctly?

Or is this media file on a DVD disc?

Regards.

---

### Post by Alan F on 2014-10-10
Open the .mp4 file with the default Videos app.

It will tell you that you need to install codecs. Accept the ones that the installer is offering.

Then reboot the computer and you will find that the properties in Nautilus are correctly populated.

---

### Post by zika on 2014-10-10
> **Alan F said:**
> Then reboot the computer and you will find that the properties in Nautilus are correctly populated.Why &#8222;reboot&#8220;? That is one of the main difference between *nix and other OS. You do not need to reboot for sure. Eventually to restart some service. At most.

---

### Post by Alan F on 2014-10-10
When the codecs were installed and Nautilus was re-opened the files properties were still not populated.

Possibly I could have restarted a service (which one?) or simply logged OFF then back ON but I took the easy route and rebooted.

---

### Post by zika on 2014-10-10
> **Alan F said:**
> When the codecs were installed and Nautilus was re-opened the files properties were still not populated. Possibly I could have restarted a service (which one?) or simply logged OFF then back ON but I took the easy route and rebooted.Log-out should be enough I presume. If I get some spare time soon I'll see if there is even „easier“ way... ;)

---

### Post by P-I H on 2014-10-10
@grahammechanical
> [COLOR=#000000]Is this media file an example for display purposes or does this happen with all media files of that type? Is 14.04 accessing the same physical file and not a copy somewhere else on the disk? If an application in XBMC is not playing the file correctly and applications in both 14.04 and 14.10 refuse to play the file then the file and not the OS becomes the suspect.[/COLOR]
It only happens on some of my .mkv files. The file is on an Ubuntu server and it's the same physical file. In 14.04 both XBMC and Totem plays the file correct.

> [COLOR=#000000]Can you confirm that Totem in 14.04 will play this video and other videos? Can you confirm that Nautilus in 14.04 does not crash when checking permissions on this file. Any chance of making another copy of that file and seeing if that copy plays correctly?[/COLOR]
As I wrote above both XBMC and Totem plays the file correct. Nautilus behaves as expected. I tried to make a copy with Nautilus on Utopic, but Nautilus crashed. I also used Natilus on 14.04 and copied the file to Videos in Utopic. There was however no changes in the properties.

> [COLOR=#000000]Or is this media file on a DVD disc?[/COLOR]
The file is stored on an Ubuntu server.

---

