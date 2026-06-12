---
title: "Installing Mixxx 1.5.0"
date: 2008-05-18
forum: Ubuntu Studio
---

### Post by ezramorris on 2008-05-18
Hi,
I notice that in Ubuntu Hardy, Mixxx 1.6.0 is the default package, but it is beta, and I have found it to be a bit buggy. So, is there any way I can downgrade to Mixx 1.5.0?

Thanks.

---

### Post by Stochastic on 2008-05-18
yup, first un-install mixxx through your favorite package manager ```
sudo apt-get remove mixxx
``` then go to [mixxx's webpage](http://www.mixxx.org/download.php) and download 1.5.0 (either the binary or the source) and install (or compile if you chose the source code).

---

### Post by ezramorris on 2008-05-18
> **Stochastic said:**
> yup, first un-install mixxx through your favorite package manager ```
sudo apt-get remove mixxx
``` then go to [mixxx's webpage](http://www.mixxx.org/download.php) and download 1.5.0 (either the binary or the source) and install (or compile if you chose the source code).

Thanks, this is what I was looking towards anyway. It's a pity, though, because I would have liked it to come up on the updates, and would have liked the ubuntustudio-audio package to remain (mixxx is a dependency).

I wonder why there is so much beta software in an OS release?

---

### Post by Stochastic on 2008-05-19
> **ezramorris said:**
> ...I would have liked it to come up on the updates, and would have liked the ubuntustudio-audio package to remain (mixxx is a dependency).

Well there may be another way (though I can't guarantee success) in which you install the mixxx in a local folder then do ```
sudo ln /home/you/mixx/mixxx1.5 /usr/bin/
``` as long as you have the executable named with the version number on the manual install then you should be able to have both versions installed.  The sticky issue with this is that some programs will write to global config files, thus screwing up the originally installed 1.6

Another way is to setup a 'sandbox' environment, but that is a little unpractical for a preferred application, not to mention a little too advanced for most.

As for loosing the meta-package, it's no big deal.  It only points to other packages as dependencies, therefore once those are installed the meta becomes essentially a useless pointer file (until October's Intrepid updates come along).  The only time this wouldn't be true would be if a new dependency was added to the meta, but I think that's fairly unlikely.

> **ezramorris said:**
> I wonder why there is so much beta software in an OS release?

Well the answer here lies more in the Ubuntu core design than in a direct choice to have (enter package name here) released in the beta format for this release.  Ubuntu is derived from a snapshot of Debian's Sid/Unstable branch - for the most part - and is intended for a quick release cycle.

I'll admit the number of beta apps in this release seems higher to me too, which is kinda ironic for a LTS release; but maybe this will allow for the programs to not be too out of date by the end of the support cycle.

---

### Post by ezramorris on 2008-05-19
> **Stochastic said:**
> Well there may be another way (though I can't guarantee success) in which you install the mixxx in a local folder then do ```
sudo ln /home/you/mixx/mixxx1.5 /usr/bin/
``` as long as you have the executable named with the version number on the manual install then you should be able to have both versions installed.  The sticky issue with this is that some programs will write to global config files, thus screwing up the originally installed 1.6
That would involve compiling it from source, wouldn't it? I tried that with not much success. It needed loads of *-dev deps, installed all off them, but still wouldn't compile. I did what you suggested and installed the binary.
> **Stochastic said:**
> The only time this wouldn't be true would be if a new dependency was added to the meta, but I think that's fairly unlikely.
This is the reason I wanted to keep it, but I can't have everything.
> **Stochastic said:**
> Well the answer here lies more in the Ubuntu core design than in a direct choice to have (enter package name here) released in the beta format for this release.  Ubuntu is derived from a snapshot of Debian's Sid/Unstable branch - for the most part - and is intended for a quick release cycle.

I'll admit the number of beta apps in this release seems higher to me too, which is kinda ironic for a LTS release; but maybe this will allow for the programs to not be too out of date by the end of the support cycle.
Yeah, I don't know much about Ubuntu's derivatives and release cycles, so does LTS imply that some people will install it and never update it until the support for it ends?

Anyhow, as I said, I installed the binary off their website and it works great.

Thanks again.

---

### Post by Stochastic on 2008-05-19
> **ezramorris said:**
> Yeah, I don't know much about Ubuntu's derivatives and release cycles, so does LTS imply that some people will install it and never update it until the support for it ends?

Yeah, some people would do such a thing.  After all I still know people running windows98 or 2000 (whom I pitty, but that's a different issue entirely).

Glad things are working, and you really don't need to worry about the meta package thing; if you manually check the contents of the meta at [http://packages.ubuntu.com/hardy/ubuntustudio-audio](http://packages.ubuntu.com/hardy/ubuntustudio-audio) then you can do the job apt was doing for you (it's quite unlikely to change though).

---

