---
title: "Recordmydesktop recording at 2x speed"
date: 2012-02-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by williammanda on 2012-02-20
I was testing out recordmydesktop and after the 1st recording every recording is recorded at 2x speed. I started last night and the 1st test recording seemed fine and I went to do a real recording. From then on all the recordings were at 2x speed. This morning (not sure what I did) the 1st recording was fine then all the rest was at 2x speed again. I have tried rebooting but it stays at 2x speed. Is there anything else I can use? Please advise.

---

### Post by mehdieft on 2012-02-21
> **williammanda said:**
> I was testing out recordmydesktop and after the 1st recording every recording is recorded at 2x speed. I started last night and the 1st test recording seemed fine and I went to do a real recording. From then on all the recordings were at 2x speed. This morning (not sure what I did) the 1st recording was fine then all the rest was at 2x speed again. I have tried rebooting but it stays at 2x speed. Is there anything else I can use? Please advise.
Hi
on the Advanced Menu change the following Setting
Performance\Frame per Second = 10
enable the following option:
1-encode on fly
2-zero compression
3-quick subsampling
4- full shot at every frame

---

### Post by mc4man on 2012-02-21
The defaults work fine here, actually just wanted to mention - with updates today here the app indicator icon for recordmydesktop (gtk) won't show, though it is actually there. And if you do click record in the gui it will start recording .
Screen shows where the indicator menu is, in this case between the workspace indicator & wicd, where the corner of the menu box is

[https://bugs.launchpad.net/bugs/938089](https://bugs.launchpad.net/bugs/938089)

---

