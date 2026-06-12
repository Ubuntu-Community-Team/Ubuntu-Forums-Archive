---
title: "Sound support in Ubutnu Server 8.04"
date: 2008-06-04
forum: Server Platforms
---

### Post by Snille on 2008-06-04
Hi all,
I'm using a Ubuntu Server 8.04 as a VMWHost. I would like to have sound in my guests. But when i have installed the host server there is no sound system (support) installed. And therefore of course the guest cant use audio either.

If i install Ubuntu Desktop 8.04 on the same computer, the sound works fine. So Ubuntu has support for my (intel) sound card.

What do I have to install on the server to get basic sound support?
Basically, what packets do I need. :)

Thank you.

---

### Post by cdenley on 2008-06-04
maybe...
```

sudo apt-get install alsa-base

```
Did you install a desktop environment? Is the device detected? Why are you using a server install?
Run this command with the server install and a desktop livecd.
```

lspci|grep Audio

```

---

### Post by trash on 2008-09-11
> **cdenley said:**
> maybe...
```

sudo apt-get install alsa-base

```
Did you install a desktop environment? Is the device detected? Why are you using a server install?
Run this command with the server install and a desktop livecd.
```

lspci|grep Audio

```

i keep getting no install candidate for anything alsa related, i am trying desperately to get any mixer installed because my detected soundblaster won't make a sound no matter what i do... is it perhaps an issue with the server kernel?

---

### Post by cariboo on 2008-09-11
Depending on what kind of Soundblaster card you have it should work with hardly any effort at all. Make sure the module for your sound card is loaded then you can install alsa-base and alsa-utils

After you have alsa installed use asoundconf to install your sound card eg:

```
asoundconf list
```

Then 

```
asoundconf set-default-card PARAMETER
```

where PARAMETER is the result of the first command.

Jim

---

### Post by trash on 2008-09-11
> **cariboo907 said:**
> Depending on what kind of Soundblaster card you have it should work with hardly any effort at all. Make sure the module for your sound card is loaded then you can install alsa-base and alsa-utils

After you have alsa installed use asoundconf to install your sound card eg:

```
asoundconf list
```

Then 

```
asoundconf set-default-card PARAMETER
```

where PARAMETER is the result of the first command.

Jim

I wish! no matter what i try i get either dependency problem or no source package for alsa... i did manage to get libalsaplayer0 instaled using -f, but the joy ended there.
I have all the right repos and i've tried just about every package related to alsa.
The card is detected and the driver loads. What is a bit wierd is that when mocp starts i can see it checking for Jack and then Alsa and then it starts playing the cd.... i am stumped.

EDIT: i reinstalled the server and alsa installed fine afterwards... no idea what the issue was.

---

