---
title: "Do USC &amp; Synaptic not prompt to remove old kernels?"
date: 2013-12-27
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2013-12-27
I'm seeing a few threads in which users have accumulated quite a few old kernels to the point that /boot is full (if I understand correctly). Here is the most recent example:  [/boot is 100% full, unable to remove any kernel images]("http://ubuntuforums.org/showthread.php?t=2195665")

Does this happen because neither the Ubuntu Software Center nor Synaptic prompt users that there are older kernels and that these can be removed?

If both USC and Synaptic are considered "GUIs" for apt-get, then why is this feature not present? I use the CLI route and am regularly prompted about older kernels.

---

### Post by cariboo on 2013-12-27
I don't use the Software Centre, but I know Synaptic lists old kernels under local or obsolete software. I would venture to guess that those that run into the problem of not enough space in /boot don't use, or have never heard of Synaptic.

---

### Post by lykwydchykyn on 2013-12-27
I have never seen any apt front end prompt to remove old kernel packages.  I've just gotten into a habit of periodically cleaning out old kernels on all our machines at the house.  It's a chore, but, eh...

---

### Post by mips on 2013-12-27
It's not a bad thing and has it's plusses.

---

### Post by Elfy on 2013-12-27
> **lykwydchykyn said:**
> I have never seen any apt front end prompt to remove old kernel packages.  I've just gotten into a habit of periodically cleaning out old kernels on all our machines at the house.  It's a chore, but, eh...

Same here.

Frankly I wonder if the people falling into this trap even have a need to use a seperate /boot partition - I suspect not.

Wonder if they have seperate /usr and others ...

---

### Post by Elfy on 2013-12-27
> **mips said:**
> It's not a bad thing and has it's plusses.

Agree with this too - it's only a bad thing when people are using too small a partition for it - which is what the threads about I think.

---

### Post by Elfy on 2013-12-27
> **vasa1 said:**
> ...

If both USC and Synaptic are considered "GUIs" for apt-get, then why is this feature not present? I use the CLI route and am regularly prompted about older kernels.

What prompt do you get? An autoremove one I assume. Then I'd assume the bug would be that USC is not showing people.

---

### Post by vasa1 on 2013-12-27
> **Elfy said:**
> What prompt do you get? An autoremove one I assume. Then I'd assume the bug would be that USC is not showing people.
Yes, it's the autoremove one.

---

### Post by Elfy on 2013-12-27
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1080661](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1080661) perhaps

---

### Post by vasa1 on 2013-12-27
> **Elfy said:**
> [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1080661](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1080661) perhaps
Close because it mentions the autoremove part but I think the report was more to do with the "incomplete" listing of dependencies to be removed when USC is employed. That's interesting by itself. I wonder if that was an isolated case.

---

### Post by Elfy on 2013-12-27
Maybe needs a new bug report then - couldn't find anything else.

---

### Post by monkeybrain20122 on 2013-12-27
You can configure yum to keep only the most recent n kernels and older ones will just be deleted when updated. Is there such a feature in apt-get or aptititude? By default fedora keeps only the most recent 2 or3 kernels and delete all the others, it is a nice feature that ubuntu could have so new users won't find themselves running out of space inexplicably.

---

### Post by malspa on 2013-12-27
I don't use a separate /boot partition, but I use Synaptic, and to keep my / partition from becoming too filled up, I manually remove all but the current kernel and the previous one.

> **vasa1 said:**
> I use the CLI route and am regularly prompted about older kernels.

Could you post what this looks like, sometime? I'm curious about what exactly you mean by "older kernels." Do you use **apt-get dist-upgrade**? 

> **cariboo907 said:**
> I don't use the Software Centre, but I know Synaptic lists old kernels under local or obsolete software. I would venture to guess that those that run into the problem of not enough space in /boot don't use, or have never heard of Synaptic.

How old do the kernels have to be before they show up under "Installed (local or obsolete)"?

> **monkeybrain20122 said:**
> You can configure yum to keep only the most recent n kernels and older ones will just be deleted when updated. Is there such a feature in apt-get or aptititude? By default fedora keeps only the most recent 2 or3 kernels and delete all the others, it is a nice feature that ubuntu could have so new users won't find themselves running out of space inexplicably.

The same thing (about Fedora and yum) came to mind here, too.

---

### Post by Elfy on 2013-12-27
> How old do the kernels have to be before they show up under "Installed (local or obsolete)"?As soon as a new one gets installed.

---

### Post by malspa on 2013-12-27
> **Elfy said:**
> As soon as a new one gets installed.

Hm. From Dec 6:

Installed the following packages:
linux-headers-3.2.0-57 (3.2.0-57.87)
linux-headers-3.2.0-57-generic-pae (3.2.0-57.87)
linux-image-3.2.0-57-generic-pae (3.2.0-57.87)

And I kept 3.2.0-56. But that one doesn't show up under "Installed (local or obsolete)" here, so I assumed that they have to be older than that.

---

### Post by vasa1 on 2013-12-27
> **malspa said:**
> ...
Could you post what this looks like, sometime? I'm curious about what exactly you mean by "older kernels." Do you use **apt-get dist-upgrade**? 
...I posted about that here: [http://ubuntuforums.org/showthread.php?t=2192955&p=12870988#post12870988](http://ubuntuforums.org/showthread.php?t=2192955&p=12870988#post12870988)
And I do use dist-upgrade instead of upgrade. Haven't broken anything as yet ;)

Although I would think that the apt-get autoremove reminder shouldn't depend on whether upgrade or dist-upgrade is used.

---

### Post by malspa on 2013-12-27
> **vasa1 said:**
> I posted about that here: [http://ubuntuforums.org/showthread.php?t=2192955&p=12870988#post12870988](http://ubuntuforums.org/showthread.php?t=2192955&p=12870988#post12870988)
And I do use dist-upgrade instead of upgrade. Haven't broken anything as yet ;)

Although I would think that the apt-get autoremove reminder shouldn't depend on whether upgrade or dist-upgrade is used.

Thanks, vasa1.

---

### Post by Irihapeti on 2013-12-27
I've noticed that old kernels show up as "local or obsolete" in Synaptic if I'm running a development release, but NOT if I'm using a released version such as 12.04

Aptitude will automatically remove old kernels when upgrading, but I don't recall if that's only for development releases.

---

### Post by Elfy on 2013-12-28
> **Irihapeti said:**
> I've noticed that old kernels show up as "local or obsolete" in Synaptic if I'm running a development release, but NOT if I'm using a released version such as 12.04...

That'llbe why I think it's standard behaviour then - other than for a couple of weeks and minor breakages I've only seen dev releases for years ...

---

### Post by vasa1 on 2013-12-28
Stupid question but I have to ask ... :(
What is a dev release? Is it any release which is not LTS? Or do you mean the alpha/beta releases of any version?

---

### Post by QIII on 2013-12-28
Development release -- i.e.: right now it's Trusty Tahr.

---

### Post by vasa1 on 2013-12-28
> **QIII said:**
> Development release -- i.e.: right now it's Trusty Tahr.
Okay, thanks!

---

