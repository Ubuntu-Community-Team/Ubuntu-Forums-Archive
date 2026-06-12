---
title: "Synaptic - now no history at all"
date: 2015-09-01
forum: Ubuntu Development Version
---

### Post by mc4man on 2015-09-01
The progression from 14.04 on has been to get a smaller & smaller history column, in 15.10 here  when dragged to expose it's now empty
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1487890](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1487890)
The response from Brad Figg makes no sense, does anyone upstream (Ubuntu/Canonical) ever actually use Ubuntu anymore??

---

### Post by flocculant on 2015-09-01
confirmed it.

Brad Figg wouldn't know a thing - it's a bot.

---

### Post by v3.xx on 2015-09-01
Added my name to the bug.

---

### Post by QDR06VV9 on 2015-09-01
[FONT=monospace, monospace]Added my self also.
> [/FONT][COLOR=#000000]Brad Figg wouldn't know a thing - it's a bot.[/COLOR][FONT=monospace, monospace]
Boy is his Wife going to be suprised.[/FONT]:oops:

---

### Post by sgage on 2015-09-01
> **mc4man said:**
> The progression from 14.04 on has been to get a smaller & smaller history column, in 15.10 here  when dragged to expose it's now empty
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1487890](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1487890)
The response from Brad Figg makes no sense, does anyone upstream (Ubuntu/Canonical) ever actually use Ubuntu anymore??

Haven't seen any history in Synaptic for quite a while. I figured it would be fixed right away, but i guess not. I've added myself to your bug report.

---

### Post by mc4man on 2015-09-01
> **sgage said:**
> Haven't seen any history in Synaptic for quite a while. I figured it would be fixed right away, but i guess not. I've added myself to your bug report.
There are 2 bugs in synaptic, both about history but likely not related in cause

The other, older  one is the history column/box is either truncated or not visible at all, it's been a progression since 14.04.
So scr. 1 is in 14.04, part of the history is visible.
scr 2 is 15.04 where it appears there is no history, it's there but the left edge needs to be pulled to expose - scr. 3
bug here - don't expect any action on for 14.04/15.04 or at all
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1471445](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1471445)

---

### Post by sgage on 2015-09-01
> **mc4man said:**
> There are 2 bugs in synaptic, both about history but likely not related in cause

The other, older  one is the history column/box is either truncated or not visible at all, it's been a progression since 14.04.
So scr. 1 is in 14.04, part of the history is visible.
scr 2 is 15.04 where it appears there is no history, it's there but the left edge needs to be pulled to expose - scr. 3
bug here - don't expect any action on for 14.04/15.04 or at all
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1471445](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1471445)

I can grab the left edge and expose what should be the date column, but it's just totally blank. In any case, I've added myself to the bug you linked to in this post. I really like Synaptic - I wish they'd give it some attention.

---

### Post by mc4man on 2015-09-01
The history in synaptic is one of the things that makes it quite useful so hopefully they'll fix it retrieving the logs which are still being created
(/root/.synaptic/log
It would be nice if they fix the view being hidden but that's more an inconvenience & a pita having to expose each time..

---

### Post by ventrical on 2015-09-02
> **mc4man said:**
> The progression from 14.04 on has been to get a smaller & smaller history column, in 15.10 here  when dragged to expose it's now empty
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1487890](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1487890)
The response from Brad Figg makes no sense, does anyone upstream (Ubuntu/Canonical) ever actually use Ubuntu anymore??

?? I just pulled the dialog open and entered 'compiz (which I had used recently) and it's all there. You can't see the history content box. You have to put it right on the line, then click n' drag. It's empty by default it seems but did not used to be this way. More cutting, slicing and economy I guess..

Regards..
EDIT:  Updating. it might be busted still.
Edit: Yep .. it's busted.

---

### Post by sgage on 2015-09-02
> **ventrical said:**
> ?? I just pulled the dialog open and entered 'compiz (which I had used recently) and it's all there. You can't see the history content box. You have to put it right on the line, then click n' drag. It's empty by default it seems but did not used to be this way. More cutting, slicing and economy I guess..

Regards..

Not sure I understand what you're getting at. What's all there? It's supposed to show a history of what Synaptic has installed/removed, by date. You shouldn't have to enter anything.

---

### Post by QDR06VV9 on 2015-09-02
What it used to show(or still dose) in Trusty.

---

### Post by ventrical on 2015-09-02
> **sgage said:**
> Not sure I understand what you're getting at. What's all there? It's supposed to show a history of what Synaptic has installed/removed, by date. You shouldn't have to enter anything.

I edited my previous post. Yep - it's busted.

---

### Post by mc4man on 2015-11-28
There has been a proposed patch to return history, no movement on yet.
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=798884](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=798884)
Till then can be tested from here, works fine for me, no regressions seen yet. (does not fix having to pull the history window open to see.

[https://launchpad.net/~mc3man/+archive/ubuntu/synaptic1](https://launchpad.net/~mc3man/+archive/ubuntu/synaptic1)
Package is just a hair above current version, will be updated by any future synaptic update (hopefully one with an 'official' fix

---

### Post by flocculant on 2015-11-28
@mc4man - thanks for the ppa including that patch :)

---

### Post by sgage on 2015-11-28
> **mc4man said:**
> There has been a proposed patch to return history, no movement on yet.
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=798884](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=798884)
Till then can be tested from here, works fine for me, no regressions seen yet. (does not fix having to pull the history window open to see.

[https://launchpad.net/~mc3man/+archive/ubuntu/synaptic1](https://launchpad.net/~mc3man/+archive/ubuntu/synaptic1)
Package is just a hair above current version, will be updated by any future synaptic update (hopefully one with an 'official' fix

Works fine here - thanks!  :KS

---

