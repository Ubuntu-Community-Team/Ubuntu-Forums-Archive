---
title: "apparmor blocking new profile for chrome"
date: 2013-04-22
forum: Security
---

### Post by ccb147 on 2013-04-22
Greetings,

Recently I added the profiles found [here]("http://rookcifer.blogspot.com/2012/09/securing-google-chrome-in-ubuntu-1204.html") to apparmor.  After enforcing them, firefox et al. worked without problems.  Chrome, however, does not open.  Following the advice of the fellow who did the write-up, I looked at var/log/syslog and found that apparmor was denying opt.google.chrome.chrome-sandbox.  Knowing essentially nothing about how apparmor profiles are written, I am at a loss as my next step.

I do not want to disable the apparmor profile, but would like to fix it so that chrome opens and works.  Below is the relevant stuff from var/log/syslog

[COLOR=#333333][FONT=Arial]Apr 19 16:33:28 patricia-Inspiron-1440 kernel: [ 540.391261] type=1400 audit(1366403608.862:50): apparmor="DENIED" operation="open" parent=1 profile="/opt/google/chrome/chrome" name="/proc/2958/auxv" pid=2958 comm="chrome" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Apr 19 16:33:28 patricia-Inspiron-1440 kernel: [ 540.394404] type=1400 audit(1366403608.862:51): apparmor="DENIED" operation="open" parent=2958 profile="/opt/google/chrome/chrome-sandbox" name="/lib/i386-linux-gnu/libpthread-2.15.so" pid=2966 comm="chrome-sandbox" requested_mask="r" denied_mask="r" fsuid=0 ouid=0[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Apr 19 16:33:28 patricia-Inspiron-1440 kernel: [ 540.394464] type=1400 audit(1366403608.862:52): apparmor="DENIED" operation="open" parent=2958 profile="/opt/google/chrome/chrome-sandbox" name="/lib/i386-linux-gnu/libpthread-2.15.so" pid=2966 comm="chrome-sandbox" requested_mask="r" denied_mask="r" fsuid=0 ouid=0



Please help!  Thank you.[/FONT][/COLOR]

---

### Post by clearski on 2013-04-22
Wasn't a Chrome profile in /etc/apparmor.d? I remember I recently deleted the Chrome profile because I'm not using it.

Try to get an official (verified) profile with

```
sudo apt-get install apparmor-profiles
```

As far as I remember, Chrome profile is included in the apparmor-profiles bundle, if it's not on the default installed profiles. I had problems too with profiles downloaded from Internet.

---

### Post by ccb147 on 2013-04-22
Thanks for the reply.  Through the course of getting apparmor up and running, I did run sudo apt-get install apparmor-profiles but didn't notice a chrome profile in /etc/apparmor.d; perhaps I missed it.  I will check into this when I get on my ubuntu box.

It seems to me (perhaps naively) that the "denied_mask r" shouldn't be a big deal to fix.  I don't know much about writing apparmor profiles and was just curious if the profile could be edited easily to get it working (I like the author's approach to sandboxing on multiple layers).

Thanks again.

---

### Post by clearski on 2013-04-23
A few days ago I tried to aa-enforce my Thunderbird using a profile from Internet, and it stopped running, so I removed the profile and I'm using it as is. Yes, I know there are config files which can be modified and there are guides to writing and understanding these, but at this time all I'm doing is using the default working (official) profiles. Maybe after some time I'll start looking at creating and modifying profiles, but right now I personally can't help you more, because I'm not qualified to guide you through this. :) Good luck, anyway!

---

### Post by Lfekey2 on 2013-04-23
> **ccb147 said:**
> Thanks for the reply.  Through the course of getting apparmor up and running, I did run sudo apt-get install apparmor-profiles but didn't notice a chrome profile in /etc/apparmor.d; perhaps I missed it.  I will check into this when I get on my ubuntu box.

It seems to me (perhaps naively) that the "denied_mask r" shouldn't be a big deal to fix.  I don't know much about writing apparmor profiles and was just curious if the profile could be edited easily to get it working (I like the author's approach to sandboxing on multiple layers).

Thanks again.
It's easy to fix.
But first you need to find out the right profile in /etc/apparmor.d/.
Maybe opt.[COLOR=#333333][FONT=Arial]google.chrome.chrome[/FONT][/COLOR] and [COLOR=#333333][FONT=Arial]opt.google.chrome.chrome-sandbox[/FONT][/COLOR].
Add 
[COLOR=#333333][FONT=Arial]owner @{proc}/[0-9]*/auxv[/FONT][/COLOR] r,
to opt.google.chrome.chrome profile
and [COLOR=#333333][FONT=Arial]
/lib/@{multiarch}/*.so rm,

to opt.google.chrom.chrome-sandbox profile.
[/FONT][/COLOR]

---

### Post by ccb147 on 2013-04-26
> **Lfekey2 said:**
> It's easy to fix.
But first you need to find out the right profile in /etc/apparmor.d/.
Maybe opt.[COLOR=#333333][FONT=Arial]google.chrome.chrome[/FONT][/COLOR] and [COLOR=#333333][FONT=Arial]opt.google.chrome.chrome-sandbox[/FONT][/COLOR].
Add 
[COLOR=#333333][FONT=Arial]owner @{proc}/[0-9]*/auxv[/FONT][/COLOR] r,
to opt.google.chrome.chrome profile
and [COLOR=#333333][FONT=Arial]
/lib/@{multiarch}/*.so rm,

to opt.google.chrom.chrome-sandbox profile.
[/FONT][/COLOR]

Thanks Lfekey2, I tried adding 

[COLOR=#333333][FONT=Arial]owner @{proc}/[0-9]*/auxv[/FONT][/COLOR] r,
to opt.google.chrome.chrome profile
and [COLOR=#333333][FONT=Arial]
/lib/@{multiarch}/*.so rm,

to opt.google.chrom.chrome-sandbox profile

however, /var/log/syslog still returns

[/FONT][/COLOR]Apr 26 13:05:46 patricia-Inspiron-1440 kernel: [   49.857233] type=1400 audit(1366995946.322:63): apparmor="DENIED" operation="open" parent=1 profile="/opt/google/chrome/google-chrome" name="/opt/google/chrome/chrome" pid=2645 comm="google-chrome" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

Any suggestions?

Thank You [COLOR=#333333][FONT=Arial]

[/FONT][/COLOR]

---

### Post by Lfekey2 on 2013-04-27
Ok, quick fix /opt/google/chrome/chrome r, to opt.google.chrome.google-chrome.  I suggest aa-complain your chrome profiles and pull all audit allow log, allow them in profiles. Then aa-enforce chrome profiles again.  Or you can use aa-logprof if you don't have lxc installed. Because lxc profiles contain some syntax incompatible with aa tools.

---

