---
title: "Sometimes Ubuntu Boggles My Mind"
date: 2007-04-21
forum: Testimonials &amp; Experiences
---

### Post by marcele on 2007-04-21
Just went to install Feisty..

Installer loads then BOOM ... popped into command prompt with this error:
/bin/sh: can't access tty; job control turned off

Now I've been a unix sys admin for a while now so I know I can fix it (or at least download the alternate cd as that will work) ...

But come on guys ? Ever heard of QA? Does this distro ever get tested before hand? .. This is the second time an Ubuntu release installer has crashed on me (Dapper did also with another machine with a separate installer bug) ..

With stuff like this you guys are HURTING THE LINUX NAME!! How in the world is a newbie supposed to fix something like this?

Update: downloaded the alternate CD and tried to install 

Installer loads then BOOM.. popped up with this error.
No common CD-ROM drive detected 

LOL well it loaded most of the installer off the cd .. so the drive should be detected ... swapped cd-roms and same error.

What a JOKE... both installers borked ... unbelievable!...SHAME ON YOU UBUNTU DEVS Let's launch a new release with a non working kernel!

---

### Post by 3rdalbum on 2007-04-22
Doesn't it feel good to blame somebody for not having the exact same hardware as you?

---

### Post by aysiu on 2007-04-22
It's weird.

There seem to be three bug reports on this.

One is importance "high," another importance "medium, and the third importance "undecided."
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89380](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89380)
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084)
[https://bugs.launchpad.net/ubuntu/+bug/75135](https://bugs.launchpad.net/ubuntu/+bug/75135)

It does seem a common enough problem that they should have fixed it, but it wasn't common enough to have swept the boards. This is the first I've heard of it, and I'm on the forums all the time.

---

### Post by kevinlyfellow on 2007-04-22
The devs don't really owe you anything.  Instead of submitting a caustic post about how terrible your installation went, file a bug report and help everyone out.  [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by aysiu on 2007-04-22
> **kevinlyfellow said:**
> The devs don't really owe you anything.  Instead of submitting a caustic post about how terrible your installation went, file a bug report and help everyone out.  [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
While I admit that this thread doesn't have any practically useful purpose, there are already three bug reports on this issue. Submitting another one probably won't get it fixed any more quickly.

---

### Post by kevinlyfellow on 2007-04-22
> **aysiu said:**
> While I admit that this thread doesn't have any practically useful purpose, there are already three bug reports on this issue. Submitting another one probably won't get it fixed any more quickly.

I agree, I just never heard of the problem and we posted at the same time, so I didn't get any of your wisdom before I posted :-)... But still, I really don't like how people will accuse the devs of being terrible just because they can't get it to work with their hardware.  People come and get the software for free and instead of being respectful when things don't go right, they just accuse them of being incompetent.  The devs work hard, and deserve a lot of respect and gratitude even if things don't work out.

---

### Post by aysiu on 2007-04-22
Well, the developers do what they can.

The best ways to help are filing bug reports, contributing code, donating money, and creating documentation. We have only the resources we have. We do only what we can. If Ubuntu had to be perfect in all situations before it could be released, it would be Debian, and it wouldn't have a six-month release cycle.

---

