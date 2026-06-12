---
title: "What virus scanner program should I install?"
date: 2009-12-30
forum: Security
---

### Post by sad1sm0 on 2009-12-30
First, I want to say, I am not looking for virus protection for my own computer, but rather a reliable way to scan files that may end up on a windows computer later on.  I fix a lot of windows computers whenever they break down or become infected with viruses, and would like to find a way to ensure that I'm not going to re-infect them by transferring files to and from my server.  Whenever possible, I convert these users to linux, but occasionally I run into users who need windows for one reason or another.  I was checking out the repos for scanner programs, and there are a lot to choose from, so I would like to know if anyone has any experience with these programs and which ones I should focus on.  Any insight would be greatly appreciated.

---

### Post by MelDJ on 2009-12-30
i use avast [http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

---

### Post by Lori700698 on 2009-12-30
I use clamAV [http://www.clamav.net/](http://www.clamav.net/)  I think it's in the repositories.  sudo apt-get install clamav (but double check this)

Lori

---

### Post by ayushcena on 2009-12-31
AVG and Avast were both pretty decent, and I am using Avast right now; while ClamAV was a bit slow for my tastes.. though your individual mileage may vary.

---

### Post by Autodave on 2009-12-31
AVIRA makes an excellent one.  And it's free!  I had used it for years while I was still running Winblows and I put it on every machine I ever worked on.  Even viruses that Norton and McAfee didn't find or couldn't eradicate, AVIRA did it with no intervention from me.  AVIRA also has a Linux version.

---

### Post by J V on 2009-12-31
2 things, avira IS indeed a good anti virus, also very low footprint so less likely to do to linux what you probably left windows for :)

You will have to hack their advertisment file though, not sure how you do it in linux...

ClamAV is generally considered the preferred...

Open source, no footprint at all unless in use, and you can rig a script to scan for anything you transfer to a non ext filesystem I'm sure...

---

### Post by sad1sm0 on 2010-01-04
Thanks for all of the replies.  I've installed clamAV and got it scanning in no time.  I see that it can move infected files to another location, but is there anyway it can try to repair a file like avast or the others?  Also, any idea where to download new virus definitions or will it find them in the updates since it's in the repositories?

---

