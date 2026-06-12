---
title: "Security updates for unsupported Versions."
date: 2010-09-29
forum: Security
---

### Post by Gervais_5H3T on 2010-09-29
Hi All,

I currently run 9.04 and, for reasons i don't wish to get into, I do not wish to upgrade. As i'm sure every good Ubuntu'er knows it's coming up to the end of it's suport cyclr from canonical.  So:

Can I simply change the repos in /etc/apt/sources.list, to their 10.04 equivalents?
So change the "deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted" line to  "deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted" or if not exactly this, something to this effect??

Essentially i would like to keep getting updates, without having to upgrade the OS, I know there is "apt-get dist-upgrade", but from what I understand this is simply a less conservative (ie kernel etc) version of "apt-get upgrade"

I would be disappointed that I could not update the security on my machine, esp if there where vulnerabilities! Thanks peeps!

Any help would be greatly appreciated.  Thanks FOSS people :P

---

### Post by snowpine on 2010-09-29
No, that definitely will not work. :(

Please read the upgrade notes for how to upgrade your 9.04 system to 9.10 (and then from 9.10 to 10.04 if you choose):

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Ubuntu is a fast-moving distro, and "only 18 months of support" is determined well in advance of each release. You can stick with the LTS versions if you want 3 years support.

---

### Post by FuturePilot on 2010-09-29
That definitely will not work and would most certainly break your system. There's really no other choice but to upgrade once a release hits end of life if you wish to still receive updates.

---

### Post by Gervais_5H3T on 2010-09-30
Hi Again,

I thought as much,:( its a little disappointing, that one can't get security updates even. Its a little hard to understand why Canonical would do so, especially since there is no real gain from them doing so. Oh well!!

Cheers for the help guys!   :P

---

### Post by snowpine on 2010-09-30
> **Gervais_5H3T said:**
> I thought as much,:( its a little disappointing, that one can't get security updates even. Its a little hard to understand why Canonical would do so, especially since there is no real gain from them doing so. Oh well!

The "real gain" is that Canonical can focus their attention elsewhere. There are currently 8 (soon to be 9) "end of life" Ubuntu releases. If Canonical were to waste their time supporting these obsolete releases, it would divert resources from fixing bugs in current releases and developing new features for future releases!

To reiterate, Ubuntu is a fast-moving distro; it is well-publicized in advance that each release is only supported 18 months. If you prefer a longer support cycle of 3 years, you may use the LTS releases.

---

### Post by bodhi.zazen on 2010-09-30
> **Gervais_5H3T said:**
> Hi Again,

I thought as much,:( its a little disappointing, that one can't get security updates even. Its a little hard to understand why Canonical would do so, especially since there is no real gain from them doing so. Oh well!!

Cheers for the help guys!   :P

No OS is supported forever. That makes as much sense as complaining that Microsoft no longer maintains Win95. Canonical makes the length of support with each release clear.

I suggest you stay with a LTS release, Debian Stable, Slackware, or Centos.

---

