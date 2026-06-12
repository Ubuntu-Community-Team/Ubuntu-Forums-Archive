---
title: "Freeze at login screen"
date: 2012-02-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tr33m4n on 2012-02-22
Hello there,

Just wondering whether anyone else is experiencing the login screen freezing without loading the user background? This has only started happening in the last couple of hours or so...

Any ideas?

Can still access ttys so something to do with x or lightdm

---

### Post by PaulW2U on 2012-02-22
> **tr33m4n said:**
> Hello there,

Just wondering whether anyone else is experiencing the login screen freezing without loading the user background? This has only started happening in the last couple of hours or so...


I've just applied quite a few updates and I don't know if this is related to what you're seeing but I've just logged out of Unity and into Gnome Shell. About 20 seconds after entering my password the screen went blank for a couple of seconds. Then I saw the login screen again and Gnome Shell appeared a few seconds later.

I've never seen that before.

---

### Post by tr33m4n on 2012-02-22
Everything seems to be running again after a couple of updates...

---

### Post by tr33m4n on 2012-02-23
Hmm, the problem is still there... Looks like it freezes just before or whilst trying to load the users background at the login screen... I'm currently using links to post here, situation is a bit desperate!

Any more ideas?

Cheers

---

### Post by tr33m4n on 2012-02-23
Hmm, removing Windbind daemon appears to of temporarily fixed it... But we shall see on next reboot

---

### Post by tr33m4n on 2012-02-23
Nope... Back on links... Do'h

---

### Post by tr33m4n on 2012-02-23
It appears the issue was with Alsa. I have removed alsa-base and pulseaudio and now I can login on every reboot... My soundcard wasn't being detected by 12.04 anyway so it's an issue I can deal with for now, but it's definitely not ideal... If you have a similar problem try that

---

