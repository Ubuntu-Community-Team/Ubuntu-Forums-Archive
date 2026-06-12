---
title: "grumpy &quot;release&quot; date?"
date: 2005-07-13
forum: The Cafe
---

### Post by windrider on 2005-07-13
Hi, just like to know when grumpy repositories would be open? did a search in forums and wiki but couldnt find info on its "release" date.

---

### Post by primeirocrime on 2005-07-13
never. grumpy is just the name for the whatever working version is being developed.

so maybe you are looking for breezy and they are already open.

just be careful.

---

### Post by windrider on 2005-07-13
i'm getting confused here...

i always thought, in debian terms, ubuntu is something like this:

now hoary is "stable"
breezy is "testing"
and theres no "unstable" yet because the devs havent got around to making it yet, but "grumpy" is going to be the equivalent of "unstable"

so essentially, when i point my apt sources to grumpy, i should be running "unstable" of ubuntu, which will never get "released", that means new versions of apps will always get added in "grumpy" cos its never ever "released", thus never freezed.

what youre saying is that there is no "grumpy", but rather "grumpy" is the current version being developed (breezy), and i would have to always change my apt sources to the current development version whenever a new ubuntu gets "released"? (eg. after breezy is released, a new development version with say the name of XXX comes out, and to use "grumpy" i have to rename my apt sources to XXX?)

---

### Post by somuchfortheafter on 2005-07-13
ding ding ding we have a winner folks :)

---

### Post by UbuWu on 2005-07-13
It is even more complicated: Grumpy doesn't exist yet. In the future, there will be a branch codenamed Grumpy Groundhog. It will be a permanently unstable development and testing branch, pulling the source directly out of the source version control systems of the various programs and applications that are shipped as part of Ubuntu. So it will even be more unstable than the actual development version.

---

### Post by windrider on 2005-07-13
so when "in the future" is this? is the date fixed yet?

---

### Post by poofyhairguy on 2005-07-13
[QUOTE=windrider]so when "in the future" is this? is the date fixed yet?[/QUOTE]

Probably the release after the release of Breezy. That release will be the first corporate release..many htings will change.

Could be after Breezy, I don't really know.

---

### Post by diwakergupta on 2005-10-31
Now that Breezy is out of the door, does anyone have an idea when Grumpy will be open?

---

### Post by Burgundavia on 2005-10-31
Grumpy is not a an exact sid replicate. What grumpy will be is stuff built straight out of upstream svn/cvs, on a daily basis. It is not expected that a user would run a complete system of this, just the parts that they are interested in. This is mostly for upstream developers to have an easy way to run and test the latest releases, but still run a stable OS.

The next version of Ubuntu is due to out in April 2006 and the repos for it have already opened. It is called Dapper Drake. Rather than with Debian, which has unstable, testing and stable, Ubuntu only has stable and development. After 6 months, the development version is frozen and called stable. Shortly thereafter, the next development version of Ubuntu is opened. The development version is the version that syncs to Sid.

Corey

---

