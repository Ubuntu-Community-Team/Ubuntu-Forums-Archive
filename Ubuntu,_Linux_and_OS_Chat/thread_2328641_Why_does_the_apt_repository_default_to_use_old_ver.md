---
title: "Why does the apt repository default to use old version packages?"
date: 2016-06-23
forum: Ubuntu, Linux and OS Chat
---

### Post by DaviesX on 2016-06-23
I don't know why is it so conservative. My ubuntu OS is upgraded to the latest 16.04. It seems to me that the default package is sometimes 1 to 2 years lagged behind the latest version. I can't come up all the examples right now. I was just trying install some JavaScript packages through npm, and it failed because the npm and nodejs package was too outdated. Therefore, I have to add the nodejs' PPA to get the latest version. There were a lot of times that this happened. Now I can't resist to ask why it wouldn't add the newer packages to the main repository? Oh right, the Eclipse package is from 2012. And it's 2016... It bothers me when I have to look up the PPA source. Or sometimes even worse, I might have to compile the package from source, and this is time consuming.

---

### Post by buzzingrobot on 2016-06-23
It's "conservative" because it's an LTS release. It's intended to be stable for an extended period of time, where "stable" means the release version of components is not expected to be upgraded. (This also increases the other kind of stability:  fewer bugs. I.e., existing bugs can be discovered and patched, while introducing new packages means introducing new code that increases the chances for new bugs.)

In some cases, newer packages cannot be added without also changing core components of the system, changes which might break installations. 

Staying on the current Ubuntu release, whether it is an LTS or not, will give you access to the newest packages in the official repos, with the cost of upgrading every 6 months.  

This kind of thing affects every distribution that releases on a fixed schedule.  Regardless of the interval between releases, there are always going to be new packages that the current release cannot support.

---

### Post by ian-weisser on 2016-06-23
Teams of volunteer Debian and Ubuntu packagers update those repositories.
They welcome your participation.

---

### Post by vasa1 on 2016-06-23
It's possible a rolling-release distro maybe more to your liking. See [http://unix.stackexchange.com/questions/740/what-distributions-have-rolling-releases](http://unix.stackexchange.com/questions/740/what-distributions-have-rolling-releases)

---

### Post by Linuxisfast on 2016-06-23
Ubuntu's best feature is stability and if these packages are old for you, wait till you see Debian or Red Hat packages. However Ubuntu updates kernels to new one every point release and for those looking for latest there is always ubiquitous ppa and mostly written by developers or Canonical members so they are all safe. This way your package stays current while the rest of the system stays stable and secure.

---

### Post by kansasnoob on 2016-06-23
> **ian-weisser said:**
> Teams of volunteer Debian and Ubuntu packagers update those repositories.
They welcome your participation.

+1!

That's the correct answer. It all depends on who the maintainer is of a package or sub-set of packages. I sometimes find myself frustrated in both directions, that is sometimes I wish a certain package were updated to a later version but other times I wish they'd have stuck with a more stable, albeit outdated, package.

---

### Post by mikodo on 2016-06-23
+1 to the other replies. Therein lies the answers.

The [Snappy Ubuntu Core]("https://developer.ubuntu.com/en/snappy/") and [Snapcraft]("https://github.com/ubuntu-core/snapcraft") with Snap Packaging are going to change the landscape. [Here is one explanation]("http://www.omgubuntu.co.uk/2016/04/ubuntu-16-04-lts-snap-packages") of what is coming for Ubuntu devs, Application devs, Maintainers and Users.

---

### Post by grahammechanical on 2016-06-24
In the past Linux users knew that Linux was under constant development and that it had a long way to go. They expected problems (bugs) and accepted the fact of the existence of bugs and looked forward to getting newer versions of libraries that may be fixed the bugs.

Today, many people use Linux and they do not expect bugs. They do not see themselves as some kind of tester. So, Linux distributors, like Canonical, are in no hurry to push out the latest upgrades to libraries. And so, with Ubuntu, at present, we have a 26 weekly release cycle. And the aim is always stability.

It is boring. But people can use a boring distribution to do useful work.

Regards.

---

### Post by nobahdi-atoll on 2016-07-03
> **grahammechanical said:**
> In the past Linux users knew that Linux was under constant development and that it had a long way to go. They expected problems (bugs) and accepted the fact of the existence of bugs and looked forward to getting newer versions of libraries that may be fixed the bugs.

Today, many people use Linux and they do not expect bugs. They do not see themselves as some kind of tester. So, Linux distributors, like Canonical, are in no hurry to push out the latest upgrades to libraries. And so, with Ubuntu, at present, we have a 26 weekly release cycle. And the aim is always stability.

It is boring. But people can use a boring distribution to do useful work.

Regards.


All this is true, but its part of what makes Linux a niche operating system, and not a goto OS for general users. 

For instance, I find i have to keep 2-3 versions of ubuntu on my system. to support all the apps i need because, going forward to support apps i want breaks the apps that used to already use. 
A good example: I installed MediaElch ([http://www.kvibes.de/mediaelch/](http://www.kvibes.de/mediaelch/)) in trusty... unfortunately the latest version available for trusy is 2.2.21 which is not as good as the latest release (2.4.2) and even broken functionality in some places (the functionality i really need) attempting to install the new version was a disaster because it needed the latest libraries from the latest kde (libqt5core5a >= 5.4.0). So I upgraded to ubuntu 16.04 and lost the ability to convert audio to aac(m4a) in SoundConverter because 16.04 no longer has the gstreamer0.10-plugins-bad-multiverse package. I know there are several ways to convert my audio as i want. But SoundConverter is an easy way to batch convert and Its my choice of apps to use.That wasn't the only broken app that i found moving forward, just an example. In any case I had to re-install 14.04 on a seperate partition while keeping 16.04 for more updated apps. The only concession is that Linux can use the same /home partition across distros (though i think this is only safe because I'm using different versions of the same distro).

Anyway I think that Linux is too modular for most users, myself included. But since the alternative is using Windows, I'm trying to be patient with the process. Plus i kinda like tinkering with my system. But before Linux could possibly be an alternative for general users, some kind of stability needs to be achieved. Too many broken apps between upgrades. Too many unsupported apps from version to version because of dependencies. Too much overall frustration to make general users comfortable. Modular is good for the kernel, but apps dependency being as modular as it is makes linux painfully frustrating for most.

---

