---
title: "Three proposals to improve ubuntu"
date: 2008-01-12
forum: Ubuntu Brainstorm
---

### Post by pedor on 2008-01-12
I've long been disturbed by some features of Ubuntu, namely

If you copy a text string(ctrl +c) from certain programs you lose it when you close the program.
why can´t it be kept?

why have removable drives  a trash?
ubuntu should instead ask directly if  you  want to remove the files permanently. I know shift + delete works  but few people seem to know that.

When you download a file in Firefox, you are asked which program you want to use to open it with. If you chose Other, shouldn't the "open with Other Application." menu  come up (the same menu you can select when you right click on a file in Nautilus) instead of the current file browser?

Do you agree?

---

### Post by smartboyathome on 2008-01-12
It can't be kept because the kernel doesn't store it. We have to use an external program like Glipper to keep it.

I agree... especially since in Thunar the trash for several devices is viewed in one place.

This is Firefox, it is not part of GNOME and it doesn't use anything GNOMEish. This would have to be taken up with the Firefox devs.

---

### Post by Jan-Nik on 2008-01-12
> **smartboyathome said:**
> It can't be kept because the kernel doesn't store it.
No, the XServer/GTK+ do this and it's possible. Press ALT + F2 and enter something, copy it. CLose the dialog and there you go: it's still in the clipboard.
The only problem is, that some applications don't support this yet.

---

### Post by Lster on 2008-01-12
[QUOTE=pedor]If you copy a text string(ctrl +c) from certain programs you lose it when you close the program.
why can´t it be kept?[/QUOTE]

This irritates me a lot too. It really is amazing that we have wobbly windows and all these other trivial improvments and yet this happens. Surely something can be done about it! :)

---

### Post by Burgundavia on 2008-01-13
Three distinct bugs there. 

1.Where this should be fixed is an interesting question that I suspect the DE and X people are just ignoring because each thinks the other should solve it. I have no idea which solution is right.

2. This is a longstanding bug in Nautilus:
[https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/12893](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/12893)

3. This is a platform integration bug in Firefox:
[https://bugs.edge.launchpad.net/ubuntu/+source/firefox/+bug/18995](https://bugs.edge.launchpad.net/ubuntu/+source/firefox/+bug/18995)

Corey

---

### Post by sstusick on 2008-01-13
One thing that has bugged me in 7.10: Compiz is enabled by default. 

It is ok to have Compiz installed by default, but why enable it on default?

This causes problems for computers that have lesser hardware. And if you want to use 7.10 on your PC you have to go out of your way and get an alternate install disc just because Ubuntu won't boot up because of Compiz being enabled by default. This should not be an issue and should be frowned upon in the Linux community.

---

### Post by smartboyathome on 2008-01-13
> **sstusick said:**
> One thing that has bugged me in 7.10: Compiz is enabled by default. 

It is ok to have Compiz installed by default, but why enable it on default?

This causes problems for computers that have lesser hardware. And if you want to use 7.10 on your PC you have to go out of your way and get an alternate install disc just because Ubuntu won't boot up because of Compiz being enabled by default. This should not be an issue and should be frowned upon in the Linux community.

I like Compiz by default, and it should disable itself on hardware that it can't run on. It does for me. It also doesn't use very many (or very powerful) effects. Are you saying that it won't disable itself for you and your hardware doesn't support it? If so, I would call that a bug.

---

### Post by sstusick on 2008-01-13
No, Compiz does not disable itself on my machines. The Windows borders are half the size of the screen and you can't do anything. So maybe it is a bug. But why not fix the REAL bugs instead of creating more by having Compiz by default. It is useless anyway.

---

### Post by smartboyathome on 2008-01-13
This has been discussed over and over, and the reason it is enabled by default is because it provides some useful effects (most importantly real transparency, ie. compositing). Also, like I said before, there is a very minimal set of effects selected for default in Ubuntu.

About your problem: it doesn't sound like a compiz problem but a screen resolution one. Would you happen to have a screenshot? Also, what screen resolution does Ubuntu run at on the livecd?

---

### Post by pedor on 2008-01-15
I have installed glipper and it does solve this "bug".
Maybe glipper should be default in ubuntu?

---

### Post by sstusick on 2008-01-15
Yes, I think glipper should be included by default in Ubuntu.

---

### Post by sstusick on 2008-01-15
> **smartboyathome said:**
> This has been discussed over and over, and the reason it is enabled by default is because it provides some useful effects (most importantly real transparency, ie. compositing). Also, like I said before, there is a very minimal set of effects selected for default in Ubuntu.

About your problem: it doesn't sound like a compiz problem but a screen resolution one. Would you happen to have a screenshot? Also, what screen resolution does Ubuntu run at on the livecd?The screen resolution is the same it always was, 1280x800. And Screenshot was impossible because the Window borders were the size of the entire screen, literally. Which made Ubuntu 7.10 useless on the machine. But I'm not going to worry about it, will stick with 7.04 until 8.04 comes out, hopefully the bugs and whatever will be straightened out by then. Thanks for the reply, though.

---

### Post by smartboyathome on 2008-01-15
Have you tried using alt+drag on the window to see it? It does sound like a huge bug. It could possibly be a graphics card problem.

---

### Post by sstusick on 2008-01-15
I would try it if I still had it installed.

---

### Post by sstusick on 2008-01-17
Well I was bored yesterday, so I ran the Ubuntu 7.10 LiveCD and was able to take a screen shot.

This is what it looks like when compiz is enabled:

---

### Post by smartboyathome on 2008-01-17
> **sstusick said:**
> Well I was bored yesterday, so I ran the Ubuntu 7.10 LiveCD and was able to take a screen shot.

This is what it looks like when compiz is enabled:

That is definately a bug. I would report that to launchpad if I were you.

---

### Post by Lster on 2008-01-17
I had something similar a while ago when trying OpenSuSe. All the text was huge on the screen to the point of which it was unusable. That was on my very old computer with 10.2 (I think). I don't have the computer anymore to test with a 10.3, but I hope it's fixed!

---

