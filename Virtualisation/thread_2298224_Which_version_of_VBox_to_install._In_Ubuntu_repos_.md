---
title: "Which version of VBox to install. In Ubuntu repos or the Vbox website?"
date: 2015-10-09
forum: Virtualisation
---

### Post by mikodo on 2015-10-09
Hi,

I haven't used VBox or any other virtualization for ~4 years. I'm on 14.04 and use the Amd64-bit install. When I used to use VBox, I used the one from its' site, rather than the version in Ubuntu repos for the release I was using. Now, I am thinking of using the release versions' because:

1. I may want to try my first release-upgrade to 16.04 to see how that goes. I don't know if is best to stick to the repos versions' for that for a better chance of a successful release-upgrade.

2.  With my next desktop machine, I want to run Ubuntu 16.04 or maybe hold off to buying the box until 18.04. With Ubuntu Snappy coming along for updates in the future, I wonder if I should stick with what Ubuntu is providing in its' repos, for Snappy updates instead of from the Vbox site.

What's your thoughts?

---

### Post by SeijiSensei on 2015-10-09
I always add the Oracle repository following the instructions for Debian-based systems on the VB site.

---

### Post by mikodo on 2015-10-09
> **SeijiSensei said:**
> I always add the Oracle repository following the instructions for Debian-based systems on the VB site.

Thank you.

Obviously, I have never read about updating VirtualBox from its' own repository, when it is available. Sounds like a sane way to do that. Nice feature, it provides for a GUI update process or one can use:

$ sudo apt-get update
$ sudo apt-get install virtualbox-X.yy

I'll try that.

Addendum: And ... who knows, maybe Oracle will provide a "Snappy" update in the future for Ubuntu.

---

### Post by CharlesA on 2015-10-10
They are usually pretty good about keeping up with the latest supported releases of Ubuntu.

---

### Post by mikodo on 2015-10-10
> **CharlesA said:**
> Snip

Good to know Charles.

Thank you.

---

