---
title: "Rootkit problem reporting"
date: 2010-01-21
forum: Security
---

### Post by ardchoille42 on 2010-01-21
I just performed a fresh install of Ubuntu 9.10 from a livecd that I received from Ship It. The install went well and I ran chkrootkit and rkhunter before putting the system online. The following happened:

1. Ran rkhunter, showed no problems

2. Ran chkrootkit the report included this:

[FONT="Courier New"]Searching for Suckit rootkit...	Warning: /sbin/init INFECTED[/FONT]

3. Re-ran rkhunter and it reported this regarding Suckit and /sbin/init:

[FONT="Courier New"]/sbin/init	[ OK ]
Suckit Rootkit	[ Not found ][/FONT]

the rkhunter summary included this:

[FONT="Courier New"]System checks summary
=====================

File properties checks...
    Files checked: 130
    [COLOR="Red"]Suspect files: 0[/COLOR]

Rootkit checks...
    Rootkits checked : 111
    [COLOR="Red"]Possible rootkits: 0[/COLOR][/FONT]

The red text emphasis was added by me for readability. As I said, I installed from trusted media and then installed several apps from the Ubuntu software repositories, so I don't think I have a rootkit. What I think happened is chkrootkit reported a false positive but I don't remember this happening on Jaunty or previous installations of Karmic.

Has anyone else seen this problem?

---

### Post by iponeverything on 2010-01-21
its a false positive 


[https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566](https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566)

---

### Post by ardchoille42 on 2010-01-21
> **iponeverything said:**
> its a false positive 


[https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566](https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566)

Yeah, I figured it was a false positive. Thank you very much for the bug report link.

---

### Post by cariboo on 2010-01-21
You can also use **ubuntu-bug** to report bugs, Press Alt-F2 and type:

```
ubuntu-bug <packagename>
```

In your case substitute rkhunter for <packagename>.

**Note:** This only works for Karmic and newer.

---

### Post by ardchoille42 on 2010-01-22
> **cariboo907 said:**
> You can also use **ubuntu-bug** to report bugs, Press Alt-F2 and type:

```
ubuntu-bug <packagename>
```

In your case substitute rkhunter for <packagename>.

**Note:** This only works for Karmic and newer.

Hey, I didn't know that.. very helpful. Thank you :)

---

