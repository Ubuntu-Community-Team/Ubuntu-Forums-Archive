---
title: "Why is APT/Debian so strict with dependencies?"
date: 2009-11-04
forum: The Cafe
---

### Post by hoppipolla on 2009-11-04
I often wondered about this. Is it even possible in a Debian-based  system to force a package to install with unmet dependencies? Or even just ONE unmet dependency?

I mean I'm not saying there's anything WRONG with this as such, but as the two other Linux distros I have used extensively (I have used others, but these two I used for years) were Suse and Slackware, these both used packaging systems that were more relaxed.

So what do we think about this? Is it good? Bad?

Oh and excuse my ignorance but what part of this system enforces this? Is it the packages themselves or the APT tool or... my knowledge tends to be quite good but little technicalities like this can slip me by!

Thanks guys!

Hoppi :)

---

### Post by Redache on 2009-11-04
I don't see why you'd even WANT to install an application that doesn't have all its dependencies met.

It's a good thing that they are strict as it means that there are no compatibility/dependency issues brought into the mix. 

I can't think of any Package Manager that ignores dependencies, because that would end up with soooo many issues, it's insane.

---

### Post by Skripka on 2009-11-04
> **Redache said:**
> I don't see why you'd even WANT to install an application that doesn't have all its dependencies met.

It's a good thing that they are strict as it means that there are no compatibility/dependency issues brought into the mix. 

I can't think of any Package Manager that ignores dependencies, because that would end up with soooo many issues, it's insane.

Some things are hard depends, others can be considered optional (under other package managers).  The way Apt handles them- you either depend on it or it is not installed- is rather annoying, to be honest.

---

### Post by FuturePilot on 2009-11-04
> **Skripka said:**
> Some things are hard depends, others can be considered optional (under other package managers).  The way Apt handles them- you either depend on it or it is not installed- is rather annoying, to be honest.

```
APT::Install-Recommends "0";
```
in /etc/apt/apt.conf will make it not install recommended packages.

---

### Post by lykwydchykyn on 2009-11-04
Theoretically, if it's truly and correctly marked as a dependency (and not a suggest or recommend), the software shouldn't function without it.

That said, the only tool I know of that will override these checks is dpkg.  dpkg has a number of switches that will force install a package even if it fails safety/dependency/security checks.  Use with caution!

There have been situations when upgrades went awry (from mixing packages from multiple releases and/or unofficial sources, usually) when I've had to force install packages, so it's handy to know the syntax.

Check out dpkg's manual page for more info.

---

### Post by praveesh on 2009-11-04
About a year ago , in OpenSUSE ,I installed virtualbox ose . But the package manager didn't install a recommended package named virtualbox kernel module (or something like that)  . The result was that no virtual machine was able to boot . Is it good or bad ?

---

### Post by ndefontenay on 2009-11-04
I started using linux with red hat 7.2 about 7 years ago.
it was a lot of fun just being different but at the same time I have to face the dependency hell.

A hell I will certainly not like to see again.

---

### Post by Skripka on 2009-11-04
> **praveesh said:**
> About a year ago , in OpenSUSE ,I installed virtualbox ose . But the package manager didn't install a recommended package named virtualbox kernel module (or something like that)  . The result was that no virtual machine was able to boot . Is it good or bad ?

Has Ubuntu gotten around to making it so you can uninstall that annoying default email client without killing Ubuntu yet?

I ask because:
a) I do not know, and haven't heard anything about it since 9.10 came out

and

b) It is an example of goofy depends handling by Apt being annoying.

---

### Post by earthpigg on 2009-11-04
if you think a depen is incorrectly listed, you can unpack the .deb, remove it from the control file, repack it, and install.

i usually test this in a VM first.

---

### Post by phrostbyte on 2009-11-04
They are called dependencies for a reason. :)

Now Ubuntu by default also installs *recommends* packages, which unlike deps are NOT needed. I this find silly. 

Like Wine recommends Winbind. Winbind is a service (started by init at start-up) that 99.9% of home users will never need. Waste of RAM imo.

---

### Post by NCLI on 2009-11-04
> **phrostbyte said:**
> They are called dependencies for a reason. :)

Now Ubuntu by default also installs *recommends* packages, which unlike deps are NOT needed. I this find silly. 

