---
title: "untrusted PPA"
date: 2010-12-30
forum: Security
---

### Post by arapaho on 2010-12-30
I want to add repository for Clementine and there is information: "You can update your system with unsupported packages from this _untrusted PPA_"
I thought PPA and keys should make adding software safe. What 'untrusted' means in this case: untrusted = security issue
or untrusted = secure but my crash?
[https://launchpad.net/~me-davidsansome/+archive/clementine](https://launchpad.net/~me-davidsansome/+archive/clementine)

Does anyone from Ubuntu team check in terms of security what is added to PPA?

---

### Post by cariboo on 2010-12-30
How did you add the ppa?  If you added ppa:riccetn/clementine to Software Sources, it should automagically download the key.

You can add the Key manually by going to [https://launchpad.net/~riccetn/+archive/clementine](https://launchpad.net/~riccetn/+archive/clementine), then clicking the Technical details about this PPA link, then clicking the Signing Key link. next click /D7BFC706 link. this will bring up public key block, copy the whole thing and paste it into a text document and save it with a name you'll remember.

The open System->Administration->Software sources, click the Authentication tab. next click the import key file button, and navigate to the key file you just saved and click open.

You should now be able to reload software sources without an error.

---

### Post by arapaho on 2010-12-30
Thank you for explaining this, although I had already known it. I was just curious why this repository is described as untrusted.

---

### Post by cariboo on 2010-12-30
It depends on how you add   the repository if you use apt-add-repository the key gets downloaded, if you just edit the sources.list you have to add the key manually.

---

