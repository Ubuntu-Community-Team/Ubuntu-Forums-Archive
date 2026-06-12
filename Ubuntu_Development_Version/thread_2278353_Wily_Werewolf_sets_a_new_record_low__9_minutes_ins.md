---
title: "Wily Werewolf sets a new record low:  9 minutes installation"
date: 2015-05-15
forum: Ubuntu Development Version
---

### Post by MikeMecanic on 2015-05-15
May 16th 2015

Testing Ubuntu 15.10 first Alpha Release amd64

I took 9 minutes to install Ubuntu 15.10 (mkusb directly in the boot-up sequence :Legacy) which is a new record low.  I lost the weather apps for 2 years and it took 9 minutes to loose it again.  :p. Ubuntu 15.04 after install 2.6 beta does not allow me to install it.
The installation generates only 1 error: Ubuntu Software Center (Opera 29 Stable installation end in a dark black freezing grey screen but the installation was successful).  Post installation was O.K.  The shadow of Vivid Vervet is still there.  What to do to recuperate the weather apps?

Version:29.0.1795.47 -
 Opera is up to date
Update stream:Stable
System:Ubuntu Wily Werewolf (development branch) (x86_64; Unity)

Regards,

---

### Post by rrnbtter on 2015-05-15
Greetings,
Weather indicator:
Try this, it is stable, has an indicator, and advanced features. Uses open weather
[I]sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update[/I]
[I]sudo apt-get install my-weather-indicator

also this is a good fork of Stormcloud

[I]sudo add-apt-repository ppa:apandada1/typhoon
sudo apt-get update[/I]
*sudo apt-get install typhoon*


[/I]

---

### Post by MikeMecanic on 2015-05-15
Here's what i get in the terminal at the end:

```
E: Some index files failed to download. They have been ignored, or old ones used instead.
ibm@ibm:~$ sudo apt-get install my-weather-indicator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package my-weather-indicator
ibm@ibm:~$ sudo apt-get install my-weather-indicator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package my-weather-indicator
ibm@ibm:~$
```

Also, for Typhoon it ends with this: Unable to locate package typhoon.  + I have to disable the ppa's to run Software Updater.

---

### Post by grahammechanical on 2015-05-15
> E: Some index files failed to download. They have been ignored, or old ones used instead.

That is common for the development version. 

Also when we use add-apt-repository it automatically puts the code name of the distribution into the url. In this case it will be wily but there is not a wily PPA for atreoo and I do not see one for typhoon either. So, we have to go to Software & updates and edit the url to replace wily with vivid. Once the software is installed we can disable the PPA.

Regards.

---

### Post by MikeMecanic on 2015-05-15
Got many PPA issues and it looks like a long journey.  Will go back to Vivid upgrade. Thanks,

---

### Post by rrnbtter on 2015-05-15
Yep, broken. Sorry

---

### Post by cariboo on 2015-05-16
You can use System Settinggs->Software & Updates tp edit ppa sources.

---

### Post by rrnbtter on 2015-05-16
Greetings,
Well! just in case anyone is interested in a weather indicator this works for me.

Edit
add-apt-repository ppa:atareao/atareao
add-apt-repository ppa:saiarcot895/myppa (also this one if you need DST)

If the ppa installs correctly (with signing key) open the ppa in the Software & Updates section and change the ppa Distribution from Wily to Vivid.
Then:
apt-get update
Then:
apt-get install my-weather-indicator python3-requests

Reboot to load the indicator. Use the preferences to set you location and units.  This thing is slow so be patient and let it do its thing. In other words, don't keep clicking.
Also use your own brand of sudo on the above terminal commands.

---

### Post by zika on 2015-05-16
> **rrnbtter said:**
> Reboot to load the indicator.Reboot is, of course, not necessary, simple (re)start of indicator should suffice.

---

### Post by rrnbtter on 2015-05-16
I agree that a reboot isn't necessary, it just loaded very slowly. When I said be patient I was talking to myself :)

---

### Post by syntaxerror74 on 2015-05-17
> **MikeMecanic said:**
> Got many PPA issues and it looks like a long journey.

And you're still wondering? ;) adconrad has finally found time to post Wily's release schedule, and this says: first alpha is set to *June 25th*!! Yes, this is more than one month to practise some patience...
So I think I should practise MY own patience as well and resist the temptation of touching my installation until first "official" alpha comes out, thus refrain from fiddling with this seemingly half-broken chain of packages...

[edit]Hey this is a JOKE or what!?
Here on Lubuntu, while doing some basic updates, Software Updater seriously offered me an "upgrade" from 15.04 to 15.10, even though official alpha won't be out before mid-June!?
I clearly remember this was different on Vivid? When alpha 1 was announced and available for installation via the Updater, it *WAS* the **official** alpha (perfectly matching the date on the Release Schedule), **not** the pre-alpha.

---

### Post by cariboo on 2015-05-17
I'm not sure what this going on about alpha's and beta's is about. They aren't anything special, just a snapshot of the repositories on a particular day, by the time you've downloaded and installed one, it is out of date anyway. :)

