---
title: "Brackets: Dependency is not satisfiable: libgcrypt11 (&gt;=1.4.5)"
date: 2015-04-03
forum: Ubuntu Development Version
---

### Post by GreatDanton on 2015-04-03
I decided to test the latest daily build, and came around this problem (see picture). I wanted to install brackets text editor. Should I fill bug report?
I am using xubuntu 15.04 daily build (3. april. 2015) 64bit.

[ATTACH=CONFIG]261078[/ATTACH]

---

### Post by harry332 on 2015-04-04
Where did you get brackets? It is not in official repos.
Also, libgcrypt11 is not either in official repos, we are using libgcrypt20 with vivid now.
Solution: brackets should be rebuild against libgcrypt20.

---

### Post by GreatDanton on 2015-04-04
I forgot to mention I got brackets from this site: [http://brackets.io/](http://brackets.io/) . I was able to install it on previous versions (14.10, 14.04, 12.04).

---

### Post by zika on 2015-04-04
[https://launchpad.net/~webupd8team/+archive/ubuntu/brackets](https://launchpad.net/~webupd8team/+archive/ubuntu/brackets)

---

### Post by orj-gmail on 2015-04-05
sent a mail to the ppa-maintainer

---

### Post by Elfy on 2015-04-05
> **orj-gmail said:**
> sent a mail to the ppa-maintener

The OP didn't install from the PPA but from elsewhere.

---

### Post by orj-gmail on 2015-04-05
> **Elfy said:**
> The OP didn't install from the PPA but from elsewhere.

I tried to install from ppa; it wants libcrypt11.

---

### Post by zika on 2015-04-05
OK, apart from some more sophisticated ways of dealing with such stuff, You could try to install [libcrypt11]("http://snapshot.debian.org/package/libgcrypt11/1.5.4-3/#libgcrypt11_1.5.4-3") from Debian or[ libcrypt11]("https://launchpad.net/ubuntu/+source/libgcrypt11") from Ubuntu, preferably later, of course ... ;)
Be careful not to break some dependency, always use dry-run switch before committing...

---

### Post by skagedal2 on 2015-05-16
I had this dependecy problem when installing the deb form brackets.io on my Ubuntu 15.04 system. The PPA worked great:

```

sudo apt-add-repository ppa:webupd8team/brackets
sudo apt-get update
sudo apt-get install brackets

```

---

