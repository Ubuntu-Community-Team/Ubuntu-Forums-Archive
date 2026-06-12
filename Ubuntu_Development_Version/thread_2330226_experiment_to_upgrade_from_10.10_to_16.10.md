---
title: "experiment to upgrade from 10.10 to 16.10"
date: 2016-07-09
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-07-09
I want to try an upgrade of an older install of 10.10 to 16.10. I know how to do it but before I do I just want to know if anybody has other way to enter commands into terminal other than the standard method.

Thanks .. regards..

---

### Post by kansasnoob on 2016-07-09
If 10.10 were the only OS installed on that system it would be interesting to know if the installer offered an upgrade. It won't if there is more than one Linux OS installed. Well, it might but for sure it won't if it sees another Ubuntu based OS because it can't possibly know which OS to upgrade.

---

### Post by ventrical on 2016-07-09
> **kansasnoob said:**
> If 10.10 were the only OS installed on that system it would be interesting to know if the installer offered an upgrade. It won't if there is more than one Linux OS installed. Well, it might but for sure it won't if it sees another Ubuntu based OS because it can't possibly know which OS to upgrade.

That's an interesting point. I will soon find out. Now that I got your attention .. perhaps you can help me with something here. Trusty ubuntu-desktop 14.04.2 software updater is absolutely useless . (I am now in process of trying to use terminal commands.)My question is .. how many other installs of trusty 14.04.2 in the wild have a defunct software updater and how will people respond ? Like do we all have to use terminal? I thought these bugs were fixed !

Regards..

note to mods: I am off topic on my own threads. My apologies.

---

### Post by ventrical on 2016-07-09
wow.... natty :)

---

### Post by kansasnoob on 2016-07-09
> **ventrical said:**
> That's an interesting point. I will soon find out. Now that I got your attention .. perhaps you can help me with something here. Trusty ubuntu-desktop 14.04.2 software updater is absolutely useless . (I am now in process of trying to use terminal commands.)My question is .. how many other installs of trusty 14.04.2 in the wild have a defunct software updater and how will people respond ? Like do we all have to use terminal? I thought these bugs were fixed !

Regards..

note to mods: I am off topic on my own threads. My apologies.

You mean Trusty installed with 14.04.2 media? And update-manager/notifier never pop up?

I still use Trusty every day and it's working OK, notifies me of updates as it should, but it started out being installed using either the original 14.04 or 14.04.1 media.

---

### Post by ventrical on 2016-07-09
> **kansasnoob said:**
> You mean Trusty installed with 14.04.2 media? And update-manager/notifier never pop up?

I still use Trusty every day and it's working OK, notifies me of updates as it should, but it started out being installed using either the original 14.04 or 14.04.1 media.

That was the 10.10  to yakkety install. I haven't tried the trusty upgrade yet because of fail of software updater. Will get to it.

---

### Post by ventrical on 2016-07-09
> **kansasnoob said:**
> You mean Trusty installed with 14.04.2 media? And update-manager/notifier never pop up?

I still use Trusty every day and it's working OK, notifies me of updates as it should, but it started out being installed using either the original 14.04 or 14.04.1 media.

On one of my surplus trusty installs (14.04.2) I updated it using software updater. It was ubuntu-desktop.  Now when I log on it is MythUbuntu in the greeter screen with xfce default and mythubuntu as regular. Don't ask me how it happened. It is probably something I did or did not do. My computer housekeeping skills need a system restore :)

regards..

---

### Post by T.J. on 2016-07-09
My advice is to backup your data and use a clean install method rather than attempting an "in place" upgrade. Debian's upgrade process is far smoother than Ubuntu's, but I suspect even Debian would have a problem upgrading cleanly from a version that was 6 versions being the current one.

That said, if I were going to try that, I'd uninstall any proprietary drivers, then shutdown X11, and use the text console.Trying a full distribution upgrade inside of X11 is dicey on the best of days and can cause severe crashes. If you don't remove the proprietary drivers first, they are likely to crash upon upgrade.

I would install aptitude, and use the command:

*aptitude full-upgrade*

Aptitude has better resolution logic than standard apt when selecting install order.  Aptitude and apt-get do the same things - that is true, but they vary in subtle ways that are important.  In almost all cases, aptitude selects and orders upgrades in a more conservative manner than apt-get that should lead to a more successful upgrade between two versions that are so disparate. Most people use apt-get because it is usually easier to remember.  Still, I do not understand why aptitude is not standard on Ubuntu.

