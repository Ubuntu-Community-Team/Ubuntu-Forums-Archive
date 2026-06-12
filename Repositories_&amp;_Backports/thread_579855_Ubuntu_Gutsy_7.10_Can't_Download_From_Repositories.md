---
title: "Ubuntu Gutsy 7.10 Can't Download From Repositories"
date: 2007-10-18
forum: Repositories &amp; Backports
---

### Post by cchester on 2007-10-18
Hey I just installed Ubuntu 7.10 from cd and I went to use synaptic to download a few programs and nothing is downloading. Also I am getting failed when I click the reload button for the repositories.

Are they down because of the new release?

Thanks.

---

### Post by exactopposite on 2007-10-18
it's most likely the high volume of traffic caused by the new release. there are so many people trying to download gutsy, update/install packages, and so forth that the servers have to be slammed.

---

### Post by cchester on 2007-10-18
Ok guess I will wait. I noticed that some people said there is a site that you can pick a different site to download from. If so do you know the link.

Thanks.

---

### Post by bapoumba on 2007-10-18
Which repositories are you using ?

---

### Post by stevoo on 2007-10-18
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://wwwftp.ciril.fr/pub/linux/ubuntu/archives/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://wwwftp.ciril.fr/pub/linux/ubuntu/archives/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://wwwftp.ciril.fr/pub/linux/ubuntu/archives/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://wwwftp.ciril.fr/pub/linux/ubuntu/archives/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://cy.archive.ubuntu.com/ubuntu/ feisty-backports main restricted multiverse
# deb-src http://cy.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
# deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
# deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

deb http://wwwftp.ciril.fr/pub/linux/ubuntu/archives/ gutsy-security main restricted
deb http://wwwftp.ciril.fr/pub/linux/ubuntu/archives/ gutsy-security universe
deb http://wwwftp.ciril.fr/pub/linux/ubuntu/archives/ gutsy-security multiverse
# deb http://download.skype.com/linux/repos/debian/ stable non-free
# deb http://wicd.longren.org gutsy all
# deb http://packages.medibuntu.org/ feisty free non-free
# deb http://archive.ubuntustudio.org/ubuntustudio feisty main
# deb http://debian.websterwood.com/ feisty main
# deb-src http://debian.websterwood.com/ feisty main
# deb http://wine.budgetdedicated.com/apt feisty main
```

This are main .... i am not certain which one to remove can someone help out here ! 

Cheers

---

### Post by cchester on 2007-10-19
For me I was just using what was the default repositories after installing. Still can't download anything. Only able to use what was installed when I installed Ubuntu Gutsy 7.10.

---

### Post by bwallum on 2007-10-19
I think the repositories may have changed. I get the same. However I do have a perfectly functional Gutsy otherwise. No updates for about 48 hours now. I have been riding the beta  and have updating as I went along. I havn't used the install CD.

Post the repositories here if you find them, I'll do the same.

rgds
Bob

---

### Post by Montrevux on 2007-10-19
I'm getting the same problems. The update process hangs at the transaltion_en us when trying to go into the update manager or SPM.

---

### Post by Roofie on 2007-10-19
My first try today , did just hang and not download.
I waited for a while and tryed again.....
Then all upgrades came down, just real slow.
Just try again later

---

### Post by DOH on 2007-10-19
I changed my country codes from us to gb..
or go to source o matic and use that.
I think high traffic is causing this other countries seem a little less congested.

---

### Post by Montrevux on 2007-10-19
Yeah, this works. Changed my server in the "Software Sources" tool and did an automatic search for the best one. It picked a Canadian one, and it's working now.

---

### Post by unf on 2007-10-19
I can't get it why there is no load balance system with ubuntu.

---

### Post by bwallum on 2007-10-20
Upgrades seem to be going again. I have just got one.

---

### Post by dondad on 2007-10-21
> **cchester said:**
> Ok guess I will wait. I noticed that some people said there is a site that you can pick a different site to download from. If so do you know the link.

Thanks.

Try going to the system>software sources. In the box that says "download from" select the dropdown, then other. In that screen there is an option to find the fastest mirror for your location. It will run some tests, then suggest a mirror for you.

---

### Post by Robeasts on 2007-10-23
I just installed Ubuntu 7.10 using the live cd.  I ran into the same issue of not being able to download from the repositories.  When I checked the software sources (System --> Administration --> Software Sources) nothing was checked under the Ubuntu Software tab, the third-party software tab or the updates tab.  Once I checked the appropriate boxes within these tabs and reloaded the repositories I was able to update and download applications.  Hope this helps someone.

---

### Post by 80211support on 2007-11-02
Same problem, anyone have better luck during daylight?

---

### Post by bwallum on 2007-11-02
Hi

Go to System>Administration>Software Sources. You will have to enter your password.

Check the first four boxes under the 'Oubuntu Software' tab. Under the 'Updates' tab check the first four boxes and then decide when you want to update.

If you  are running unsupported software make sure the repository is added under the 'Third Party Software' tab. A really good one here is:-

[http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy

You can cut and paste the line above and add it to your system.

To check if you are up to date then go to System>Administration>Update Manager.  Click on the check button. If your internet connection is ok you will see the manager work. Days can go by without updates simply because there aren't any.

Bob

---

