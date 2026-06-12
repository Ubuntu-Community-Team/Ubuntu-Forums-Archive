---
title: "Lucid + One Music Store + Banshee + Extension??"
date: 2011-06-12
forum: Ubuntu One (CLOSED)
---

### Post by fm1234 on 2011-06-12
Hi,

I'm running a recent version of Banshee (2.0.1) in my oldish Lucid system.

I would like to use the Ubuntu One Music Store with Banshee but I have problems installing the extension.

```

The following packages have unmet dependencies:
  banshee-extension-ubuntuonemusicstore: Depends: banshee-extensions-common (= 1.6.1-1ubuntu1~lucid2) but 2.0.1-1ubuntu1~hyper1+lucid is to be installed
E: Broken packages

```

How can I make all this pieces work together?

---

### Post by paulb42 on 2011-08-19
I'm experiencing this also, does anyone have a solution?


paul@paul-desktop:~$ sudo apt-get install banshee-extension-ubuntuonemusicstore
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  banshee-extension-ubuntuonemusicstore: Depends: banshee-extensions-common (= 1.6.1-1ubuntu1~lucid2) but 2.0.1-1ubuntu1~hyper1+lucid is to be installed
E: Broken packages
paul@paul-desktop:~$

---

### Post by duanedesign on 2011-08-23
> **fm1234 said:**
> Hi,

I'm running a recent version of Banshee (2.0.1) in my oldish Lucid system.

I would like to use the Ubuntu One Music Store with Banshee but I have problems installing the extension.

```

The following packages have unmet dependencies:
  banshee-extension-ubuntuonemusicstore: Depends: banshee-extensions-common (= 1.6.1-1ubuntu1~lucid2) but 2.0.1-1ubuntu1~hyper1+lucid is to be installed
E: Broken packages

```

How can I make all this pieces work together?

It is having trouble satisfying the dependencies. It is looking for a different version of banshee-extensions-common. It wants [this version]("http://packages.ubuntu.com/lucid-updates/banshee-extensions-common"). I have not looked in enough detail to tell you if installing this version will, or will not work.

---

