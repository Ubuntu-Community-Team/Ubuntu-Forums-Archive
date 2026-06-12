---
title: "Old Firefox Concerns"
date: 2011-01-16
forum: Security
---

### Post by webster922 on 2011-01-16
You wouldn't willingly use Firefox 3.0.6 on Windows or OS X, but what if you had no other option on your Linux distro? Would it be safe to log in to sites like Gmail and Facebook?

I am just wondering as I am referring to an old PPC iMac (G4). Firefox 3.0.6 (really Iceweasel) is my only option. Thank you for your time.

---

### Post by snowpine on 2011-01-16
It sounds like you might be using Debian (Ubuntu does not use Iceweasel), so have you tried asking this question on the [Debian Forums]("http://forums.debian.net")?

Also, you can always get the latest Firefox [from the Mozilla website]("http://mozilla.com"). You are not stuck with the default version your distro provides.

---

### Post by webster922 on 2011-01-16
Yes, I am using Debian 5, mainly because the iMac has only 256 MB RAM and an 800 MHz processor. Debian 5 (Xfce) works fairly well for such an old computer.

Really all I want to know is if using outdated browsers is dangerous...

(Yes, I could upgrade to the official Firefox, but being the resource hog that it is I'm worried that it wouldn't be as functional on a computer with only 256 MB RAM. Think it's worth a try?)

---

### Post by CharlesA on 2011-01-16
Using an out-of-date browser can be a security risk. You can try running something like noscript, but that will only go so far.

---

### Post by snowpine on 2011-01-16
[packages.debian.org]("http://packages.debian.org/changelogs/pool/main/i/iceweasel/iceweasel_3.0.6-3/changelog") suggests Iceweasel 3.0.x has not had any security patches since Sept. 2009.

However it appears you can get 3.5.x from [backports]("http://packages.debian.org/lenny-backports/iceweasel"). That would be my suggestion (if you are uncomfortable simply grabbing the latest from the Mozilla website).

---

### Post by snowpine on 2011-01-16
[packages.debian.org]("http://packages.debian.org/changelogs/pool/main/i/iceweasel/iceweasel_3.0.6-3/changelog") suggests Iceweasel 3.0.x has not had any security patches since Sept. 2009.

However it appears you can get 3.5.x from [backports]("http://packages.debian.org/lenny-backports/iceweasel"). That would be my suggestion (if you are uncomfortable simply grabbing the latest from the Mozilla website).

I would also encourage you to ask on the Debian forums as I suspect this is a very frequently-asked question over there. :)

---

### Post by webster922 on 2011-01-16
Uh-oh. I tried to dpkg the newer version of Iceweasel and there was an error. Now there is no web browser on my Debian machine (whenever I try to launch the web browser it says "Failed to execute default Web Browser: Input/Output error"). :P

I'll try to see what I can find out on the Debian Forums and update this later. Thanks for the help so far snowpine and CharlesA.

---

### Post by snowpine on 2011-01-16
> **webster922 said:**
> Uh-oh. I tried to dpkg the newer version of Iceweasel and there was an error. Now there is no web browser on my Debian machine (whenever I try to launch the web browser it says "Failed to execute default Web Browser: Input/Output error"). :P

I'll try to see what I can find out on the Debian Forums and update this later. Thanks for the help so far snowpine and CharlesA.

You might find these instructions helpful for installing a package from Backports:

[http://backports.debian.org/Instructions/](http://backports.debian.org/Instructions/)

---

### Post by webster922 on 2011-01-16
Thanks again for all of the help snowpine. I once again have a functioning browser on this Debian machine.

If anyone ever needs to refer to this thread in the future, I also have asked about upgrading Iceweasel here: [http://forums.debian.net/viewtopic.php?f=10&t=59300]("http://forums.debian.net/viewtopic.php?f=10&t=59300")

Hopefully I'll have this sorted out soon.

---

### Post by lovinglinux on 2011-01-16
> **webster922 said:**
> Yes, I am using Debian 5, mainly because the iMac has only 256 MB RAM and an 800 MHz processor. Debian 5 (Xfce) works fairly well for such an old computer.

Really all I want to know is if using outdated browsers is dangerous...

(Yes, I could upgrade to the official Firefox, but being the resource hog that it is I'm worried that it wouldn't be as functional on a computer with only 256 MB RAM. Think it's worth a try?)

I recommend downloading Firefox 4 from Mozilla. It is 3 times faster than Firefox 3.

---

### Post by webster922 on 2011-01-16
Hey lovinglinux, I'm pretty sure Mozilla dropped support in Firefox 4 for the PPC. You must have missed that I'm using a 9 year old computer. :P

---

### Post by lovinglinux on 2011-01-16
> **webster922 said:**
> Hey lovinglinux, I'm pretty sure Mozilla dropped support in Firefox 4 for the PPC. You must have missed that I'm using a 9 year old computer. :P

Yes, I missed that. Sorry. :oops:

---

### Post by webster922 on 2011-01-17
Everyting is sorted out for now. Running Firefox 3.5.16! Surprisingly there are no security benefits by using 3.5.16 over 3.0.6 in Debian though. See my thread at [http://forums.debian.net/viewtopic.php?f=10&t=59300](http://forums.debian.net/viewtopic.php?f=10&t=59300).

Eck explained it to me like this:

> Debian separates the packages so that they may provide continual security updates for the stable version of Iceweasel. That's why stuff like xulrunner are installed as separate packages instead of the one big package that mozilla provides.

Mozilla hates this, and is one of the reasons we have Iceweasel rather than Firefox. They wanted to approve every security and bug fix update, etc, etc, lots of reading available on the reasons.

So you're not a bit less secure using the version in the stable, testing, unstable, or experimental repos, as the security parts are either in the separate Debian packages or released by the security team as point updates for the repo's version.So the security updates are provided by other packages. That's good to know. Thanks again for all of the help here!

---

### Post by movieman on 2011-01-18
Another thing to consider is that any exploit is likely to only attack x86 machines unless it's using Javascript, Java or some other common language that you can mitigate by disabling Java and using Noscript or another Javascript-blocker. I'd be very surprised if any web site in the world was sending out an exploit tailored for old Firefox versions running on PowerPC.

---

