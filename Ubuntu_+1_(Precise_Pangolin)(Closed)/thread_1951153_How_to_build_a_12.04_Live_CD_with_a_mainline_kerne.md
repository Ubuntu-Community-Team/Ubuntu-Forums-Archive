---
title: "How to build a 12.04 Live CD with a mainline kernel"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Kensey on 2012-04-02
As part of an earlier-filed bug report, I was asked by a maintainer to test with the latest mainline kernel in the latest 12.04 build.  Since I didn't want to install a beta version on my laptop, I ended up stumbling my way through the process of customizing the live CD and figured I might save some other folks time in the future.

The first step of course is to download the live CD ISO.  You are also going to need a few packages -- in my case:

From the mainline kernel PPA (daily/current)

* linux-headers-3.4.0-999-generic_3.4.0-999.201204010405_amd64.deb
* linux-headers-3.4.0-999_3.4.0-999.201204010405_all.deb
* linux-image-3.4.0-999-generic_3.4.0-999.201204010405_amd64.deb

From the Precise Pangolin main pool:

* fuse-utils_2.8.6-2ubuntu2_all.deb

From the Precise universe pool:

* unionfs-fuse_0.24-2.1ubuntu1_amd64.deb

You don't have to download the packages right now, but have the links to them handy.

Now you will need to install Ubuntu Customization Kit on the system you downloaded the ISO to.  Fire it up and point it at the ISO, making sure you tell it at the beginning that you want to customize manually later.  I had it only install and make available the English language packs (your language may vary of course), remove the Windows files, and only include the GNOME environment.  At the point where it offers to run a package utility, open a shell, or continue the build, have it open a shell.

You will now be at a root prompt in a chroot jail of the ISO contents.  You won't be able to apt-get install things not in the image (at least I wasn't), but you can use the network.  At this point you should be able to wget all five packages you need.  Install them in this order:

1. fuse-utils
2. unionfs-fuse
3. the three kernel packages all together

Now to save space, delete the .debs; you also want to remove the stock Ubuntu kernel images and headers:

linux-image-3.2.0-20-generic
linux-headers-3.2.0-20-generic
linux-headers-3.2.0-20

I did this with dpkg one package at a time, tracing the dependencies, but you may be able to just apt-get remove all three and have it do the right thing.

So, you installed the new kernel packages, removed the stock kernel packages, and cleaned up your package files.  Now exit the root shell and choose to continue building.

Assuming all goes well, you should end up with a live CD image, hopefully small enough to burn onto a CD if, like me, you have no blank DVD media handy. :)  Burn it, boot it and enjoy it!

---

### Post by stefaneb on 2012-04-10
How did you get UCK past the copy of resolv.conf?  I have seen others having the same issue I am, it fails to copy /etc/resolv.conf as follows:

Copying resolv.conf...
cp: `/etc/resolv.conf' and `/home/<username>/tmp/remaster-root/etc/resolv.conf' are the same file
Failed to copy resolv.conf, error=1
Build ended at 2012-04-10 11:42:27

I am preparing to move all my machines from 10.04 to 12.04, but not making a custom install is a deal breaker.  Granted we are only beta right now, but I am starting the ground work now (determining what needs to be in the custom distro).

---

### Post by wadl on 2012-04-11
> **stefaneb said:**
> How did you get UCK past the copy of resolv.conf?  I have seen others having the same issue I am, it fails to copy /etc/resolv.conf as follows:

Copying resolv.conf...
cp: `/etc/resolv.conf' and `/home/<username>/tmp/remaster-root/etc/resolv.conf' are the same file
Failed to copy resolv.conf, error=1
Build ended at 2012-04-10 11:42:27


Seems that this is a known bug in UCK. See [https://bugs.launchpad.net/uck/+bug/946480]("https://bugs.launchpad.net/uck/+bug/946480")

---

### Post by kaldor on 2012-04-11
Off topic, but I just wanted to mention that these sorts of guides are much appreciated in this forum. While not directly related to Precise, it's a good way to contribute to the community. Thanks :)

---

### Post by stefaneb on 2012-04-12
> **wadl said:**
> Seems that this is a known bug in UCK. See [https://bugs.launchpad.net/uck/+bug/946480]("https://bugs.launchpad.net/uck/+bug/946480")

Thanks for the pointer, I had found that about 15 minutes after posting my query.  Having tried their fix, I have run into another problem, and I clean install shows the same thing...after selecting the language pack to install, it thinks (no matter what pack I select it seems) I canceled the script with a return code of 139 instead of zero.  I wonder if anyone else has seen this...off to Google I go.

---

### Post by Kensey on 2012-04-13
Hm, you know, I remember running into the resolv.conf thing, but not how I solved it... and I didn't get it just now when I tried again.  I have a vague memory that I edited /usr/lib/uck/remaster-live-cd.sh to remove the bit about copying resolv.conf, and I see my current copy of that file has those lines intact and a modified date three days after I posted this guide.  So I think somehow those files got updated with a bug fix even though apt doesn't show any such thing in its logs.

---

