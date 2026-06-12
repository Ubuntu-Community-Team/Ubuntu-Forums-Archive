---
title: "Is there nay way to install Photoshop CS5 ?"
date: 2011-05-18
forum: Wine
---

### Post by Udavid on 2011-05-18
Hey forums,
I would not never return to Windows if I could use Photoshop CS 5 in my Ubuntu. Is there any way to do it?
I know there are a lot of discussions about those kinds of questions. and some of them are totally reasonable. So Adobe has its own consideration too. 
):P

---

### Post by josephmills on 2011-05-18
why not gimp? but if you need ps try it in a virtual box dont know if it runs in wine or crossover

---

### Post by Gone fishing on 2011-05-18
Crossover office? 

[http://www.codeweavers.com/compatibility/browse/name/?app_id=7715](http://www.codeweavers.com/compatibility/browse/name/?app_id=7715)

---

### Post by Hedgehog1 on 2011-05-18
Right now, you have two choices:

Dual boot for CS5 (and get GPU Speed enhancement if your hardware supports it) or run CS5 in a virtual machine (like Vbox) and you will no get GPU speed enhancement even if your hardware does Support it.

GIMP does a number of useful basic tasks. Using it for these tasks works fine. The folks who keep asking 'what about GIMP' are not Photoshop power users, and honestly don't know what all you can do in PS.

I dual boot for CS5 and Sony Vegas.  At this time there are no professional level non-linear editors in Linux (this is about to change soon). So I dual boot for these 2 tasks, and use Ubuntu for everything else.

It works fine.

***The Hedge***

:KS

---

### Post by Kaplan Crunch on 2011-05-18
I Agree with Hedge, Dual Boot 'em! I tried CS4 on the VM and it was really finicky.  I definitely keep my art stuff and my linux stuff separate! At least for the moment ;)

---

### Post by jre6 on 2011-05-18
You can also use Wine in Ubuntu to install Photoshop CS5. To install wine, type the following in a terminal (with an active internet connection, and the second statement is optional, if you have Synaptic installed): 
```

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get install synaptic
sudo synaptic

```Now, click the Reload button. After all the files have been downloaded, quit synaptic and type this in the terminal:
```

sudo apt-get install wine1.3

```Having done this, you can install CS5 by double clicking the installer, or through the terminal (replacing foobar.exe with the location of the installer):
```

wine foobar.exe

```
There may be a few minor problems here and there while using CS5, but it should work fine for most of the time.

---

### Post by josephmills on 2011-05-18
> **Hedgehog1 said:**
> 

GIMP does a number of useful basic tasks. Using it for these tasks works fine. The folks who keep asking 'what about GIMP' are not Photoshop power users, and honestly don't know what all you can do in PS.

not a power user huh? I have used ps for close to 4 years and gimp for six months and Have only found about 10 things that I can not do in gimp and that is because I am not use to it the theory is there how DARE you call us non-power users shame on you sir shame on you. If you want gimp to get better say then photoshop you need to talk to the dev of gimp its self an tell them your troubles. you also should use it. It is the open source. And cents you are such a power user I would love to here what gimp wont do that photoshop will please enlighten the n00b here please blind statements start wars my fine sir:o

---

### Post by uRock on 2011-05-18
Personally, I do not see why folks recommend Photoshop users to use GIMP. They are completely different. It is the same as telling MS Office users to use OpenOffice.

I used to edit photos with PS and I have not been able to get the same usability out of GIMP.

The OP wants PS on their system, so lets help him/her get what they want. :P

Cheers & Beers,
uRock

---

### Post by Elfy on 2011-05-18
Thread moved to Wine.

---