---

### Post by syntaxerror74 on 2015-05-17
cariboo, short 'n simple answer: betas *are*  commonly distinguished from alphas for a reason, because the former are known to be way more stable and free of (severe) bugs.

---

### Post by cariboo on 2015-05-18
> **syntaxerror74 said:**
> cariboo, short 'n simple answer: betas *are*  commonly distinguished from alphas for a reason, because the former are known to be way more stable and free of (severe) bugs.

You obviously haven't been running Ubuntu development versions for long. :) The alpha and beta release dates are set at the beginning of the development cycle, when that date comes around, an image is made of the repositories, and it is then called an alpha or beta. No extra effort is made to make sure it is more reliable than the previous or following days releases. As you can see from the release schedule located [here]("https://wiki.ubuntu.com/WilyWerewolf/ReleaseSchedule"), the alpha release is marked as opt in for the flavours, as Ubuntu does not release an alpha version. There is a beta Ubuntu release, but note the beta 1 release on August 27th is opt in for the flavours and September24th is the final Ubuntu beta release.

We here in this section recommend that if you do download and install an alpha or beta release that you keep updating your installation daily, to keep up with newly released packages and bug fixes.

---

### Post by syntaxerror74 on 2015-05-19
> **cariboo said:**
> You obviously haven't been running Ubuntu development versions for long. :) 
Only for a couple of years TBH; but yes, it's less than three years.
Well, I was simply trying to deduce the alpha vs. beta thing from *common software development*: whilst an alpha version is pretty unstable and prone to bugs, testing cycle has already advanced a lot with a beta release. Sometimes the betas even have *lower* version numbers for a reason, which says in fact that if you do want the bleeding edge stuff from the developers' trunk featuring all new bells 'n whistles, you should rather download the latest alpha (but---for Windows software in particular---not go angry if your system goes all wonky, e. g. your mouse pointer gets "lost on the way" and remain invisible even after quitting the program).

But as *you* are trying to make me learn, this is **not** to be understood the same way in the Ubuntu world.

---

### Post by cariboo on 2015-05-19
With Ubuntu focusing on quality, most of the problems we have seem in previous development releases are not as wide spread. There are still problems, but they seem to affect fewer users all the time. In previous development release there were times when everyone's install was inaccessible for several days, we haven't seem anything like this in the last couple of years. You could almost say running a development release is fairly boring, but with all the choices we may have this cycle, Plain old Ubuntu, Ubuntu Next and Snappy, as well as all the flavours, there may be some fun to be had.

That other software company based in Redmond may still have traditional alpha and beta releases, but here they don't quite mean the same thing.

---

### Post by dino99 on 2015-05-19
yeah, Canonical have decided some times ago (Utopic UOS time) that 'alpha/beta' old school style was meaningless due to the actual devs pre-testing building steps made. So even packages landind in 'proposed' archive are way more stable now compared to previous versions.

---

### Post by MikeMecanic on 2015-05-24
Sorry Wily. on second installation (LVM to LVM Default) Rebecca (300Mb bigger) takes 5 minutes. 2.0 Legacy on boot sequence.  I guess that with the X99 chip set, it would be under 4 minutes?  To be confirmed ! ):P

---

### Post by sammiev on 2015-05-24
> **MikeMecanic said:**
> Sorry Wily. on second installation (LVM to LVM Default) Rebecca (300Mb bigger) takes 5 minutes. 2.0 Legacy on boot sequence.  I guess that with the X99 chip set, it would be under 4 minutes?  To be confirmed ! ):P

All my installs of Wily has been to VM so far and usually takes mins to install. ( Must add that my computer is fairly high in )

---

### Post by jerrylamos on 2015-05-25
Getting the .iso installed is maybe half of my installation.  Usually boot the .iso directly from the hard disk or do a "restore" onto a USB for the other 64bit pc.

I then run an exec to set preferences, install synaptic, flash, chromium, pepperflash, samba.conf customization, of course the update and dist-upgrade since "today's" .iso is always out of date, of course turn off screen lock and password when waking - the pc is in my house and is only used by me - copy in a bunch of execs to do updating, archiving, boot up Firefox and do a Snc, boot up Chromium and logon google to get bookmarks, set wallpaper, reboot, I've probably forgotten something by now.  Oh yes, for my laptop which runs a monitor, use settings > displays to turn off the laptop monitor and make the external monitor the primary.  

BTW, installed WW on three pc's so far, this desktop, a wide screen laptop with external monitor, and a 32 bit 3 GHz tower.

Usually the first few weeks of a U+1 are O.K. until there's a barrage of updates of code which has never seen each other before then all @#$%^& breaks loose.  Unicorn was O.K. then got updated and wouldn't boot for 6 weeks.   Vivid was O.K. got an update which screwed up wallpaper on this Lenovo M58p.  Bug written.  Wily is better but not fixed.

Anyway still cleaner than install was a couple releases ago when install insisted on logging in to some cloud or other.

Not at all sure how continuous update vs. releases will work.....

Running, waiting for a Dread Update.

---

