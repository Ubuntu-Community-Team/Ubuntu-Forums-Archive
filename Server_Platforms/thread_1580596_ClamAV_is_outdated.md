---
title: "ClamAV is outdated"
date: 2010-09-23
forum: Server Platforms
---

### Post by MacGoose on 2010-09-23
Hi!

I have two servers complaining about ClamAV being outdated:

WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.96.1 Recommended version: 0.96.3

Doing an aptitude update says I don't have to upgrade anything.  Why is this?  Must ClamAV be updated manually?

, MacGoose

---

### Post by lykeion on 2010-09-24
The clamav version you are using is tested with Ubuntu.
If you want a later version you'll have to use a PPA repository.
You'll have to decide whether to use a later version (for security) or a thoroughly tested version (for stability).

If you'll go for the PPA here's how to do it:
1. Edit the software sources (use vim, nano, emacs or whatever text editor you're familiar with)
```
sudo vim /etc/apt/sources.list
```
2. Add this line
```
deb http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu lucid main
```
3. Save and close
4. Add the key for the PPA
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5ADC2037
```
5. Update and upgrade 
```
sudo apt-get update
sudo apt-get upgrade
```

Links:
[LIST]
[*][Ubuntu Documentation ClamAV]("https://help.ubuntu.com/community/ClamAV")
[*][PPA for Clamav Update Team]("https://launchpad.net/~ubuntu-clamav/+archive/ppa")
[/LIST]

---

### Post by MacGoose on 2010-09-24
Thanx!

So if I go for the tested Ubuntu version I will get these warnings all the time?

I think I'll go for the PPA repository then.  I like to see warnings that are "real" and can be dealth with.

Thanx again!

, MacGoose

---

### Post by krull677 on 2010-09-24
hi thanks for the info but i get a
"Type ‘[http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu’](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu’) is not known on line 56 in source list /etc/apt/sources.list " on updating any ideas what causes this, not that I hold out much hope clam will the my virus that I know is there.

---

### Post by lykeion on 2010-09-25
@krull
What are you trying to do here? Are you following my steps on how to install the PPA version of ClamAV?
If so, you have to copy the **whole** line in step 2, incl. the "deb" before the url.

Also I would recommend using the main Ubuntu repositiories, not adding extra PPA repos just for the sake of it.

---

### Post by SeijiSensei on 2010-09-25
> **lykeion said:**
> Also I would recommend using the main Ubuntu repositiories, not adding extra PPA repos just for the sake of it.

Bug report filed at Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/644707](https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/644707)

The patch is included in the version for Maverick but hasn't been applied to earlier releases.  I don't know much about how backports work, but perhaps it's available to him that way?

[https://bugs.launchpad.net/bugs/cve/2010-0405](https://bugs.launchpad.net/bugs/cve/2010-0405)

ClamAV gets continuously updated and patched, almost on a daily basis according to its [Changelog](http://git.clamav.net/gitweb?p=clamav-devel.git;a=blob_plain;f=ChangeLog;hb=master).  I presume it's constantly being targeted by virus developers and other hackers given its widespread use.  So I wouldn't say trying to keep current with its development constitutes "adding extra PPA repos just for the sake of it."  I've used ClamAV for many years now as part of a mail scanning server, and it seems to need updating more than most of the other software on that box.

That said, I just tried to update a CentOS 5.5 server I run, and the upgrade doesn't seem to be in its repositories yet either.

Update:  I'm building 0.96.3 on that system from [source]("http://freshmeat.net/urls/c9bfa0aa2a4b8f3dc21e37debf0b05e5") now.  I had to upgrade bzip2 and bzip2-devel since that's the origin of the vulnerability.  The ClamAV source for 0.96.3 checks the bzip2 code to make sure the patch is installed and complains loudly if it's not there.

---

### Post by lykeion on 2010-09-25
Yes, if I ran a server and used ClamAV I would try to keep it updated. That is why I suggested a way to get an updated package via PPA to OP.
But for the normal user who may be unsure of what he's doing I think it's easier to use the main repository version, that's all I was saying.

---

### Post by krull677 on 2010-09-26
Ok. i did add the lines exactly as written on your post bu that is what the error message says. i will probably stick to the ubuntu repo. and just wait for them to update clam.

---

