---
title: "installing clamav-0.98.4"
date: 2014-07-11
forum: Security
---

### Post by dapps2 on 2014-07-11
I wanted to install ClamAV but the version in Synaptic is out dated so i went along to the ClamAV site and downloaded the latest version 0.98.4 and after extracting all files to the /tmp folder i thought it would be a simple case of going to the /tmp folder and typing: sudo apt-get install clamav-0.98.4 but this don't work? Could someone help me please.

---

### Post by SeijiSensei on 2014-07-11
There are no pre-built packages on the ClamAV site.  The Ubuntu instructions tell you to use the repositories.

Is the file called clamav-0.98.4.tar.gz? If so, you downloaded the source code.   You'd need to compile it to make it work; it won't install with apt since its not a .deb package.  Last time I compiled ClamAV it went pretty smoothly so you're welcome to give it a try.  First [read this document]("https://help.ubuntu.com/community/CompilingEasyHowTo") on what you need to compile a program from source on Ubuntu.

---

### Post by Gyokuro on 2014-07-11
Hi

Or you wait until it's get update as it's already in the works ([https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/1317587](https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/1317587)).

---

### Post by SeijiSensei on 2014-07-11
The posting that said the update was "in the works" is dated near the end of May.  The current 14.04 release version is still 0.98.1+dfsg-4ubuntu1.1.  There's a [newly-released version]("https://launchpad.net/ubuntu/+source/clamav") of 0.98.4 for Utopic, but not for stable LTS releases like 14.04.

ClamAV goes through "point releases" like 0.98.4 all the time; my mail server will complain that its version of clamav is out of date a few times a year.

There's a PPA with updated ClamAV packages for Ubuntu: [https://launchpad.net/~ubuntu-clamav/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-clamav/+archive/ubuntu/ppa).  That one includes an 0.98.4+dfsg-0ubuntu1~14.04.1~ppa1 version for Trusty.

---

### Post by Gyokuro on 2014-07-13
Hi

Yes but it's only a matter of time and clamav 0.98.4 is now in Debian Wheezy 7.6 so it's a minor task to repackage it for Precise/Trusty as mentioned in the launchpad bug report.

---

### Post by SeijiSensei on 2014-07-13
Version 0.98.4 was released on May 21st.  Dag Wieers released the [version]("http://pkgs.repoforge.org/clamav/") running on my CentOS servers on June 17th.  Even that seems awfully long to me.  My mail server's logs are full of recommendations to update to 0.98.4 during that period.  Considering that Canonical is a commercial organization, and that it has the Debian developers behind it as well, I would hope to see quicker releases for updates to a piece of software widely used on servers around the world.

As I said, ClamAV issues new point releases all the time. 0.98.3 was released just two weeks before 0.98.4, and 0.98.2 came out just a couple of weeks before that.  I don't know whether there are different streams for different packages, but ClamAV ought to be in the high-speed lane.

---

