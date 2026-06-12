---
title: "FF updates"
date: 2009-11-10
forum: Security
---

### Post by P.KO on 2009-11-10
Hi,

I'm a little disappointed to the fact, that FF 3.5.5 were officially released 5th of November and still at writing moment 10th of November is not offered through standard updates.

If security is at measures at Ubuntu a 5 days delay is not acceptable on a standard component. Normally OSS is proudly announcing that errors get fixed much faster than in other environments. 

So please consider changing how you handle this.

---

### Post by cdenley on 2009-11-10
What security fixes are you concerned about? Were they not fixed with the last security update?
[http://www.ubuntu.com/usn/USN-853-1](http://www.ubuntu.com/usn/USN-853-1)
Ubuntu is not windows. Security fixes are backported to the releases already in the repos. They don't need to risk introducing new bugs, potentially creating new vulnerabilities, by upgrading packages after ubuntu's release.

The way they "handle this" is more secure and stable than what you seem to be suggesting.

---

### Post by P.KO on 2009-11-10
Hi,

FF 3.5.5 is only a bugfix version and as such should not introduce new features.

But I'm not convinced that [Fixed in 3.5.5]("https://bugzilla.mozilla.org/buglist.cgi?quicksearch=ALL%20status1.9.1%3A.5-fixed") is released to Ubuntu.

Anyhow I have not observed that Ubuntu didn't follow the versions from FF earlier. We do not speak about 3.6 or even 3.7.

---

### Post by witeshark17 on 2009-11-10
> **P.KO said:**
> Hi,

FF 3.5.5 is only a bugfix version and as such should not introduce new features.

But I'm not convinced that [Fixed in 3.5.5]("https://bugzilla.mozilla.org/buglist.cgi?quicksearch=ALL%20status1.9.1%3A.5-fixed") is released to Ubuntu.

Anyhow I have not observed that Ubuntu didn't follow the versions from FF earlier. We do not speak about 3.6 or even 3.7. FF 3.5.5 is out for Ubuntu; I have it.

---

### Post by wojox on 2009-11-10
Firefox 3.5.4 is the latest in the repos

If you want a newer version now you'll need to get it yourself.

---

### Post by snowpine on 2009-11-10
Arch!

---

### Post by cdenley on 2009-11-10
> **P.KO said:**
> Hi,

FF 3.5.5 is only a bugfix version and as such should not introduce new features.

But I'm not convinced that [Fixed in 3.5.5]("https://bugzilla.mozilla.org/buglist.cgi?quicksearch=ALL%20status1.9.1%3A.5-fixed") is released to Ubuntu.

Anyhow I have not observed that Ubuntu didn't follow the versions from FF earlier. We do not speak about 3.6 or even 3.7.

Ubuntu does not upgrade packages for an already-released repository. They backport patches, as I already said. Any critical bug fixes introduced in 3.5.5 should also be fixed in any package currently in the repository. If you feel there is a bug which hasn't been patched, file a bug report with ubuntu.
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
[http://changelogs.ubuntu.com/changelogs/pool/main/f/firefox-3.5/firefox-3.5_3.5.4+nobinonly-0ubuntu0.9.10.1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/f/firefox-3.5/firefox-3.5_3.5.4+nobinonly-0ubuntu0.9.10.1/changelog)

---

### Post by witeshark17 on 2009-11-10
I guess what I have applies to those using Ubuntuzilla.

---

### Post by P.KO on 2009-11-11
Hi,

Well despite I got bashed earlier in this thread, by some excuses, well now they released FF 3.5.5 under important security updates.

And I still find that the release is too late! It shouldn't take more than 1 - 2 days to have this fixed.

---

### Post by sarloth on 2009-11-11
> **P.KO said:**
> Hi,

Well despite I got bashed earlier in this thread, by some excuses, well now they released FF 3.5.5 under important security updates.

And I still find that the release is too late! It shouldn't take more than 1 - 2 days to have this fixed.

You didn't get bashed, you got corrected.

What is happening is when Mozilla releases version 3.5.5 with security updates this is noted by Ubuntu developers. When Ubuntu developers see this they take the security updates and apply them to the most recent version of Firefox in the Ubuntu repositories, and release and update for that.

In other words, the fixes in 3.5.5 are now in whatever Version ubuntu is using. (Which is still 3.0.15 unless you are using Shiretoko 3.5.4) The point is the updates are there, they just didn't change the version number.

---

### Post by cdenley on 2009-11-11
They actually did bump the version number. However, all the fixes they list with this new version (3.5.5+nobinonly-0ubuntu0.9.10.1) are an identical copy of the fixes for the last security update for firefox in ubuntu (3.5.4+nobinonly-0ubuntu0.9.10.1). If you compare the security notices, the original which you see I already linked to, the security fixes introduced with firefox 3.5.5 were already backported to all firefox versions still supported by ubuntu. In fact, the bugs were patched for ubuntu before 3.5.5 was even released!

[http://www.ubuntu.com/usn/USN-853-1](http://www.ubuntu.com/usn/USN-853-1)
[http://www.ubuntu.com/usn/USN-853-2](http://www.ubuntu.com/usn/USN-853-2)

---

### Post by witeshark17 on 2009-11-11
> **cdenley said:**
> They actually did bump the version number. However, all the fixes they list with this new version (3.5.5+nobinonly-0ubuntu0.9.10.1) are an identical copy of the fixes for the last security update for firefox in ubuntu (3.5.4+nobinonly-0ubuntu0.9.10.1). If you compare the security notices, the original which you see I already linked to, the security fixes introduced with firefox 3.5.5 were already backported to all firefox versions still supported by ubuntu. In fact, the bugs were patched for ubuntu before 3.5.5 was even released!

[http://www.ubuntu.com/usn/USN-853-1](http://www.ubuntu.com/usn/USN-853-1)
[http://www.ubuntu.com/usn/USN-853-2](http://www.ubuntu.com/usn/USN-853-2) Very cool; thanks for the heads up!

---

