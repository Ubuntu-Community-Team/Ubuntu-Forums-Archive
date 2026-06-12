---
title: "HOWTO: Set Gnome Calendar First Day of Week"
date: 2008-05-31
forum: Tutorials
---

### Post by drs305 on 2008-05-31
Here is how to change the gnome calendar first day of the week to Monday. 

Check which locale you are using (mine is en_US, don't worry about the .UTF ending):
```
locale
```
Next, backup and edit the applicable locale file (use the result of the previous command if not en_US). 
```

sudo cp /usr/share/i18n/locales/**en_US** /usr/share/i18n/locales/**en_US**.bak
gksudo gedit /usr/share/i18n/locales/**en_US**
```
Locate the following line and change the value. The value for Monday in en_US was 2. Select the appropriate number if you desire another day to be the start day.
```
first_weekday **2** 
```
Save the file and then:

Update the locales:
```
sudo locale-gen
```
Refresh the desktop:
```
killall gnome-panel
```
The first day should now be Monday \\:D/

---

### Post by qalisto on 2008-06-14
Magnificently useful!  Thank you.

---

### Post by executor on 2008-06-14
Thank you

---

### Post by malath on 2008-06-14
Is saturday weekday number 7?

---

### Post by drs305 on 2008-06-14
> **malath said:**
> Is saturday weekday number 7?

Yes, in the US en at least. Sunday is the first day and Saturday is day 7.

---

### Post by Selmi on 2008-07-19
perfect, i didn't wanted to use slovak localisation because its very incomplete, and this week start from sunday was driving me crazy. (btw, its possible to set 24h time, celsius temperatures, kilometers per hour for wind - why not start of week????)

thanks a lot

---

### Post by Darkshade on 2008-07-21
Thanks! That was simple but really usefull at the same time. Just when I thought that I would never find a fix for it :)

---

### Post by pmorch on 2008-10-07
While this is usefull and will do the trick temporarily, it will only work until the "locales" package (which contains the /usr/share/i18n/locales/en_US file) is updated or reinstalled, because then this file will be overwritten/replaced with a new one from the locales package again.

Is there a bug / changerequest for this issue? I think it should be something one can change in the calendar applet, as Selmi pointed out: "its possible to set 24h time, celsius temperatures, kilometers per hour for wind - why not start of week????"

And FYI: This is not just a cosmetic thing; it affects week numbers too. Some years will have an offset of one for week numbers, depending on what the first day of the week is. I think in years where the first day is a monday (although I'm not 100% sure exactly when/how this offset occurs)

Peter

---

### Post by jaumellarden on 2009-01-18
Hi,

I happened to have the same problem with openSUSE, which doesn't include locale-gen. Instead of doing this:

$ sudo locale-gen

I had to do this:

$ gunzip -c /usr/share/i18n/charmaps/UTF-8.gz > /tmp/UTF-8
$ sudo localedef -i /usr/share/i18n/locales/en_US --charmap /tmp/UTF-8 /usr/lib/locale/en_US.utf8 
$ rm /tmp/UTF-8

I know, not really Ubuntu-related, but hopefully useful :-)

Best regards,
jaume

---

### Post by AbtZ on 2009-01-29
> **Selmi said:**
> perfect, i didn't wanted to use slovak localisation because its very incomplete, and this week start from sunday was driving me crazy. (btw, its possible to set 24h time, celsius temperatures, kilometers per hour for wind - why not start of week????)

thanks a lot

Because it's Gnome, and the Gnome philosophy seems to be "Remove as many options from the user as possible! Then we get a better and cleaner interface!!". From what I've heard the option to change first day of week was included before, but they REMOVED it.

Anyway, thanks a million for the tip! I like running my OS in English, but starting the week on a Sunday is not for me.

---

