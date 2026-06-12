---
title: "A quick few questions."
date: 2009-11-23
forum: The Cafe
---

### Post by NoaHall on 2009-11-23
About Karmic.

1) Is it true Songbird doesn't work on it?
2) How well does Skype work with it?
3) Is Synaptic completely missing? I mean, have they just got rid of it completely?
4) I don't like the sound of this software center. Can I remove it?

---

### Post by Irihapeti on 2009-11-23
I know that synaptic is still there. I don't know about your other questions.

---

### Post by FuturePilot on 2009-11-23
> **NoaHall said:**
> 
2) How well does Skype work with it?
Use the Beta version of Skype. It works great with Pulse Audio

> 3) Is Synaptic completely missing? I mean, have they just got rid of it completely?
No, it's still there.

> 4) I don't like the sound of this software center. Can I remove it?
Yes, but it will take the "ubuntu-desktop" package with it.

---

### Post by garikaib on 2009-11-23
Why on earth do you want to remove the software center? It a  great tool and does not interfere with synaptic

---

### Post by Spike-X on 2009-11-23
> **NoaHall said:**
> About Karmic.

1) Is it true Songbird doesn't work on it?

No, that is not true. I use Songbird, and it works fine.

> **NoaHall said:**
> 2) How well does Skype work with it?

I can't answer this one.

> **NoaHall said:**
> 3) Is Synaptic completely missing? I mean, have they just got rid of it completely?

No. It's still there, same as always.

> **NoaHall said:**
> 4) I don't like the sound of this software center. Can I remove it?

Just don't use it. It's simply a more new-user-friendly version of Synaptic or Add/Remove programs.

---

### Post by ZankerH on 2009-11-23
Synaptic is still there, software centre can and should be removed. Songbird and Skype work.

---

### Post by Prodigal Son on 2009-11-23
> 1) Is it true Songbird doesn't work on it?Mine works.

> 2) How well does Skype work with it?Better than on Jaunty ( haven't had any problems at all ).

> 3) Is Synaptic completely missing? I mean, have they just got rid of it completely?No, it's still there.

> 4) I don't like the sound of this software center. Can I remove it?You can do whatever you want. Like other applications, it's just a package ( software-center ).

---

### Post by 3rdalbum on 2009-11-23
Skype in Karmic with Pulseaudio works a little differently. You use the Pulseaudio volume control or padevchooser to set up what devices you want to use in Skype. You don't tell Skype what devices to use.

About 25% of complaints about Pulseaudio are due to this change; people see that Skype itself doesn't let you choose the input and output devices and think that it's not working properly.

---

### Post by ZankerH on 2009-11-23
> **BradSterling said:**
> Ubuntu is an operating system built by a worldwide team of expert developers. It contains all the applications you need: a web browser, office suite, media apps, instant messaging and much more. 
   Ubuntu is an open-source alternative to Windows and Office.
__________________
[eco diagnostic pret taux zero immobilier | ](http://prettauxzero.org/)[Credit pret a taux zero 0 | ](http://prettauxzero.org/)[Pret taux zero a 0](http://prettauxzero.org/pret-taux-zero/)

cool story, bro

---

### Post by NoaHall on 2009-11-23
> **3rdalbum said:**
> Skype in Karmic with Pulseaudio works a little differently. You use the Pulseaudio volume control or padevchooser to set up what devices you want to use in Skype. You don't tell Skype what devices to use.

About 25% of complaints about Pulseaudio are due to this change; people see that Skype itself doesn't let you choose the input and output devices and think that it's not working properly.

This is the same with the beta version on Jaunty.

---

### Post by samh785 on 2009-11-23
> **NoaHall said:**
> About Karmic.

1) Is it true Songbird doesn't work on it?
2) How well does Skype work with it?
3) Is Synaptic completely missing? I mean, have they just got rid of it completely?
4) I don't like the sound of this software center. Can I remove it?
2) Skype works just fine on Karmic. Make sure that you use the new beta version though (it has pulse audio support)

---

### Post by samh785 on 2009-11-23
> **FuturePilot said:**
> it will take the "ubuntu-desktop" package with it.
Isn't the ubuntu-desktop package just a meta package? I might be mistaken, but that was what I thought it was.

---

### Post by RiceMonster on 2009-11-23
> **samh785 said:**
> Isn't the ubuntu-desktop package just a meta package? I might be mistaken, but that was what I thought it was.

Yes, but if ubuntu-desktop is removed, everything it brings in is removed.

---

### Post by 23meg on 2009-11-23
> **RiceMonster said:**
> Yes, but if ubuntu-desktop is removed, everything it brings in is removed.

```
$sudo apt-get remove software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  software-center ubuntu-desktop
0 upgraded, 0 newly installed, 2 to remove and 16 not upgraded.
After this operation, 1,540kB disk space will be freed.
Do you want to continue [Y/n]?
```

---

### Post by RiceMonster on 2009-11-23
> **23meg said:**
> ```
$sudo apt-get remove software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  software-center ubuntu-desktop
0 upgraded, 0 newly installed, 2 to remove and 16 not upgraded.
After this operation, 1,540kB disk space will be freed.
Do you want to continue [Y/n]?
```

Ooops, my bad. Looks like that's been fixed since I last checked.

---

### Post by nobodysbusiness on 2009-11-23
I installed Songbird from Getdeb.net and there was a little problem running it. I fixed it by changing the /usr/bin/songbird file to this:

```
#!/bin/sh
export LD_BIND_NOW=1
cd /usr/share/Songbird
./songbird

```

---

