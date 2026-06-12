---
title: "Cinnamon on Precise"
date: 2012-01-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by VMC on 2012-01-10
I just installed Cinnamon on the current Precise. It worked so well on Fedora16, I thought I would try it on Precise. 25megs of gnome-shell packages later and logout and back in to Cinnamon. Works great.

There is a ppa supposedly for Precise, but it failed 404 every time I tried it.

I know about the gnome2 project for Ubuntu and Precise, but I wanted something current. Oddly, Cinnamon doesn't work that well on Mint12. At least for me. Or rather it works better on Fedora16.

I don't like Unity, but love Ubuntu's speed and its community. But now, at least I have both, or rather three options to try.

Anyone else try Cinnamon on Precise?

---

### Post by JOHNNYG713 on 2012-01-10
:D Runs fine in precise ! I think it needs some more polish, but it has a lot of potential !
Here is the ppa [https://launchpad.net/~merlwiz79/+archive/cinnamon-ppa]("https://launchpad.net/%7Emerlwiz79/+archive/cinnamon-ppa")  < open software sources and set it to oneiric, or you will get a 404 error !
It has two .debs that install Cinnamon! and by adding the ppa to your software sources you will be able to get all the updates !

---

### Post by cbowman57 on 2012-01-10
Yep, tried it on both Precise & Arch.

Doesn't suit me, at least not in it's current iteration, I prefer the gnome shell.

---

### Post by VMC on 2012-01-11
> **JOHNNYG713 said:**
> :D Runs fine in precise ! I think it needs some more polish, but it has a lot of potential !
Here is the ppa [https://launchpad.net/~merlwiz79/+archive/cinnamon-ppa]("https://launchpad.net/%7Emerlwiz79/+archive/cinnamon-ppa")
It has two .debs that install Cinnamon! and by adding the ppa to your software sources you will be able to get all the updates !

Yes, that's the one that failed. I kept getting 404's, so I just installed the two cinnamon files myself after I installed gnome-shell.

The benefit of installing cinnamon on a gnome-shell distro, like Fedora, Mine12, is all one needs are the two small files two install.

---

### Post by mc4man on 2012-01-11
> **VMC said:**
> 

There is a ppa supposedly for Precise, but it failed 404 every time I tried it.
?
That ppa is oneiric, if you add with sudo add-apt-repository ppa:merlwiz79/cinnamon-ppa then you'll get 404, you'd need to edit the source entries to oneiric to use.

---

### Post by VMC on 2012-01-11
> **mc4man said:**
> That ppa is oneiric, if you add with sudo add-apt-repository ppa:merlwiz79/cinnamon-ppa then you'll get 404, you'd need to edit the source entries to oneiric to use.

I thought I did. Somewhere along the line I was told how to. Thanks for the tip.

---

### Post by cecilpierce on 2012-01-13
Cinnamon was removed in one of the upgrades and cant seem to put it back ???
The following packages have unmet dependencies:
 cinnamon : Depends: libecal1.2-10 (>= 3.2.2)
            Depends: libedataserver1.2-15 (>= 3.2.2)
E: Unable to correct problems, you have held broken packages.

Any sugestions ?
Thanks  :confused:

---

### Post by TerryNewton on 2012-01-13
> **cecilpierce said:**
> Cinnamon was removed in one of the upgrades and cant seem to put it back ???
The following packages have unmet dependencies:
 cinnamon : Depends: libecal1.2-10 (>= 3.2.2)
            Depends: libedataserver1.2-15 (>= 3.2.2)
E: Unable to correct problems, you have held broken packages.

Any sugestions ?
Thanks  :confused:

The packages were renamed, libecal1.2-10 is now libecal-1.2-10 etc.
Cinnamon 1.1.3 was still incomplete (but promising) so I just let
Synaptic remove it to complete the updates... but LibreOffice failed
to install - something seems to be messed up with the repositories
at the moment.

---

### Post by cecilpierce on 2012-01-13
> **TerryNewton said:**
> The packages were renamed, libecal1.2-10 is now libecal-1.2-10 etc.
Cinnamon 1.1.3 was still incomplete (but promising) so I just let
Synaptic remove it to complete the updates... but LibreOffice failed
to install - something seems to be messed up with the repositories
at the moment.

Thanks for the reply, I thought it was just something I screwed up.
Update Manager runs all the time even after I update, just wait and see what happens I guess,
I still have Mint installed to fiddle with   :P

---

### Post by TerryNewton on 2012-01-13
> **cecilpierce said:**
> Thanks for the reply, I thought it was just something I screwed up.
Update Manager runs all the time even after I update, just wait and see what happens I guess,
I still have Mint installed to fiddle with   :P

Investigated a bit more... fixed the issue with LibreOffice by emptying the /usr/lib/libreoffice/basis3.4/program directory (or something like that, known bug) then running apt-get install -f, that's another issue but possibly semi-related. The broken libecal dependency isn't directly specified by the cinnamon package but in one of the other sub-dependencies, and cinnamon does work if the install is forced but then the package system flags it as broken. This should correct itself once all the packages affected by the renamed libecal package are sorted - the real question is why was libecal (and some others) renamed to begin with? That's a sure way to break stuff.. maybe just a mistake. But it's alpha, expect these things :-)

Edit - the libecal dependency was in fact in the deb, my fault didn't see it. But no matter, there is now a WebUpd8 PPA for Cinnamon for Precise and it seems to work fine, no need to use a downloaded deb and no dependency issues. ATM anyway...

---

### Post by cecilpierce on 2012-01-13
I think precise is jelious of mint, haha!
When I tried to reinstall cinnamon it wated to take out gnome-shell along with alot of other things.

---

### Post by cbowman57 on 2012-01-13
Well I'm using it but it's pretty rough compared to Arch right now, so I don't use it much.

Figured I'd go for broke, running it with ricotz/testing & xorg-edgers switched on.  Some strangeness ( doesn't display hovered & active popup-menus correctly)  but it's pretty solid.

