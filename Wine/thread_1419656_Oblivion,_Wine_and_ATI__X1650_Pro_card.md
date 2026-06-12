---
title: "Oblivion, Wine and ATI  X1650 Pro card"
date: 2010-03-02
forum: Wine
---

### Post by ThePinkWitch on 2010-03-02
I tried to Install and play Oblivion with wine and the game ran excruciatingly slow and choppy. Is there anyone who knows if Oblivion will run properly with my graphics card through Wine? I've only been using Ubuntu a short while and I'm not really cluey with the techs of setting up graphics and games. Thanks for any help. :p

---

### Post by handy on 2010-03-03
In the past, Oblivion had the reputation of being an incredibly demanding game, as far as GPUs are concerned.

These days, if your GPU won't handle Oblivion, then in relation to the current crop of games, you are kind of left back in the retro' dark ages of games.

Your R500 GPU, is most likely not capable of handling Oblivion.

The only tips I can offer are for you to turn every graphic setting to its lowest & see how you go then, if it is ok, try turning up some of the settings a notch at a time & keep the settings whilst ever the game is still running at a playable frame rate.

---

### Post by namluc on 2010-03-03
there is a mod called oldblivion that you might want, it lowers the specs substantially

---

### Post by Progressive on 2010-03-03
Back when the catalyst binary blob was supported for R500 series, my X1800 ran ok but with [some glitching]("http://ubuntuforums.org/showthread.php?t=984826"). Don't know if recent versions of wine corrected that, as it may have been a driver issue. You would need to revert to Gutsy or so to use it. If you don't wish to do that, your only option is the open source drivers.

The open source divers are superior in many senses, and are progressing quickly, but as of this moment I can barely get Morrowind to run, let alone Oblivion, even with oldblivion and every tweak in the book.

I have been keeping up with Wine's progress, and in the next development release ([on friday]("http://bugs.winehq.org/show_bug.cgi?id=21515#c99")) we will likely see support for Gallium3D which means the next generation open source graphics drivers will work.

The only way to get acceptable graphics performance is with the absolute bleeding edge. If you are obsessed like me, you might want to set aside a partition of your hard drive to test out Lucid Lynx. I have Lucid Lynx and actually custom compiled a patched version of the 2.6.33 kernel on top of that. Then I installed the [xorg-edgers PPA]("https://launchpad.net/~xorg-edgers/+archive/ppa"). 

Then, even though xorg-edgers includes a daily snapshot of mesa, I have compiled mesa from git using [these instructions]("http://www.phoronix.com/forums/showpost.php?p=109708&postcount=2"). After the configure line you will need to do 

```
make
```

and 

```
sudo make install
```

The last line will need to be executed whenever you want to switch from classic mesa to Gallium3D. Gallium3D is surprisingly stable with a bleeding edge setup, but still a bit glitchy. Classic mesa is more stable, but less feature-full and no longer making progress since it is being superceded by Gallium3D.

After installing everything mentioned above, plus tons of tweaks, mods, and so forth, I am still unable to get more than glitchy unplayable garbage in Oblivion. Morrowind renders fine, but it is slow. However, I can notice improvement literally *daily* and I can easily just do a 

```
git pull
```

in my mesa directory every day whenever I see some progress [here]("http://cgit.freedesktop.org/mesa/mesa/")

Lucid will be out soon enough, though even that wont have the 2.6.33 kernel with the needed graphics enhancements. The first Lucid +1 alpha will have it, and might even have 2.6.34. Waiting is an easier option, though learning how to compile a kernel is sort of a novelty... and you can compile it for your CPU, to get more efficiency. If you have Core2 or i7 for instance.

I have left Plato's allegorical cave, and I guess for now I might recommend waiting in the shadows a bit and watching the primitive light show, because outside there is some crazy glitching goin on. ;-)

Though the xorg-edgers PPA mentioned above will work just fine on Karmic, and will work better than what you have now, it will just be slower than what I have.

---

### Post by handy on 2010-03-03
Best thing for the OP to do, is wait patiently for the development kernels, mesa & associated packages to come on down to Ubuntu stable.

Playing in -git land won't necessarily solve your problem, as you will need a little luck to catch just the right version that works for you & not the next version that doesn't...

---

### Post by Progressive on 2010-03-03
The Gallium3D [detection code]("http://source.winehq.org/git/wine.git/?a=commit;h=74a059d21b36b7aa0b852955e9254e7d0fbf7d8b") made it into Wine... yay!

They even used my coding suggestion! :guitar:

---

### Post by handy on 2010-03-03
> **Progressive said:**
> The Gallium3D [detection code]("http://source.winehq.org/git/wine.git/?a=commit;h=74a059d21b36b7aa0b852955e9254e7d0fbf7d8b") made it into Wine... yay!

They even used my coding suggestion! :guitar:

Congratulations, & good news all round. :)

---

### Post by ThePinkWitch on 2010-03-04
> **handy said:**
> In the past, Oblivion had the reputation of being an incredibly demanding game, as far as GPUs are concerned.

These days, if your GPU won't handle Oblivion, then in relation to the current crop of games, you are kind of left back in the retro' dark ages of games.

Your R500 GPU, is most likely not capable of handling Oblivion.

The only tips I can offer are for you to turn every graphic setting to its lowest & see how you go then, if it is ok, try turning up some of the settings a notch at a time & keep the settings whilst ever the game is still running at a playable frame rate.

The game runs beautifully with WinXP :)

---

### Post by ThePinkWitch on 2010-03-04
THANKYOU EVERYONE. I really appreciate the replies and suggestions. I'm sorry I'm cyber-challenged and have absolutely no clue as to how to try those suggestions lol. I'll just play it on WinXP for now. I was hoping to ditch the dual boot thing but I'll have to wait I think. I still have a couple of issues to solve with ubuntu. Thanks again :)

