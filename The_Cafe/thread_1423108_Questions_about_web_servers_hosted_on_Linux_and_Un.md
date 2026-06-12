---
title: "Questions about web servers hosted on Linux and Unix"
date: 2010-03-06
forum: The Cafe
---

### Post by blueshiftoverwatch on 2010-03-06
Why is it that it seems like the overwhelming majority of Unix-like web servers are hosted on RedHat, Suse, Fedora, or CentOS and it's very rare to hear of a distro being hosted on Debian or a Debian based distro like Ubuntu. Out of all of those, while Suse does use RPM it's the only one that's not based on RedHat. Does this have something to do with RedHat based distros being generally more stable, with the RPM package format, or something unrelated? If they're after stability, it doesn't get much more stable than Debian.

When a company that develops Linux (like RedHat or Novell) says "we provide good support", what exactly does that mean? Generally anything you want to know about an open source project can be found for free online. If your too paranoid to trust a howto guide that some anonymous person posted on their blog, I'm sure you could find the same information in a book. Or is it because if they want to know how to do something they want to be able to get ahold of a professional paid service representative through email or the phone right_now and not have to dig around help websites or leave work to run to a book store to get the latest edition of whatever book is relevant to their problem?

Even if RedHat or Novell released something as open source, within a short period of time it would make it's way into a free alternative like CentOS, Fedora, or OpenSuse. So, why do people host their web servers on commercial distros like RedHat or SLES? Is it because they want the new stuff (like security patches) as soon as they're available and don't want to wait around for them to be implemented into the free versions?

Also, what about the various BSD's? You rarely hear anything about them despite that they're supposed to be even more stable and secure than Linux, for example OpenBSD.

Which also makes me wonder why Canonical is focusing so much on providing good server support when people who want to run a server on a non-RPM based distro are probably just going to use Debian instead because of it's stability. Ubuntu might be easier to use but I doubt that hardened network admins are going to care about it's ease of use. They're probably tech savvy enough that they could setup, configure, and use a Gentoo, Slackware, or Arch system without the GUI and have no problems.

---

### Post by dragos240 on 2010-03-06
Many servers run on debian, it's very convenient. It's not that BSDs' are more secure, it's just that the port system is useful to sysadmins.

---

### Post by blueshiftoverwatch on 2010-03-06
> **dragos240 said:**
> Many servers run on debian, it's very convenient
This might not be the best example to use for reasons that should be obvious. But almost every time I go to a website that is down it'll say in the lower right hand corner that it's running Apache on CentOS. Occasionally it will say RedHat or Fedora. I can't recall ever seeing Debian. For that matter, I rarely if ever see Windows/IIS either.
> **dragos240 said:**
> It's not that BSDs' are more secure, it's just that the port system is useful to sysadmins.
I've heard it's very good and comprehensive. But if that's one of the reasons and they want to use Linux instead of Unix. Why use RedHat or Fedora at all instead of Debian? RPM distros tend to have smaller repositories for some reason. Or does the fact that with RPM apps like Yum you can choose to ignore dependencies that it asks to install have a certain appeal?

---

### Post by blueshiftoverwatch on 2010-03-26
Also, what is the point of Mac OSX Server? Your basically paying for Unix (with a shiny GUI) when you can get Linux or BSD for free.

---

### Post by lykwydchykyn on 2010-03-26
> **blueshiftoverwatch said:**
> But almost every time I go to a website that is down it'll say in the lower right hand corner that it's running Apache on CentOS. Occasionally it will say RedHat or Fedora. I can't recall ever seeing Debian. 

That's because debian servers never go down :D

ok, not really.

---

### Post by lisati on 2010-03-26
> **lykwydchykyn said:**
> That's because debian servers never go down :D

ok, not really.

The default setup is fairly robust: about the only time mine is down is when I've had to take it down because I've been tinkering with something and borked one or more of the settings. Even then, I have a backup machine to use (also running Ubuntu) so that my web presence doesn't vanish completely for too long if the repairs take more than a few minutes.

---

### Post by HermanAB on 2010-03-26
One very, very, big reason - probably the biggest reason for server farm operators, is RedHat Kickstart and the trivial ease of setting up your own installation and update server.

Another reason is government security requirements that are only addressed by the RedHat type systems.

---

### Post by blueshiftoverwatch on 2010-04-04
> **HermanAB said:**
> Another reason is government security requirements that are only addressed by the RedHat type systems.
You mean SELinux?

---

### Post by juancarlospaco on 2010-04-04
Red Hat sucks, download CentOS and try it yourself, 
but the support brains make the difference...

---

### Post by MaxIBoy on 2010-04-04
> **blueshiftoverwatch said:**
> You mean SELinux?[s]Yeah, pretty much. In order to get SELinux on Ubuntu, you need to recompile the kernel, which is not supported (so paid support will not help you with it.)[/s] (So much for knowing what I'm talking about.)

The reason Ubuntu is preferred for professional server setups instead of Debian is that Ubuntu is sponsored by an actual company. (I think it's irrational, but there you go.) But Ubuntu isn't necessarily less stable than Debian. If you give them a few months to stabilize, the LTS releases are completely solid.

---

### Post by NCLI on 2010-04-04
> **MaxIBoy said:**
> Yeah, pretty much. In order to get SELinux on Ubuntu, you need to recompile the kernel, which is not supported (so paid support will not help you with it.)

Uh, no. [That is simply not true]("https://wiki.ubuntu.com/SELinux").

[Click here to install SELinux]("apt:selinux"). It's in the repos, it's a one click procedure, and [it's supported]("https://wiki.ubuntu.com/HardyHeron/RC#SELinux%20Support").

---

### Post by MaxIBoy on 2010-04-04
> **NCLI said:**
> Uh, no. [That is simply not true]("https://wiki.ubuntu.com/SELinux").

[Click here to install SELinux]("apt:selinux"). It's in the repos, it's a one click procedure, and [it's supported]("https://wiki.ubuntu.com/HardyHeron/RC#SELinux%20Support").Fixed, thanks.

---

### Post by koenn on 2010-04-04
it's probably a combination of several factors. Corporate support and SLA's is probably a big one. Tradition another (Redhat was the first to do this type of thing, and if it's good, why change ?). Then there's ISVs like Oracle and such who certify their products on Redhat e.a. but not on Debian etc. Then there's formal training/certification programs for staff.  

Redhat, Suse, ... have this. Debian doesn't. You can think you'll get away with google, community forums, your own troubleshooting skills and a bit of luck, but do you want to bet your job or your business on it ?

And now there's Canonical who wants to put ubuntu there as well, but they're still new, and, as I said before, if you've been running Redhat for a decade without trouble, why change ?

---

### Post by Luke has no name on 2010-04-04
> **koenn said:**
> 

...

And now there's Canonical who wants to put ubuntu there as well, but they're still new, and, as I said before, if you've been running Redhat for a decade without trouble, why change ?

This. From my observation, it seems what Ubuntu Server is trying to do is differentiate themselves not on service (I'm sure it's good), but on cloud services and ease of setup. UServer wants to be the go-to operating system for creating your own cloud, and while I haven't tested personally, I've heard good things.

---

### Post by kaldor on 2010-04-04
In gaming, my clan has 3 servers. One hosted on CentOS and the other 2 on Ubuntu.

Another person I know hosts his website on Debian.

Another person I know used to run game servers on FreeBSD; he'd use the Linux version of the dedicated server files and make it work under BSD. 

I personally use Ubuntu Server; I don't need to fiddle with it at all. Pop in the disc, install, and do whatever. No true setup and tweaks needed for me.

---

