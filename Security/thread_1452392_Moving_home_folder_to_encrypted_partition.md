---
title: "Moving home folder to encrypted partition"
date: 2010-04-11
forum: Security
---

### Post by ShawnB391 on 2010-04-11
What are the steps I must take to move my existing home folder to a separate, encrypted partition? Can I create this partition without damaging my current partition? Where is a trusted location to download App Armor profiles? What else can I do to harden the security of Ubuntu?

---

### Post by uRock on 2010-04-12
Since you have already installed, I would recommend creating an encrypted private folder using the directions on this page written by one of the forum's talented Amins. Scroll down to "Private (encrypted) Directories" [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

For downloading AppArmor Profiles, just run the ```
sudo apt-get install apparmor-profiles
``` in a terminal or search for apparmor-profiles within Synaptic Package Manager. Here you can find Custom made AppArmor profiles for various program and releases of ubuntu. [http://bodhizazen.net/aa-profiles/](http://bodhizazen.net/aa-profiles/)

To learn more about security on ubuntu in general go to this sub-forum and read the security stickies. They are very informative. [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Cheers,
Ronnie

---

