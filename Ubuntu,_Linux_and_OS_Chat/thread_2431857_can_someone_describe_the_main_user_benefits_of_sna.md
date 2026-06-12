---
title: "can someone describe the main user benefits of snaps?"
date: 2019-11-23
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-11-23
can someone describe the main user benefits of snaps (the way it works, and so on)?  i don't even try to use them, but who knows which way i might go in the future.

---

### Post by CatKiller on 2019-11-23
The benefits aren't really for the user directly.

I think you already know how libraries and dependencies work with the package manager: there is one version of a given library or framework on the system, and every application that needs that library uses the same one. The package maintainers make sure that the applications in the repository work with the libraries in the repository, and the package manager makes sure that libraries are installed when needed and uninstalled when no application needs them any more. 

For software in the repositories this is perfect; there is only one version that needs to be downloaded, one version on disc, one version in RAM, one version to be patched for security, and so on. 

If you write software that isn't in the repository, though, because it's proprietary or niche or whatever, you either need to get someone else to package your software for you or you need to test your software against the libraries that are in (different versions of) Ubuntu, the libraries that are in Fedora, the libraries that are in Arch, and so on, and keep it working even as those distros get updated.

Snaps bundle together an application with all the libraries that it needs and sandbox them from the rest of the system. If you have lots of snaps then that's lots of different versions of the same libraries that need to be downloaded, need to take up space, need to take up RAM, and need to be patched for security. Because they're sandboxed there are limits on where they can read or write, and they're easier to switch between versions independently of the rest of the system. 

Ultimately the user benefit is that you get access to (particularly proprietary) software that you otherwise wouldn't. Because Canonical have got Snapcraft as a repository of snaps, which is integrated into their Software Centre, snaps can be installed and updated in the same way as traditional packages.

---

### Post by crip720 on 2019-11-23
From what little I have read, most of the benefits are for the Devs.  One snap program can work on many different versions, instead of needing different builds of a program of the different versions of ubuntu/linux.  For the user snaps need to have more permissions given to them by the user for full functionally.  Some programs have already been seen to have only a snap way of installing them, no debs or other ways, like Chromium.

---

### Post by Tadaen_Sylvermane on 2019-11-23
i love ubuntu but i moved my main server to debian because i wanted the maximum stability and reliability i could get. with snapd being available on debian i was able to effortlessly add lxd and move my ubuntu infrastructure lxd containers over to the new server without a problem. total transfer time to full network operation? a couple minutes. i love lxd and it's network availability and snaps made it available for me on debian without any trouble.

i've already seen the downside of snaps though and it will only get worse. i've seen a few threads on various forums about some snaps being out of date with current software offerings. the way snaps work, there is little reason to keep them updated unless they are backed by someone like canonical directly. snaps are going the way of most windows software, very out of date, full of security holes, and not much anyone can do about it other than repacking the snap themselves. maybe the sandboxing will protect them and this isn't an issue. i don't know i guess. it seems they solved a problem, but caused a bigger one in my opinion. we will end up with millions of snaps, dozens of versions of the same software, most severely out of date, but still working and most people won't have a clue. without a way to force people to keep snaps updated, they really didn't change much for the better imho.

there is definitely a benefit to the way things have been done in linux for a long time with package management, maintainers, and shared libraries. it's just a shame it's duplicated work for every distro. i like the idea of a universal package. but i'm afraid snaps aren't the way to go unless backed by someone who has a vested interest in keeping them current.

---

### Post by Skaperen on 2019-11-23
let me try to rephrase a benefit.  packages that may or do have difficulty with a wide range of versions of other software they use, libraries for binary programs, commands for scripts, can be packaged with the optimal versions, which will likely be different in different snaps.  then a disadvantage will be that having a lot of snaps means a larger amount of file system usage than if all those package were done the traditional way.

does that mean that snaps is not destined to be a replacement for the traditional method, but is, instead, a supplement that can make things like specialized software and backporting easier to do, benefitting the user with greater availability and improved stability?

---

### Post by Skaperen on 2019-11-23
> **Tadaen_Sylvermane said:**
> there is definitely a benefit to the way things have been done in linux for a long time with package management, maintainers, and shared libraries. it's just a shame it's duplicated work for every distro. i like the idea of a universal package. but i'm afraid snaps aren't the way to go unless backed by someone who has a vested interest in keeping them current.

perhaps the benefit will be more realized by the original developer who can make a single snap of her software and expect it to work across a wide range of distributions and the many versions of those (for one architecture in the case of binary executables).

---

### Post by SeijiSensei on 2019-11-23
From CatKiller's description, snaps sound like most Windows programs which are compiled with static libraries. Sounds like unnecessary redundancy to me.  Plus I don't want to run every program in a sandbox.

---

### Post by Skaperen on 2019-11-24
at this point it sounds like snaps are useful in a few cases but not in the general case.  there might be a wide choice in the Snap Store but most people that have any will have few, i suspect.  i have heard that lxc and lxd are going to be snap-only.  i probably won't use them.

---

### Post by mclark2145 on 2019-11-24
With everything installed on my system, I don't (as it happens) have any Snap-delivered software. I've played with snap and I have used AppImage-distributed software before, and they're fine but the problem is they tend to be slow and sometimes have visual integration issues with the host system.

---

### Post by Artim on 2019-11-24
As much as I hate PPAs for software that isn't available in the Ubu repos, I would rather use a PPA than a snap, having seen multiple threads in these forums about trouble with snaps.

---

### Post by CatKiller on 2019-11-24
However useful they might be for developers, and however much Canonical want people to use them because they're The Future™, and however useful it is to have snaps for third-party stuff available in the same place as you'd install anything else, having both snaps and normal packages show up for the same software is just *horrible* for users, especially new users. Any snaps that are also in the repositories should just be hidden.

---

### Post by Skaperen on 2019-11-24
> **CatKiller said:**
> However useful they might be for developers, and however much Canonical want people to use them because they're The Future™, and however useful it is to have snaps for third-party stuff available in the same place as you'd install anything else, having both snaps and normal packages show up for the same software is just *horrible* for users, especially new users. Any snaps that are also in the repositories should just be hidden.

i totally agree.  having both for the same package can be confusing.

---

### Post by Skaperen on 2019-11-24
i wonder: is a snap any good for containerization?

---

