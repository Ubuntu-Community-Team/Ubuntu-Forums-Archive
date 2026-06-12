---
title: "Correctly upgrading from python 3.6.9 to 3.7"
date: 2019-12-15
forum: Server Platforms
---

### Post by DigiAngel on 2019-12-15
Is there a good method to do this?  Just an apt install 3.7 or something different?  Thank you.

---

### Post by oldfred on 2019-12-15
It used to be that you never touches python as you destroyed system.
Key parts of Ubuntu run using the current version of python. And one of those used to be launching network. So once broken, you could not fix. Usually reinstall and restore from backups or maybe a chroot.

You can install additional versions of python, but why?
Just be sure not to change any default settings.
And then when you run python you have to be explicit on which version you are running.
Running python3 must always be default.

---

### Post by DigiAngel on 2019-12-15
Splunk will be requiring 3.7 at the end of January.

---

### Post by oldfred on 2019-12-15
I only see support for Python 3.7.
It does say it wants Python3 and that is because python2 reaches EoL in Jan, 2020.

---

