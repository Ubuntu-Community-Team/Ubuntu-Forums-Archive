---
title: "Is apt-secure appropriately secure ?"
date: 2008-10-21
forum: Security
---

### Post by PACSFerret on 2008-10-21
Given comments from [Kaspersky]("http://www.cio.com/article/455619/Mac_Linux_BSD_Open_for_Attack_Kaspersky") - which you may agree with or not (although Kaspersky does carry a lot of cred), is apt-secure secure enough?  And indeed, does apt-secure actually kick in for auto-updates?

---

### Post by cdenley on 2008-10-21
I think the article makes this assumption.
> 
Users will always want to run whatever they want, whenever they want, regardless of security concerns.

Of course if users install software from untrusted sources, they are vulnerable to malware. If users stick to the ubuntu software repositories, which use gpg signatures to verify authenticity, they aren't vulnerable. The only thing you need to worry about is if someone manages to spoof your update server, hold back a specific security update, then exploit the vulnerability which would have been fixed by the update. This can be prevented (or at least detected) by adding SSL encryption to the repos.

---

### Post by noerrorsfound on 2008-10-21
> **cdenley said:**
> If users stick to the ubuntu software repositories, which use gpg signatures to verify authenticity, they aren't vulnerable.
Most people don't, since the repositories don't have everything and sometimes they're out of date.

---

### Post by hyper_ch on 2008-10-22
> **noerrorsfound said:**
> Most people don't, since the repositories don't have everything and sometimes they're out of date.

In that case they (a) first have to know how to add different repos (b) find different repos (c) install from those different repos and (d) those different repos have to be unsecure

---

### Post by cdenley on 2008-10-22
> **noerrorsfound said:**
> Most people don't, since the repositories don't have everything and sometimes they're out of date.

I can't speak for most people, but the only software I install from outside the repos is Zimbra. You can only do so much to protect a user from himself. What would "most people" need to install which isn't in the repos?

---

### Post by pirattrev on 2008-10-22
I usually stick to the repos as well, although every now and then I've added one, such as for virtual box.  the problem seems to me to be at the repo end, not the user side, because, as they said, people will always do things that end up being bad and I guess as long as the repos keep up with stable updates and no rogue files get it then it'll stay secure. The secure repos in apt-secure however are most likely closely monitored by Canonical and others for defects or malcode

---

### Post by noerrorsfound on 2008-10-23
> **cdenley said:**
> What would "most people" need to install which isn't in the repos?
A little bit of word twisting there? I didn't claim there was any certain type of application that everyone/most people needed, but I'm sure most people can't rely on the repos for everything. I think games are what I frequently can't get from the repositories. Some applications like DarkRadiant or GtkRadiant, which are level editors for all Quake based or Doom 3 based games (AKA: most FPS games on Linux), have to be installed "manually" as well. One notable out-of-date package is NVIDIA's video drivers, which for me resulted in my system being broken after uninstalling those and installing using NVIDIA's own installer in an attempt to update them.

---

### Post by cdenley on 2008-10-23
> **noerrorsfound said:**
> A little bit of word twisting there? I didn't claim there was any certain type of application that everyone/most people needed, but I'm sure most people can't rely on the repos for everything. I think games are what I frequently can't get from the repositories. Some applications like DarkRadiant or GtkRadiant, which are level editors for all Quake based or Doom 3 based games (AKA: most FPS games on Linux), have to be installed "manually" as well. One notable out-of-date package is NVIDIA's video drivers, which for me resulted in my system being broken after uninstalling those and installing using NVIDIA's own installer in an attempt to update them.

I had doubts about your statement that most people would need to install software from third parties. I'm not a gamer, though, and hadn't considered that a lot of ubuntu users would install games. Of course, there is no way for ubuntu to make installing commercial software safer.

---

