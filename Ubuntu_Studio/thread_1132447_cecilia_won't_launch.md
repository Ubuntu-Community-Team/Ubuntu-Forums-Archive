---
title: "cecilia won't launch"
date: 2009-04-21
forum: Ubuntu Studio
---

### Post by ireneshusband on 2009-04-21
When I try to launch Cecilia, it hangs at the splash screen with the output:
```
Cecilia installation located in /usr/share/cecilia (automatic)
Loading the sources on Linux!
note: creating new prefs
info: /usr/bin/csound found; verifying version
```

There was [a bug with the same symptoms]("http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;bug=476300") reported some time ago, but that was fixed with the a very simple patch. Does anyone have any idea what else might be going on to cause this?

Thanks in advance.

---

### Post by Stochastic on 2009-04-22
can you post the output of ```
apt-cache policy cecilia
```

---

### Post by ireneshusband on 2009-04-22
```
robert@ermintrude:~$ apt-cache policy cecilia
cecilia:
  Installé*: 2.0.5-2.1ubuntu2
  Candidat*: 2.0.5-2.1ubuntu2
 Table de version*:
 *** 2.0.5-2.1ubuntu2 0
        500 http://archive.ubuntu.com intrepid/universe Packages
        100 /var/lib/dpkg/status

```

I have also extracted the scripts for Cecilia 2.5 from the OS X app and I get the same problem with those.

---

### Post by Stochastic on 2009-04-22
You've stumped me.  That version has the csound version fix in it, so that's probably not where the problem lies.  Mine boots up fine (in Jaunty) and did back when I was running Intrepid too, so there's a good chance it could be your system's configuration.  What's the output of apt-cache policy csound ?

The next troubleshooting step I'd go to is either a debugger or inserting print statements into the startup code (old school debugging) to see where the hang is occurring.

---

### Post by sandwormblues on 2009-08-04
I'm having the exact same issue and I'm using Hardy.  Cecilia starts the "wish" process and then hangs.

```
apt-cache policy cecilia
cecilia:
  Installed: 2.0.5-2ubuntu5.1
  Candidate: 2.0.5-2ubuntu5.1
  Version table:
 *** 2.0.5-2ubuntu5.1 0
        500 http://us.archive.ubuntu.com hardy-updates/universe Packages
        500 http://security.ubuntu.com hardy-security/universe Packages
        100 /var/lib/dpkg/status
     2.0.5-2ubuntu5 0
        500 http://us.archive.ubuntu.com hardy/universe Packages

```

---

