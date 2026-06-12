---
title: "Extending a Timeline of a Linux Distro"
date: 2011-12-19
forum: The Cafe
---

### Post by GreenDance on 2011-12-19
Hi, I was wondering (I'm learning), is it possible to take a distro that has a short shelf life, for example Fedora, it has a 13 month timeline before another release is on the shelf, and extend it past 13 months, say for example to 24/36 months?

This question applies to all distro's available.

I was just wondering, Thank You. :)

---

### Post by grahammechanical on 2011-12-19
What are you talking about? A computer is a machine. The operating system and the programs/applications on the computer are just computer code. They do not stop working after a certain date.

What stops in the case of Ubuntu is support for security fixes. I have Ubuntu disks for 2007, 2008, 2009. The OS will still install and work. I would not be able to get any security updates for those releases because support has stopped. But if my machine is still working then the code will still work. It does not date expire in the sense of no longer working.

Regards.

---

### Post by BrokenKingpin on 2011-12-19
What do you mean by shelf life... the time between the next release, or the time a release is supported.

If you want a long term support release, you could always use the Ubuntu LTS, which is supported for 5 years.

---

### Post by Dragonbite on 2011-12-19
While security updates will no longer be shipped after the distro versions EOL, it will still work beyond that time which may work find depending on how you use it.

For openSUSE, look at Evergreen, which is a project to extend an older version of openSUSE (11.?).  Also they have Tumbleweed which makes openSUSE into a rolling-release of some sort though it is still fairly new (or in other words has kinks to work out)

---

### Post by 3Miro on 2011-12-19
The only way is to take all the packages in the repository and keep updating them with security updates, then host them on a gigantic server somewhere.

This can be done by a large community of people, it is not a one-man project.

The other way is to use an OS without the updates and without the ability to install software from the Internet. This may work for you, depending on what you are doing.

---

### Post by GreenDance on 2011-12-20
Hi, sorry for not being more specific with my question before, what I was talking about is the updates, if someone took a distro that is no longer supported, could a community continue to build updates for it?

---

### Post by Erik1984 on 2011-12-20
In theory one could do that :P However it makes little sense as there already are up to date repositories, you just need to upgrade your OS to use them.

The repositories for old Ubuntu versions are still online by the way (to install software from with apt-get) however you won't receive any updates from after the date support was stopped. You do receive 'updates' from up till that moment. For example: You can install Gutsy Gibbon (7.10), add the old-releases repository, install software and receive all updates for your installed software published during Gutsy's lifetime.

---

### Post by BrokenKingpin on 2011-12-20
> **GreenDance said:**
> Hi, sorry for not being more specific with my question before, what I was talking about is the updates, if someone took a distro that is no longer supported, could a community continue to build updates for it?
Why would you want to though, as already stated there are releases supported up to 5 years, at that point just do a dist upgrade or install the latest version. The communities time is better spent on currently supported releases.

---

### Post by GreenDance on 2011-12-20
> **BrokenKingpin said:**
> Why would you want to though, as already stated there are releases supported up to 5 years, at that point just do a dist upgrade or install the latest version. The communities time is better spent on currently supported releases.

Hi, I was just wondering if it "could be done", that's all, :KS

---

### Post by snowpine on 2011-12-20
You could theoretically set up a repository with updated packages for, say, Fedora 13. However, Fedora 13 users would not see these updates unless they manually change to your repository.

You would have to convince the user base that your updates are a) trustworthy and b) superior in some way to the updates provided by Red Hat (Fedora 14, 15, 16).

For example Fedora 13 uses Firefox 3.6; what are the advantages of choosing Fedora 13 with security-patched-by-GreenDance Firefox 3.6 instead of the latest Fedora with the latest Firefox?

---

### Post by GreenDance on 2011-12-20
> **snowpine said:**
> You could theoretically set up a repository with updated packages for, say, Fedora 13. However, Fedora 13 users would not see these updates unless they manually change to your repository.

You would have to convince the user base that your updates are a) trustworthy and b) superior in some way to the updates provided by Red Hat (Fedora 14, 15, 16).

For example Fedora 13 uses Firefox 3.6; what are the advantages of choosing Fedora 13 with security-patched-by-GreenDance Firefox 3.6 instead of the latest Fedora with the latest Firefox?
Hi, I didn't say I was going to "do it", I was simply wondering if "it could be done".

---

### Post by snowpine on 2011-12-20
> **GreenDance said:**
> Hi, I didn't say I was going to "do it", I was simply wondering if "it could be done".

Do you feel we have adequately answered your question, or is there more you'd like to know?

---

### Post by GreenDance on 2011-12-20
> **snowpine said:**
> Do you feel we have adequately answered your question

Yes, Thank You.

---

### Post by snowpine on 2011-12-20
Now, sometimes, new distros get started because users aren't happy with the release/support schedule of their favorite distro.

For example one of the reasons Ubuntu got started was that some Debian users felt the releases were too far apart (2 years) and wanted a 6 month release cycle.

In that case however it is "starting a new distro based on another distro" rather than "extending the timeline of an existing distro."

---

### Post by Dragonbite on 2011-12-20
> **GreenDance said:**
> Hi, I didn't say I was going to "do it", I was simply wondering if "it could be done".

My first reaction is "Of course it can be done". At least for a limited time.

Eventually versions will change so much they can't be backwards compatible.

If you are always rolling up to the newer version (even if it is a couple of version behind the others) you may be better off just looking for a rolling release because that's effectively what you are creating.

Unfortunately things like Gnome3 happen, where in order to keep Gnome2 you have to do a LOT of work that is not really reasonable.  If Mate takes off, then you can have the equivalent of holding on to Gnome2 but not all applications work out so nicely.

---

### Post by ssam on 2011-12-21
You may have to worry about trademarks. For example Canonical may not be happy if you made your security updates look like they were official.

I am sure if a group of people approached Canonical or Fedora or who ever, and said "we want to put in the effort required to extent the support life of your distro" they might be interested. You might want to make a name for yourself first by helping out with the stable release updates, [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

### Post by snowpine on 2011-12-21
I think Canonical is going to extend support for 10.04 desktop through April 2015, make it 5 years just like 12.04, just a hunch. :)

---

