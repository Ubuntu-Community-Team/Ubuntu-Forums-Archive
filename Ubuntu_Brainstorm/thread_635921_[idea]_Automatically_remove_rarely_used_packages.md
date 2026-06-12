---
title: "[idea] Automatically remove rarely used packages"
date: 2007-12-09
forum: Ubuntu Brainstorm
---

### Post by k99goran on 2007-12-09
I don't know if this is feasible, but would it be possible to have a system set up where all packages have an expiration date (based on a countdown of sorts) and where...

1. Using the package will reset the date.
2. Letting the expiration date on the package pass will remove it from the system, leaving a kind of placeholder for the package.
3. Accessing the placeholder will prompt the system to download and install the package again and to do this automatically.

Would it reduce software bloat and downloaded updates?

---

### Post by rockin_goliath on 2007-12-09
I like this idea. I was always a little frustrated because sometimes I'll install a package with 50 dependencies, but when I uninstall the same package it only removes that one package and not the other dependencies. 

Could this be expanded into a larger idea, such as a System Cleanup GUI? Something where you could remove expired or orphaned packages, delete packages from the apt archive, delete expired configuration folders in the Home directory, etc.

---

### Post by k99goran on 2007-12-09
I just found that this was being considered to some degree as a clean-up wizard. [link]("https://wiki.ubuntu.com/HardyFullDiskHandling")

There were two things that prompted this idea:
1. The emerging market of cheap flashed-based sub-notebooks such as the EEE-PC. I think that Ubuntu in its current form is too fat to work properly on the small 2GB/4GB SSD.

2. Vista, as a cautionary tale. A recommended 40GB storage capacity for just the operating system just isn't necessary. I just don't believe most people will use all the things that come pre-installed.

---

### Post by Nekiruhs on 2007-12-09
This is not necessary. Just run apt-get ---autoremove (I think, i'm in windows now.) and it removes orphaned packages

---

### Post by k99goran on 2007-12-09
> **Nekiruhs said:**
> This is not necessary. Just run apt-get ---autoremove (I think, i'm in windows now.) and it removes orphaned packages
I wasn't just referring to orphaned packages.

---

### Post by coolen on 2007-12-09
The solution seems to be correct removal of orphaned packages.
For exaqmple, if you download a package that depends on several others, then remove it, they should be removed, unless another package has been downloaded which depends on them.
You can do this manually, as mentioned above (I think this was a feature of Edgy?). Perhaps setting an anacron job for it would be appropriate (with an option to disable).


As for programs you simply don't use very often, I think this could turn very negative. New (as well as experienced) users would become frustrated when a program takes several minutes to start because it's no longer present on their system, or feel pressured not to neglect programs they do want on their system lest they be axed.

---

### Post by k99goran on 2007-12-09
> **coolen said:**
> As for programs you simply don't use very often, I think this could turn very negative. New (as well as experienced) users would become frustrated when a program takes several minutes to start because it's no longer present on their system, or feel pressured not to neglect programs they do want on their system lest they be axed.
A few things I should add:

1. The function should be completely optional, and the user should be able to turn it off at any time. Keep in mind that this is mostly meant for small drives where software bloat is a big problem.
2. The rate at which packages are removed should be alterable, setting the 'aggressiveness' of the clean-up tool.
3. Certain critical, yet rarely used packages should obviously never be removed by the tool.
4. Perhaps a function to protect packages would be in order, though I don't see why someone would want to keep an application on their system that they never use.
5. Packages that are not available in the repositories should be protected unless they are orphaned.
6. Old log-files and other junk should of course periodically be purged from the system.
7. Removal of orphaned packages would be automatic as these packages are by definition never used.

---

### Post by smartboyathome on 2007-12-09
I would say if this is included, it should be turned off, since most drives aren't that small anymore (I find that many computers come with at least an 80GB drive).

---

### Post by k99goran on 2007-12-09
> **smartboyathome said:**
> I would say if this is included, it should be turned off, since most drives aren't that small anymore (I find that many computers come with at least an 80GB drive).
Perhaps the default could be based on the size of the partition where you install Ubuntu.
6GB or less -> ON by default.
Over 6GB -> OFF by default.
The exact execution of the tool isn't that important, it could be automated and clean up the operating system on each boot-up or it could be a program that needs to be run manually. The important part is that there should be a system in place to keep track of which packages are used infrequently.

---

### Post by coolen on 2007-12-09
I'd say less than 3GB would be more reasonable. 6GB is big enough.

---

### Post by rockin_goliath on 2007-12-12
So, how hard would it be to make a easy to use GUI that can remove orphaned packages automatically, as well as temporary and cached files, such as the apt-get archive?

---

### Post by coolen on 2007-12-12
So not very that they already exist.

---

