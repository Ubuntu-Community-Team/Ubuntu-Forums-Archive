---
title: "Disk burning music"
date: 2015-01-11
forum: Ubuntu Studio
---

### Post by simon d w on 2015-01-11
I have toshiba satellite i havent burnt any music CDs for years since i changed to ubuntu. So i tryed brasero and i wont burn then i tried K3b wont work either. Its recognising the disk fine but wont burn. Is there a driver problem? Maybe it has the driver for reading not burning?  Or is it privilege problem? I am a newbie so need to be take through step by step. I don't know how to run programs in the terminal hence in using the graphic interfaces. 

I need some music in my car!! 

Thanks.

---

### Post by simon d w on 2015-01-11
no still not working, Not a driver issue because it burns data fine, but its just audio option, it wont let me press the burn button, its not highlighted.

---

### Post by simon d w on 2015-01-11
I made a video illustrating my problem. Just want some music on a fricking CD is it that much to ask? 
[https://www.youtube.com/watch?v=OCEImPbEMgg&feature=youtu.be&hd=1](https://www.youtube.com/watch?v=OCEImPbEMgg&feature=youtu.be&hd=1)

---

### Post by SuperFreak on 2015-01-11
Are you clicking on "only create image". I think that will only create a temp file. You need to click "create image" and there has to be a cd already in the drive

---

### Post by SuperFreak on 2015-01-11
I notice a difference between our setupps inthe permission window. See attch
Not sure if that is relevant, but K3B works for me

---

### Post by simon d w on 2015-01-11
Yeah thanks, Im pretty sure its a rights issue, it some how thinks i don't have privilege to burn? I'm not sure how do I fix that issue is the dilemma! lol

---

### Post by simon d w on 2015-01-11
W:Failed to fetch cdrom://Ubuntu-Studio 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.1)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu-Studio 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.1)/dists/trusty/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM 
Just looked in the repositary information and the CD ROM is showing a problem
recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu-Studio 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.1)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu-Studio 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.1)/dists/trusty/universe/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

What does this mean? I am a newbie!

---

### Post by jejeman on 2015-01-12
I means that you have CD-ROM as APT repository. Just turn it off.

---

### Post by simon d w on 2015-01-12
Doh!

---

