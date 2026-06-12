---
title: "Regarding 12.10 Release Candidate"
date: 2012-10-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by craig10x on 2012-10-11
where would you find the isos for it when they are posted? (link please)...

also, basically, what is the difference between the r/c and the final release next week?

when final is release, is an upgrade needed and offered through the update manager or does it just become the final on the basis of doing your daily updates?

---

### Post by pqwoerituytrueiwoq on 2012-10-11
if you install the daily you will have the final come the 18th, as long as you install the update via the update manager

---

### Post by IWantFroyo on 2012-10-11
I'm pretty sure there's no release candidate scheduled.

The difference between the beta and the final is pretty much some bug fixes.

You should get the final result just by doing daily updates.

---

### Post by cgolson84 on 2012-10-11
Is it true that there will be no RC?  If that is true I'll just go ahead and run the daily of 12.10.

---

### Post by linuxvstheworld on 2012-10-11
What feature and/or improvements did they add to Ubuntu 12.10?

---

### Post by jrog on 2012-10-11
The schedule below suggests that anyone running the Beta is now effectively running the Release Candidate; the Release Candidate is to be completed by today. However, there is no Release Candidate release listed in the final ("Notes") column, as there is for other releases. So, it looks like while we're technically at the RC, there will be no RC ISO or RC "new version available" in update-manager.

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule)

---

### Post by grahammechanical on 2012-10-11
According to Quality Assurance the milestone ISO being tested now is the Final ISO image. No Release Candidate up for testing.

[http://iso.qa.ubuntu.com/]("http://iso.qa.ubuntu.com/")

The same thing happened with Precise did it not?

Regards.

---

### Post by lemming465 on 2012-10-11
The daily CD's are at [the cdimage site]("http://cdimage.ubuntu.com"); you may be able to find nearby mirrors if you hunt for them.

If you are doing repeated testing of the ISO's, you may want to use **zsync** to update your existing ISO; that will typically download a lot less than a fresh new ISO.  E.g. ```
sudo apt-get install zsync
zsync -i old.iso http://cdimage.ubuntu.com/daily-live/20121011/quantal-desktop-amd64.iso.zsync
```
Change that to match the date & version you are playing with; I usually cut&paste the URL part from a browser window, like anyone would.

If you are just playing around with the post-beta2 status of things, simply keep running **update-manager** or *sudo apt-get update; sudo apt-get upgrade* or synaptic or whatever your favorite tool for syncing with the repositories is.  With occasional glitches when you try an update during a repository refresh or stumble over a buggy version of a package, it will eventually and more or less smoothly take you to the release version and beyond.

Upgrading to newer package versions within a given release is done with just *update-manager*.  This is true from the first alpha all the way through the final release and beyond until end-of-life.  One of the things we like about debian style package management; over in enterprise redhat land you can't reliably go from a beta to a release, there you have to reinstall completely.

Upgrading in place from a current release to a test (alpha, beta, release candidate, daily) version of the next release is done with *update-manager --devel-release*.

Upgrading in place from a current production release to the next version (or if LTS, the +4 next LTS verson) is done by *update-manager --check-dist-upgrades*

Thanks for your interest in helping test Ubuntu!

---

### Post by philinux on 2012-10-11
> **linuxvstheworld said:**
> What feature and/or improvements did they add to Ubuntu 12.10?



There are quite a few. [http://ubuntuforums.org/showthread.php?t=1973822](http://ubuntuforums.org/showthread.php?t=1973822)

---

### Post by craig10x on 2012-10-11
Great information....i installed the daily build and based on what i read here, will just need to continue to do the updates to take me to final and through the entire release cycle...if i read that right? ;)

---

### Post by lemming465 on 2012-10-11
Yes.

---

### Post by andrewfn on 2012-10-11
But one the page [iso.qa.ubuntu.com/]("http://iso.qa.ubuntu.com/")
it says:
**12.10 Release Candidate Testing: coming soon to the iso tracker...**
Which suggests that the 12.10 is identified more specifically than today's daily build.

---

### Post by sammiev on 2012-10-11
Just wait and it will be posted here. Still a few bugs to be revolved yet.

---

### Post by craig10x on 2012-10-12
Thanks guys...would they really bother with an r/c iso now when the final is only 6 days away?   Wouldn't seem very likely...

Anyway, i did download and install the daily build today and will run the updates into next week's final...and past that, of course (lol)... :)

---

