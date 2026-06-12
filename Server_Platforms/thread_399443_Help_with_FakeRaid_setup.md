---
title: "Help with FakeRaid setup"
date: 2007-04-02
forum: Server Platforms
---

### Post by MacsRock on 2007-04-02
I have set up a server with version 6.06 on a machine with an AMI megaraid controller. I guess this is Fake RAID. Ubuntu is installed on /dev/hda (non raid ide). I have two 15 GB drives attached to the raid controller. I have installed dmraid and from what I can tell, it is working correclty. /dev/mapper lists the two drives and mounts them at /dev/hde. I tried formatting the drive, but the process hangs.

I am not sure how to diagnose this problem. If someone could walk me through how to troubleshoot, I would be most grateful.

Thanks

---

### Post by cprophecy on 2007-04-02
have you thought of using linux software raid? i think most people would agree that it is a better option than FRAID.. you'll want to install the mdadm package for it..

---

### Post by MacsRock on 2007-04-02
I had not thought of that. I will give it a try. Thanks

---

### Post by Aberrix on 2007-04-02
do not use dmraid, I tried for days with no luck. simply use the alternate install cd and it works effortlessly.

gl mate.

---

