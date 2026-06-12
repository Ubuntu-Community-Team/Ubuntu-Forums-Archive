---
title: "get a list of pending security updates"
date: 2007-11-11
forum: Server Platforms
---

### Post by niobos on 2007-11-11
Hi,

I'm fairly new to Ubuntu, but I have experience with other distros (Gentoo). I'm setting up a server with Ubuntu (console only, no X).
Of course, I'd like to keep the software up-to-date, especially the security fixes.

If I understand [this post]("http://ubuntuforums.org/showthread.php?t=28729") correctly, I'll only get security updates. The only way to get non-security updates is to change the sources.list to include a new feisty/gusty/... line.
Is this correct?

What I'd like to get is a daily mail from my server containing a list of pending security updates. This mail should list the packages, current version, new version, and changelog between them.

I know how to do the mail-part. I only need some apt-tools command to get a list of pending updates.
I found [this wiki]("https://help.ubuntu.com/community/AutomaticSecurityUpdates") which looks a bit like it. But instead of updating automatically, I'd like to receive a list of packages+versions

So in short: how do I get a list of pending updates with the following info: package name, current version, new version (and preferably changlog between these, but I can do this myself).

Don't worry about the format things are in. I'm fairly good with perl/sed/... to change that to the format I like.

---

### Post by MJN on 2007-11-11
> **niobos said:**
> If I understand [this post]("http://ubuntuforums.org/showthread.php?t=28729") correctly, I'll only get security updates. The only way to get non-security updates is to change the sources.list to include a new feisty/gusty/... line.
Is this correct?

No! You are correct in thinking that you will only get security updates (and major major bug fixes for critical packages, but I'm talking about those that threaten the stability of the distribution) however that's it. If you want newer versions you need to either i) upgrade your entire distribution to a newer release, ii) grab newer versions (if available) from the backports repository, iii) grab newer versions from other unofficial repositories, or iv) compile newer versions yourself from source. You can't cherry pick packages simply by changing the release in your repository sources.list as you'll end up with a right mess of conflicting dependencies.

> What I'd like to get is a daily mail from my server containing a list of pending security updates. This mail should list the packages, current version, new version, and changelog between them.Running **apt-show-versions -u** will give you a list of upgradable packages (see the man page for other options such as -a to give version info). I don't know about getting the changelog as such info is part of the package and hence would need to be downloaded and unpacked first. No doubt there is a tool available to do this (perhaps by alternatives means such as scraping the Ubuntu packages site).

Mathew

---

### Post by niobos on 2007-11-11
> **MJN said:**
> No! You are correct in thinking that you will only get security updates (and major major bug fixes for critical packages, but I'm talking about those that threaten the stability of the distribution) however that's it. If you want newer versions you need to either i) upgrade your entire distribution to a newer release, ii) grab newer versions (if available) from the backports repository, iii) grab newer versions from other unofficial repositories, or iv) compile newer versions yourself from source. You can't cherry pick packages simply by changing the release in your repository sources.list as you'll end up with a right mess of conflicting dependencies.
Well, that's what I meant, although I agree that my phrasing was confusing.
> **MJN said:**
> Running **apt-show-versions -u** will give you a list of upgradable packages (see the man page for other options such as -a to give version info). I don't know about getting the changelog as such info is part of the package and hence would need to be downloaded and unpacked first. No doubt there is a tool available to do this (perhaps by alternatives means such as scraping the Ubuntu packages site).
This is exactly what I was looking for! thank you!

---