Like Wine recommends Winbind. Winbind is a service (started by init at start-up) that 99.9% of home users will never need. Waste of RAM imo.

Out of personal interest: What does it actually do? I've always wondered about that.

---

### Post by FuturePilot on 2009-11-04
> **NCLI said:**
> Out of personal interest: What does it actually do? I've always wondered about that.

> This package provides winbindd, a daemon which integrates authentication
 and directory service (user/group lookup) mechanisms from a Windows
 domain on a Linux system.  User/group lookups are configured via
 /etc/nsswitch.conf, and authentication is integrated using the winbind
 module for PAM.
.

---

### Post by ad_267 on 2009-11-04
```
apt-get install --no-install-recommends package_name
```

I find that usually the recommended packages are actually a good idea to install though, so I agree with them being installed by default.

---

### Post by phrostbyte on 2009-11-04
> **NCLI said:**
> Out of personal interest: What does it actually do? I've always wondered about that.

It's for authenticating against a server running Microsoft's proprietary LDAP software, and for using services available on that authenticated network (eg: fileshares). 

Useful in businesses, eg, when you have to "log in to the network" to use your computer. This allows Linux machines to likewise login to the network, using the same credentials.

There is another tool that makes this setup easier then Winbind interestingly called [likewise]("apt:likewise-open"). :)

To be honest I have no idea what use Wine would have for Winbind.

---

### Post by praveesh on 2009-11-05
> **Skripka said:**
> Has Ubuntu gotten around to making it so you can uninstall that annoying default email client without killing Ubuntu yet?

.

What do you mean ? IF you are talking about the removal of Ubuntu-desktop , it's not a problem . That package does nothing . It just depends on other packages so that if you install it , the other packages will also be installed automatically . Removing Ubuntu-desktop won't do any harm to your setup

---

### Post by earthpigg on 2009-11-05
> **praveesh said:**
> What do you mean ? IF you are talking about the removal of Ubuntu-desktop , it's not a problem . That package does nothing . It just depends on other packages so that if you install it , the other packages will also be installed automatically . Removing Ubuntu-desktop won't do any harm to your setup

however, do ***not*** remove that package then play with the semi-broken 'janitor' app or 'apt-get autoremove' without looking very closely at what you are removing.

if you want to be super 'correct' about things....

unpack the ubuntu-desktop .deb file, modify the 'control' file to not list what you want to remove as a depend, rename it 'earthpigg-desktop' or whatever you want, repackage it and install it. ***then*** go ahead and autoremove/janitor/whatever.

---

### Post by koenn on 2009-11-05
> **Skripka said:**
> Has Ubuntu gotten around to making it so you can uninstall that annoying default email client without killing Ubuntu yet?

I ask because:
a) I do not know, and haven't heard anything about it since 9.10 came out


I've been doing that since 6.06 without any problem.
Although since the introduction of 'autoremove', earthpigg has a point there.


> **Skripka said:**
> 
and

b) It is an example of goofy depends handling by Apt being annoying.

No, it's an example of Ubuntu (mis-)using one specific function of apt.

They used to have ubuntu-desktop Depend on all packages, then changed that to Recommends but apt changed along and installs Recommends by default, then auto-remove came into play so you risk unintended uninstalls ...
They probably should have managed this through Tasks (-> tasksel) or through dpkg (eg set-selections)

---

### Post by koenn on 2009-11-05
> **hoppipolla said:**
> 
Oh and excuse my ignorance but what part of this system enforces this? Is it the packages themselves or the APT tool or...

essentially, the system provides mechanism, the human makes policy. It's a Unix thing. 
In this case, the control is in the control file, a text file in side the .deb that lists version, dependencies, recommends, short and long description (i.e the descriptions you get in synaptic), ...
This file is written by the maintainer/packager so he decides what apt will do. apt just processes the information the maintainer feeds it.

---

### Post by Hallvor on 2009-11-05
*deleted*

---

### Post by hoppipolla on 2009-11-05
hmm, I'm glad there are ways to do this! I guess giving it more direct flexibility like RPMs brings it's own problems. I mean I usually hear that RPM based systems often have dependency problems (or is that just openSUSE? lol).

But yeah, I'll be leaving it on for now too! Good to hear that are ways to ignore the recommended ones though, it can make things easier sometimes! :)

---

