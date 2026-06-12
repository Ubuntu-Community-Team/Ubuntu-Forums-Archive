---
title: "Ubuntu 12.04 Update Error"
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mirandalc on 2012-04-14
I just updated and restarted Ubuntu 12.04. I got a black screen after the log in. After suspending by closing the lid, I get the a black desktop, not the usual, and my desktop icons, nothing else.
Any help would be amazing.
Thanks.

---

### Post by MG&amp;TL on 2012-04-14
What does logging into unity2d do?

---

### Post by mirandalc on 2012-04-14
It loads just fine. Interesting.

---

### Post by MG&amp;TL on 2012-04-14
Okay, try:

```
unity --reset
```

and can you post the output of:

```
/usr/lib/nux/unity_support_test -p
```

in case your graphics stopped working for some reason.

---

### Post by mirandalc on 2012-04-14
I can open a terminal window using CTRL+Shift+T and can paste text, but I can't enter the command.

---

### Post by pqwoerituytrueiwoq on 2012-04-14
try to enter the command in a tty [ctrl]+[alt]+[f1]
[ctrl]+[alt]+[f7] to get back

---

### Post by mirandalc on 2012-04-14
I tried the unity --reset command in tty and got a bunch of errors and warnings.
when i tried the second, i got "unable to open display"
Thanks for helping.

---

### Post by lolpenguin on 2012-04-14
Probably a problem with your Xorg config.
(shouldn't this be in Ubuntu +1?)

---

### Post by dcstar on 2012-04-15
> **lolpenguin said:**
> 
(shouldn't this be in Ubuntu +1?)

Yes it should, have **you** reported the post asking it to be moved?

---

### Post by MG&amp;TL on 2012-04-15
You should get a bunch of errors and warnings for the first command, it's an imperfect procedure which seems to work. Leave it to run for a bit, then try Unity again. Also, can you remember a few of the more important ones and paste them here?

The second one needs to be run in an X session, so login to Unity2d and open a terminal. When you say 'can't enter' what do you mean?

Sorry this is happening, 12.04 is still unstable software.

---

