---
title: "[SOLVED] Error running apt-get update"
date: 2008-11-18
forum: Server Platforms
---

### Post by keymoo on 2008-11-18
Hi,

I'm running ubuntu server 8.04 and have just run 
```
sudo apt-get update
```and got this output
```
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com hardy-security Release
Hit http://gb.archive.ubuntu.com hardy Release.gpg
Hit http://gb.archive.ubuntu.com hardy/main Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy/restricted Translation-en_GB
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://gb.archive.ubuntu.com hardy/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy-updates Release.gpg
Ign http://gb.archive.ubuntu.com hardy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/restricted Translation-en_GB
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://gb.archive.ubuntu.com hardy Release
Hit http://gb.archive.ubuntu.com hardy-updates Release
Hit http://gb.archive.ubuntu.com hardy/main Packages
Hit http://gb.archive.ubuntu.com hardy/restricted Packages
Hit http://gb.archive.ubuntu.com hardy/main Sources
Hit http://gb.archive.ubuntu.com hardy/restricted Sources
Hit http://gb.archive.ubuntu.com hardy/universe Packages
Hit http://gb.archive.ubuntu.com hardy/universe Sources
Hit http://gb.archive.ubuntu.com hardy/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy/multiverse Sources
Hit http://gb.archive.ubuntu.com hardy-updates/main Packages
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://gb.archive.ubuntu.com hardy-updates/main Sources

```with this error

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```So, I run 

```
sudo dpkg --configure -a
```and get this output
```

dpkg: parse error, in file `/var/lib/dpkg/updates/0060' near line 9:
 duplicate value for user-defined field `171008'

Hit http://gb.archive.ubuntu.com hardy-updates/restricted Sources
```Anyone know how to fix?

Thanks

---

### Post by mrtomservo on 2008-11-18
What does 

```
sudo apt-get check
```

tell you?

---

### Post by keymoo on 2008-11-18
> **mrtomservo said:**
> What does 

```
sudo apt-get check
```tell you?
I get:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

---

### Post by cariboo on 2008-11-18
Have you tried :

```
sudo apt-get install -f
```

Jim

---

### Post by mrtomservo on 2008-11-18
Did a little research and it seems like your package cache is corrupted.
You could try running this:

```
sudo dpkg --clear-avail && sudo apt-get update
```

---

### Post by keymoo on 2008-11-18
> **cariboo907 said:**
> Have you tried :

```
sudo apt-get install -f
```Jim

hi Jim, I get 
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```
:confused:

---

### Post by keymoo on 2008-11-18
> **mrtomservo said:**
> Did a little research and it seems like your package cache is corrupted.
You could try running this:

```
sudo dpkg --clear-avail && sudo apt-get update
```

Hi mrtomservo, I get the same:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

---

### Post by mrtomservo on 2008-11-18
Hmmm..  Ok, well here's what i'd try next.  Make sure you backup this directory before removing it just in case you have to put it back... but on my Ubuntu /var/lib/dpkg/updates is completely empty.  So try backing up that directory, and then cleaning it out. Then re-run apt-get update.  I'm hoping that removing the corrupt 0060 file will solve the problem.

---

### Post by keymoo on 2008-11-19
> **mrtomservo said:**
> Hmmm..  Ok, well here's what i'd try next.  Make sure you backup this directory before removing it just in case you have to put it back... but on my Ubuntu /var/lib/dpkg/updates is completely empty.  So try backing up that directory, and then cleaning it out. Then re-run apt-get update.  I'm hoping that removing the corrupt 0060 file will solve the problem.

Great, that did the trick, thanks!

---

