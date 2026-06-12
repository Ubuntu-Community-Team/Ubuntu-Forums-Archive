---
title: "Sound via xrdp on my VM"
date: 2016-04-18
forum: Virtualisation
---

### Post by kek3 on 2016-04-18
Hello world

I apologize if this post does not belong in this category, I didn't know where to post it. And sorry for my bad english.

I'm trying to run a remote desktop from a virtual machine (on vcenter  vsphere client) via xrdp. The VM is a Lubuntu 15.10 or Ubuntu 15.10  (both of them are working, being ubuntu with xfce desktop). The phisical  device where I want to see the remote desktop is a thin client (running  ubuntu 15.10) and raspberry pi (running last raspbian). All is working,  I can make the rdp connection between em...

My problem comes when I want to transfer sound. I've followed some  internet tutorials about using pulse audio to transfer the audio, but  even if I follow them, I get the audio being "played" (in pavucontrol  the blue bar moves, but there is no sound:confused:). I must add that without remote desktop, each device plays sounds Ok.

I've installed pavucontrols, paman, paprefs (enabled all thing that has "share", I think I have more than the 90% onf the ticks enabled)

Any one has any idea of what the problem is? Any help will be very apreciated.

Have a nice day!

Edit: I've followed this ( [http://dp.nonoo.hu/forwarding-sound-on-lan/](http://dp.nonoo.hu/forwarding-sound-on-lan/)) and I don't know why this time worked. I'll make more test tomorrow and see if this is working. Also I'll look for what theproblems was, to post a solution to it.

---

### Post by howefield on 2016-04-18
Thread moved to the "*Virtualisation*" forum, probably a better fit than Tutorials.

---

### Post by MAFoElffen on 2016-04-18
Will wait to see how that goes...

---

### Post by kek3 on 2016-04-21
Sorry for being late anserwing:

Okay, the sound works awesome on  the thin client! I think it was not working before cause I didn't  restart the service (I'm newbie ;.;).

I still cant make the  raspberry work :l If I load remote desktop all looks to work except  video and audio, it does not play. I mean, If I press play button on  youtube, audacious or vlc, it does not play. The same system (vm) in  being played on the thin client and works.

Probably it is becase the low cpu of the raspberry, this can't play more.

Does anyone make rdp work properly with media transfer on rpi? (ah, I've got raspbian jessie)

---

### Post by MAFoElffen on 2016-04-21
Congrats.

Please revisit this thread > Link on top right of page "Thread Tools" > "Mark As Solved"... That way others may finds resolves answers to their similar questions.

---

### Post by kek3 on 2016-04-25
I've found this awesome project ( [https://forum.armtc.net/index.php](https://forum.armtc.net/index.php)) where I can make sound and video work (with a quite good performance) on my raspberry pi !

---

