---
title: "Cannot view AVI files"
date: 2017-08-17
forum: Ubuntu, Linux and OS Chat
---

### Post by Corvair on 2017-08-17
Failed to fetch [http://mirror.atlantic.net/ubuntu/dists/xenial-updates/main/binary-amd64/by-hash/SHA256/2d70b286cc97a7196993c2ad98c651098621e68bf427e2bab1eb5d1adc9f868d](http://mirror.atlantic.net/ubuntu/dists/xenial-updates/main/binary-amd64/by-hash/SHA256/2d70b286cc97a7196993c2ad98c651098621e68bf427e2bab1eb5d1adc9f868d)  Hash Sum mismatchFailed to fetch [http://mirror.atlantic.net/ubuntu/dists/xenial-updates/main/binary-i386/by-hash/SHA256/ad090e7a628e6ce1571c1c9cb396957369d5c8b11289f2ed0e430c8be47ce667](http://mirror.atlantic.net/ubuntu/dists/xenial-updates/main/binary-i386/by-hash/SHA256/ad090e7a628e6ce1571c1c9cb396957369d5c8b11289f2ed0e430c8be47ce667)  Some index files failed to download. They have been ignored, or old ones used instead.

Hello I am trying to view AVI files with different viewers and nothing works.

I installed Gnome MPlayer, Audacious and nothing works. When installing from Synaptic and reloading I get the above message. Can anyone help me translate the above message into a workable language, in other words what can I do to solve this?.

I have the latest version for Ubuntu.

---

### Post by oldos2er on 2017-08-17
There are some suggestions here ([https://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error](https://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error)) on fixing the hash sum mismatch error.

---

### Post by gordintoronto on 2017-08-17
Try VLC Media Player.

---

### Post by Corvair on 2017-08-17
VLC is  my favorite but has the same problem with AVI files. Thanks anyway.

---

### Post by papibe on 2017-08-17
Hi Corvair.

Do you hear sound at least?

Since AVI is just a container, it would be helpful to know what kind of CODECs the video file has.

Open the file with VLC and either press Ctrl+j or using the menu: Tools -> Codec Information, and tell us what you see there.

Or even better, install mediainfo:
```
sudo apt-get install mediainfo
```
then get the codec information by running:
```
mediainfo /path/to/your/videofile.avi
```
Please copy the output using the mouse, and post it back here.

Regards.

---

### Post by Corvair on 2017-08-17
I already have mediainfo.  The codec for the file is : H264-MPEG-4  AVC(Part 10)  avc 1

---

### Post by Corvair on 2017-08-17
oldos2er.   I followed your instruction and now I can install Audacious ans Gnone player and reload without a problem.  I also tried another .AVI file and can view it from VLC, so I think it is my file that has a problem.Thanks for the help.

---

### Post by Corvair on 2017-08-17
gordintoronto. Looks like it is my present .AVI file that is corrupt because I can read other .AVI files. Thank you.

---

### Post by Corvair on 2017-08-17
Thanks to everyone for your help.

---

### Post by oldos2er on 2017-08-18
You're welcome. Next time you have a support question, it's best to post in the support areas of the forum. Also we prefer that people ask one question per thread; otherwise threads tend to become needlessly convoluted.

---

