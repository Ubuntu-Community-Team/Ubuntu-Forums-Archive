---
title: "whhaaaaat????  my Iphone installs .debs????"
date: 2010-03-06
forum: The Cafe
---

### Post by switch10 on 2010-03-06
I was installing some packages in Cydia today, and I noticed debian flash across the screen a few times.  After a closer look I saw this..

```
(Reading database ... 2616 files and directories currently installed.)
Preparing to replace apt7-key 0.7.20.2-1 (using .../apt7-
key_0.7.25.3-3_iphoneos-arm.deb) ...
Unpacking replacement apt7-key ...
Setting up apt7-key (0.7.25.3-3) ...
(Reading database ... 2616 files and directories currently installed.)
Preparing to replace apt7-ssl 0.7.20.2-1 (using .../apt7-
ssl_0.7.25.3-3_iphoneos-arm.deb) ...
Unpacking replacement apt7-ssl ...
Setting up apt7-ssl (0.7.25.3-3) ...
(Reading database ... 2616 files and directories currently installed.)
Preparing to replace apt7 0.7.20.2-4 (using .../
apt7_0.7.25.3-6_iphoneos-arm.deb) ...
Unpacking replacement apt7 ...
Setting up apt7 (0.7.25.3-6) ...
(Reading database ... 2620 files and directories currently installed.)
Preparing to replace us.hackulo.security 1.1.0 (using .../
us.hackulo.security_1.2.1_iphoneos-arm.deb) ...
Unpacking replacement us.hackulo.security ...
Setting up us.hackulo.security (1.2.1) ...
Creating a working directory...
Checking for hosts file...
Checking for original backup...
Cleaning hosts file...
Checking for local key...
Verifying local key...
Downloading security updates...
Verifying signature...
Installing secure updates...
Installed.
Cleaning up...
Done.

```

---

### Post by mickie.kext on 2010-03-06
Um... are you sure it is an iPhone and not Maemo powered phone? 

It is pretty weird.

---

### Post by Revolutionary101 on 2010-03-06
I have noticed this on my iPod touch too. I know that when you jailbreak your iPhone, Cydia automatically installs something like "Deb tools" and my guess is that allows the iPhone to install .debs

---

### Post by squilookle on 2010-03-06
I've never used macs in an great depth, I have a few friends that have them and I've used their computers for the odd task, or to have a look around to satisy my own curiosity about macs, but I have heard macos uses rpm's. 

If that is correct, then I would guess it is POSSIBLE that the iphone os uses .debs?

---

### Post by jrothwell97 on 2010-03-06
It doesn't use RPMs. Mac OS X uses .pkg files which drive a package manager under the hood, but packages and updates aren't automatically downloaded from the Internet.

However, since it's a *nix, dpkg/apt or RPM can be installed on it, as can many different ports collections.

---

### Post by AllRadioisDead on 2010-03-06
Cydia uses apt. It's as simple as that. You can use it to connect to a repository and download third party software.

---

### Post by mickie.kext on 2010-03-06
Aha... that explains it. I do not know much about iSfuff, and iDon't use it.  So, naw can run Debian packages for ARM?

---

### Post by AllRadioisDead on 2010-03-06
The iphone will not run debian apps if that's what you're asking.

---

### Post by blackened on 2010-03-06
The applications must be specifically compiled for iphoneOS. 

If you install the mobile terminal, then you can use it to install downloaded debs via dpkg or to access apt directly using the repos you have enabled in cydia.

I for one hate my iphone and can't wait till I have enough cash to get an n900. Sure wish one of the US carriers would subsidize it.

---

### Post by mickie.kext on 2010-03-06
> **ihermit said:**
> The iphone will not run debian apps if that's what you're asking.

Of course, silly me. iGot it now. iRead wikipedia article about cydia.

---

### Post by Islington on 2010-03-06
Cydia is great. you can even add *unofficial* repos on there, unfortunately it is a bit slow for me.

---

### Post by ubunterooster on 2010-03-06
just imagine: 
```

isudo apt-get enya-my_my_time_flies

```

THEN iwant an iphone too. But not until then.

---

### Post by ssj6akshat on 2010-03-07
That's not a surprise.Cydia is a GUI to Apt and dpkg and other debian tools.Even the another instaler Icy is Based on debian tools.This shows Apt Rocks

---

### Post by wieman01 on 2010-03-07
Closed for review!

---

