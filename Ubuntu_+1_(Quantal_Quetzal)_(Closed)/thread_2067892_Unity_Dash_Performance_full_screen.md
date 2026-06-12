---
title: "Unity Dash Performance full screen"
date: 2012-10-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cromat on 2012-10-07
Hey,

I have noticed that the performance of the dash is 3x slower if I make the dash full screen. If I keep the dash at the default size performance is blazing fast.  Anyone know if there is a solution to this or if there is a bug for this already? I couldn't find one.

---

### Post by mc4man on 2012-10-07
A FS Dash is not only slow here with nouveau, basically a disaster after a few opening over a window. Causes the indicators to disappear while open, video degradation in the Dash & sometimes the right click on the Dash icon stops doing anything.

Also writes a 100,000 or 2 lines to .xsession-errors starting with 
nouveau: kernel rejected pushbuf: Cannot allocate memory
nouveau: ch4: krec 0 pushes 1 bufs 137 relocs 0
nouveau: ch4: buf 00000000 00000003 00000006 00000006 00000000
ect. ect.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1063523](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1063523)

(there are other issues with each of the blurs & the Dash, normal or maxed

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1054649](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1054649)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1055308](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1055308)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1058391](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1058391)
variation of last link
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1059916](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1059916)

---

