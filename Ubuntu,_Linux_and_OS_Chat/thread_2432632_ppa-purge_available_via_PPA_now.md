---
title: "ppa-purge available via PPA now"
date: 2019-12-05
forum: Ubuntu, Linux and OS Chat
---

### Post by jis on 2019-12-05
Development of the [official ppa-purge]("https://launchpad.net/ppa-purge") has been dead long time. I did a lot of fixes and improvements to the ppa-purge in my own [Git branch]("https://code.launchpad.net/~jarnos/ppa-purge/+git/ppa-purge"). Thanks to Tim Lunn for helping me with Git and Launchpad. I even made a [merge proposal]("https://code.launchpad.net/~jarnos/ppa-purge/+git/ppa-purge/+merge/313001"), but it has not been approved, maybe because there are so many commits and because of my laziness to clean up commit history. Anyway, in my experience the code works, and I finally managed to release my version in a [PPA]("https://launchpad.net/~jarnos/+archive/ubuntu/ppa-purge").

You can remove more than just PPAs by the utility; you could even remove distribution such as bionic-proposed by it, but not distribution components, such as universe, separately. (You can add distribution components by add-apt-repository, but as far as I know, you can not add distributions by it. And removing by add-apt-repository does not remove/downgrade packages.)

The old ppa-purge did need aptitude at least in some cases, but my version uses apt only. The old one relies somewhat on sophisticated guesswork on package names, as some package names may vary from version to version. I find this quite rare, thought, and improved guesswork is optional via --figure-soname-bumps command-line option. Bash-completion function makes using the utility easy. And --simulate option makes it safe to try.

Feedback and ideas are welcome.

BTW I have also done [linux-purge]("https://launchpad.net/linux-purge") for removing excessive linux kernels and related packages and files.

---

### Post by gnusci on 2019-12-05
Awesome, thanks. I will test it soon!

---

