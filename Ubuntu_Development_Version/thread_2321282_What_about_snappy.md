---
title: "What about snappy?"
date: 2016-04-21
forum: Ubuntu Development Version
---

### Post by Chanath on 2016-04-21
If snappy is available in 16.04, how to get it working?

---

### Post by philinux on 2016-04-21
Maybe this.

[http://www.webupd8.org/2016/04/ubuntu-1604-lts-to-offer-updates-via.html](http://www.webupd8.org/2016/04/ubuntu-1604-lts-to-offer-updates-via.html)

---

### Post by mc4man on 2016-04-21
Try - 
```
sudo apt install snapd
```
```
snap find
```
sudo snap install pick one from ^

Ex. in screen

---

### Post by ventrical on 2016-04-21
wow... hmmmm .. that was fast..

---

### Post by mc4man on 2016-04-21
So after installing the clock app nowhere to be found in an ubuntu session, system (gnome) doesn't have /snap/ in it's binary or .desktop path.
hacky solution in screen, then shows in Dash with a search of clock (if one can see due to forum downsizing (a bit archaic

---

### Post by grahammechanical on 2016-04-21
May I draw everyone attention to this thread?

[http://ubuntuforums.org/showthread.php?t=2321161](http://ubuntuforums.org/showthread.php?t=2321161)

EDIT

Earlier today I was able to install both the calculator & the clock app. They appeared in the Dash. I cannot see much else in the snap store that is suitable for a desktop UI. The ability to install these snaps from Ubuntu Software is something that will happen later on in the year. Needs some useful snap apps as well. I would like to see how the intended Firefox snap works in comparison with the deb version.

Regards.

---

### Post by ventrical on 2016-04-21
> **mc4man said:**
> So after installing the clock app nowhere to be found in an ubuntu session, system (gnome) doesn't have /snap/ in it's binary or .desktop path.
hacky solution in screen, then shows in Dash with a search of clock (if one can see due to forum downsizing (a bit archaic

snapd came with the latest updates with ubuntu-unity spin.

---

### Post by ventrical on 2016-04-21
> **grahammechanical said:**
> May I draw everyone attention to this thread?

[http://ubuntuforums.org/showthread.php?t=2321161](http://ubuntuforums.org/showthread.php?t=2321161)

Regards.

Yeah graham... thanks. we should ask to  move that thread to development ?

@Cariboo 

Can we move the above thread-link to development version please?

regards..

---

### Post by QDR06VV9 on 2016-04-21
> **ventrical said:**
> **snapd came with the latest updates with ubuntu-unity spin**.
Ok that explains alot for me.
Thanks:D

---

### Post by ventrical on 2016-04-21
Found this interesting.

Is it slipstreaming in a lxc container or somthing?

---

### Post by ventrical on 2016-04-21
and this ..

```

ventrical@ventrical-System-Product-Name:~$ sudo -i
[sudo] password for ventrical: 
root@ventrical-System-Product-Name:~# snap install ubuntu-clock-app
120.11 MB / 120.11 MB [==================================] 100.00 % 307.37 KB/s 

root@ventrical-System-Product-Name:~# 

```

---

### Post by ventrical on 2016-04-21
> **grahammechanical said:**
> May I draw everyone attention to this thread?

[http://ubuntuforums.org/showthread.php?t=2321161](http://ubuntuforums.org/showthread.php?t=2321161)

EDIT

Earlier today I was able to install both the calculator & the clock app. They appeared in the Dash. I cannot see much else in the snap store that is suitable for a desktop UI. The ability to install these snaps from Ubuntu Software is something that will happen later on in the year. Needs some useful snap apps as well. I would like to see how the intended Firefox snap works in comparison with the deb version.

Regards.

the snapd came with regular updates today  (or even earlier). It is working very sleek. The 'snaps' including the clock app behaves very graphical like if on a phone or tablet.

---

### Post by ventrical on 2016-04-21
@graham n all

I did this.

```

root@ventrical-System-Product-Name:~# snap install canonical-pc-linux
109.53 MB / 109.53 MB [==================================] 100.00 % 306.27 KB/s 

root@ventrical-System-Product-Name:~# 

```

will try some other stuff..

---

### Post by cariboo on 2016-04-21
> **ventrical said:**
> Yeah graham... thanks. we should ask to  move that thread to development ?

@Cariboo 

Can we move the above thread-link to development version please?

regards..

Done, I guess we have to have something to talk about, until the next version is named. :)

**Edit:** it seems the next version was named while I was asleep, Yakkety Yak. :)

---

### Post by ventrical on 2016-04-21
> **cariboo said:**
> Done, I guess we have to have something to talk about, until the next version is named. :)

**Edit:** it seems the next version was named while I was asleep, Yakkety Yak. :)

Awwwwwwe....some  ..thats what I call a heads up. :) Time to get rid of the dust and cobwebs thats been collecting :)

---

### Post by ventrical on 2016-04-21
> **runrickus said:**
> Ok that explains alot for me.
Thanks:D

I am honestly tempted to install unity8 but I can't install it from the 'snap' method because it's not there in the (stable) :) hehehe  yep .. it's called a stable now rather than a repo :) jk  .. hehe I wonder what else is going to get shovel... nevermind .. I won't go there :)