---

### Post by gsmanners on 2010-03-04
I think you made the right decision. Wine is good, but IMHO it isn't quite there just yet.

---

### Post by ThePinkWitch on 2010-03-04
> **Progressive said:**
> Back when the catalyst binary blob was supported for R500 series, my X1800 ran ok but with [some glitching]("http://ubuntuforums.org/showthread.php?t=984826"). Don't know if recent versions of wine corrected that, as it may have been a driver issue. You would need to revert to Gutsy or so to use it. If you don't wish to do that, your only option is the open source drivers.

The open source divers are superior in many senses, and are progressing quickly, but as of this moment I can barely get Morrowind to run, let alone Oblivion, even with oldblivion and every tweak in the book.

I have been keeping up with Wine's progress, and in the next development release ([on friday]("http://bugs.winehq.org/show_bug.cgi?id=21515#c99")) we will likely see support for Gallium3D which means the next generation open source graphics drivers will work.

The only way to get acceptable graphics performance is with the absolute bleeding edge. If you are obsessed like me, you might want to set aside a partition of your hard drive to test out Lucid Lynx. I have Lucid Lynx and actually custom compiled a patched version of the 2.6.33 kernel on top of that. Then I installed the [xorg-edgers PPA]("https://launchpad.net/~xorg-edgers/+archive/ppa"). 

Then, even though xorg-edgers includes a daily snapshot of mesa, I have compiled mesa from git using [these instructions]("http://www.phoronix.com/forums/showpost.php?p=109708&postcount=2"). After the configure line you will need to do 

```
make
```

and 

```
sudo make install
```

The last line will need to be executed whenever you want to switch from classic mesa to Gallium3D. Gallium3D is surprisingly stable with a bleeding edge setup, but still a bit glitchy. Classic mesa is more stable, but less feature-full and no longer making progress since it is being superceded by Gallium3D.

After installing everything mentioned above, plus tons of tweaks, mods, and so forth, I am still unable to get more than glitchy unplayable garbage in Oblivion. Morrowind renders fine, but it is slow. However, I can notice improvement literally *daily* and I can easily just do a 

```
git pull
```

in my mesa directory every day whenever I see some progress [here]("http://cgit.freedesktop.org/mesa/mesa/")

Lucid will be out soon enough, though even that wont have the 2.6.33 kernel with the needed graphics enhancements. The first Lucid +1 alpha will have it, and might even have 2.6.34. Waiting is an easier option, though learning how to compile a kernel is sort of a novelty... and you can compile it for your CPU, to get more efficiency. If you have Core2 or i7 for instance.

I have left Plato's allegorical cave, and I guess for now I might recommend waiting in the shadows a bit and watching the primitive light show, because outside there is some crazy glitching goin on. ;-)

Though the xorg-edgers PPA mentioned above will work just fine on Karmic, and will work better than what you have now, it will just be slower than what I have.

Thanks so much for all the info but that looks way outta my league :D I'm an Ubuntu noob and don't know my way at all when it comes to tweaking and modding anything on computers. :rolleyes: Cheers :)

---

### Post by ThePinkWitch on 2010-03-04
> **gsmanners said:**
> I think you made the right decision. Wine is good, but IMHO it isn't quite there just yet.

Thanks :) I think for me it is. I'm just not experienced enough to mess with all the stuff needed to try to get it working.

---

### Post by handy on 2010-03-05
> **ThePinkWitch said:**
> Thanks :) I think for me it is. I'm just not experienced enough to mess with all the stuff needed to try to get it working.

All that can be gained by tweaking now, & a whole lot more, will become mainstream this year.

Hopefully the Ubuntu released in October will have at least kernel .34, which will see the implementation of power management & a whole lot more for the open-source ATi drivers.

Here is where the ATi OSS support is up at the moment:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

---

### Post by Bwathke on 2010-03-05
What version do you have? 1.0 (No patches or GotY) is rated as Platinum. If you have a patched version its Bronze to Garbage and GotY is Silver to Bronze. Your best bet is to get a console version if you can. I got it for the Xbox 360 for around 20$ but if you dont or cant do that then try running it in -opengl. I hope this helps great game I can understand why you want to fix it lol =)

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3150](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3150)

---

### Post by ThePinkWitch on 2010-03-06
> **Bwathke said:**
> What version do you have? 1.0 (No patches or GotY) is rated as Platinum. If you have a patched version its Bronze to Garbage and GotY is Silver to Bronze. Your best bet is to get a console version if you can. I got it for the Xbox 360 for around 20$ but if you dont or cant do that then try running it in -opengl. I hope this helps great game I can understand why you want to fix it lol =)

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3150](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3150)

I have Goty version with Shivering Isles installed. It runs great on WinXP in 1400X900 resolution. I want to get that and Morrowind working because that's the only reason I boot up XP these days since I put Karmic on here. Apart from a couple of issues I can do almost everything else on Ubuntu. I tried Oblivion on Ubuntu but the frame rate was laughable. Like 1 PM lol. OK slight exaggeration :D Maybe if I knew what I was doing and could understand what I was reading in the WINE forum I may have been able to get it going but it was all Swahili to me :D Looking forward to later when everyone says it could be a lot better in the new version :)

---

### Post by ThePinkWitch on 2010-03-06
> **handy said:**
> All that can be gained by tweaking now, & a whole lot more, will become mainstream this year.

Hopefully the Ubuntu released in October will have at least kernel .34, which will see the implementation of power management & a whole lot more for the open-source ATi drivers.

Here is where the ATi OSS support is up at the moment:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

Cool :D (Clapping hands and dancing on tippy toes) :D

---