You will probably have to run the upgrade in stages, using aptitude and then *apt-get install -f *a few times to fix dependencies that crash during install; and then repeat.  Because the versions database for packages for the two releases are so far apart, you are likely to encounter some strange problems.

---

### Post by ventrical on 2016-07-09
> **T.J. said:**
> My advice is to backup your data and use a clean install method rather than attempting an "in place" upgrade. Debian's upgrade process is far smoother than Ubuntu's, but I suspect even Debian would have a problem upgrading cleanly from a version that was 6 versions being the current one.



It is surplus hdd and install. There is nothing to back up. We are testing the in house default upgrader.

Thanks for pointers..

Regards..

---

### Post by T.J. on 2016-07-09
> **ventrical said:**
> On one of my surplus trusty installs (14.04.2) I updated it using software updater. It was ubuntu-desktop.  Now when I log on it is MythUbuntu in the greeter screen with xfce default and mythubuntu as regular. Don't ask me how it happened. It is probably something I did or did not do. My computer housekeeping skills need a system restore :)

regards..

A KMS/Plymouth or greeter screen is really cosmetic and can be changed, often by installing the necessary artwork, reconfiguring the theme and then regenerating the initramfs image.

---

### Post by T.J. on 2016-07-09
After rereading your post I realized what you plan and slapped my forehead.  Added more to my original note - sorry half asleep today.  The extras should help make your odds more successful

---

### Post by ventrical on 2016-07-09
> **T.J. said:**
> After rereading your post I realized what you plan.  Added more to my original note - sorry half asleep today.  The extras should help make your odds more successful

Thanks T.J. I can't download anything on that install at all. Tried aptitude in terminal. No way. It recomends fresh install. I think that's par for the course. :)

regards..

---

### Post by T.J. on 2016-07-09
> **ventrical said:**
> Thanks T.J. I can't download anything on that install at all. Tried aptitude in terminal. No way. It recomends fresh install. I think that's par for the course. :)

regards..

If you really want to see if you can do this, then how about baby-stepping it - using a CD or USB?  You download the next version after 10.10; then "in-place" upgrading to that without using Internet. After you get that installed, then try again.  At the very least, it should give you some notion of how many steps would be needed.


In my case, if I were going to "in place" upgrade from Debian 4 to Debian 8, I would definitely upgrade in sequence to Debian 6 or 7 first; then 8 - just to keep things in sync.  Usually, only upgrades from the last two versions of Debian to the current are actually tested.  I'd assume Ubuntu does the same with the last release, plus the last LTS.

---

### Post by deadflowr on 2016-07-09
> **ventrical said:**
> Thanks T.J. I can't download anything on that install at all. Tried aptitude in terminal. No way. It recomends fresh install. I think that's par for the course. :)

regards..

I guess that's the 14.04.2 install, but what's happening with the 10.10 > 11.04 upgrade?
Or is this the same thing?

It's interesting.
If only for the audacity of seeing how an EOL >EOL >EOL > LTS > LTS >LTS > Dev goes.
:twisted:

---

### Post by ventrical on 2016-07-09
> **deadflowr said:**
> I guess that's the 14.04.2 install, but what's happening with the 10.10 > 11.04 upgrade?
Or is this the same thing?

It will not happen. it just wont work. It comes with a popup advising a fresh install so thats how they  sealed that closed.


> 
It's interesting.
If only for the audacity of seeing how an EOL >EOL >EOL > LTS > LTS >LTS > Dev goes.
:twisted:

I just love experimenting with this stuff. Actually I am waiting  for a bug in Libertine to get released (fix commited) so I can go back to testing unity8 and containers. :)

Regards..

---

### Post by ventrical on 2016-07-09
> **T.J. said:**
> If you really want to see if you can do this, then how about baby-stepping it - using a CD or USB?  You download the next version after 10.10; then "in-place" upgrading to that without using Internet. After you get that installed, then try again.  At the very least, it should give you some notion of how many steps would be needed.


In my case, if I were going to "in place" upgrade from Debian 4 to Debian 8, I would definitely upgrade in sequence to Debian 6 or 7 first; then 8 - just to keep things in sync.  Usually, only upgrades from the last two versions of Debian to the current are actually tested.  I'd assume Ubuntu does the same with the last release, plus the last LTS.

Some good ideas.

Thanks

Regards..

---

