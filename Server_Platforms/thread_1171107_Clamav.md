---
title: "Clamav"
date: 2009-05-27
forum: Server Platforms
---

### Post by EmanresuusernamE on 2009-05-27
I'm having an issue with installing Clamav.  I keep getting an error telling me that libltdl3 is a virtual package and that it can't install Clamav because it relies on libltdl3. I made sure libltdl7 was installed on my system from suggestions on other websites, but still no dice. I did a purge of Clamav, and it has installed fully on the system, but won't update at all stating that I need to be at a higher version.  Are the repositories using old versions by some chance?

I get this:
```
sudo aptitude install clamav-daemon
sudo: cannot get working directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  clamav clamav-daemon clamav-freshclam libclamav6 
The following NEW packages will be installed:
  clamav-base{a} 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 1494kB/22.9MB of archives. After unpacking 24.7MB will be used.
The following packages have unmet dependencies:
  clamav: Depends: libltdl3 (>= 1.5.2-2) which is a virtual package.
  clamav-freshclam: Depends: libltdl3 (>= 1.5.2-2) which is a virtual package.
  libclamav6: Depends: libltdl3 (>= 1.5.2-2) which is a virtual package.
  clamav-daemon: Depends: libltdl3 (>= 1.5.2-2) which is a virtual package.
The following actions will resolve these dependencies:

Install the following packages:
clamav [0.94.dfsg.1~rc1-0ubuntu2 (intrepid)]
clamav-freshclam [0.94.dfsg.2-1ubuntu0.3 (intrepid-updates, intrepid-security)]

Keep the following packages at their current version:
clamav-daemon [Not Installed]
libclamav6 [Not Installed]

Score is -9932
```

Can anyone point me in the right direction?  I'm trying to get this up and running as an email server, and this is blocking me.  I've configured the server to use postfix and dovecot for incoming and outgoing mail. Anything else I need to post?

---

### Post by LepeKaname on 2009-05-27
Something may be wrong with you repositories...

I tried in Jaunty and Intrepid and there is no problem. Actually if you install clamav, it will automatically install:

-clamav-base
-clamav-freshclam
-libclamav5

Then I installed clamav-daemon without any warning or error.

---

### Post by EmanresuusernamE on 2009-05-27
Well, I found out why it was giving me that error, I had this line in my sources.list:
deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) hardy main

Which I believe some website told me to put in there.  Thing is, it's still not updating properly.
```
sudo freshclam
ClamAV update process started at Wed May 27 19:46:51 2009
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.94.2 Recommended version: 0.95.1
DON'T PANIC! Read http://www.clamav.net/support/faq
main.cld is up to date (version: 51, sigs: 545035, f-level: 42, builder: sven)
daily.cvd is up to date (version: 9397, sigs: 18738, f-level: 42, builder: ccordes)
```

I've ran sudo aptitude update and upgrade, but no dice.

---

### Post by cariboo on 2009-05-28
Freshclam sets up a cron job to go out and look for new virus definitions daily.

---

### Post by jowilkin on 2009-05-28
It looks like your definitions are updated just fine.

Your version is not the newest version because of Ubuntu's 6 month release model.  They will not update the version until the next release.  Only way to get it updated is to find a ppa that maintains the newest version or to manually install the newest version.

---

