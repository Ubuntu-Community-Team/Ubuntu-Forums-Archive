---
title: "Apport dissappears when clicking Continue. No bug report"
date: 2012-11-26
forum: Ubuntu Development Version
---

### Post by philinux on 2012-11-26
Anyone else seeing this.

Pop up says a problem. Password entered. Click continue and it's gone. No bug report or any other messages. I can see .uploaded file in /var/crash

I think It might be the same in 12.10 too.

---

### Post by howefield on 2012-11-26
Yep.

I assumed it was the new reporting system talked about at UDS.

---

### Post by ventrical on 2012-11-26
This has been par for the course for the last several weeks. Bug reporting is at a very pernickity stage atm.

---

### Post by philinux on 2012-11-26
> **howefield said:**
> Yep.

I assumed it was the new reporting system talked about at UDS.

> **ventrical said:**
> This has been par for the course for the last several weeks. Bug reporting is at a very pernickity stage atm.

Any idea where the reports are going if at all.

---

### Post by howefield on 2012-11-26
If it is the error tracker, an application called Whoopsie sends the report to a Canonical server called Daisy. :)

[http://www.youtube.com/watch?v=PPQ7k0jRUE4&feature=g-all-u](http://www.youtube.com/watch?v=PPQ7k0jRUE4&feature=g-all-u)

30 minutes in.

---

### Post by ventrical on 2012-11-26
> **philinux said:**
> Any idea where the reports are going if at all.


@philinux,

I think that there is a thread on this here in the forums.  We were talking about exactly this... sort of like a deja-vu here... :)

---

### Post by ventrical on 2012-11-26
deja-vu

[http://ubuntuforums.org/showthread.php?t=2077634](http://ubuntuforums.org/showthread.php?t=2077634)

---

### Post by jbicha on 2012-11-26
I believe that was added in Ubuntu 12.04. Crash reports go to [https://errors.ubuntu.com/](https://errors.ubuntu.com/) without the need to fill out a bug report. But there's still a lot about what apport is doing that I don't understand.

Unfortunately, people that aren't using to seeing notifications of crashes got the mistaken idea that Ubuntu 12.04 LTS was less stable than 11.10.

---

### Post by philinux on 2012-11-26
> **howefield said:**
> If it is the error tracker, an application called Whoopsie sends the report to a Canonical server called Daisy. :)

[http://www.youtube.com/watch?v=PPQ7k0jRUE4&feature=g-all-u](http://www.youtube.com/watch?v=PPQ7k0jRUE4&feature=g-all-u)

30 minutes in.

> **ventrical said:**
> deja-vu

[http://ubuntuforums.org/showthread.php?t=2077634](http://ubuntuforums.org/showthread.php?t=2077634)

Gotcha.

So when does a launchpad bug report get sent?

I've manually installed activity-log-manager to get the reports sent to canonical.

---

### Post by cariboo on 2012-11-26
> **jbicha said:**
> I believe that was added in Ubuntu 12.04. Crash reports go to [https://errors.ubuntu.com/](https://errors.ubuntu.com/) without the need to fill out a bug report. But there's still a lot about what apport is doing that I don't understand.

Unfortunately, people that aren't using to seeing notifications of crashes got the mistaken idea that Ubuntu 12.04 LTS was less stable than 11.10.

I've also seen some users assume that apport is malware, because the window seems to be too ordinary. :-D

---

### Post by ventrical on 2012-11-26
> **cariboo907 said:**
> I've also seen some users assume that apport is malware, because the window seems to be too ordinary. :-D


So , again , 'no heads up' and what I do (at times) is reboot, thinking that there has been a crash, and interupting the report being sent. so, perhaps after login it continues to send the bug report?

  I am not saying this is an ineffectual way of gathering information but the 'no heads up' kind of leaves us in the dark.

---

### Post by mc4man on 2012-11-26
> **ventrical said:**
> deja-vu

[http://ubuntuforums.org/showthread.php?t=2077634](http://ubuntuforums.org/showthread.php?t=2077634)

That was something different, (apport* broken
Current behavior mentioned here in this thread
[http://ubuntuforums.org/showthread.php?t=2084222](http://ubuntuforums.org/showthread.php?t=2084222)

> **philinux said:**
> Gotcha.

So when does a launchpad bug report get sent?

I've manually installed activity-log-manager to get the reports sent to canonical.
Only when using 'ubuntu-bug <whatever>'

If one chooses they can cause crashers to open LP reports thru a config edit, never did find out if that is currently discouraged though I guess it is..
(there aren't that many crashes that I've seen to date so somewhat a moot point?

---

### Post by ventrical on 2012-11-26
@mac4man

Thanks for tracking that down.

regards..

---

### Post by philinux on 2012-11-26
I'm guessing that the number of "bug" reports could drop drastically.

---