regards..

---

### Post by vasa1 on 2016-04-21
> **ventrical said:**
> Yeah graham... thanks. we should ask to  move that thread to development ?

@Cariboo 

Can we move the above thread-link to development version please?

regards..

I started [http://ubuntuforums.org/showthread.php?t=2321161](http://ubuntuforums.org/showthread.php?t=2321161) outside the dev forum yesterday taken in by the buzz that it was release day and because I got the impression dev threads relating to 16.04 would be closed sooner or later :)

---

### Post by ventrical on 2016-04-21
> **vasa1 said:**
> I started [http://ubuntuforums.org/showthread.php?t=2321161](http://ubuntuforums.org/showthread.php?t=2321161) outside the dev forum yesterday taken in by the buzz that it was release day and because I got the impression dev threads relating to 16.04 would be closed sooner or later :)

This is a major development cookie that has been thrown at us to chomp on.  Actually it's been too long. :) I hope no offence taken  by my suggestion.  Not trying to hijack your thread or anything .. but I think we have all been waiting for some movement on this. Thanks for catching this one.

regards..

---

### Post by QDR06VV9 on 2016-04-21
> **ventrical said:**
> I am honestly tempted to install unity8 but I can't install it from the 'snap' method because it's not there in the (stable) :) hehehe  yep .. it's called a stable now rather than a repo :) jk  .. hehe I wonder what else is going to get shovel... nevermind .. I won't go there :)
regards..

:lol: I know nothing :lol:
Regards

---

### Post by ventrical on 2016-04-21
> **runrickus said:**
> :lol: I know nothing :lol:
Regards

That is first step on road to wisdom grasshopper.:)

Regards..

---

### Post by ventrical on 2016-04-21
> **mc4man said:**
> Try - 
```
sudo apt install snapd
```
```
snap find
```
sudo snap install pick one from ^

Ex. in screen

Don't need qml any longer.

---

### Post by grahammechanical on 2016-04-21
I am posting this from Xubuntu core 16.04 upgraded from Xubuntu core 15.10. I have the ubuntu calculator app & the Ubuntu clock app running. So, I guess that confirms these snaps will install and run on the flavours.

[ATTACH=CONFIG]268503[/ATTACH]

---

### Post by cariboo on 2016-04-21
> **vasa1 said:**
> I started [http://ubuntuforums.org/showthread.php?t=2321161](http://ubuntuforums.org/showthread.php?t=2321161) outside the dev forum yesterday taken in by the buzz that it was release day and because I got the impression dev threads relating to 16.04 would be closed sooner or later :)

This thread will also be valid during the next several development cycles, so this is probably the best place for it. Most of our average users won't be using snaps until they become standard in a release version.

No harm, no foul vasa1 :)

---

### Post by Chanath on 2016-04-22
120mb for calculator app and another 120mb for clock app is bit too much. What if we have 50 such apps? We'd need 6GB, just to hold them.

---

### Post by mc4man on 2016-04-22
> **Chanath said:**
> 120mb for calculator app and another 120mb for clock app is bit too much. What if we have 50 such apps? We'd need 6GB, just to hold them.

6GB isn't much for desktop users, 100GB likely wouldn't matter. However they'll have to do better as those are just simplistic mobile apps, comparative on Android would only be about 5 - 15 MB at best. Maybe they'll need to increase their core, whatever. Otherwise actual desktop apps will be in the hundreds or more.
Plus I wonder who's going to be responsible for licensing compliance & at what point do snaps allows pricing, in app purchasing or advertising (if ever??

---

