---
title: "Problems after updating software"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by northwestern on 2012-03-05
Just downloaded the latest updates which included kernel 2.2.0.18, some strange things have happened on restart.
1/ Unity icons have gone back to the larger size, ubuntu tweak, my unity and appearance have lost the ability to alter the size.
2/ In the log in screen Gnome and Gnome classic have appeared. Last time I downloaded these manually and they bust my system when I tried to load them (are they safe to use now ?).
3/ Before the update both screens use to auto hide the unity panel, now only my main screen shows unity.

Regards 
Northwestern.

PS
Has anyone got minitube working yet?

---

### Post by northwestern on 2012-03-06
Is there a problem with kernel 3.2.0.18 causing the problems I quoted above, If I boot up using 3.2.0.17 everything runs normally.

Regards
Northwestern

---

### Post by mc4man on 2012-03-06
sounds like w/ that kernel your being thrown back to unity-2d, you should ck.
```
echo $DESKTOP_SESSION
```
if so maybe see what this says
```
/usr/lib/nux/unity_support_test -p
```

minitube works fine here, biggest issue was the phonon-backend-gstreamer fails to decode a couple of common youtube encoding formats (mainly avc1 Baseline@L2.1 or Baseline@L1.1
I modded the package to allow installing & using phonon-backend-vlc instead which works perfectly. (phonon-backend-gstreamer has to be removed

Requested minitube be built to allow that, nothing as yet
[https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586](https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586)

---

### Post by northwestern on 2012-03-06
Thanks for your reply.

The first test  was unity 2d as you thought.

The second test came out as failed request.

Is there anything I can do to get to work properly.

Regards
Northwestern

---

### Post by northwestern on 2012-03-06
This is the error I receive when entering the second input.


X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  23
  Current serial number in output stream:  23


Regards
Northwestern

---

