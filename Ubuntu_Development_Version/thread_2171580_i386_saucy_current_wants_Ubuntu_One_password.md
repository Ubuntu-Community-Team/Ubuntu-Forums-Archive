---
title: "i386 saucy current wants Ubuntu One password"
date: 2013-08-31
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-08-31
Just zsynced saucy-desktop-i386.iso.

 Proceeded to install and Ubiquity presents me with a  screen that wants my Ubuntu One e-mail address and password. I tired one and it didn't work. Tried another (my launchpad account) and now it is just hanging...

 what fresh E'll is this ?

---

### Post by Hylas de Niall on 2013-08-31
It's the new thing :)

[http://www.omgubuntu.co.uk/2013/08/ubuntu-one-log-in-added-to-ubuntu-13-10-installer](http://www.omgubuntu.co.uk/2013/08/ubuntu-one-log-in-added-to-ubuntu-13-10-installer)

(i think you can select 'not now' though)

---

### Post by OrangeCrate on 2013-08-31
It was present in the Xubuntu 64-bit daily, a few days ago, but, absent from yesterday's download.

---

### Post by ventrical on 2013-08-31
I am just curious if it is a security risk. I actually did try to log on - but it carfunkled.

---

### Post by ventrical on 2013-08-31
> **Hylas de Niall said:**
> It's the new thing :)

[http://www.omgubuntu.co.uk/2013/08/ubuntu-one-log-in-added-to-ubuntu-13-10-installer](http://www.omgubuntu.co.uk/2013/08/ubuntu-one-log-in-added-to-ubuntu-13-10-installer)

(i think you can select 'not now' though)


But it won't install to disk .. it just hangs after login fail..

---

### Post by OrangeCrate on 2013-08-31
Adding to previous post...

It worked fine when I logged in a couple of days ago. Reinstalled yesterday, but moot point now, since it wasn't there (new install did clean up a couple of other hiccups though). I'll reinstall again to check on everything after the 5th, when Beta 1 (for the flavors) is released...

---

### Post by ventrical on 2013-08-31
ok.. I chose nomodset>Install Ubuntu> login later> at the last step before install.

Now installing.

btw .. this was todays zsync..Sat. Aug/31/2013

edit:  Actually you don't need nomodeset... just choose <login later> when the last Ubiquity screen displays.

---

### Post by ventrical on 2013-08-31
> **OrangeCrate said:**
> Adding to previous post...

It worked fine when I logged in a couple of days ago. Reinstalled yesterday, but moot point now, since it wasn't there (new install did clean up a couple of other hiccups though). I'll reinstall again to check on everything after the 5th, when Beta 1 (for the flavors) is released...


 I am using ubuntu-(unity) .. not xubuntu ... are we on the same page here?

---

### Post by OrangeCrate on 2013-08-31
> **ventrical said:**
> I am using ubuntu-(unity) .. not xubuntu ... are we on the same page here?

No we aren't, and never were on the same page. I'm commenting about Xubuntu, which you should extract from said comments, that if you're having a problem, it's probably limited to **Unity**. Personally, during the development cycle, I've always wanted the perspective of what the other versions were doing when I had a problem with a specific version, but, apparently you don't. Good luck.

Edit:

Correction...

"Unity" should read "Ubuntu".

---

### Post by ventrical on 2013-08-31
> **OrangeCrate said:**
> No we aren't, and never were on the same page. I'm commenting about Xubuntu, which you should extract from said comments, that if you're having a problem, it's probably limited to Unity. Personally, during the development cycle, I've always wanted the perspective of what the other versions were doing when I had a problem with a specific version, but, apparently you don't. Good luck.


 It's not a problem related to Unity. It's a problem related to ubuntu. That's why I chose that (ubuntu) topic heading. You did mention xubuntu but I assumed you were testing Ubuntu daily .iso also. I too test multiple flavours. I was asked to test xubuntu, kubuntu and try to do so as dilligently as possible , time permitting. Obviously I had not tested the particular version of Xubuntu you have mentioned and thank you for letting us all know that this apparently new feature existed there also but I fail to see why you would think I would not appreciate other's perspective.

Regards..

---

### Post by jerrylamos on 2013-08-31
> **ventrical said:**
> Just zsynced saucy-desktop-i386.iso.

 Proceeded to install and Ubiquity presents me with a  screen that wants my Ubuntu One e-mail address and password. I tired one and it didn't work. Tried another (my launchpad account) and now it is just hanging...

 what fresh E'll is this ?

Me too.  I actually had to do a killall -15 ubiquity (I think that's what I did) and gave it another go, clicking on the "later" option.

My opinion, "clutter".

---

### Post by ventrical on 2013-08-31
> **jerrylamos said:**
> Me too.  I actually had to do a killall -15 ubiquity (I think that's what I did) and gave it another go, clicking on the "later" option.

My opinion, "clutter".


  I also think there is something wrong with the daily/current and the 3.11.0.4 kernel because I was having problems with one machine and the updates/upgrade killed the mouse. This was on two seperate saucy installs on the same machine. Even the fresh install failed - leading me to believe that I blew up my nVidia GeForce 210/218 adapter card because I overclocked to 4.002 GHz. I also tried different mouse and took the machine off the KVM network and those two installs still would not work.

  I then disconnected the hdd and put in an ealier state of saucy on an IDE hdd 3.11.0.2 and it is working just fine, nouveau, unity-system-co and all !! I have seen strange behaviour before during cycles but not like this. also the daily/current still has those several  horizontal bars going across the top during startup.

---

### Post by jerrylamos on 2013-09-01
I can get through the SSO or however that is spelled on my netbook and notebook and tower running ubuntu.
I can get through the SSO on my Chromebook running Google Chrome or whatever it is.
I can't get by login any more on my Samsung Galaxy Tablet 2 7" which hangs up on some screen with "Ubuntu One", I enter all the right email, userid, and password and the screen just sits there.

BTW, I haven't done anything with Ubuntu One for years.  At that time I didn't want any more complications, things to enter, ...
All my pc's are on my home network and I can use Samba or sneaker net when I wish.

Hmmm.  Competition.  Using Chromium or Google Chrome dead pipe simple to use the same bookmark set even on the Samsung and Nook and Asus Transformer and Chromebook.  I haven't done any cloud stuff yet - granted I use yahoo mail and aol mail from everywhere on anything (even Apple and Microsoft).

On installs I use the "later" option since Ubuntu One didn't want to recognize my password.  Not a problem, just an extra step on install.

---

### Post by craig10x on 2013-09-01
When i did my upgrade today from 13.04 to 13.10 using the live iso, i simply hit the button that said "log in later" and that bypasses this step altogether....i didn't try logging in to see if it would work but it is kind of an unnecessary feature i would say...i guess they just want to encourage newbies to set up a ubuntu one account...

---

