---
title: "To all 8.04 at later Firefox Users- use Mozilla PPA"
date: 2011-03-04
forum: Ubuntuzilla
---

### Post by hangfire on 2011-03-04
For all you folks who have been enjoying ubuntuzilla, well, this is not an official announcement, but it seems this PPA is now unmaintained. Hope I'm wrong. It was very nice while it lasted.

I found an official ubuntu build of the latest mozilla FF at:

[https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/)

To find your O/S release (e.g., 8.04LTS) click the green "Technical details about this PPA" link and select your O/S from the dropdown.

Follow the rest of the instructions to add the PPA to your sources.

Print this out:
Exit firefox
```
sudo apt-get remove firefox-mozilla-build
```
(or follow instructions if you installed from the python script.)

Delete or comment from /etc/apt/sources.list:
**deb [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main**


```
sudo apt-get update
sudo apt-get install firefox firefox-branding
```

You should be at 3.6.15 or later.

I'm not sure what happens on the jump to FF4.

Good luck!

---

### Post by mikewhatever on 2011-03-04
The main 8.04 repository has the latest stable FF-3.6.14, not sure why you need to use PPAs.

---

### Post by hangfire on 2011-03-10
> **mikewhatever said:**
> The main 8.04 repository has the latest stable FF-3.6.14, not sure why you need to use PPAs.

Then why use ubuntuzilla?

I guess it has to do with Canonical's 8.04 repos being stuck on FF 3.0 for months, and then finding ubuntuzilla, which came into existence for the same reason. There was a lot of banter on ubuntuforums.org and no one at Canonical stepped up to the plate to fix it at the time... so... haven't relied on them for FF ever since.

---

### Post by the.phantom on 2011-03-10
> haven't relied on them for FF ever since.

agree 100%

most of the updates deal with security and severe bugs and when weeks late that is bad for my system and me  ;-D

along the same lines, where is the t-bird update from 2 weeks ago?
3.1.9 came out the same time as the ff update and still quiet on the repo's

wish someone knew enough to take over from nanotube !!!!

---

### Post by nanotube on 2011-03-11
> **the.phantom said:**
> agree 100%

most of the updates deal with security and severe bugs and when weeks late that is bad for my system and me  ;-D

along the same lines, where is the t-bird update from 2 weeks ago?
3.1.9 came out the same time as the ff update and still quiet on the repo's

wish someone knew enough to take over from nanotube !!!!

ubuntu lucid + later do have timely updates for ff/tb/sm...

---

### Post by Karlchen on 2011-03-24
For Firefox 3.6.16, I can confirm that the official repositories offered the update for Ubuntu 9.10 (Karmic Koala) tonight. :D
Friday morning will show whether the update will be offered to the office machine running Ubuntu 10.04 (Lucid Lynx) as well.
Have not spotted Firefox 4.0 in the official repositories so far for Karmic or Lucid.

<Added, Friday morning>
Lucid Lynx is running the official Ubuntu release of Firefox 3.6.16 now. So it is in the repositories.
</Added, Friday morning>

Karl

---

