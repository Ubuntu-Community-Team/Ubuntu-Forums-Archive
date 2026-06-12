---
title: "How to stop installing kernel on upgrade on artful?"
date: 2017-07-13
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-07-13
I have kernel 4.12.0-041200-generic installed, but when I want to upgrade, apt says, it'd upgrade to  kernel 4.11.0-10-generic. It looks like that apt doesn't see the installed 4.12.0-041200-generic kernel. How to stop apt from (unnecessarily) installing the lower kernel?

---

### Post by dino99 on 2017-07-13
4.12 is not yet a supported/known version, so apt propose the latest genuine one. Note that 4.12 should land into artful archive in the coming days; before getting 4.13 when AA will be released.

---

### Post by Chanath on 2017-07-13
That's not what I wanted to know. I wanted to know how to tell apt to see what's in the system, rather than what might come there. When the number of the package is lower than the one that's installed, apt shouldn't propose its installation. Looks like a bug in dpkg/apt. 

In this case, because the higher number kernel was installed manually, apt can't propose to delete it. Any package installed manually cannot be 'autoremoved' by apt. I believe, apt should see even the manually installed packages. After all, it was apt/dpkg that installed them.

Any suggestions?

---

### Post by dino99 on 2017-07-13
apt only know the kernel format x.xx.x-xx
every other format is unknown (mainly daily/custom format naming)

---

### Post by QIII on 2017-07-13
How did you install the newer kernel?

---

### Post by Chanath on 2017-07-13
[FONT=arial]Used Ubuntu Kernel Update Utility to install the mainline kernel.[/FONT]

---

### Post by mc4man on 2017-07-13
The upgrades in question come from the linux-meta packages, i.e.  linux-generic, linux-image-generic, linux-headers-generic

---

### Post by Chanath on 2017-07-14
> **mc4man said:**
> The upgrades in question come from the linux-meta packages, i.e.  linux-generic, linux-image-generic, linux-headers-generic

Yes, I understand that. I was thinking about Apt. Why can't it see that the number of installed app is higher than the one it proposes? linux-image-4.12.0-...against linux-image-4.11.0-...

---

### Post by mc4man on 2017-07-14
> **Chanath said:**
> Yes, I understand that. I was thinking about Apt. Why can't it see that the number of installed app is higher than the one it proposes? linux-image-4.12.0-...against linux-image-4.11.0-...

Has noting to do with that at all.
Apt is upgrading the linux-meta packages, period. As part of that they pull in their dependencies which are specific latest Ubuntu linux source packages.
If you don't want this behavior then remove the meta packages.

---

### Post by ventrical on 2017-07-15
I was just wondering if you had proposed enabled and then  shut it off? I know that during last cycle there were problems while during an update it would turn proposed off or on. It was fixed .. but I wonder if it's back.

 Just  thinking out loud.

Regards..

---

### Post by Chanath on 2017-07-15
> **mc4man said:**
> Has noting to do with that at all.
Apt is upgrading the linux-meta packages, period. As part of that they pull in their dependencies which are specific latest Ubuntu linux source packages.
If you don't want this behavior then remove the meta packages.

Can you tell me which linux-meta packages to remove?

---

### Post by Chanath on 2017-07-15
> [COLOR=#000000]I was just wondering if you had proposed enabled and then shut it off?[/COLOR]

No, I didn't do that, ventrical.
Regards!

---

### Post by deadflowr on 2017-07-15
> **Chanath said:**
> Can you tell me which linux-meta packages to remove?

The 3 mc4man already listed:
linux-generic linux-image-generic and linux-headers-generic.

---

### Post by Chanath on 2017-07-17
> **deadflowr said:**
> The 3 mc4man already listed:
linux-generic linux-image-generic and linux-headers-generic.

Okay. Could you tell me, what would happen, if I uninstall linux-generic linux-image-generic and linux-headers-generic? What would break?

---

### Post by dino99 on 2017-07-17
this is the linux-generic description:

This package will always depend on the latest complete generic Linux kernel and headers.

I let you grab the other meta-packages description (easily done via synaptic for example). As you can understand, these meta packages are 'scripts' calling the required dependencies. 
When removed, then you have to do job yourself indeed.

---

### Post by Chanath on 2017-07-17
> **dino99 said:**
> this is the linux-generic description:

This package will always depend on the latest complete generic Linux kernel and headers.

I let you grab the other meta-packages description (easily done via synaptic for example). As you can understand, these meta packages are 'scripts' calling the required dependencies. 
When removed, then you have to do job yourself indeed.

I was wondering what would break, if I remove the meta packages. I have the mainline kernel installed, so it is not dependent on the meta package. Anyway, using 17.10 is experimenting.

---

### Post by mc4man on 2017-07-17
New kernel versions aren't upgrades, they're new versions. So without the linux-meta packages you'll never be informed or offered a new version
Installed versions can occasionally get an update, in that case you'd be informed, i.e. this has nothing to do with the meta packages.

---

### Post by Chanath on 2017-07-17
> **mc4man said:**
> New kernel versions aren't upgrades, they're new versions. So without the linux-meta packages you'll never be informed or offered a new version
Installed versions can occasionally get an update, in that case you'd be informed, i.e. this has nothing to do with the meta packages.

Have you tried Ubuntu Kernel Update Utility? That's what I used to install kernel 4.12. Its letting me know about  the next available kernels. I can install 4.13-rc1 from it.

---

### Post by #&amp;thj^% on 2017-07-17
> **Chanath said:**
> Have you tried Ubuntu Kernel Update Utility? That's what I used to install kernel 4.12. Its letting me know about  the next available kernels. I can install 4.13-rc1 from it.

If this is the one you are referring to.
```
apt policy ukuu
ukuu:
  Installed: 17.2.3~77~ubuntu16.04.1
  Candidate: 17.2.3~77~ubuntu16.04.1
  Version table:
 *** 17.2.3~77~ubuntu16.04.1 500
        500 http://ppa.launchpad.net/teejee2008/ppa/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```
There is not yet even a build (.deb) for 17.10 yet....and this had caused many problems on my systems in the past. (Just Saying)
[http://ppa.launchpad.net/teejee2008/ppa/ubuntu/pool/main/u/ukuu/](http://ppa.launchpad.net/teejee2008/ppa/ubuntu/pool/main/u/ukuu/)
Albeit it has been a long time since i used it also, nor do  I think I will revisit it any time soon.:)
But there is a setting you can use to stop showing the newer kernels:
By unticking the top 2 in Settings
1.Notify if a major release is available.
2.Notify if a point release is available.
Then just open the Update utility when you want to see or check for changes.

---

### Post by Chanath on 2017-07-17
> **1fallen said:**
> 
There is not yet even a build (.deb) for 17.10 yet.
But there is a setting you can use to stop showing the newer kernels:

It doesn't matter, if there is no deb package made for 17.10. Artful is not yet released. And I'm experimenting with 17.10, just like most of us using it. I don't have Gnome or any DE, just Openbox. Nothing much to break, really. I'll remove the Linux meta packages to see how far I can go.

I want UKUU to show the availability of newer Ubuntu mainline kernels. Its nice to know.

---

