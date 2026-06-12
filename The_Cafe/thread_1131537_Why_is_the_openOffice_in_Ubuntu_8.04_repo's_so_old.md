---
title: "Why is the openOffice in Ubuntu 8.04 repo's so old ?"
date: 2009-04-20
forum: The Cafe
---

### Post by rucadulu on 2009-04-20
Why is the openOffice in _U_buntu 8.04 repo's so old it is 2.4  and the latest release is 3.0.1 ??

---

### Post by Skripka on 2009-04-20
> **rucadulu said:**
> Why is the openOffice in _U_buntu 8.04 repo's so old it is 2.4  and the latest release is 3.0.1 ??

Because at the time of HH release, that was the current OOO.  

That is inline with Ubuntu's stated policy of official release repos software, and what needs backported.

---

### Post by rucadulu on 2009-04-20
I understand that it was the latest at the time of release for 8.04 But, why does Ubuntu not make newer versions of software available on their LTS release repo's as the software is updated. I can go download and install it from Sun but it would be nice to have the versions of key software like openOffice upgrade in the repo's of LTS release's as the newer versions become available.

---

### Post by swoll1980 on 2009-04-20
> **rucadulu said:**
> I understand that it was the latest at the time of release for 8.04 But, why does Ubuntu not make newer versions of software available on their LTS release repo's as the software is updated. I can go download and install it from Sun but it would be nice to have the versions of key software like openOffice upgrade in the repo's of LTS release's as the newer versions become available.

They do, It's called backports. You have to enable them.

---

### Post by smartboyathome on 2009-04-20
> **rucadulu said:**
> I understand that it was the latest at the time of release for 8.04 But, why does Ubuntu not make newer versions of software available on their LTS release repo's as the software is updated. I can go download and install it from Sun but it would be nice to have the versions of key software like openOffice upgrade in the repo's of LTS release's as the newer versions become available.

Because newer versions may have bugs, and they wouldn't be as well tested.

---

### Post by rucadulu on 2009-04-20
I do have the backports enabled.

---

### Post by swoll1980 on 2009-04-20
You could always use a rolling release distro like Sid, or PCLinuxOS. If the packages aren't sharp enough for you.

---

### Post by smartboyathome on 2009-04-20
> **swoll1980 said:**
> You could always use a rolling release distro like Sid, or PCLinuxOS. If the packages aren't sharp enough for you.

Or Arch Linux.[/promotion] ;)

---

### Post by Ticketoride on 2009-04-20
> **rucadulu said:**
> Why is the openOffice in _U_buntu 8.04 repo's so old it is 2.4  and the latest release is 3.0.1 ??
I downloaded OO301 when I still ran 8.04 directly from their Site, double-clicked on the *.deb File, all installed without a Hitch, and ran perfectly.

---

### Post by Skripka on 2009-04-20
> **smartboyathome said:**
> Because newer versions may have bugs, and they wouldn't be as well tested.

Or they may just plain not work with older versions of Ubuntu.

---

### Post by rucadulu on 2009-04-20
I have the latest version of openOffice installed. It would just be nice to have it in the repo's for the distro I am using (makes life a little easier). I chose the Ubuntu 8.04LTS distro because I like the idea of staying with the same base release for more than 6 to 18 months. I was just under the impression that the software in the LTS distro's would also remain as fresh as possible (taking stablity into account). I should have learned that this was not the case when I used Ubuntu 6.10LTS. Oh well you can not blame a guy for asking.

---

### Post by JC Cheloven on 2009-04-20
Add this to sources.list (third party software) and update:

```
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
```

Edit: this is for intrepid. For Hardy should be similar.

---

### Post by SunnyRabbiera on 2009-04-21
The ppa repo will update to a more current version.

---

### Post by zugu on 2009-04-21
Use of third-party repositories is not recommended by Canonical. It's not safe. For example, if the latest version of OpenOffice.org were safe to use in 8.04, it would have been already present in the official repositories.

So unless you upgrade, you won't find a newer OpenOffice.org in the official repositories.

---

### Post by nandemonai on 2009-04-21
> **rucadulu said:**
> (taking stablity into account)

That's the whole point.

---

### Post by forrestcupp on 2009-04-21
You completely misunderstood.

Do you want cutting edge, or do you want stability.  You can't have them both.  LTS is the opposite of cutting edge.  They make a stable system and keep it that way.  The only thing that gets updates are bug fixes.

If you want cutting edge, then just upgrade to the latest release.  That's why they have them.  If you wait until a new version is released, and don't go with the betas, you pretty much get the same stability you do in an LTS; they're just not supported as long.  In fact, some people might argue that the last LTS was less stable when it was released than some of the in-between versions.

---

### Post by snowpine on 2009-04-21
It is simple really, 8.04 means April 2008; if you use a year-old stable Linux release, you get a year-old stable release of OpenOffice. That is the way it should be, in my opinion. :) If you want applications from 2009, use an Ubuntu release with a 9 in it.

---

### Post by 3rdalbum on 2009-04-21
"Stable" doesn't just mean "does this new software crash" - it means "will I get a lot of support calls from users who complain of missing/changed features or regressions if I update this software".

If there's a chance that some features may not work as well as before, than Canonical will not put them into an already-released version of Ubuntu.

If you run an Ubuntu LTS release, you know that there will be NO unpleasant surprises for the next 3 years - and after 3 years it's time to upgrade to the next LTS. Unpleasant surprises cost businesses a lot of money. Businesses chasing up Canonical Support every 5 minutes due to unpleasant surprises, costs Canonical a lot of money.

In terms of "does this software crash" or "does this software have bugs", an Ubuntu LTS release is exactly the same as a non-LTS release. So if you're running Hardy LTS because "it surely has fewer problems than Intrepid or Jaunty which are not LTSes", then maybe you should rethink your choice of distribution version.

---

### Post by 23meg on 2009-04-21
[QUOTE=zugu]
It's not safe. For example, if the latest version of OpenOffice.org were safe to use in 8.04, it would have been already present in the official repositories.
[/QUOTE]

That makes it sound as if arbitrary new upstream versions that pass a "safety" check can be included in the repositories for a stable release. There's no such policy.

The rationale for not updating to latest upstream releases is not *safety*, but *stability*, in the "does not change substantially over time" sense, not the "does not do something unexpected or crash whatsoever" sense.

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates) has more information regarding the policy.

---

### Post by zugu on 2009-04-22
> **23meg said:**
> That makes it sound as if arbitrary new upstream versions that pass a "safety" check can be included in the repositories for a stable release. There's no such policy.

The rationale for not updating to latest upstream releases is not *safety*, but *stability*, in the "does not change substantially over time" sense, not the "does not do something unexpected or crash whatsoever" sense.

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates) has more information regarding the policy.

What he said.

---

