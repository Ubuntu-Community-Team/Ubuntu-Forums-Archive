---
title: "Firefox 11.0 too new. Need an older version"
date: 2012-02-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ernestj on 2012-02-12
I installed 12.04 and along with came it Firefox 11.0.  I need an older version for college.

How can I install a older version of Firefox?

Thanks,
Ernie

---

### Post by Ibidem on 2012-02-12
Good reason to not use 12.04, I think.

If you just need a slightly older version, you could add natty-security or oneiric-security, and pin firefox + xulrunner* + ... to that version.
Otherwise, you can download a binary from mozilla, or build from source (which is NOT easy, I know).

What version do you need?

---

### Post by ernestj on 2012-02-12
I was using the version with Ubuntu 11.10 without problems. Any way can I sudo a older version?

Ernie

---

### Post by Ibidem on 2012-02-12
gksu gedit /etc/apt/sources.list #sudo vim, or your favorite editor
Copy the line containing "deb ...precise-security ...", paste, and change the "precise-security" to "oneiric-security"
(Only in one line, not in both!) 
Then read up on apt-pinning, and pin firefox to the proper repo (hint: use apt-cache policy firefox to find out how to specify the repo).

Sorry for not having the apt-pinning howto handy

---

### Post by pqwoerituytrueiwoq on 2012-02-12
you should never ever[FONT=Courier New] sudo firefox[/FONT]
aside from the scurity risk it screws up the permissions of it's app data
if you want to install a different version of firefox use this script (do not use sudo)

[http://ubuntuforums.org/attachment.php?attachmentid=212505&d=1328983655](http://ubuntuforums.org/attachment.php?attachmentid=212505&d=1328983655)

edit line 2 with the desired version

---

### Post by Ibidem on 2012-02-12
Reading comprehension fail.
(sudo as in sudo dpkg | apt-get | ...)

The way I suggested, you'll get security updates; that script may not work as well.

---

### Post by screaminj3sus on 2012-02-12
Why the heck are you using an alpha release for college work?

---

### Post by pqwoerituytrueiwoq on 2012-02-13
> **Ibidem said:**
> The way I suggested, you'll get security updates; that script may not work as well.
you will get updates even faster (direct from mozilla via firefox's update manager) as long as you don't install it with sudo
> **Ibidem said:**
> Reading comprehension fail.
(sudo as in sudo dpkg | apt-get | ...) as in never run a web browser as root

---

### Post by cariboo on 2012-02-13
> **pqwoerituytrueiwoq said:**
> you will get updates even faster (direct from mozilla via firefox's update manager) as long as you don't install it with sudo
 as in never run a web browser as root

I don't see anywhere in this thread where someone has suggest running Firefox as root.

---

### Post by Harry33 on 2012-02-13
> **ernestj said:**
> I installed 12.04 and along with came it Firefox 11.0.  I need an older version for college.

How can I install a older version of Firefox?

Thanks,
Ernie

You can get the latest stable version (10.0.1+build1) from the Ubuntu Mozilla Security Team PPA. There is no separate Precise-alfa version, but the Oneiric branch version is fully working in Precise-alfa too. 

Here:
[https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric)

---

### Post by dcstar on 2012-02-13
> **screaminj3sus said:**
> Why the heck are you using an alpha release for college work?

+1

This is one of those threads where the answer should be "Bad luck, use a supported version of Ubuntu and stop wasting everybody's time".

---

### Post by prusswan on 2012-02-13
> **screaminj3sus said:**
> Why the heck are you using an alpha release for college work?

to do work and test at the same time, it helps when you are not relying on specific package versions :)

---

### Post by Ibidem on 2012-02-13
> **dcstar said:**
> +1

This is one of those threads where the answer should be &quot;Bad luck, use a supported version of Ubuntu and stop wasting everybody's time&quot;.

 I'm at a university too. This is my second LTS-testing cycle running Ubuntu+1 for the spring semester. I install over Christmas break, and keep it fairly current until release.  Then I have an LTS install.  It works decently.  That said, I dual-boot (Debian Squeeze in this case, Jaunty/Kuki last cycle), which I use for a lot (but certainly not all) of the work.

---

### Post by kevpan815 on 2012-02-13
I believe that the Ubuntu Staff already answered that question as a reply to one of my posts. Here was the question that I asked: Now that Mozilla Thunderbird 11.0 Beta 1 Build 2 has been released 2 12.04, will we see Mozilla Firefox 11.0 Beta 1 as well in 12.04? Their answer was the following: Absolutely yes, we always test new Beta's of Mozilla Firefox and Mozilla Thunderbird in Ubuntu Development Releases so that we can eventually Back Port them to all previously supported Releases (That are still currently supported) as they are also considered as security updates in nature. Just FYI.

---

### Post by pqwoerituytrueiwoq on 2012-02-13
> **cariboo907 said:**
> I don't see anywhere in this thread where someone has suggest running Firefox as root.
opps, i think i may have gotten similar threads in different tabs mixed up

---