### Post by vasa1 on 2016-04-22
I installed the ubuntu-clock-app but before that ubuntu-core was "automatically" installed. While I could uninstall the clock app, it seems ubuntu-core can't be removed.
```
06:29 PM ~ $ sudo snap remove ubuntu-core
[sudo] password for vasa1: 
error: can't remove "ubuntu-core": snap "ubuntu-core" is not removable
06:29 PM ~ $ 
```

Edit: fixed "While I could install" to "While I could _un_install"

---

### Post by grahammechanical on 2016-04-22
I see this feature as a proof of concept & advance publicity for what is coming in the next 6 - 12 months. Do I need a phone clock & calculator on my desktop install? Certainly not. On the other hand if Mozilla should come through with a snap packaged version of Firefox I would willingly trade a few MBs to install & test it. It may get to the point where one could balance the books by removing the deb packaged version.

Depending on the take up of application developers converting their apps from deb to snap, then I predict that 16.10 & 17.04 will have a smaller default install size as some of the traditional default deb apps are left out of the ISO image to be replaced by snaps installed through Ubuntu Software.

Regards.

---

### Post by ventrical on 2016-04-22
> **grahammechanical said:**
> I am posting this from Xubuntu core 16.04 upgraded from Xubuntu core 15.10. I have the ubuntu calculator app & the Ubuntu clock app running. So, I guess that confirms these snaps will install and run on the flavours.

[ATTACH=CONFIG]268503[/ATTACH]

Also ubuntu-gnome..

---

### Post by ventrical on 2016-04-22
> **grahammechanical said:**
> I see this feature as a proof of concept & advance publicity for what is coming in the next 6 - 12 months. Do I need a phone clock & calculator on my desktop install? Certainly not. 

Regards.

With the 32bit capability it may be useful on older machines.  A clock , a calendar and a web browser for those on the run. With mir  and graphics support - we may not have to get rid of those old laundry hampers after all :)

Regards..

---

### Post by lee295012-gmail on 2016-04-22
When they do start being made how do we install other apps, will they automatically show up in the find command or will we have to add them like a ppa?

---

### Post by ventrical on 2016-04-22
> **lee295012-gmail said:**
> When they do start being made how do we install other apps, will they automatically show up in the find command or will we have to add them like a ppa?

There will be updates every 3 to 4 weeks. However , I believe you can just continue to sudo apt-get update/upgrade and they will come in. With yakkety tool chain now released it may happen sooner than later.

[http://ubuntuforums.org/showthread.php?t=2321439](http://ubuntuforums.org/showthread.php?t=2321439)

---

### Post by grahammechanical on 2016-04-22
> When they do start being made how do we install other apps, will they  automatically show up in the find command or will we have to add them  like a ppa?

We already have threads in this section that provide information about this matter.

[http://ubuntuforums.org/showthread.php?t=2321161](http://ubuntuforums.org/showthread.php?t=2321161)

It seems that the important software is called snapd & it is installed by default in 16.04 & it also seems to be installed by default on the flavours built on Ubuntu 16.04. Snap apps were originally meant for Snappy Ubuntu core which was in turn meant for the Cloud & the Internet of Things and so the snaps in the snap store were not meant for a Graphical User Interface (GUI). This is why there are at present only 2 GUI apps that can be installed on Unity 7 and we have to do that through the command line.

It is intended that we will in future install snap apps through Ubuntu Software but first, app developers will need to convert their deb apps to snap packages. Of 
course, if the code is open source, then anyone can do it. There are tools available. We may have to give the resulting app a slightly different name. And comply with licensing & copy right requirements.

Over the next few months Ubuntu phone/tablet OS will move onto 16.04 code & snappy Ubuntu core with snaps replacing clicks. So, as phone apps get converted to snaps they will also become available. But at the moment I guess that running "snap find" is the way to find what snaps are being added.

Regards.

---

### Post by ventrical on 2016-04-22
And just as an add-on .. you have to be connected to the internet for 'snap find' to work. That will show the rudimentary available current apps.  'snap update' does not work btw. but these things will most likely  quickly change as it is only 24 hours post release and the yakkety base-files have already been seated if that is any indicator for progress.

Regards..

---

### Post by mc4man on 2016-04-22
> **Chanath said:**
> 120mb for calculator app 
Seems to be a bit more here, the snap "5"  folder for it is 393MB, most of which is in the /5/usr/lib/x86_64-linux-gnu folder

---

