---
title: "Lubuntu + HP Thin Client T510 with BCM970015"
date: 2018-12-04
forum: Ubuntu, Linux and OS Chat
---

### Post by pandorax on 2018-12-04
I completed install Lubuntu base on Ubuntu 16.04, I try command "lspci" and found Video Decoder card BCM70015 (Broadcom CrystalHD). However, VLC not detect encoding card it's show "Not Available XVideo adapter". 

That Thin client using VIA Eden X2, I try install right driver with OpenChrome. 
Open Chrome requirement xorg-video-abi-20 and xserver-org-core

sudo apt-get install xorg-video-abi-20
sudo apt-get install xserver-org-core
sudo apt-get install xserver-xorg-video-openchrome

After finish install Desktop is freeze, I can't typing or control mouse.  Currently we can be access from remote only. How to dissolve this problem and continue install BCM970015 later.

Thank you.



 [IMG]https://i.imgur.com/RposJ6h.png[/IMG]

---

