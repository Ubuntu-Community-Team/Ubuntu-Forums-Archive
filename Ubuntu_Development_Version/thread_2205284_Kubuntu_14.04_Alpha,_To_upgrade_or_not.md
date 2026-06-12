---
title: "Kubuntu 14.04 Alpha, To upgrade or not?"
date: 2014-02-13
forum: Ubuntu Development Version
---

### Post by su:bhatta on 2014-02-13
Hi, I am posting after sometime, so If i post in the wrong place, will be glad if that mistake is corrected.

I had downloaded Kubuntu 14.04 Alpha, 05-02-2014 iso and installed. Everything worked fine out of the box.
In fact, thanks to 3.13 kernel, since 12.04 this is the first time I did not have to use 'nomodeset' for a live session :)

But Monday, On opening Muon Discover I found 'updates' for installed apps which I did and borked my system. Partial update or not, it was not clearly mentioned.

I reinstalled. 

Now today I am having a notification : 'A newer version of Kubuntu is available'. The screenshot of the authorisation box opened is attached.

My question, Is this a 'partial-update' or can I go for it safely ?[ATTACH=CONFIG]250301[/ATTACH]

---

### Post by cariboo on 2014-02-13
While running a development release, it may not be to wise running the default update tools, unless you intend on creating a bug report. I just finished updating my Ubuntu Gnome-shell install for the first time in two weeks. I usually use synaptic, as it is just a couple of clicks to do an update, but this time, synaptic let me down, as it took to long to register all the updates (I'm running gnome-shell from a 32GiB usb thumb drive). I used:

```
sudo dist-upgrade
```

after having to answering **Y** three times during the upgrade process, it finally finished, with a few errors, that seem to be resolved as the upgrade progressed.

Before you reboot, I'd suggest you make sure the upgrade has been completed, by opening a terminal, and running:

```
 sudo apt-get -f install
```

even if the upgrade seemed to finish successfully. In my experience it is always better to be a bit extra cautious, than to just assume things have gone the way they should.

---

### Post by Bucky Ball on 2014-02-13
I bang in all updates, upgrades, dist-upgrades everyday! But then, my 14.04 install is for testing as that's what 14.04 is at the moment. I have it only to update and check, not for everyday stuff.

It's not necessarily going to be a smooth ride for the next couple of months so if you're using 14.04 as a production machine or for everyday work or reliability of any kind, I wouldn't. ;)

---

### Post by su:bhatta on 2014-02-13
Thanks for the quick responses, ah, the reason why i like being here... the help :)

In the last 13.10 cycle, I was trying out UbuntuGnome from September,  and if I remember correctly, it told me 'there are partial updates  available'.
Whenever the word 'partial' was written, I avoided. Was a  smooth ride, one thing I learned from 'grahammechanical' and reading up  U +1 !
Since this time I did not get it('partial updates available'), I am a little confused.


And, nah, this ain't my production machine... this installation is for trying out the flavors, I am currently trying out Ubuntu Studio 14.04  too...

And, my Wheezy 7.3, is my fallback :)

---

### Post by grahammechanical on 2014-02-13
I am not using Kubuntu so I am not familiar with the ways of Muon Discover. It is usual to get updates when we install an Alpha or a daily image. If you re-installed the Alpha image there will be updates to bring it up to date with the changes since the Alpha image was released.

I am using Ubuntu and I update every day using Update Manager (Software Updater) and it has been giving me this message for some weeks.

> Not all updates can be installed. Run Partial Upgrade, to install as many updates as possible. This can be caused by

* A previous upgrade which did not complet
* Problems with some of the installed software
* Unofficial software packages not provided by Ubuntu
* Normal changes of a pre-release version of Ubuntu

Despite the last comment I never click Partial Upgrade. I always click Continue and then the update process continues as usual. It is normal to get the Partial Upgrade message for a development cycle.

Try running the update/upgrade commands in a terminal. The update/upgrade will not take place until you have entered Y. I never update if it is going to remove ubuntu-desktop. This may be happening to the Kubuntu version of the desktop.

```
sudo apt-get update
suso apt-get upgrade
```

One of the things I like about Software Updater is that it has easily understood labels compared with what we used to get. And we can untick a package if we are worried about it. We also get information about what is being held back.

Regards.

---

### Post by Bucky Ball on 2014-02-13
Don't forget

sudo apt-get dist-upgrade 

... at the end of all that. Nothing much happened with the first two the other day but this brought a bunch of stuff.

---

### Post by su:bhatta on 2014-02-14
Thanks again Grahammechanical & Bucky Ball. I will use the Terminal this time. 

Currently, playing with Compiz on my Ubuntu Studio 14.04 install and I must say, it is much less buggy than when I tried it last time, 13.04 I think. 

And yes, quite loving the cusomizations that can be done with Xfce and its light on resources, next best thing after FVWM I run on my Wheezy install :)

---

