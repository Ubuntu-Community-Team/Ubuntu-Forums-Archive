---
title: "Firefox Locks Up - Not Hogging Resources"
date: 2017-02-12
forum: Ubuntu/Debian BASED
---

### Post by pfthizzz on 2017-02-12
AMD FX-8320
16 gb ram
/ and /home on an ssd with plenty of space

I installed Maui Linux 2 (Firefox comes bundled with this) a couple days ago. Everything has been running smoothly. Then Firefox begins acting up last night. I don't recall what, if any, changes I made that immediately preceded the issues.

Firefox will lock-up completely for a minute or more. Then it will unlock for maybe 3 to 30 seconds, and lock up again. And it will just continue doing this. Sometimes it locks up while launching. Sometimes it will work fine for a few minutes before it begins locking up.

When it locks up, I can look at it in System Monitor and see it's not using much RAM, and its CPU usage is zero. 
Running iostat, vmstat, and pidstat for more details shows little is going on with FF or the rest of the system.

I've purged firefox (and ubufox), emptied-out the ~/.mozilla folder, rebooted and tried again. Same problem. Even a fresh installation will not work right.


I'm installing the following packages out of the xenial repository:
firefox
1:51.0.1+build3-0ubuntu0.16.04
 
xul-ext-ubufox
3.2-0ubuntu1
 

If I download FF directly from Mozilla's website, it comes as an archive file. I can extract that to a folder, run it from that folder, and it works flawlessly. But installing the package from the repository just will not work.

How can I track down the source of this issue?

thanks

---

### Post by QIII on 2017-02-12
Moved to Ubuntu/Debian BASED.

Hello!

Maui Linux is not an official flavor of Ubuntu.  It is based on Debian, not Ubuntu.

But we still welcome your question in this section of the Forums.

Best wishes!

---

### Post by pfthizzz on 2017-02-12
> It is based on Debian, not Ubuntu.

Maui is definitely based on Ubuntu, and is only based on Debian by virtue of being based on Ubuntu.

The current version is based on 16.04, and will be until the next LTS comes out.

---

### Post by pfthizzz on 2017-02-13
I don't know if the issue is related to something contained within the packages in the repository, or if it's something elsewhere in my system that the repository FF interacts with that the FF from Mozilla does not.

---

### Post by QIII on 2017-02-13
Maui is most certainly not based on Ubuntu. It is based on Debian and KDE Neon, which uses Canonical's repos.  Neither of those is Ubuntu.  It may use Canonical's repos, but it is not an Ubuntu flavor.

Your post has been moved to this sub-forum because it is not a request for support for an official flavor of Ubuntu.  The Maui devs may have made any number of changes that might produce conditions where an answer based on Ubuntu might not work.

---

### Post by pfthizzz on 2017-02-13
> **QIII said:**
> Maui is most certainly not based on Ubuntu. 
The homepage for KDE Neon describes it as "using a stable Ubuntu long-term release as its core."
[https://neon.kde.org/](https://neon.kde.org/)

This article from Linux.com describes KDE Neon as based on Ubuntu.
[https://www.linux.com/learn/kde-neon-offers-near-perfect-desktop-solid-platform](https://www.linux.com/learn/kde-neon-offers-near-perfect-desktop-solid-platform)

This February 2 article from OMG! Ubuntu! describes KDE Neon as "Ubuntu-based."
[http://www.omgubuntu.co.uk/2017/02/plasma-5-9-update-now-available-kde-neon](http://www.omgubuntu.co.uk/2017/02/plasma-5-9-update-now-available-kde-neon)

This Phoronix article describes KDE Neon as "a new distribution freshly forked from Ubuntu."
[http://www.phoronix.com/scan.php?page=article&item=kde-neon-rock&num=1](http://www.phoronix.com/scan.php?page=article&item=kde-neon-rock&num=1)

The About page for Maui Linux describes Maui as "based on KDE Neon/Ubuntu."
[https://mauilinux.org/about/](https://mauilinux.org/about/)

This article from Ubuntu Maniac states Maui is, "a part-rolling distribution based on Ubuntu 'Xenial'."
[http://www.ubuntumaniac.com/2016/11/maui-linux-21-released-bring-kde-plasma.html](http://www.ubuntumaniac.com/2016/11/maui-linux-21-released-bring-kde-plasma.html)

This Softpedia article describes Maui as a "KDE Plasma 5.8.2 LTS desktop environment on top of an updated Ubuntu 16.04 LTS base."
[http://news.softpedia.com/news/maui-2-blue-tang-linux-still-based-on-ubuntu-16-04-lts-ships-kde-plasma-5-8-2-509771.shtml](http://news.softpedia.com/news/maui-2-blue-tang-linux-still-based-on-ubuntu-16-04-lts-ships-kde-plasma-5-8-2-509771.shtml)

> **QIII said:**
> Your post has been moved to this sub-forum because it is not a request for support for an official flavor of Ubuntu. 

 I thought the "General" sub-forum was for any Ubuntu-based distro. I misunderstood. Thank you for moving it to the correct sub-forum. 

> **QIII said:**
> The Maui devs may have made any number of changes that might produce conditions where an answer based on Ubuntu might not work.

This is a valid point, and I would not want someone taking the time to provide suggestions for a Debian-based distro that might not be valid if I'm running an Ubuntu-based distro.

---

### Post by QIII on 2017-02-13
KDE Neon is not Ubuntu.  It is *based* on Ubuntu.

Maui is based on Debian and KDE Neon.  It is *NOT BASED ON UBUNTU*, despite any number of incorrect anecdotal articles you with to refer to.  This is a common misconception.  Being based on a derivative of Ubuntu does not mean being based on Ubuntu.

KDE Neon is not Ubuntu.  KDE Neon posts are moved to this sub-forum as well.

I would suggest that arguing with the Staff is not the approach most likely to help your cause.

---

### Post by pfthizzz on 2017-02-14
> **QIII said:**
> KDE Neon is not Ubuntu.  It is *based* on Ubuntu.
Yes, I agree. That is what I said.

> **QIII said:**
> Maui is based on Debian and KDE Neon.  It is *NOT BASED ON UBUNTU*, despite any number of incorrect anecdotal articles you with to refer to.
The homepage for Maui states it is based on KDE Neon & Ubuntu, as I quoted in my previous post. Your comment is the only statement that Maui is based on Debian that I have seen. Would you kindly explain why you say it is based on Debian?

> **QIII said:**
>  KDE Neon posts are moved to this sub-forum as well.
I understand. I don't have an issue with my post being moved to this sub-forum.

> **QIII said:**
> I would suggest that arguing with the Staff is not the approach most likely to help your cause.
I trust that the Staff desires to help me and would not, on account of an honest and polite disagreement, do something to make it difficult for me to receive the assistance I seek.

---

### Post by pfthizzz on 2017-02-19
I purged firefox again, reinstalled it (1:51.0.1+build3-0ubuntu0.16.04) this time *without* xul-ext-ubufox (3.2-0ubuntu1), but the problem remains.

I purged it once again, and installed firefox-mozilla-build (51.0.1-0ubuntu1) from the ubuntuzilla repository instead. This package works just fine, without problems. I may stick with this, but I'd still like to find out what's causing the lockups with the package from the xenial repository.

---

### Post by pfthizzz on 2017-03-01
Incidentally, I've a second pc on which I installed Maui a few days after the system in question, and it has never had a problem with the FF package from the xenial repo.

---

