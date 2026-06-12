---
title: "can't install proftpd"
date: 2005-10-07
forum: Server Platforms
---

### Post by belgampaul on 2005-10-07
Hello, I would like to set up an ftpd
but when i do this

apt-get install proftpd proftpd-common ucf

I got this a s a result.


Reading package lists... Done
Building dependency tree... Done
ucf is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  proftpd: Depends: libc6 (>= 2.3.4-1) but 2.3.2.ds1-20ubuntu14 is to be installed
  proftpd-common: Depends: libc6 (>= 2.3.4-1) but 2.3.2.ds1-20ubuntu14 is to be installed
                  Depends: libncurses5 (>= 5.4-5) but 5.4-4 is to be installed
E: Broken packages

and i'm stuck at this 

can anyone help me with this?

I followed this tutorial to set up my machine

[http://www.howtoforge.com/perfect_setup_ubuntu_5.04_p5](http://www.howtoforge.com/perfect_setup_ubuntu_5.04_p5)

what can be wrong? 

Here's my /etc/apt/sources.list
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5 hoary
deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5 breezy

```

Tnx for your help guys.

---

### Post by belgampaul on 2005-10-08
ok, i found a workaround

i've installed "breezy"

---

