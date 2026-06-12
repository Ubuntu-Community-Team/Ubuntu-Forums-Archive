---
title: "ISO image current is still 2021-01-23"
date: 2021-02-27
forum: Ubuntu Development Version
---

### Post by corradoventu on 2021-02-27
[http://cdimages.ubuntu.com/daily-live/current/](http://cdimages.ubuntu.com/daily-live/current/) is still 2021-01-23
while [http://cdimages.ubuntu.com/daily-live/pending/](http://cdimages.ubuntu.com/daily-live/pending/) is already 2021-02-27
... problems?

---

### Post by corradoventu on 2021-03-10
today mer 10 mar 2021 [https://cdimage.ubuntu.com/daily-live/current/](https://cdimage.ubuntu.com/daily-live/current/) is still dated 2021-01-23

---

### Post by oldfred on 2021-03-10
But if I zsync I get new file  with Kubuntu, with lots of updates from Feb download.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~/ISO**[/COLOR][COLOR=#000000]$ zsync http://cdimage.ubuntu.com/kubuntu/daily-live/current/hirsute-desktop-amd64.iso.zsync [/COLOR]
#################### 100.0% 438.3 kBps DONE  
[/FONT][FONT=monospace][COLOR=#000000]Read hirsute-desktop-amd64.iso. Target 47.4% complete.      **************************************************** [/COLOR]
downloading from http://cdimage.ubuntu.com/kubuntu/daily-live/current/hirsute-desktop-amd64.iso: 
#########----------- 47.4% 7.2 kBps          
#################### 100.0% 10692.0 kBps DONE      

verifying download...checksum matches OK 
used 1390600192 local, fetched 1545878221

[/FONT]
```

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~/ISO**[/COLOR][COLOR=#000000]$ ll h*.iso [/COLOR]
-rw------- 1 fred fred 2936012800 Mar 10 06:08 hirsute-desktop-amd64.iso 
[COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~/ISO**[/COLOR][COLOR=#000000]$ ll h*.zs-old [/COLOR]
-rw------- 1 fred fred 2896187392 Feb 15 04:41 hirsute-desktop-amd64.iso.zs-old

[/FONT]
```

---

### Post by dino99 on 2021-03-10
Will get 5.11 soon [https://bugs.launchpad.net/kernel-sru-workflow/+bug/1917335](https://bugs.launchpad.net/kernel-sru-workflow/+bug/1917335)

---

### Post by VMC on 2021-03-10
Yes, the zsync shows current date. That's what is puzzling. Not usre if dates are correct.

---

### Post by corradoventu on 2021-03-14
They are 2 bugs about this problem:
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1919079](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1919079)
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1918929](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1918929)

---

### Post by xyz-t on 2021-03-14
This bug is old and still there for today's build. Clicking on parent directory ends on Jan. 23 ISO. We did not make the fresh install of March 8th build because of this. Kubuntu has no bug now.

[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)
[http://cdimage.ubuntu.com/daily-live/20210314/](http://cdimage.ubuntu.com/daily-live/20210314/)

Mount > dists > Hirsute > Release >  

```
Origin: Ubuntu
Label: Ubuntu
Suite: hirsute
Version: 21.04
Codename: hirsute
Date: Sat, 23 Jan 2021  2:42:07 UTC
Architectures: amd64 i386
```

Clicking parent directory first and the top right link after gives this:

```
Origin: Ubuntu
Label: Ubuntu
Suite: hirsute
Version: 21.04
Codename: hirsute
Date: Sat, 13 Mar 2021  2:33:57 UTC
Architectures: amd64 i386
Components: main restricted
Description: Ubuntu Hirsute 21.04
```

There are two ISOs in the same page: Jan 23rd labeled March 14th + March 13th instead of 14th.

---

### Post by guiverc on 2021-03-14
Lubuntu hasn't had any such issue I can report.

Thanks for the post though; I did a QA-test of Ubuntu Desktop a few days ago, and just `zsync` the *hirsute* ISO & didn't think to check the dates/manifest for changes (*I do for Lubuntu and any flavors I check regularly*) and assumed I was testing the latest..  

Turns out the date was Jan-23 & I hadn't noticed.....

---

### Post by corradoventu on 2021-03-15
Other flavors don't have the same problem, few days ago the dates was:
current for Lubuntu is dated 2021-03-11 16:59 [http://cdimages.ubuntu.com/lubuntu/daily-live/current/](http://cdimages.ubuntu.com/lubuntu/daily-live/current/)
current for Kubuntu is dated 2021-03-12 05:49 [http://cdimages.ubuntu.com/kubuntu/daily-live/current/](http://cdimages.ubuntu.com/kubuntu/daily-live/current/)
current for Xubuntu is dated 2021-03-12 01:57 [http://cdimages.ubuntu.com/xubuntu/daily-live/current/](http://cdimages.ubuntu.com/xubuntu/daily-live/current/)
current for ubuntu-mate is dated 2021-03-12 03:08 [http://cdimages.ubuntu.com/ubuntu-mate/daily-live/current/](http://cdimages.ubuntu.com/ubuntu-mate/daily-live/current/)

---

### Post by xyz-t on 2021-03-15
Today's build from parent directory and top right link is 03132021. 

There were only 9 packages after the fresh install. Proposed has 65 packages including Kernel 5.11. 

We also have the show applications issue with activities hidden.  The rest appears ok so far.

---

### Post by corradoventu on 2021-03-16
Look inside [http://cdimages.ubuntu.com/daily-live/current/](http://cdimages.ubuntu.com/daily-live/current/) the ISO for arm64 is dated 2021-03-15 08:22 while the one for amd64 is 2021-01-23 08:36 
they are 2 bugs for this problem: [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1919079](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1919079) and [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1918929](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1918929)

---

