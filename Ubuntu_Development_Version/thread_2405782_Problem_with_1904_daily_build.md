---
title: "Problem with 1904 daily build"
date: 2018-11-11
forum: Ubuntu Development Version
---

### Post by brisch on 2018-11-11
Here is what was posted:
/lib/recovery-mode/recovery-menu:
line 80: /etcc/default/rcs:
no such file or directory
fsck from util-linux 2.32
/dev/sda5 is mounted
e2fsck: cannot continue, aborting
fsckd-cancel-msg: Press ctrl+c
system locked up and so further ability to control it.
Note: 
This problem is the same for 1810 release and 1904 daily build
back to debian

---

### Post by VMC on 2018-11-11
Not sure if you want help, since you stated 'back to debian'.

It would help us if you stated how you installed ubuntu. On a partition, virtual, etc.
What were the error messages? At what point did  it fail. Did you check 'journalctl' ?

---

### Post by Doug S on 2018-11-11
Yes, the daily build has been broken for a week now.
For whatever reason, the Ubuntu kernel developers don't seem to notice until someone (often me, which I have not done yet) goes on IRC and mentions it.
As a side note, there doesn't seem to have been any activity on the kernel [IRC channel]("https://irclogs.ubuntu.com/") for a long time (the channel disappears from the list if it isn't used for awhile). See also the [kernel 4.20-rc series ]("https://ubuntuforums.org/showthread.php?t=2405365")thread.

---

### Post by brisch on 2018-11-11
Ok here is a bit more info:
I did a normal install on logical in a stand alone disk drive.
I did a complete install of 1810 from the release.
It started normally and worked the first time,
the second time fsck was invoked and the above problem showed up.
The same exact situation for the daily of 1904.
I used the option for testing on the grub menu with the same problems.
I put a lot of time chasing what I thought were my problems
and found out there is a build problem.
Further : this problem has been around since 1710 and shows up and
destroys my work.
My statement back to debian is I don't have time to loose work.
Find a bigger club than what I have and use it as needed.

---

### Post by brisch on 2018-11-11
Let me blow off a bit of steam.
I have been using linux for about 15 years now.
The only thing I will say about Windows is I keep a
release to use programs that are not available on linux.
As an example Mailwasher,  try to find that on linux
I have been on the development threads for years.
It used to be there was an active group that did debugging of 
a pre release to alert the developers of problems.
Do you see that now?
They throw it over the wall and run.

---

### Post by Doug S on 2018-11-11
Hmmm... I thought you were referring to the mainline daily kernel build, but it seems you are talking about something else. Anyway, I went on IRC and notified the kernel team.

---

### Post by brisch on 2018-11-11
Grumpy old geezer here
I started over  doing a fresh copy of the iso, another disk drive and a complete reinstall of 1810.
When it was installed I used apt-get install to include items that I normally use.
After each install I rebooted.
Surprise,  after several installs
system crashed on startup reporting Started LSB:  automatic crash report generation
end of story. No further progress

---

