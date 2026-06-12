---
title: "howto create your own repository? going crazy"
date: 2005-08-07
forum: Repositories &amp; Backports
---

### Post by lateo on 2005-08-07
hi, need help on this.
i wanna create an online repository, with my home-made packages or some non-free apps in.
my webhost gives me an anonymous ftp, so that's where i wanna upload all stuff.

i've already looked at
[http://ubuntuforums.org/showthread.php?t=46663](http://ubuntuforums.org/showthread.php?t=46663) (not interesting for what i want)
[http://www.ubuntuforums.org/showthread.php?t=7455&page=2&pp=10&highlight=local+repository](http://www.ubuntuforums.org/showthread.php?t=7455&page=2&pp=10&highlight=local+repository) (same, not interesting)
[http://www.debian.org/doc/manuals/repository-howto/repository-howto.html](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html) (good but lack of lots of things)
[http://familiasanchez.net/~roberto/?page=debrepository](http://familiasanchez.net/~roberto/?page=debrepository) (better explained but not enough yet, & i dont need apt-ftparchive or so, a manual update is all i need)
(few others...)
so don't tell me to have a look at it.

i've tested lots of things in sources.list and put Packages.gz and Realease file quite everywhere in the tree (apt-get update gives me an error "not found" for Packages.gz, even if the right path is shown just before the error msg ?!!).
tested trivial and automatic repository, got none workin'.

a trivial repository as explained in the debian howto is good as i won't upload lots of packages.
could anybody give a complete example?
- needed files for ubuntu
- a working ftp file tree and so may be good(?).

have to stop testing at the time or i may crush keyboard and screen. help needed before i go crazy.

---

### Post by Abhi Kalyan on 2007-02-28
Is it possible to have a Repository on a DVD, Is it trus that if we burn the necessary .Deb files to a CD and if it is added as a repository than it can be added in the sourceslist?

---

### Post by mlind on 2007-02-28
I've been using reprepro to manage repository. You might be interested in falcon too [https://launchpad.net/falcon](https://launchpad.net/falcon)

---

