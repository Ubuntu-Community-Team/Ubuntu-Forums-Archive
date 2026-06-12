---
title: "broke my wine"
date: 2010-01-26
forum: Wine
---

### Post by pdk902 on 2010-01-26
hi all. i installed wine via synaptic and then tried to install utorrent. during the installation of utorrent i changed the directory to point to my /etc instead of c:\program files\. obviously the install failed. whenever i try to reinstall utorrent, it also fails. i have tried uninstalling wine (including the hidden .wine folder in home folder) but i'm still unsuccessful. did i fubar my linux?

ubuntu 9.10
regular wine not wine 1.2
utorrent 1.8.5 (i think)

---

### Post by psavva on 2010-01-26
> **pdk902 said:**
> hi all. i installed wine via synaptic and then tried to install utorrent. during the installation of utorrent i changed the directory to point to my /etc instead of c:\program files\. obviously the install failed. whenever i try to reinstall utorrent, it also fails. i have tried uninstalling wine (including the hidden .wine folder in home folder) but i'm still unsuccessful. did i fubar my linux?

ubuntu 9.10
regular wine not wine 1.2
utorrent 1.8.5 (i think)

Try purging wine.  The purge command will remove all associated files with wine, and hopefully fixing your problem :D

```
sudo apt-get purge wine
sudo apt-get install wine
```

---

### Post by arubislander on 2010-01-26
> **psavva said:**
> Try purging wine.  The purge command will remove all associated files with wine, and hopefully fixing your problem :D

```
sudo apt-get purge wine
sudo apt-get install wine
```

And if that doesn't help try
```
cd ~
rm -Rf .wine
```

The above will remove the .wine directory in your home directory along with all its configurations and the "C:\"  drive it thinks it has. That should be enough to get wine thinking you're running it for the very first time.

---

### Post by ajgreeny on 2010-01-26
You might also want to check for anything related to utorrent in /etc, where you asked for it to go, just in case.  I think it is unlikely, but worth a check.

---

### Post by pdk902 on 2010-01-26
yep, did those. didnt work.
am i supposed to reboot after each uninstall of wine? because i have.

any further suggestions?

/etc/utorrent did not exist, and wasnt hidden either
home folder/.wine was removed
also did the purge.

---

### Post by arubislander on 2010-01-27
You do not need to uninstall wine at all. Just deleting the .wine folder in your home folder should be enough.

---

### Post by pdk902 on 2010-01-28
in case deleting .wine was insufficient, are there alternative solutions or issues that still need resolving? cause right now i'm considering backing up my data and doing a reinstall.

---

### Post by dino99 on 2010-01-28
there is an ubuntu app for cleaning system in synaptic: bleachbit. It saved me several times when i was having crashs or no sound or video problems: use it : app --> system --> bleachbit (as root)

Take time to understand what you ask it to do as he can wipe your data.

---

