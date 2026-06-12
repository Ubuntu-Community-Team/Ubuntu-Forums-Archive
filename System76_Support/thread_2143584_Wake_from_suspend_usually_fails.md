---
title: "Wake from suspend usually fails"
date: 2013-05-09
forum: System76 Support
---

### Post by Dave_L on 2013-05-09
Model: System76 star3

Under 10.04, wake up from suspend works.

Under 12.04 (clean install, not upgrade), wake up from suspend usually fails. The screen is blank with a cursor in the upper left corner, and I have to power off and on again.

Any suggestions on how to diagnose this?

---

### Post by JonPaul on 2013-05-09
Check which kernel you are on. There was a problem with the 3.8 kernel that affected some laptops (mine is HP G60) which seems to have disappeared in 3.9.

I am now on raring with kernel 3.9.0-0-generic #4-Ubuntu and so far so good:P

I should have said (in case you don't know) that the terminal command uname -a gives the kernel name. 

I am fairly new with linux so i am sure others could probably give more detailed answers.

JonPaul

---

### Post by Dave_L on 2013-05-09
The kernel is 3.5.0-28-generic #48~precise1-Ubuntu SMP, which is the current one for 12.04.  Also, it's 64-bit.

---

### Post by JonPaul on 2013-05-09
Then I suspect it is almost certainly not what I suggested:o

Good luck 

JP

---

### Post by Dave_L on 2013-05-17
Any ideas?

---

### Post by isantop on 2013-05-17
12.04 has known issues with suspend. I'd recommend upgrading to 13.04.

---

### Post by Dave_L on 2013-05-17
> **isantop said:**
> 12.04 has known issues with suspend. I'd recommend upgrading to 13.04.

I just upgraded from 10.04 to 12.04.  12.04 LTS is supposed to be fully supported until 2017.

I'm not going to do a major upgrade every few months to an unstable version.

If 12.04 has known issues with suspend, why aren't they getting fixed?

---

### Post by isantop on 2013-05-20
Because it's no longer under development. It was an upstream kernel issue that was fixed in 12.10.

---

### Post by Dave_L on 2013-05-20
> **isantop said:**
> Because it's no longer under development. It was an upstream kernel issue that was fixed in 12.10.

Can you provide more details about the issue, e.g. a link to the bug report/fix?

The kernel in 12.04 is still regularly updated. The most recent update (3.5.0-30) was last week.

Doesn't LTS (long term support) include bug fixes?

---

### Post by isantop on 2013-05-20
In some cases, but in general it will only receive security fixes after it's no longer the most recent release.

---

### Post by Dave_L on 2013-05-23
> **isantop said:**
> In some cases, but in general it will only receive security fixes after it's no longer the most recent release.

I found that there is a policy for fixing bugs in the LTS: [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

Also, as per the advice [here](http://ubuntuforums.org/showthread.php?t=2147101&p=12660351#post12660351), I upgraded the kernel from 3.5.0-30 to the newest one in precise-updates, 3.8.0-21, and that seems to have fixed the issue. But I'll continue to test it for a few days to make sure.

---

