---
title: "running Itunes"
date: 2011-01-24
forum: Wine
---

### Post by manish411 on 2011-01-24
How do we run itunes in ubuntu??
do we just run the itunes setup.exe via wine??

---

### Post by trinitydan on 2011-01-24
iTunes does not run well in WINE.  You will not have USB support and performance is choppy. You can read about it at the AppDB [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=21302").

You should either look for open source alternatives that will meet your needs (i.e. RhythmBox, Banshee, etc.), run iTunes in VirtualBox (requires a Windows install disc), or keep a dual boot configuration until USB support is implemented for WINE and iTunes runs a little more smoothly.

Edit:  Sorry, forgot to answer your question, yes, you should run iTunes from the terminal like:
```

wine /path/to/iTunesSetup.exe
```If you really want to see how it works that is (not recommended).

---

### Post by 1clue on 2011-01-24
Crossover Office, the commercial version of Wine, officially supports iTunes.  It's rated "bronze" which means there are some flaky parts, but generally worth using.

I no longer have the machine I installed it on, but at one point I used Crossover Office.  Worked very well for what I was doing.

---

### Post by trinitydan on 2011-01-24
iTunes 10 has a Silver rating if you check out the AppDB link I posted above, but in reality it just doesn't run well IMO.  I have tried it on a couple different computers with WINE 1.2, 1.3, 1.3.1 patched with USB support, all with very unimpressive results.  I wouldn't waste my time on it if I were you.  See if you can get your iPod (if you have one) to work with RhythmBox or Banshee since it definitely will not work with iTunes in WINE.

---

### Post by ivanovnegro on 2011-01-24
> **manish411 said:**
> How do we run itunes in ubuntu??
do we just run the itunes setup.exe via wine??

And if you want to run apps that support your iPod e.g. there are great players in Ubuntu to do that.
Some were also mentioned here like Banshee, Rhythmbox etc.
Im running Clementine and love it.
And really, some of the players here are really better as iTunes ever was/is, I know ppl are used to iTunes when they come to Ubuntu but just try some of the alternatives, you could be really surprised.

---

### Post by manish411 on 2011-01-24
If we use other applications to sync songs to my ipod , would it  do any harm to my ipod??

---

### Post by ivanovnegro on 2011-01-24
> **manish411 said:**
> If we use other applications to sync songs to my ipod , would it  do any harm to my ipod??

No, why should it do this? You would sync yor iPod normally like with iTunes, it would only be a different program, for Windows there are also different programs to sync an iPod.

---

### Post by Tony Flury on 2011-01-24
it wont harm your iPod - but it might do harm to your sanity getting any of of the Ubuntu tools to work.

I tried Banshee and Amarok and could get none of them to work - they would not recognise either audio CDs or recognise either my iPod or iPhone. Rythmbox could see and play the AudioCD but not see the iPod or iPhone.

If you want a stable solution that works out of the box then iTunes in a dual boot or in Virtualbox is your only solution - sadly you have to scrifice Linux purity but when the Linux tools don't cut it, then you have few other options.

---

### Post by cascade9 on 2011-01-24
> **Tony Flury said:**
> it wont harm your iPod - but it might do harm to your sanity getting any of of the Ubuntu tools to work.

I tried Banshee and Amarok and could get none of them to work - they would not recognise either audio CDs or recognise either my iPod or iPhone. Rythmbox could see and play the AudioCD but not see the iPod or iPhone.

Blame apple for that. When they update the firmware/OS on ipods/iphones, it breaks compatibility with the linux tools. 

> **Tony Flury said:**
> If you want a stable solution that works out of the box then iTunes in a dual boot or in Virtualbox is your only solution - sadly you have to scrifice Linux purity but when the Linux tools don't cut it, then you have few other options.

Or, for a different solution, sell the ipod and buy a media player with support.....or at the very least one made by a company that doesnt do its best to stop 'its' portable media players working with linux distros.

---

### Post by trinitydan on 2011-01-24
> **Tony Flury said:**
> it wont harm your iPod - but it might do harm to your sanity getting any of of the Ubuntu tools to work.


This should not be the case with older iPods.  I have a 1st gen 16GB iPod touch, an 80GB classic, and a 160GB classic, all of which can be synced with Linux software (I had to install Banshee to get the 160GB to work).  It was not always this way for me, I was stuck with a dual boot for ear on account of owning those iPods, while the Linux hackers had to reverse engineer Apples software.  That is why I have been so motivated trying to get iTunes to work in WINE for others who are stuck.
> **cascade9 said:**
> 
Or, for a different solution, sell the ipod and buy a media player with support.....or at the very least one made by a company that doesnt do its best to stop 'its' portable media players working with linux distros.
Absolutely!  If you haven't already bought an iPod, dont!  They aren't that great. I have purchased 3 of them, so believe me, I have seen the selling points.  Back in the day they might have been the only quality option, but nowadays there are much better options out there.  [I personally found this pretty offensive where Steve Jobs quipped about 7" tablets being so small they will have to ship with sandpaper so you can sand your fingers down to use it]("http://forums.appleinsider.com/showthread.php?threadid=113920").  While I was reading that, I was picturing my little 3.5" iPod screen with the on screen keyboard, especially when you are holding it vertically.  Now that is where you need sandpaper!  However none was included in the $370 price tag of my iPod touch.  To me the iPad looks just a little to big and cumbersome.  I wish I had a device between the iPod and iPad.  Plus it is always fun after you buy a new Apple product to watch the one you really wanted (the one with the mic, or the speaker, or the GPS, etc.) come out three months later since they already had it finished and are just metering out the technology to keep the prices up (notice how the iPod you really want never gets any cheaper?).  

Sorry for the mini rant, but absolutely avoid iPods if you want to avoid headaches from incompatibility issues with non Win/Mac software!

---

### Post by BHEJU on 2011-01-24
IMHO:
There are bunch of apps that support ipod/ipad/ihpones. just check out the wikipedia page here:

[http://en.wikipedia.org/wiki/Comparison_of_iPod_managers](http://en.wikipedia.org/wiki/Comparison_of_iPod_managers)

However, I have messed with all of them and none of them work as seamless as itues (or copy trans on win)
FYI: I hate itues, but it works like charm with their products.

GTKpod is as close to itues as any app on linux, I am still not happy with it. (if you do not care about the order of playlist, then this will be fine).
I run virtual win just for this.

NOTE: If you have auto-sync on (check-box in itunes) then you will loose your data first time. but that is normal even when you try to change/sync it with other win/itunes machine.

---

