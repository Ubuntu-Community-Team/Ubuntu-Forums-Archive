---
title: "Known dangerous repos?"
date: 2011-05-11
forum: Security
---

### Post by Isaacgallegos on 2011-05-11
Is there a list of known dangerous software sources?

Sure, the safest thing to do is not stray outside the the ubuntu repositories, but, as anyone who has completely replaced windows with Ubuntu knows, finding everything you need won't always be found there. Especially when it comes to getting the latest version of something.

Has there ever been a comprehensive list of repos that have software that could be malicious? Like a banned list of debs?

---

### Post by Paddy Landau on 2011-05-11
It would be impossible to compile a comprehensive list, because the owner of any scam repo would regularly change his site.

Instead, do two things:

[LIST=1]
[*]Install Web of Trust (WOT) on your Firefox or Chromium. Although it is not perfect, it will flag many dodgy sites.
[*]Research. If you find a repo, find out what comments other people have to say about it.
[/LIST]

---

### Post by rookcifer on 2011-05-11
If you need a newer version of something that's not in the repos, just install the official PPA for that particular software.  PPA's don't go through the checks that the regular repos do, but if you do a little research, you can find PPA's that lots of people use and are considered trustworthy.

---

### Post by Irihapeti on 2011-05-12
I sometimes install packages from outside repos, but they are always from the developer's website.

If I've got into trouble by doing this, I've not been aware of it.



I've often wondered how a new developer is supposed to get his/her software used if we virtually restrict people to the official repos. Isn't there an involved process to get your offering in those?

---

### Post by Paddy Landau on 2011-05-12
> **Irihapeti said:**
> Isn't there an involved process to get your offering in those?
It is involved, and even more so to get a new version ported to an already-released Ubuntu version.

---

### Post by rookcifer on 2011-05-12
> **Irihapeti said:**
> I've often wondered how a new developer is supposed to get his/her software used if we virtually restrict people to the official repos. Isn't there an involved process to get your offering in those?

Yes, you have two choices:

1) Submit your package to Debian and let them eventually put it in their stable repo (it automatically goes to Ubuntu since Ubuntu is forked from Debian.)

2) Submit it directly to Ubuntu's MOTU team, which bypasses Debian but still requires that people check and vouch for your package.

The Ubuntu [Wiki page]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages") says step one is faster, plus it affords you the benefit of having your package available to both Debian and ubuntu users.  I think I am about to go through the process because I have a python package I wrote that I wouldn't mind getting pushed to the main repos.

---

