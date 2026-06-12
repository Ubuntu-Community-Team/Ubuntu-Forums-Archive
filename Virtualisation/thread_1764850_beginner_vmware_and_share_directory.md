---
title: "beginner: vmware and share directory"
date: 2011-05-22
forum: Virtualisation
---

### Post by then_dude on 2011-05-22
hello,

i hav ejust installed a winxp on my ubuntu.

i have no network on my xp;

i wonder if sharing a directory is harmfull when it comes down to virusses ? 

i wonder if my ubuntu can be infected in any way ? 

thanks

---

### Post by fjgaude on 2011-05-22
I've been running like you for years without an issue. I normally set the net connection to **Host-only**, after getting the latest updates to WinXP. I don't run any anti-virus software. Notice my signature.

---

### Post by adipramono on 2011-05-22
I'm running XP SP3 on my Ubuntu 10.04. I shared folder in my /media/external/shared/. I know that some files in that shared folder are containing sality and now my XP are infected. But it doesn't touch Ubuntu system I guess.

---

### Post by then_dude on 2011-05-23
thanks guys, 

but some questions

1) in vmware i disable the network adapter, cause i don't need any privat network between my host and my gast system

2)i cannot share a directory. i have specified one in the configuration part of vmware, but nowhere to find this directory in the guest system. 

(there was something that always came up, but i clicked it away, permantly: that i had to make a user if i wanna use the share dir option )

can anybody help me on this topic

thanks

---

### Post by fjgaude on 2011-05-24
You have to have a connection between host and guest to share directories.

Why doesn't **Host-only** work for you?

Okay, where are the shares with respect to the host?

---

### Post by then_dude on 2011-05-25
aha, i didn't know that. (that i needed a host only connection)  okee, i got a host connection.   then i need to install guest additions   but no luck, nothings happens,  i try to load it via the mount cd ; then choose usr/share/.../  then pick the iso vboxguestadditions,   then again install guest additions but nothing happens.   can anybody tell me why?   (i use a tinyxp version, and yes i got a license for an normal xp, which came with the pc);   thanks

---

### Post by fjgaude on 2011-05-26
Say, are you running Virtual Box or VMware Player?

---

### Post by then_dude on 2011-05-26
oracle vm virtualbox thanks (i didn't know that there was a difference)

---

### Post by fjgaude on 2011-05-27
Off and on I've used VBox and tried it in 11.04... it worked and I had no issues with shares, or installing the issues. It seemed seamless following the prompts.

Sorry I can't be of any help.

---

### Post by Ayazen on 2011-05-27
Hello Everyone! I'm a newbie tryin to get my ubuntu to work that suits my preferences. I'd like to install vmware and get xp loaded and install some games in xp. The problem is I don't know how to do it. I've used to be a microsoft user, but now I've switched to ubuntu for financial purposes and it's potential. I was hoping someone could walk me through the process since I don't know anything about linux, the commands and so on. HELP!

---

### Post by Pres_ on 2011-06-01
Having a similar issue, but I'm using VMware (running Ubuntu as a client) and I cannot get my shared folder to show up. Spent most of yesterday trying to get it to work, and everything I try ends up FAIL!

---

### Post by fjgaude on 2011-06-01
To get features in a guest VP to work you have to install the Tools or Additions. Without them lots of things don't work, like shares, and the video and mouse are slow.

---

