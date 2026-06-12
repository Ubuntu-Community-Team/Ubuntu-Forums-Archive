---
title: "Ubuntu Server 13.10 and Bash Vulnerbility"
date: 2014-09-25
forum: Security
---

### Post by James_Yun on 2014-09-25
Hi

I have an application running on this server and need to update bash due to the recent vulnerability.  The current version is end of life.  Is there a bash update I can download somewhere?

---

### Post by Lars Noodén on 2014-09-25
Welcome.

Support for 13.10 ended back in July, so there are no updates that you do not make on your own.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Is there a particular reason you are holding back from 12.04 LTS or 14.04 LTS server?  The choice is using LTS or else going through frequent upgrades of the whole system.  

Anyway, about bash, the souce can be found via the project's web site:
[https://www.gnu.org/software/bash/](https://www.gnu.org/software/bash/)

If you can still download source packages for 13.10, then you should be able to substitute in the new source code and make a new package.

---

### Post by walker11452 on 2014-09-26
Microsoft made updates available for Internet Explorer even to Windows XP user after XP's end of life in April of this year as the exploits affected most versions of IE and there were still (and still are) many XP users. Why would Canonical not do the same thing with Ubuntu? I use Ubuntu 13.10 and when ever I try to upgrade I am told I have been a bad boy and added in software that was not available through the normal channels so it will not upgrade. All because I needed the current version of some software and not the version that is 2 or 3 versions old that is all that is available via the normal Ubuntu channels.


> **Lars Noodén said:**
> Welcome.

Support for 13.10 ended back in July, so there are no updates that you do not make on your own.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Is there a particular reason you are holding back from 12.04 LTS or 14.04 LTS server?  The choice is using LTS or else going through frequent upgrades of the whole system.  

Anyway, about bash, the souce can be found via the project's web site:
[https://www.gnu.org/software/bash/](https://www.gnu.org/software/bash/)

If you can still download source packages for 13.10, then you should be able to substitute in the new source code and make a new package.

---

### Post by mörgæs on 2014-09-26
> **walker11452 said:**
> Why would Canonical not do the same thing with Ubuntu?

Because developers' time is scarce and better spent on recent versions.

[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

### Post by walker11452 on 2014-09-26
So was Microsoft's developer's time. But somehow I can not see the logic behind your statement. The sources are available all that needs to be done is to be compiled and packaged and place on the repositories for all versions affected possibly back to 12. 

But the comment that developer time is scarce and better spent on the current version (note not recent as I am running a recent version which is being ignored) just makes me rethink my decision not to use windows and to use Ubuntu. While I am fully capable to compiling the source on my own others are not. There are other versions of linux and then there is always windows. At least then support will be more likely to the end user rather than to the programmer.

One reason Linux will never take over the desktop.

> **mörgæs said:**
> Because developers' time is scarce and better spent on recent versions.

[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

### Post by Lars Noodén on 2014-09-26
Is there a particular reason you have 13.10 still instead of 12.04 or 14.04?  Version 12.04 on the server will last until April next year and 14.04 will last another 4.5 years until April 2017.  

The 13.10 version is not supported.  It had a 9-month life.  It is done since July.  

On (actually well before) the day 13.10 was published, it was public both how long that version would be supported and what supported and not-supported mean in regards to the distro.  Even the trade magazines mentioned this and it has been on the download page.  Again, it was on a 9-month cycle.  For people that want a longer life cycle, there are the Long Term Support versions.  Currently they are [14.04, 12.04 and on the server 10.04](https://wiki.ubuntu.com/Releases).  The End-of-life for support cannot be a surprise, it is widely published.  The idea is for people to plan ahead and choose either LTS or prepare to schedule frequent system upgrades.  When downloading, there were (are) three choices: go with  LTS, plan for frequent upgrades, plan for eventual self-support.

About self-support, individuals and groups of individuals and even companies are free to provide self support for discontinued versions.  The source packages should still be there and in most cases it should be easy to roll in a patch and make a new versions of the package.  There are also companies like M:Tier that make money providing extended support for OpenBSD which has an even shorter cycle, so there might be corresponding companies for Ubuntu somewhere.

---

### Post by Michael_McKenney on 2014-09-26
Microsoft customers paid for the OS and it has corporate users that are still moving to Windows 7 from XP Pro.  So Microsoft made a decision to patch this problem.  It usually does not do this.

---

### Post by QIII on 2014-09-26
Canonical has about 500 employees and takes in meager revenue -- one man makes up for the loss out of his own pocket.  It is likely that no more than 1/3 of those employees are developers.

Microsoft just announced that they will be laying off four times that and didn't bat an eye.

Canonical does not have brigades of developers to maintain out-dated and unsupported releases.

None of us here are Canonical employees.  We cannot answer for Canonical's decisions.

---

