---
title: "Howto: Install EMACS without X Windows"
date: 2006-04-25
forum: Server Platforms
---

### Post by charlie. on 2006-04-25
Is it possible to install EMACS without installing X-Windows? I have always thought that EMACS is able to run in pure text mode, but...

apt-get install emacs21

... shows a message saying that it will install a whole load of X-Windows components. I don't want those on my squeaky-clean server.

Thanks for any help.

---

### Post by kaamos on 2006-04-25
```
sudo apt-get install emacs21-nox
```
:)

---

### Post by charlie. on 2006-04-25
Thanks kaamos. I tried...

apt-get install emacs21-nox

... and was presented with: "Package emacs21-nox is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source." along with a suggestion of the 'emacs21' package which replaces it and "E: Package emacs21-nox has no installation candidate"

From previous experience, I expect this means that I am trying to install a universe or multiverse package and I don't have those repositories enabled. I used pico to edit /etc/apt/sources.list and appended " universe multiverse" to both the lines that listed my mirror (za.archive.ubuntu.com) and tried again... same result!

I suspect that an 'apt-get update' is in order. For some reason, between running install a second time and update, the DNS record for that host has changed to 1.0.0.0 on whatever DNS our ISP uses - a fact confirmed on other machines too, with ping. Argh!

---