### Post by artm on 2009-02-25
see also [http://ubuntuforums.org/showthread.php?p=6798112#post6798112](http://ubuntuforums.org/showthread.php?p=6798112#post6798112) for a solution without editing package files.

---

### Post by pmorch on 2009-02-25
> **artm said:**
> see also [http://ubuntuforums.org/showthread.php?p=6798112#post6798112](http://ubuntuforums.org/showthread.php?p=6798112#post6798112) for a solution without editing package files.

Thanks, artm, works perfectly. And avoids messing with files that are overridden by apt-get upgrade later. Just grand.

---

### Post by nico80 on 2009-04-28
Thank you very much!

Having Sunday as first day was really annoying.

I'm actually using Fedora, but it works the same, only little thing I had to change is the locale-gen call (as it is an Ubuntu-specific command) with:

```
sudo localedef -f UTF-8 -i en_US en_US.UTF-8
```

---

### Post by smiletobehappy on 2009-06-21
Thank You very much!
Very helpful tutorial, works perfectly with Ubuntu 9.04 Jaunty.

---

### Post by XCan on 2009-07-12
I had seen bunch of other ways to do this, but they all imposed some locale errors in especially Python scripts. This has so far worked wonderful, thanks!

---

### Post by petike on 2009-10-08
It works perfectly!

Great article - "easy", "fast" and "reliable".

---

### Post by kevinguillorytraining on 2009-10-09
Very useful. Where I can get other days code? i.e. Friday and Saturday.

---

### Post by drs305 on 2009-10-09
> **kevinguillorytraining said:**
> Very useful. Where I can get other days code? i.e. Friday and Saturday.

For the US, Friday should be 6 and Saturday 7. I don't know of a listing, so you would just have to experiment. Since I wrote this guide it would seem there are probably other ways to set the DOW.

For instance, Evolution's start day can now be set with gconf-editor:
```

gconf-editor /apps/evolution/calendar/display/week_start_day

```
In Evolution, Sunday is 0 and Saturday is 6.

---

### Post by gtrdp on 2010-11-17
great, this is what i'm looking for exactly
thanks :D

---

### Post by drs305 on 2010-11-17
Well, I'm a bit surprised that 2 1/2 years later this fix is still required, but I'm glad it worked for you.  :-)

---

### Post by Reptile1712 on 2011-02-21
Even more than 2 & 1/2 years, and still useful here, thx ;)

---

### Post by MacHaddock on 2011-03-30
> **AbtZ said:**
> Because it's Gnome, and the Gnome philosophy seems to be "Remove as many options from the user as possible! Then we get a better and cleaner interface!!". From what I've heard the option to change first day of week was included before, but they REMOVED it.

Anyway, thanks a million for the tip! I like running my OS in English, but starting the week on a Sunday is not for me.


Same here. Thanks

---

### Post by MacHaddock on 2011-03-30
If your swedish this might help [http://comments.gmane.org/gmane.linux.debian.user.swedish/10109](http://comments.gmane.org/gmane.linux.debian.user.swedish/10109)

---

### Post by Zmicier on 2012-02-14
In case of unity   the last step should look like

> killall unity-panel-service


---

### Post by Peter Ketel on 2012-10-06
> **drs305 said:**
> Yes, in the US en at least. Sunday is the first day and Saturday is day 7.
That's is incorrect. The Gregorian calendar (that's the one we use on a daily basis) and the ISO calendar state clearly that the first day of the week is Monday!

Unless you're sticking to the Hebrew calendar. For this calendar Sunday is the first day of the week!

So this is an error in Ubuntu!!!!

By the way: NONE of the brilliant suggestions to fix this error will deal with the problem. ALL SUGGESTION HAVE FAILED and I followed them to the letter!  The capital letters are there to illustrate my disappointment and frustration!

---

### Post by drs305 on 2012-10-07
> **Peter Ketel said:**
> By the way: NONE of the brilliant suggestions to fix this error will deal with the problem. ALL SUGGESTION HAVE FAILED and I followed them to the letter!  The capital letters are there to illustrate my disappointment and frustration!

I can no longer edit this thread, but the solutions presented here were first posted 4 years ago. Much has changed since then, and I'm surprised the solutions still worked as long as they did.

I'lll ask the mods to close the thread.

---

### Post by Elfy on 2012-10-07
So done.

---

