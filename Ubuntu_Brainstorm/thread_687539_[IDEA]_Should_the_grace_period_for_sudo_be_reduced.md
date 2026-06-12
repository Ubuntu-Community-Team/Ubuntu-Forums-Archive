---
title: "[IDEA] Should the grace period for sudo be reduced?"
date: 2008-02-04
forum: Ubuntu Brainstorm
---

### Post by angryfirelord on 2008-02-04
I feel that the 5 minute (or whatever it is) period seems a bit long for sudo. I always append my sudoers file so that it's cut down to one minute. Does anyone else agree/not agree?

---

### Post by rabi.fettig on 2008-02-04
Usually I tend to perform multiple administrative tasks in a row. Often I'm reading some sort of instructions or documentation while I'm at it. I think that having to constantly re-type a password (especially a secure password with mixed cases, numbers and symbols) would be unnecessarily irritating.

---

### Post by smartboyathome on 2008-02-04
I think that it is fine as it is, and that it only happens in the current session (terminals count as a separate session). It would be just as dangerous (or probably more) to have a person run an unknown script as root, but that is a flaw in social engineering, not Ubuntu. ;)

---

### Post by Keith Hedger on 2008-02-04
I agree with  rabi.fettig  if your password is secure its a pain having to keep retyping it specially as i am the only user on my main machine

---

### Post by Jay_Bee on 2008-02-04
No, that would make it as annoying as that Vista UAC that everybody is turning off as soon as they google how to do it.

---

### Post by hellion0 on 2008-02-05
Five minutes is plenty short enough. Sometimes a person will need to run several administrative tasks in a row, and one minute just isn't enough time, especially if one of those is a lengthy apt-get or aptitude install, update or upgrade.

---

### Post by angryfirelord on 2008-02-05
Well, I'm paranoid and I single-task, so maybe it's just my perspective. Thanks for your input!

---

### Post by Vadi on 2008-02-05
No, it's fine as it is.

---

### Post by aysiu on 2008-04-07
Me feeling is that 5 minutes is too long.

However, given how many people get frustrated at having to type their passwords over and over again, shortening the sudo timeout might bombard us with even more new users wanting to log in as root.

---

