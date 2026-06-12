---
title: "Kde"
date: 2014-03-13
forum: Ubuntu Development Version
---

### Post by mJayk on 2014-03-13
14.04 - with KDE,

Im currently running 13.10 kubuntu, should I expect a horrendous fail if I try to upgrade to 14.04? I ask as I would prefer not to do a full reinstall, I have upgraded distro's in the past with no problems but always on straight ubuntu and never a *buntu.

Any thoughts or comments welcome.

Thanks

Matt

---

### Post by grahammechanical on 2014-03-13
When are you thinking of doing this upgrade? If you wait until Kubuntu 14.04 is released you should not have any problems. It is too soon, in my opinion to upgrade from 12.04 to 14.04 or from 13.10 to 14.04 on any version of Ubuntu because development is not finished and the upgrade path has not been tested.

Of course, the Kubuntu developers would welcome you as an upgrade path tester.

Regards.

---

### Post by QDR06VV9 on 2014-03-13
I agree with grahmmechanical whole heartily!
But I have taken two installs of Saucy to Trusty(_**NOT RECOMMENDED**_) 
By way of
```
sudo sed -i 's/saucy/trusty/g' /etc/apt/sources.list
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get upgrade 
```
One was smooth minimal problems. The second one I had forgotten to uninstall  Nvidia(PPA)Driver
But I was able to reinstall Nvidia and all is good on both.

---

### Post by Bucky Ball on 2014-03-13
I'd wait. It is due in a month, April 17th. Not to say it will be rock solid by then, but better. A month out is when you generally see some  breakage before the final, usually stable-ish release.

If you have the room, why not install and dual (triple?) boot 14.04 LTS and simply switch when released? You could do that anyhow, even if you intend to do the upgrade you mention. A separate install might indicate when it is stable enough and safe to do so.

---

### Post by SeijiSensei on 2014-03-13
I've installed both the alpha and beta versions of Kubuntu 14.04 and found them generally free of any major bugs.  I'd agree that it might make more sense to wait until April to upgrade, but if you're installing from scratch, I'd use the 14.04 beta.

---

### Post by sffvba[e0rt on 2014-03-13
I did an upgrade to 14.04 from 13.10 and it went flawlessly... and there has been several others. Then again, YMMV.

---

### Post by mJayk on 2014-03-14
Yea thanks for the advice people, ill overwrite my borked arch install with a fresh 14.04 kubuntu. Thanks again.

---

