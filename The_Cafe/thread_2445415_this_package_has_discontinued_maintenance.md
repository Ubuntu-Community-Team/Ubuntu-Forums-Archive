---
title: "this package has discontinued maintenance"
date: 2020-06-13
forum: The Cafe
---

### Post by Skaperen on 2020-06-13
i have noticed that many FOSS packages have been considered discontinued because there has been no maintenance activity in some specific period of time.  i can understand this happening when the developer(s) don't have the time, anymore.  but what if the package has reached a point where there is nothing more to maintain?  what if it lacks a need for new features?  what if it lacks any need for bug fixes?  what if there are no security issues for it?  what if its developer(s) is/are just waiting for any reports to act on but none have come in since before the last X.0.0 version bump?  is it now "fully mature"?  what would that mean?

---

### Post by EuclideanCoffee on 2020-06-14
Likely there are many compatibility issues, making it difficult to maintain. For example, one may fully support GTK2 but has a core feature broken in GTK3 with no one to repair it. There have been similar issues with crossfire and the switch from python2 to python3. If there are no users left, there is little motivation to maintain something.

---

### Post by DuckHook on 2020-06-14
I think we need to descend from the rarified heights of the theoretical to the real. You are positing an app that has attained perfection. Which app would qualify as such?

Apps as central and fundamental to Linux as ssh and bash have been shown to have awful holes that went unnoticed for years. The very nature of software is such that holes will always be discovered and the environment in which they were written will always evolve to render them obsolete.

Since the definition of "unmaintained" means that no one bothers to review them anymore, how can such holes even hope to be discovered? If by sheer chance they are discovered, who will fix them?

The principle behind "maintenance" is inseparably conjoined with "responsibility". Unmaintained apps mean apps that have abandoned their responsibility for your safety, security, utility… you name it. Therefore, it would be irresponsible for distro devs to stamp such apps with their imprimatur.

---

### Post by Skaperen on 2020-06-15
an app with holes/bugs that have existed for years is a good example.  what if none have been discovered for X years, but a distribution decides that the app is unmaintaned because there has been no change activity for N years?  what if N < X?  what if the developer is still watching for reports of holes or bugs?

---

### Post by QIII on 2020-06-15
> **Skaperen said:**
> what if none have been discovered for X years

By whom?  A hacker with ill intent surely isn't going to report a discovered bug/vulnerability ... except perhaps to his other living-in-mother's-basement-nacho-eating-mountain-dew-guzzling hacker buddies.

---

### Post by Skaperen on 2020-06-15
a hacker won't.  but how does this show a package is unmaintained for N years if no one discovers it in all that time?

---

### Post by Irihapeti on 2020-06-15
What seems to happen in the real world is this, assuming that there's no security issue: there comes a point when the package won't work because it needs libraries that are no longer available.

Once that happens, all the alleged perfection is rather irrelevant.

---

### Post by Skaperen on 2020-06-15
yes, such a point in time can happen.  but not for all packages.  a typical example is a library that calls nothing else.

---

### Post by Skaperen on 2020-06-15
given such a long time before Python2's end of life, i suspect Python3 to be supported for quite many years.  most of the apps i have written in Python3 need nothing beyond what is in Python itself.  i expect those apps will be able to be run to the year 2030.  maybe even well beyond that.  some of the small ones may even be well mature, now.  if any are widely useful enough to be packaged and distributed, what happens if, after 5 years of nothing needing to be changed, someone thinks it is no longer being maintained?

---

### Post by zer010 on 2020-06-18
> **Skaperen said:**
> what happens if, after 5 years of nothing needing to be changed, someone thinks it is no longer being maintained?
Just add something trivial to it, even a comment saying you're still checking up on it. That change will update the last changed date. Its an interesting thought really.

---

### Post by Skaperen on 2020-06-18
so, a fake change.

---

### Post by zer010 on 2020-06-24
its not fake if you actually change something. it just doesn't have to be a major change. 
Comment: Still here!

---

### Post by Skaperen on 2020-06-25
or maybe bump the version.

---

