---
title: "Mir gpu testing"
date: 2013-08-16
forum: Ubuntu Development Version
---

### Post by philinux on 2013-08-16
I assume a few of you have seen this. 

Thought I'd post this for anyone who might have missed it.

[https://wiki.ubuntu.com/Mir/GPUTesting](https://wiki.ubuntu.com/Mir/GPUTesting)

[http://iloveubuntu.net/mirxmir-available-public-testing-process-gpu-oriented](http://iloveubuntu.net/mirxmir-available-public-testing-process-gpu-oriented)

---

### Post by ventrical on 2013-08-16
Hadn't seen the wiki.

Thanks.

So far it has been very successful across all GPUs that I have tested, especially Intel based. No performance lag that I can see. Processors running cool, low usage .. etc..

Nice work team ! :)

---

### Post by grahammechanical on 2013-08-16
It is nice to see that they have included the results that were sent in about the Xubuntu-Xmir ISO testing. I am not sure how we can add results. Edit the wiki page? Still, my GPU is already there so I am out. We need ways like this of informing the developers of our results other than bug reports.  Without shutting our eyes to bugs, we also need positive results published.

Regards.

---

### Post by philinux on 2013-08-16
Yes edit the wiki page. The only caveat is about duplicates. ;)

---

### Post by ventrical on 2013-08-16
> **philinux said:**
> Yes edit the wiki page. The only caveat is about duplicates. ;)



 Now I know where the entry I made on the q&a tracker back about  two or three weeks ago went to. I entered some data during a test and , voila' .   it went to the wiki :) Manually editing the wiki is a lot easier posting the results.

---

### Post by grahammechanical on 2013-08-17
I am finding different instructions on how to install.

do we do this?

```
sudo apt-get mir-demos unity-system-compositor
```

[http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html](http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html)

or this?

```
 apt-get install unity-system-compositor
```

[https://wiki.ubuntu.com/Mir/Installing](https://wiki.ubuntu.com/Mir/Installing)

I see this on packages.qa.ubuntu.com

> You can remove the repository version of mir by uninstalling: 
**sudo apt-get remove --purge mir-demos unity-system-compositor**
You may remove the experimental packages by using ppa-purge
1) Install ppa-purge
**sudo apt-get install ppa-purge**
2) Remove the ppa
**sudo ppa-purge ppa:mir-team/system-compositor-testing**
3) PPA Purge will find the packages installed and offered to downgrade them.
Say yes and ppa-purge will remove the upgraded versions and reinstall the versions from the archive.
4) In addition you may remove the /etc/apt/preferences.d/50-pin-mir.pref file
**sudo rm /etc/apt/preferences.d/50-pin-mir.pref**

But on this Launchpad page that PPA is listed as obsolete.

[https://launchpad.net/~mir-team/+archive/system-compositor-testing](https://launchpad.net/~mir-team/+archive/system-compositor-testing)

I have several flavours where I installed the system-compositor-testing PPA and yesterday when I tried to purge the PPA I could not purge it as it did not exist. And neither did 50-pin-mir.pref. Running dist-upgrade brought in upgrades to the libraries used by unity-system-compositor. I have yet to test those installs to see if the xmir module loads. But there we go.

Regards.

---

### Post by ventrical on 2013-08-17
I had problems with one install.. removing the ppa, but, I dropped to root and was able to do it there, remove all the old files and :

sudo apt-get install unity-system-compositor

I also had the experimental on several other desktops but I had to do some hardware house-cleaning and retired 4 machines and built (or rebuilt) 3 new ones so I just fresh installed from an early July saucy iso, update/upgrade and then put xmir on them - no problems.

  I do not want to say too much about the current state or condition of the daily-live because it may sound too controversial but the fact is that the earlier saucy isos are much better suited to test xmir with.

regards..

---

### Post by ventrical on 2013-08-17
> **grahammechanical said:**
> 

I have several flavours where I installed the system-compositor-testing PPA and yesterday when I tried to purge the PPA I could not purge it as it did not exist. And neither did 50-pin-mir.pref. Running dist-upgrade brought in upgrades to the libraries used by unity-system-compositor. I have yet to test those installs to see if the xmir module loads. But there we go.

Regards.

Ok.. just had this happen on another install. I then opened synaptic. Since the previous proceedure already updated the hive I just chose to upgrade unity-system-compositor, then :

sudo apt-get dist-upgrade

and all went well. Not sure what happened to ppa but it's working.

---

### Post by VMC on 2013-08-17
Failure using Ubuntu on a "NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)"

---

### Post by philinux on 2013-08-21
> **grahammechanical said:**
> I am finding different instructions on how to install.

do we do this?

```
sudo apt-get mir-demos unity-system-compositor
```

[http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html](http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html)

Regards.

From Jono.
[http://www.jonobacon.org/2013/08/15/mir-update-and-testing-mir-in-ubuntu-13-10/](http://www.jonobacon.org/2013/08/15/mir-update-and-testing-mir-in-ubuntu-13-10/)

[edit] forgot to say Success here too with gpu already entered "Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)". Not noticed anything different apart from conky not transparent.

---

