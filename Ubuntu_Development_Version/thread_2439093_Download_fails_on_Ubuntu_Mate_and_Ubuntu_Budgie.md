---
title: "Download fails on Ubuntu Mate and Ubuntu Budgie"
date: 2020-03-22
forum: Ubuntu Development Version
---

### Post by wildmanne39 on 2020-03-22
I have tried several times to download Ubuntu Mate and Ubuntu bungie daily iso's and they keep failing, anyone else having this issue? I can download the regular versions of Ubuntu from the official site.

---

### Post by Frogs Hair on 2020-03-22
I just started and the download time and speed keeps jumping all over the place which is not a good sign. I'm cancelling, there is obviously something wrong. Edit: Budgie and Mate both have problems. Could be the flavors download mirror.

---

### Post by wildmanne39 on 2020-03-22
I thought that is the case but needed to be sure since I am also having issues staying connected to irc, though I believe irc is the only thing I am having connection issues with.

Thanks

---

### Post by guiverc on 2020-03-22
I just wrote Lubuntu's 20.04 daily to thumb-drive, having completed download just before that (within last 65 mins anyway) and I didn't notice anything unusual; though I just kick job off and it runs in a terminal window usually partially hidden (so if slow, I'd possibly not notice). 

`zsync` detected I had 89.8% & just downloaded it with the next message that it was done; no restart issues (that I sometimes see), for the flavor I grabbed.

---

### Post by Frogs Hair on 2020-03-22
I think the problem is the US mirror.

---

### Post by wildmanne39 on 2020-03-22
> **Frogs Hair said:**
> I think the problem is the US mirror.

I suspect you are correct, I do not see a way to change the mirror when downloading the daily iso's though.

---

### Post by Frogs Hair on 2020-03-22
> **wildmanne39 said:**
> I suspect you are correct, I do not see a way to change the mirror when downloading the daily iso's though.

I've had this happen before and just waited until the next day. The problem fixed on the other end.

---

### Post by VMC on 2020-03-22
I just sync'ed up Budgie a little over an hour ago without issue. It only needed less than 4% to complete the sync. Haven't tried the full download for several days now.

---

### Post by wildmanne39 on 2020-03-22
I tried a couple of more times but the download still fails so I will wait until tomorrow and see if the issue is resolved by then.

Thanks everyone.

---

### Post by Frogs Hair on 2020-03-23
Still failing a day later. The link is for Vanilla only.

[https://launchpad.net/ubuntu/+cdmirrors](https://launchpad.net/ubuntu/+cdmirrors)

---

### Post by P-I H on 2020-03-23
Have you tried to download from the Testing tracker
[http://iso.qa.ubuntu.com/qatracker/milestones/408/builds](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds)

Tried this just now with Ubuntu Budgie and the download worked OK. I haven't installed and don't know if it really is Budgie.

---

### Post by wildmanne39 on 2020-03-23
> **P-I H said:**
> Have you tried to download from the Testing tracker
[http://iso.qa.ubuntu.com/qatracker/milestones/408/builds](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds)

Tried this just now with Ubuntu Budgie and the download worked OK. I haven't installed and don't know if it really is Budgie.

I am downloading from this site now, post back when I now if the download completes.

This is an official ubuntu site, I have seen it before but never used it.

Thanks

---

### Post by wildmanne39 on 2020-03-23
> **P-I H said:**
> Have you tried to download from the Testing tracker
[http://iso.qa.ubuntu.com/qatracker/milestones/408/builds](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds)

Tried this just now with Ubuntu Budgie and the download worked OK. I haven't installed and don't know if it really is Budgie.

This failed as well, must be an issue with the US servers.

---

### Post by VMC on 2020-03-23
I used:
[http://cdimage.ubuntu.com/ubuntu-budgie/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-budgie/daily-live/current/)
and it worked for me.

---

### Post by Frogs Hair on 2020-03-23
> **VMC said:**
> I used:
[http://cdimage.ubuntu.com/ubuntu-budgie/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-budgie/daily-live/current/)
and it worked for me.
Just tried that one and made to 1.3 gb in 20 minutes before failing.

---

### Post by VMC on 2020-03-23
I rarely download a complete ISO, but zsync an older one. If you have an eariler ISO try zsyncing to Budgie:
```
zsync -i* **some.ubuntu.iso*** http://cdimage.ubuntu.com/ubuntu-budgie/daily-live/pending/focal-desktop-amd64.iso.zsync
```

---

### Post by Frogs Hair on 2020-03-23
> **VMC said:**
> I rarely download a complete ISO, but zsync an older one. If you have an eariler ISO try zsyncing to Budgie:
```
zsync -i* **some.ubuntu.iso*** http://cdimage.ubuntu.com/ubuntu-budgie/daily-live/pending/focal-desktop-amd64.iso.zsync
```

Thanks, my current daily build is not that old so, I'll just update daily unless there is a problem.

---

### Post by VMC on 2020-03-23
Here's another link if that one fails:
[http://ftp.heanet.ie/mirrors/ubuntu-cdimage/ubuntu-budgie/daily-live/current/focal-desktop-amd64.iso](http://ftp.heanet.ie/mirrors/ubuntu-cdimage/ubuntu-budgie/daily-live/current/focal-desktop-amd64.iso)

---

### Post by wildmanne39 on 2020-03-24
I decided to try to download budgie one more time before contacting someone on irc to let them know there is a problem downloading daily iso's from the U.S. and it finally downloaded successfully at a good speed.:)

---

### Post by wildmanne39 on 2020-03-24
I spoke to soon Ubuntu Mate still does not download successfully.

---

