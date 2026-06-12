---
title: "Can't scroll all the way down in System ..."
date: 2009-11-11
forum: Ubuntu Moblin Remix
---

### Post by jezebel on 2009-11-11
I just started (about a week ago) running UNR 9.10 Karmic Koala

I've got UNR installed and (finally) running smoothly after updates etc on my Acer Aspire One netbook. 

But – I think I've found a bug. 

Under System – Administration I cannot scroll down to see all of the options (i.e. update manager and Users/groups is totally invisible; I get to them by hitting the arrow key and blindly hitting enter).

Also - how the heck can I locate my network (I should be able to find other pcs on my network, right?).

Thanks so much.

---

### Post by jezebel on 2009-11-11
I'm trying to attach a screenshot... Okay - Ii can get no further down than what you see in the screenshot. Any help for this? Thanks again.

---

### Post by EzeAris on 2009-11-11
What about clicking on the bar? I know that isn't a solution, but maybe it goes down :S

---

### Post by jezebel on 2009-11-11
If you mean the 'scroll bar', of course I did do that! UNR seems to think that the page just stops there and I can't scroll. 

Any help?

---

### Post by jezebel on 2009-11-16
Okay, well, guess I'll just never be able to see my update manager!

---

### Post by dannyboy79 on 2009-11-16
> **jezebel said:**
> Okay, well, guess I'll just never be able to see my update manager!

open a terminal and run sudo apt-get update, then sudo apt-get upgrade. are you running the correct video driver? what does lspci -v, if it's an nvidia card you need to run the proprietary video driver

---

### Post by jezebel on 2009-11-18
Hi Dannyboy and thanx for the command line for the update manager.

I'm all up to date; but I don't know what video driver I've got; I'm on an Acer Aspire One D250 (netbook)...

---

### Post by djgregstar on 2010-01-08
I too am having this issue, tried to create a new user from CLI but still no joy so I don't think related to user profile. I have tried it from a fresh install and this works fine, only seems to be upon an update from Ubuntu 9.10 karmic. If anyone has any ideas really would be useful! Thanks

---

### Post by maubp on 2010-01-29
[https://bugs.launchpad.net/netbook-remix/+bug/449790](https://bugs.launchpad.net/netbook-remix/+bug/449790)

---

