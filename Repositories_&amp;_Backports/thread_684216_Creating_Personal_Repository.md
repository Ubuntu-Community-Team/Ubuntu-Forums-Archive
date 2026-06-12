---
title: "Creating Personal Repository"
date: 2008-01-31
forum: Repositories &amp; Backports
---

### Post by neurostu on 2008-01-31
I am managing some custom software that is going to be under constant update and will be distributed onto several machines in my LAN. I am thinking about setting up a APT repo that will contain the latest version of my programs but I can't get it to work quite right: 

I have all my .DEB files in a folder named debs/  I tried the following:
```

acq@ubuntu:~/debs$ apt-ftparchive | gzip -9 > repo.gz
```
I then added the following line to the sources.list file
```
 deb file:///home/acq/debs/ gutsy repo 
```
When I run 
```
 sudo aptitude update 
```

Aptitude gives me an error saying File Not Found.

I don't know if I am doing this right please help!

---

### Post by shirilover on 2008-01-31
You could use the following command to generate the Packages file:
From the folder debs
```

dpkg-scanpackages . /dev/null > Packages

```
The reason for the error is apt is looking in /home/acq/debs/gutsy/repo.
So, change the line in sources.list to
```

deb file:///home/acq/debs/ ./

```

---

### Post by neurostu on 2008-02-01
What exactly does this command do?
```
dpkg-scanpackages . /dev/null > Packages
```

Also I fixed my entry in sources.list and now I get
```

acq@display6:~/repo$ sudo aptitude update
Ign file: ./ Release.gpg
Ign file: ./ Translation-en_US
Ign file: ./ Release
Ign file: ./ Packages                 
Get:1 http://archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy/main Translation-en_US
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US
Hit http://archive.ubuntu.com gutsy Release
Hit http://archive.ubuntu.com gutsy/main Packages
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy/universe Sources
Hit http://archive.ubuntu.com gutsy/main Sources
Hit http://archive.ubuntu.com gutsy/multiverse Sources
Hit http://archive.ubuntu.com gutsy/restricted Sources
Fetched 1B in 0s (2B/s)  
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/_home_acq_repo_._Packages
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
```

What does this error mean and how do I fix it?

---

### Post by neurostu on 2008-02-01
Ok...

So i found this thread:
[http://ubuntuforums.org/showthread.php?t=42862](http://ubuntuforums.org/showthread.php?t=42862)

It showed me what to do!

---