---

### Post by VMC on 2012-01-13
It runs best on Fedora 16, for me. Cinnamon 1.1.4 is soon to come, with mutter to replace muffin.

Regarding Ubuntu Precise, what I do is install the current each day. I have both gnome-shell and cinnamon deb files in one folder. Then just:```
sudo dpkg -i *
```
on the folder and everything installs in one fell swoop.

---

### Post by JOHNNYG713 on 2012-01-21
> **VMC said:**
> Yes, that's the one that failed. I kept getting 404's, so I just installed the two cinnamon files myself after I installed gnome-shell.

The benefit of installing cinnamon on a gnome-shell distro, like Fedora, Mine12, is all one needs are the two small files two install.

You have to open software sources and change the repo to oneiric !! :P 
When you load a repo through terminal it automatically sets that repo to the running disro if it is not stated in the command line !! :D  same goes with upgrading your distro, thats why third party reos are disabled on upgrade, you must set the third party repos to the old ditro if there is not an up dated one, or you get 404 !!! JFYI :D

---

### Post by bmbaker on 2012-01-23
there is a precise repo now :-)
[https://launchpad.net/~merlwiz79/+archive/cinnamon-ppa?field.series_filter=precise](https://launchpad.net/~merlwiz79/+archive/cinnamon-ppa?field.series_filter=precise)

---

### Post by JOHNNYG713 on 2012-01-23
> **bmbaker said:**
> there is a precise repo now :-)
[https://launchpad.net/~merlwiz79/+archive/cinnamon-ppa?field.series_filter=precise]("https://launchpad.net/%7Emerlwiz79/+archive/cinnamon-ppa?field.series_filter=precise")

Very cool !! :guitar:  I think Cinnamon  might be one to watch !! looks promising ! :KS

---

### Post by bmbaker on 2012-01-23
ya it is a good mix but i really prefer gnome-shell :-)

---

### Post by t.rei on 2012-01-26
This is strange. I am getting a collision between cinnamon and cinnamon-session and -settings when I tried to install it today (precise).

---

