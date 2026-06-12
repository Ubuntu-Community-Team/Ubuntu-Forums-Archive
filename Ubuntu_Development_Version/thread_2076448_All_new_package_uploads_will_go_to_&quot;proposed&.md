---
title: "All new package uploads will go to &quot;proposed&quot; first for Raring"
date: 2012-10-26
forum: Ubuntu Development Version
---

### Post by JMB74 on 2012-10-26
As per:

[https://lists.ubuntu.com/archives/ubuntu-devel/2012-October/036043.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-October/036043.html)

> I'm still frantically putting the bits together for this, but it's now far enough along that I feel comfortable saying we're going to be doing it for Raring, so:  

In the continuing cause of trying to make the development series more usable at all times, not just around milestones, I'm rearranging the way our uploads are processed.  For Raring, all uploads will go to raring-proposed, and a modified instance of "britney" (the software that handles migration from Debian unstable to testing) will copy them to raring when they've been built everywhere and do not reduce the count of installable packages in the archive.  

The intent of this is to come as close as possible to eliminating transient uninstallability problems in the development release.  We probably won't get all the way there.  It will still be possible for uninstallability to be introduced by copies not all happening in a single publisher run, transient uninstallability in -proposed will still affect package builds, and it won't catch all cases where sets of packages that used to be simultaneously installable stop being so (the general case of this is NP-complete anyway).  Even with these limitations, though, it should make things a lot better.and

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2012-October/000989.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2012-October/000989.html)

> As I described in [https://lists.ubuntu.com/archives/ubuntu-devel/2012-October/036043.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-October/036043.html), all uploads to raring will now be automatically redirected to raring-proposed by default.  

They will be automatically copied to raring once they pass various tests such as being no less installable than the previous version, and soon I hope to take autopkgtest results into consideration as well. 

Attempts to copy ("sync") directly into raring will be refused. syncpackage's default will be changed in the next ubuntu-dev-tools upload, but in the meantime please use 'syncpackage -r raring-proposed'. 

This was one of the last blockers to opening raring for general development, so we should be able to get moving on this fairly soon.  Cheers,

---

### Post by dino99 on 2012-10-26
hey good decision, at least something clever: will have less partial installation issues/broken packages  and less useless reports.

---

### Post by jppr on 2012-10-26
Did Toolchain update out yesterday, or if that's gone past me when I have not noticed any change in the system ... I'm using Proposed Updates

---

### Post by dino99 on 2012-10-26
> **jppr said:**
> Did Toolchain update out yesterday, or if that's gone past me when I have not noticed any change in the system ... I'm using Proposed Updates

as the title says : "will go"
UDS is still not closed, so RR cycle still has not started yet (only got a few updates about python)

---

### Post by pressureman on 2012-10-26
This sounds suspiciously like Debian's unstable -> testing -> stable flow.

I always wondered when Ubuntu would implement something like that.

---

### Post by zika on 2012-10-26
So, if I've got it right, we should not use raring-proposed because there will be completely fresh stuff there and once it ripened it will be moved into proper other sections... Right?
If raring-proposed would be left open that is invitation to breakege² ... ;) ?

---

### Post by dino99 on 2012-10-26
> **zika said:**
> So, if I've got it right, we should not use raring-proposed because there will be completely fresh stuff there and once it ripened it will be moved into proper other sections... Right?
If raring-proposed would be left open that is invitation to breakege² ... ;) ?

yes you're right, but if you're a pure tester and cant be satisfied without your daily breakage, then continue with raring-proposed activated  :P

---

### Post by JMB74 on 2012-10-26
Well, I think the idea is that testers will get things broken only when there is a good reason or benefit.

i.e. not just because someone carelessly messed up with a new package version. That sort of things wastes testers and developers time to no end.

---

### Post by zika on 2012-10-26
> **dino99 said:**
> yes you're right, but if you're a pure tester and cant be satisfied without your daily breakage, then continue with raring-proposed activated  :PYes, now You're right... :P
> **JMB74 said:**
> Well, I think the idea is that testers will get things broken only when there is a good reason or benefit.

i.e. not just because someone carelessly messed up with a new package  version. That sort of things wastes testers and developers time to no  end.Tester do their own breakages but developers do that in a more clandestine way... ;)

---

### Post by jbicha on 2012-10-26
> **zika said:**
> So, if I've got it right, we should not use raring-proposed because there will be completely fresh stuff there and once it ripened it will be moved into proper other sections... Right?
If raring-proposed would be left open that is invitation to breakege² ... ;) ?

