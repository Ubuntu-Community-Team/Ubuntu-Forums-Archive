---
title: "The following packages have unmet dependencies"
date: 2011-07-22
forum: Server Platforms
---

### Post by DeepakAnandani on 2011-07-22
i m using ubuntu server 10.10 and when i m trying to install CLAMAV-DAEMON it is showing me the error

user1@ubuntucserver:~$ sudo apt-get install amavisd-new spamassassin clamav-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
amavisd-new is already the newest version.
spamassassin is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

[U]The following packages have unmet dependencies:
 clamav-daemon : Depends: clamav-base (= 0.96.3+dfsg-2ubuntu1) but 0.96.5+dfsg-1ubuntu1.10.10.2 is to be installed
E: Broken packages[/U]

:confused:   plz help me i cannot solve this error......  i m using ubuntu server 10.10

i also tried the following

user1@ubuntucserver:~$ sudo apt-get install clamav-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 clamav-daemon : Depends: clamav-base (= 0.96.3+dfsg-2ubuntu1) but 0.96.5+dfsg-1ubuntu1.10.10.2 is to be installed
E: Broken packages

both the commands r not working..

what to do.....????:confused:

---

### Post by DeepakAnandani on 2011-07-25
the problem was solved  by doing some changes in ''source.list''
file... plzz note this problem as solved... i m providing u with the information what changes i have made......

i took a back-up of ''source.list'' file..... and replaced the whole file with the following,.....


First try to set your sources server (from update-manager) to use the main server... and retry...
  if still don't works please
made a backup copy of your actual sources.list file and then
try to put some as my standard /etc/apt/sources.list
  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) naverick-updates main restricted universe
  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse main universe restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse
  deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
 

 

 problem is solved....:guitar:

---

