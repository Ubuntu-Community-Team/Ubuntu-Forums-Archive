---
title: "Today's Trusty Updates included the first wave of New Files (not just existing ones)."
date: 2013-10-31
forum: Ubuntu Development Version
---

### Post by kevpan8152 on 2013-10-31
Just in case you guys and gals did NOT notice the following: Today's Trusty Updates included the first wave of New Development Files, NOT just existing Saucy Updates!

---

### Post by kevpan8152 on 2013-10-31
It even upgraded my Kernel to 3.12.0.1-generic!

---

### Post by ventrical on 2013-11-01
A big thanks to all those kernel testers .. (you kow who you are) ! :)

---

### Post by kevpan8152 on 2013-11-02
> **ventrical said:**
> A big thanks to all those kernel testers .. (you kow who you are) ! :)

Yeah, I read the other post about NVIDIA Drivers. Thankfully I have Intel Integraded Video Graphics.

---

### Post by kevpan8152 on 2013-11-02
> **kevpan8152 said:**
> Yeah, I read the other post about NVIDIA Drivers. Thankfully I have Intel Integraded Video Graphics.

I should also note that since I all ready had 3.12 RC 7 Mainline Kernel on my system, it did NOT affect my system in any way.

---

### Post by infectedorganism on 2013-11-02
Do they do a staged rollout of packages and kernels? I see 3.12 kernel available via Synaptic, but I have yet to get the update via apt-get. Ubuntu.info references Trusty, but not devel -- if that makes any difference.

---

### Post by cariboo on 2013-11-02
I got the 3.12 kernel upgrade vai synaptic a couple of days ago, mind you I'm lazy, and would rather click and icon than open a terminal and use:

```
sudp apt-get update && sudo apt-get -y dist-upgrade
```

:-)

---

### Post by zika on 2013-11-02
> **cariboo907 said:**
> I got the 3.12 kernel upgrade vai synaptic a couple of days ago, mind you I'm lazy, and would rather click and icon than open a terminal and use:

```
sudp apt-get update && sudo apt-get -y dist-upgrade
```

:-)It is very brave indeed to put &#8222;[COLOR=#ff0000]-y[/COLOR]&#8220; in dist-upgrade in testing...

---

### Post by deadflowr on 2013-11-02
> **zika said:**
> It is very brave indeed to put „-y“ in dist-upgrade in testing...

I find some people might as well put a -y in there as they don't pay attention to what's going on anyway.
Then they post about some function inexplicably disappearing out of nowhere.

---

### Post by kevpan8152 on 2013-11-02
> **cariboo907 said:**
> I got the 3.12 kernel upgrade vai synaptic a couple of days ago, mind you I'm lazy, and would rather click and icon than open a terminal and use:

```
sudp apt-get update && sudo apt-get -y dist-upgrade
```

:-)

That is the same command I used as I saw your earlier post telling Ventrical to use it! :-)

---

### Post by zika on 2013-11-02
> **deadflowr said:**
> I find some people might as well put a -y in there as they don't pay attention to what's going on anyway.
Then they post about some function inexplicably disappearing out of nowhere.Exactly... ;)
At least I've saved my soul by writing a warning (if only I had 1¢ for each)...

---

### Post by kevpan8152 on 2013-11-02
> **zika said:**
> It is very brave indeed to put „[COLOR=#ff0000]-y[/COLOR]“ in dist-upgrade in testing...

Why is that? After all this is the command that Cariboo907 (a Moderator for this Forum) told  Ventrical to use.

---

### Post by grahammechanical on 2013-11-02
> **infectedorganism said:**
> Do they do a staged rollout of packages and kernels? I see 3.12 kernel available via Synaptic, but I have yet to get the update via apt-get. Ubuntu.info references Trusty, but not devel -- if that makes any difference.

I think that it takes time for the various mirrors to get up to date. I have a trusty install with devel repositories and another install with trusty repositories and they are both still on kernel 3.11. I see that some kernel stuff (headers etc) are being held back. And then again yesterday I installed Edubuntu saucy because we do not yet have an Edubuntu trusty ISO image and then I changed repositories to trusty and the dist-upgrade brought in kernel 3.12. So, it is case of wait awhile.

It now comes to mind that there was talk of having a staged roll out of updates. I was not sure they were going to do that for development. The idea is to push an update to 10% of users and if none of them scream, then push the update to another 10% and so on. But if they get reports of regression bugs they will then hold back the update from the remaining 90% - 80% - 70% and so on until the bug is fixed.

Regards.

---

### Post by kevpan8152 on 2013-11-02
I am using the Standard U.S.A. Download Server with Sudo Apt-Get Update && Sudo Apt-Get -Y Dist-Upgrade just in case anyone is wondering what I am using.

---

