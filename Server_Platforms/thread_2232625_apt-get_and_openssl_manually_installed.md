---
title: "apt-get and openssl manually installed"
date: 2014-07-03
forum: Server Platforms
---

### Post by fabio11 on 2014-07-03
Hello,
i have manually installed openssl compyling the source code present in the official website on account of the heartbleed bug because my ubuntu version is 12.04 and i didn't find one fixed version of openssl in the repository.
Now i would like to install other application via apt-get but i can't suceed because of coure apt say that openssl is not installed in my system.
I have tried to mark openssl as manually installed using apt-mark but i think this is the wrong way because apt-mark told me that the package is not installed.
So i would like to know if there is some way to tell to apt that i have installed the openssl manually or if i could use apt-get ignoring this dependecy.
Best regards
Fabio

---

### Post by nerdtron on 2014-07-03
> heartbleed bug because my ubuntu version is 12.04

You compiled the openssl package manually because of the heartbleed bug? And 12.04 is affected?

Just run ```
sudo apt-get update && sudo apt-get upgrade
```
 Then install the openssl package ```
using sudo apt-get install openssl
```

You'll get the version that is not affected by the heartbleed bug. No need to compile.

---

### Post by fabio11 on 2014-07-03
Yes i did on account of heartbleed bug, and before manually compilying openssl i have also tryed the way u suggest me. But from what i read 

> 
[FONT=Lato]What versions of the OpenSSL are affected?[/FONT][FONT=Lato][SIZE=2]Status of different versions:[/SIZE][/FONT]

[LIST]
[*][SIZE=2]OpenSSL 1.0.1 through 1.0.1f (inclusive) are vulnerable[/SIZE]
[*][SIZE=2]OpenSSL 1.0.1g is NOT vulnerable[/SIZE]
[*][SIZE=2]OpenSSL 1.0.0 branch is NOT vulnerable[/SIZE]
[*][SIZE=2]OpenSSL 0.9.8 branch is NOT vulnerable[/SIZE]
[/LIST]


with the apt-get i wasn't able to get the 1.0.1g so i thought it was still bugged. Am I missing something?

---

### Post by ian-weisser on 2014-07-03
There are *two* ways to address a vulnerability like heartbleed, and Ubuntu does both. That confuses some people.

One way is update to the latest upstream version (upstream applies the patch). Ubuntu does this in the development release - when heartbleed was revealed, 14.04 was pre-release. 14.04 uses the upstream's patched 1.0.1f release.

The other way is to take the upstream patch and apply it to an older version (downstream applies the patch). The [Ubuntu Security Team]("https://wiki.ubuntu.com/SecurityTeam") does this in already-released versions. Version numbers can be misleading in this case. Backporting the patch won't increment the upstream version number (1.0.1), but will increment the (XubuntuY) build version number. So OpenSSL 1.0.1 may be vulnerable, but 1.0.1-4ubuntu3 isn't vulnerable.

If I recall correctly, the Ubuntu Security Team pushed patched, heartbleed-invulnerable OpenSSL packages to all Ubuntu repositories within 24 hours of the upstream release of the patch. All you needed to do was ordinary regular security updates.

If you have questions about vulnerabilities in general, check the [Ubuntu Security Team's Wiki page]("https://wiki.ubuntu.com/SecurityTeam").
If you have questions about a specific vulnerability, see the [Ubuntu Security Team CVE tracker]("http://people.canonical.com/~ubuntu-security/cve/").

---

