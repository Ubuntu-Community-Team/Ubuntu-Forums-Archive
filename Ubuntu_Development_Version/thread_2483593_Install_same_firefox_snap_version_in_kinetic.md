---
title: "Install same firefox snap version in kinetic"
date: 2023-02-03
forum: Ubuntu Development Version
---

### Post by ronzo on 2023-02-03
I have had Lunar installed temporarily but went back to kinetic. Now firefox is complaining about its profile being to new. Can I install the same firefox snap version that is used in Lunar? 

If yes, how would I do that?
```
sudo snap refresh firefox --channel latest/beta
```

Or can I modify the snap package source URL to use lunar instead of kinetic somehow?

```

apt policy firefox
firefox:
  Installed: 1:1snap1-0ubuntu2
  Candidate: 1:1snap1-0ubuntu2
  Version table:
 *** 1:1snap1-0ubuntu2 500
        500 http://at.archive.ubuntu.com/ubuntu **kinetic**/main amd64 Packages

```

---

### Post by MyMurry on 2023-02-04
On lunar you have:

snap info firefox

```
name:      firefox
summary:   Mozilla Firefox web browser
publisher: Mozilla&#10003;
store-url: [https://snapcraft.io/firefox](https://snapcraft.io/firefox)
contact:   [https://support.mozilla.org/kb/file-bug-report-or-feature-request-mozilla](https://support.mozilla.org/kb/file-bug-report-or-feature-request-mozilla)
license:   unset
description: |
  Firefox is a powerful, extensible web browser with support for modern web
  application technologies.
commands:
  - firefox
  - firefox.geckodriver
snap-id:      3wdHCAVyZEmYsCMFDE9qt92UV8rC8Wdk
tracking:     latest/stable/ubuntu-23.04
refresh-date: vor 3 Tagen, um 08:31 CET
channels:
  latest/stable:    109.0.1-1    2023-01-31 (2311) 250MB -
  latest/candidate: 109.0.1-1    2023-01-28 (2311) 250MB -
  latest/beta:      110.0b9-1    2023-02-03 (2330) 189MB -
  latest/edge:      111.0a1      2023-02-04 (2334) 196MB -
  esr/stable:       102.7.0esr-1 2023-01-17 (2270) 183MB -
  esr/candidate:    102.7.0esr-1 2023-01-09 (2270) 183MB -
  esr/beta:         &#8593;                                    
  esr/edge:         &#8593;                                    
installed:          109.0.1-1               (2311) 250MB -
```

---

### Post by guiverc on 2023-02-04
Snap packages are the same for all Ubuntu releases if from the same channel (*refer MyMurry's answer for a list of channels & versions available*).

I suspect your issue isn't with the firefox snap version you have, but profile being used as you said.

I'm not good with profiles, as I only touch them when something has gone wrong, but where I'd look is **likely**

```
guiverc@d7080-next:~/snap/firefox$   ls -lah
total 40K
drwxr-xr-x 10 guiverc guiverc 4.0K Feb  1 09:43 .
drwx------ 24 guiverc guiverc 4.0K Jun 20  2022 ..
drwxr-xr-x  4 guiverc guiverc 4.0K Mar 22  2022 1115
drwxr-xr-x  4 guiverc guiverc 4.0K Mar 30  2022 1154
drwxr-xr-x  4 guiverc guiverc 4.0K Jun  4  2022 1406
drwxr-xr-x  4 guiverc guiverc 4.0K Jun 29  2022 1498
drwxr-xr-x  4 guiverc guiverc 4.0K Jul 13  2022 1551
drwxr-xr-x  4 guiverc guiverc 4.0K Jan 25 17:04 2277
drwxr-xr-x  4 guiverc guiverc 4.0K Feb  1 09:43 2311
drwxr-xr-x  4 guiverc guiverc 4.0K Mar 22  2022 common
lrwxrwxrwx  1 guiverc guiverc    4 Feb  1 09:43 current -> 2311

```

ie. I believe my current profile is 2311 with the *current* link highlighting that.

Looking at the dates of my options, I have a few from earlier this year; but they'll have come from backups as this install is only a little over a week old, with `/var/log/installer/media-info` telling me I used the 20230124 *daily* *lunar* ISO (ie. 2023-Jan-24 *daily* so my install would likely have been 25th Feb. my local time).

I installed two OSes on this box on the 25th Feb, this *lunar* install, and a *jammy* install in dual boot. I opted to use one of the older profiles on *jammy*, and am tempted to do the same thing on this box too. On this *lunar* install I tried to keep this install cleaner (*closer to original*), but I really like how the profile i opted to use in *jammy* can auto-predict my URLs from just a few characters (*due to the **much longer history of me using it*).

When/**if** I make the change to this *lunar* install [profile], or maybe after I've just booted into my *jammy* install & confirm what I believe I did, I'll provide more useful advice (*instead of just this pointer*), but I'd hate to give advice that wasn't well tested, and this is an area I rarely touch & for my own system, and I can just restore from my [*ancient as was done here, or not-so-ancient*] backups if I make a mistake (*or more commonly forget something*).

I'd look for any other profiles you have available in the directory I used in my paste (`~/snap/firefox` firstly).  

**I'd also wait for others to advise**!, unless I tried what I believe I'd do firstly myself, or I confirmed what I did for my *jammy* install, as I'd not trust my own memory (*if you understand what I've suggested**; I've only done it maybe 5-7 times, and twice had to fix something as I overlooked something, and can't be sure I've not done it yet again.. which is why I'm being vague*).

---

