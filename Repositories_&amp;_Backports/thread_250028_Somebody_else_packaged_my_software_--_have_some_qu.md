---
title: "Somebody else packaged my software -- have some questions"
date: 2006-09-03
forum: Repositories &amp; Backports
---

### Post by neilp85 on 2006-09-03
I've been working on Brutal Chess, an 3D chess game inspired by Battle Chess, with a couple friends for about a year now. The game is in a playable state with a builtin AI but it is still in the early stages of development. Recently I've noticed that packages have been built and placed in repos for several Linux distros including the upcoming Edgy Eft release. We had planned on providing these packages further down the road but it looks like other people are beating us to that.

Anyway, my first question is about tracking the downloads. Currently we solely rely on download tracking through sourceforge since that was the only place our game was available. Now that it's in other places these only provide us with partial statistics. Is there a way to query the repos or some  site we could visit to get download stats? It would be nice to be able to combine those stats with the ones on sourceforge.

My other question is about making any updates available in the repos. As I said earlier, the game is still pretty immature so there will definately be updates, hopefully at a much more frequent rate than in the past. The problem before was that we dove right in without thinking things through so the code has had to go through a couple major rewrites. Now things are getting on track so we should be able to follow the 'release early, release often' mantra of open source software.

Back to the question, how do we go about putting our updates in repos? Is it a simple matter of just providing a repository maintainer with an updated debian package? Also, can we get our game in the Dapper repos since it's already in the ones for Edgy?

---

### Post by mssever on 2006-09-03
If you look at the package properties in Synaptic, you'll see the maintainer listed on the common tab. You need to contact that person and work out the details with hm/her.

---

### Post by az on 2006-09-03
> **neilp85 said:**
> 
Anyway, my first question is about tracking the downloads. Currently we solely rely on download tracking through sourceforge since that was the only place our game was available. Now that it's in other places these only provide us with partial statistics. Is there a way to query the repos or some  site we could visit to get download stats? It would be nice to be able to combine those stats with the ones on sourceforge.


I wonder if launchpad can do that?  Did you consider using launchpad for the development of your project?

> **neilp85 said:**
> 

Back to the question, how do we go about putting our updates in repos? Is it a simple matter of just providing a repository maintainer with an updated debian package? Also, can we get our game in the Dapper repos since it's already in the ones for Edgy?

Again, I wonder if doing things from launchpad can make things happen.

---

### Post by mssever on 2006-09-03
> **azz said:**
> I wonder if launchpad can do that?  Did you consider using launchpad for the development of your project?

Again, I wonder if doing things from launchpad can make things happen.

Isn't launchpad Ubuntu-specific? They're wanting packages for a number of distros.. They're also producing Win and Mac versions.

---

### Post by az on 2006-09-04
> **mssever said:**
> Isn't launchpad Ubuntu-specific? 

No, not at all.

---

### Post by neilp85 on 2006-09-04
> **azz said:**
> Did you consider using launchpad for the development of your project?

Only recently have I heard of Launchpad so I'm not familiar with it at all. Besides, I don't see the benefits of moving from sourceforge to launchpad. Wouldn't we be in the same boat as before? All we want is to know where we can get the number of downloads for our package. Once we have that it's pretty simple to combine and store the data from the different sites ourselves.

---

