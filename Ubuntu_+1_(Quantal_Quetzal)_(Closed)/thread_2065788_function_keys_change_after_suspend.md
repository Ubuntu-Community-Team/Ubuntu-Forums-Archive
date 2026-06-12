---
title: "function keys change after suspend"
date: 2012-10-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by sawjew on 2012-10-02
Hi all,

I am hoping someone here can help me with a small problem. I have a Toshiba Satellite E300 notebook which has a series of function keys across the top of the keyboard (as most notebooks do now). I have a dual boot with Windows 7 and in Windows the function keys operate as the marked function and you have to use the function key to change them to the standard F keys.

The problem I have is that some of the keys work when I start the computer up (volume, eject, wireless on/off, sleep) but the brightness keys don't. However they work the opposite to Windows requiring the function key to operate.

This isn't too much of an issue as there are a number of ways of getting the keys to work (they register in xev) but the strange part is that after the computer is suspended and then woken up the keys change. The keys which didn't work before now do without the use of the function key and those that did no longer do, they don't even show up in xev.

I don't care which way it goes because I can fiddle around and make them work but I just need it to remain consistent. I am currently using 64 bit Kubuntu Quantal but it was exactly the same in Precise with Unity and KDE. I upgraded (clean install) to see if it would fix the problem. It also occurs in Mint but seems to be alright with OpenSuse (tested with live flash drives) so it appears to be an Ubuntu issue.

Thanks for your help.

---

