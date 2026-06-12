---
title: "Back to Ubuntu, again"
date: 2009-08-03
forum: Testimonials &amp; Experiences
---

### Post by drudogg on 2009-08-03
i have been using linux off and on for a few years. i went away for a while, because of wireless drivers, but i came back with a vengance a few months ago. i am definetly a linux newb, but i like it a lot.

i have more computers in my house than i really need, but the main 2 have ubuntu 9.04 on them. also an extra older laptop with 8.04 for my son. i find myself using ubuntu more than leopard, xp, vista, or win 7 rc. i do have a quad boot on my desktop, so i have to keep up with windows for my wife/kids, but i don't usually boot into windows, unless i need something particular that i haven't found in linux yet.  (such as a good video encrypter/burner, or formatting a flash card) i guess if i could run nero on linux i would be happy. 

at work a guy came in and struck up a linux conversation. he came back and gave me a mint 6 disc. i tried it, and really liked it a lot, but had a few probs on multiboot with it, and decided to try Ubuntu again. thanks to support from this forum i now have 2 laptops exclusively running Ubuntu, and also have it on a spare drive in my desktop.  out of 6 computers in my house (4 of which are mine) 3 have linux on them. the other 3 - one osx leopard, one XP, and 1 win 7 rc1. the windows exclusive ones are my stepson's.

have tried fedora, mint, dreamlinux, DSL, arch, xubuntu, ubuntu, a few enlightenment builds, and have also run ubuntu with LXDE, which is great looking, lighter, faster, and not so foreign from gnome.

anyway, in addition to telling anyone who may want to know, i was curious how many of you are running only linux, what builds, and who is running windows also.  if anyone wants to point me in the right direction on formatting a flash card or flashdrive (other than gparted, which keeps giving me errors) please let me know.

---

### Post by lvleph on 2009-08-03
I have vista sitting on a partition, but it has not been used since it was installed. In fact, it has no programs installed and no drivers installed yet. I have a waranty on my comp that I have to bring it in for. It is there so that they can't claim it is the OS. I do have XP in VirtualBox.

EDIT: For formatting: In terminal type 
```
 man dd 
```

---

### Post by hetx on 2009-08-04
Remember to unmount the drive before trying to format it in gparted!

I run Ubuntu on my main desktop, #! CrunchBang on one laptop and Arch with OpenBox on my EEE. I admit I spend way too much time playing around with different distros, but how can one help oneself with the amount of choice in the Linux community!

Also tried openSUSE, eeeBuntu, EasyPeasy, Fedora, Puppy Linux, Zenwalk and Slackware. Keep coming back to Ubuntu when it comes to a full desktop though. As long as you have a decent computer it runs smooth, works out of the box and has a great community!

---

### Post by ukripper on 2009-08-04
> **drudogg said:**
> (such as a good video encrypter/burner, or formatting a flash card) i guess if i could run nero on linux i would be happy. 



You need to try K3b burner(it is in ubuntu repos, just use sudo apt-get install k3b) which is by far superior than nero in terms of functionality. I am surprised this is holding you back.

---

### Post by Viva on 2009-08-04
There is a version of Nero for linux

---

### Post by HappyFeet on 2009-08-04
You need open gparted with:
```
gksudo gparted
```
Then unmount the volume you want to format. (from within gparted)
Has always worked for me.

Glad to hear you are enjoying it.

---

### Post by Maheriano on 2009-08-04
> **drudogg said:**
> if anyone wants to point me in the right direction on formatting a flash card or flashdrive (other than gparted, which keeps giving me errors) please let me know.

If you ever figure this out, let me know. I've failed on every attempt at trying to format a flash drive, they don't even show up in gparted at all.

K3B is much, much better than Nero (to me), seems simpler to use. Just go to a command terminal and type:
```
sudo apt-get install k3b
```
...or go to Add/Remove and search for it.

And to install gparted, use:
```
sudo apt-get install gparted
```
...and to run it, use:
```
sudo gparted
```

---

### Post by solwic on 2009-08-04
I'm running Linux only. Ubuntu 9.04.  No dirty Windows on this puppy....  :)

---

### Post by Maheriano on 2009-08-04
> **HappyFeet said:**
> You need open gparted with:
```
gksudo gparted
```
Then unmount the volume you want to format. (from within gparted)
Has always worked for me.

Glad to hear you are enjoying it.

But once you unmount the volume, how do you format it? Once it's unmounted there's nothing to click on to select to format. It's gone.

---

### Post by drudogg on 2009-08-04
well any software will have issues, because regardless of who makes it, it is MAN-MADE. and nobody is perfect. 

i have tried the gparted and cannot get it to work right... but i will give it another go. i will say that windows makes this feature easier. and the K3B i will look it up. i tried a few programs one acted like it worked, but gave me an unplayabe disc. i was just trying to burn a couple of .mov files to a vcd or dvd. also looked up the nero for linux, and it is 20 euros...

only complaint i have about ubuntu is that some things (hardware) are a bit of a pain to get working. i can't use the card reader or s-video on my laptop, because of this. 

i appreciate all of the responses and advice. i can't find much info on the "man dd" command mentioned earlier. can someone explain this or point me to some more info?

---

### Post by HappyFeet on 2009-08-04
> **Maheriano said:**
> But once you unmount the volume, how do you format it? Once it's unmounted there's nothing to click on to select to format. It's gone.

Then try it mounted.

---

### Post by drudogg on 2009-08-04
> **Maheriano said:**
> But once you unmount the volume, how do you format it? Once it's unmounted there's nothing to click on to select to format. It's gone.


if you open gparted gui, and select the card, the right click on it and choose unmount. then you can delete the partition, create new partition and format. i tried to just right click and do format, but it failed. i did get it to work the way i just said though. 


thanks for you others who told me what to do! and k3b looks pretty good so far. i have not tried it out yet, just looked at it.

---

### Post by Maheriano on 2009-08-05
> **drudogg said:**
> if you open gparted gui, and select the card, the right click on it and choose unmount. then you can delete the partition, create new partition and format. i tried to just right click and do format, but it failed. i did get it to work the way i just said though.
I've tried this. When I right click and hit UNMOUNT, the whole partition and card disappear from the GUI. There's nothing to format, it's unmounted....gone. There's nothing to click on.

---

### Post by por100pre1 on 2009-08-05
> **drudogg said:**
> i tried a few programs one acted like it worked, but gave me an unplayabe disc. i was just trying to burn a couple of .mov files to a vcd or dvd.

Are you trying to *encode* DVDS? If so try using *Devede*. It create ISO files that can be burned with any burner to create video DVDs and Video CDs.

---

