---
title: "[SOLVED] What happens if you just forget your password?"
date: 2008-12-23
forum: Security
---

### Post by upapilot on 2008-12-23
What happens if you forget your password to log into Ubuntu?:popcorn:

---

### Post by Masuran on 2008-12-23
You'll have to reset it using a live cd and some CLI magic. It's stupid to forget your password but unfortunately not uncommon.

---

### Post by tubbygweilo on 2008-12-23
upapilot,
It has happened to me ages ago and from what I can remember I used something along the lines of sisco311's reply in [Lost my password to log on, what do i do?]("http://ubuntuforums.org/showthread.php?t=863224&highlight=reset+password") but it was a long time ago. Hope it helps you.

---

### Post by hyper_ch on 2008-12-23
however if you fully encrypt your system and you forget it then, you're in trouble.

And generally: always have backups!

---

### Post by albinootje on 2008-12-23
> **upapilot said:**
> What happens if you forget your password to log into Ubuntu?:popcorn:

Boot with the "recovery console" option.
Drop to root shell prompt (if you see that option).
Then at the # prompt type (assuming your username is upapilot) :
```

passwd upapilot

```
hit <enter> key after filling in the password,
then again to verify the password, then type :
```

init 2

```

---

### Post by upapilot on 2008-12-23
I see.....forgetting your password is still something you can save yourself from.....Thanks!

---

### Post by KevinHarr on 2008-12-23
> **upapilot said:**
> I see.....forgetting your password is still something you can save yourself from.....Thanks!
Did you have any luck? I am in the same situation as you but only diff is I have XP on a shared drive.

---