Right, we strongly discourage people from running -proposed on a development release; packages will automatically migrate to the regular archives when they're ready.

After release, -proposed is for testing SRUs and we want people to use -proposed and help out with that testing.

---

### Post by mc4man on 2012-10-26
> **jbicha said:**
> Right, we strongly discourage people from running -proposed on a development release; packages will automatically migrate to the regular archives when they're ready.
That may be good if the 'inhouse' testing of these proposed packages is fairly complete, certainly at times in 12.10 didn't always seem to be the case
On a somewhat minor case/example will be curious to see what happens when you upload nautilus-3.6.1, as it stands now it will (re)break some previously fixed focus issues in Unity
> **jbicha said:**
> 
After release, -proposed is for testing SRUs and we want people to use -proposed and help out with that testing.
That's what many here should be doing now

---

### Post by zika on 2012-10-26
> **mc4man said:**
> That's what many here should be doing nowPoint taken. We embrace testing-version too soon and do not participate in that part of cycle...
I'm sorry to admit that we've been talking about that at least previous two times, but... No excuses, from me at least...

---

### Post by wheeze on 2012-10-26
I've got proposed enabled, and I'll keep it that way until it blows my system away :lol:

---

### Post by jbicha on 2012-10-26
> **mc4man said:**
> That may be good if the 'inhouse' testing of these proposed packages is fairly complete, certainly at times in 12.10 didn't always seem to be the case
On a somewhat minor case/example will be curious to see what happens when you upload nautilus-3.6.1, as it stands now it will (re)break some previously fixed focus issues in Unity

But because the migration from proposed is automatic and fast (it may be a 1 hour delay, but it depends on how long it takes all architectures to build), reporting a bug in -proposed won't stop the migration.

I do plan to upload Nautilus 3.6.1 when the archives open. Have you filed those bugs yet or are you going to wait for it to actually land first?

---

### Post by grahammechanical on 2012-10-26
Let me see if I understand this correctly. The concern is that the packages build correctly and not that the package contains bugs that will break the install once they are integrated?

OK. That's why we are here. That's why you need us.

Regards.

---

### Post by jbicha on 2012-10-26
Yes, -proposed for the development cycle is only to fix the temporary uninstallability problem, where packages haven't built on all architectures. In the future, failing to pass automated tests can also block the automated migration from -proposed. More details in Colin's [email]("https://lists.ubuntu.com/archives/ubuntu-devel/2012-October/036043.html").

So if you want to fix problems before they hit the development release, it sounds like learning how to write automated tests would be useful.

---

### Post by zika on 2012-10-26
> **wheeze said:**
> I've got proposed enabled, and I'll keep it that way until it blows my system away :lol:Away or anyway... ;)

---

### Post by mc4man on 2012-10-26
> **jbicha said:**
> But because the migration from proposed is automatic and fast (it may be a 1 hour delay, but it depends on how long it takes all architectures to build), reporting a bug in -proposed won't stop the migration.

I do plan to upload Nautilus 3.6.1 when the archives open. Have you filed those bugs yet or are you going to wait for it to actually land first?
No, not yet, was waiting for it to show in repo. It came up the other night when I was testing some builds by Dmitry to fix the segfault in nautilus-3.6.1 caused by [http://git.gnome.org/browse/nautilus/commit/?id=629c9bc27a](http://git.gnome.org/browse/nautilus/commit/?id=629c9bc27a)
(I thought he CC'ed you on the issue & progression of fixes?

So the final fix was to revert 21_correct_timestamp_use_fix_focus_issue.patch
This causes no issue in GS, but brings back in Unity
(there was a small gtk patch that fixed All focus issues inc. nautilus but it was rejected in favor of the 21 patch

So here, for the moment have applied a gtk fix for using 3.6.1 & 3.7.1 in a unity session

(3.7.1 has a nice fix on recursive searching, would be something to consider adding to 3.6.1 if that's the one used in 13.04, have tested just applying the 3 related commits to the gnome3 ppa source with no apparent issue yet.

---

### Post by dino99 on 2012-10-26
> **jbicha said:**
> But because the migration from proposed is automatic and fast (it may be a 1 hour delay, but it depends on how long it takes all architectures to build), reporting a bug in -proposed won't stop the migration. 

im wondering if "proposed" will be used to:
- wait for all the dependencies been uploaded before migration of the main package

---

### Post by ventrical on 2012-10-26
I have one PC commited to just 'proposed' and ignoring all other quantal security updates repositories. I just want to see what happens.   I did a fresh install from the Oct. 14th RC and it has not  hiccupped  once yet. Currently downloading some upgrades...

---

