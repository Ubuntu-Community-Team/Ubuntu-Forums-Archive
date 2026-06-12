---
title: "default-display-manager==lightdm, but lxdm runs"
date: 2024-07-03
forum: Ubuntu/Debian BASED
---

### Post by ruwolf on 2024-07-03
Hello.

I use Xubuntu 24.04 LTS (Noble Numbat) with minimal mix of Debian (Stable with highest priority) due hating of Snap's disk waste and I love FireFox.

```

$ cat /etc/X11/default-display-manager
/usr/sbin/lightdm

```

Journal of systemd contains absolutely no mention about LightDM.
Instead of it, LXDM is running.
Please, how is it possible? Why is [FONT=courier new]**/etc/default-display-manager**[/FONT] ignored? Where is it configured? And how to automatically run LightDM without purging LXDM?

---

### Post by &amp;KyT$0P# on 2024-07-03
> **ruwolf said:**
> I use Xubuntu 24.04 LTS (Noble Numbat) with minimal mix of Debian (Stable with highest priority) 

This could be the problem.  [Don't make this type of "FrankenXubuntu".]("https://wiki.debian.org/DontBreakDebian#Don.27t_make_a_FrankenDebian")  There are better, safer ways to use software or software versions not available in the standard Xubuntu repositories.

What Debian packages are you trying to use in Xubuntu?

---

### Post by ruwolf on 2024-07-03
I know dangers of Debian/Ubuntu monsters/chimeras. I have used them for years without severe problems.
I use mentioned FireFox from Debian.

---

### Post by &amp;KyT$0P# on 2024-07-03
Normally this would be controlled by running
```
sudo dpkg-reconfigure lightdm
```
which then prompts you which display manager you want to use.  Is this not working for you?

> **ruwolf said:**
> I know dangers of Debian/Ubuntu monsters/chimeras. I have used them for years without severe problems.
I use mentioned FireFox from Debian.

If it's only Firefox, there are other options:

[LIST]
[*][Official Mozilla build]("https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-deb-package-for-debian-based-distributions")
[*][Mozillateam PPA]("https://launchpad.net/~mozillateam/+archive/ubuntu/ppa")
[/LIST]

---

### Post by ruwolf on 2024-07-04
Of course, I tried dpkg-reconfigure, but it does not work.

Thank you for official PPA from Mozilla Team.

I dislike Snap and FlatPak; I do not know, what else is not in regular repository of Ubuntu.
Can I make list of such software? I know AWK or Python, so I need only information, where is it available (except .dep packages, where is mentioned in dependency section, because I do not want to download whole repositories.). apt-cache rdepends snapd gives confusing results, it includes apparmor, but in aptitude, I cannot see, that apparmor_4.0.0-beta3-0ubuntu3_amd64.deb depends on snapd.
I like also selenium browser, e.g. chromium & chromium-driver (with python3-selenium, of course).

---

### Post by &amp;KyT$0P# on 2024-07-05
> **ruwolf said:**
> Of course, I tried dpkg-reconfigure, but it does not work.

In that case, maybe look into the systemd services for the two display managers, e.g. which one has its service(s) active/enabled, which one [FONT=monospace]graphical.target[/FONT] is pulling in,...?  One thing to check would be
```
systemctl status display-manager.service
```
and make sure it's showing details for LightDM.

I have never used LXDM myself so don't know details of what else might need to be checked here, sorry.

> I dislike Snap and FlatPak; I do not know, what else is not in regular repository of Ubuntu.
Can I make list of such software? I know AWK or Python, so I need only information, where is it available (except .dep packages, where is mentioned in dependency section, because I do not want to download whole repositories.). apt-cache rdepends snapd gives confusing results,

Assuming you mean software that looks like it's installable as a .deb, but is actually a stub for a snap?  Here's a quick attempt at a Python program to find such packages, it's not ideal (has some false positives) but maybe you can tune it to your liking -
```
#!/usr/bin/env python3

import re, subprocess

maybe_snap = subprocess.run(['apt-cache', 'rdepends', 'snapd'], stdout=subprocess.PIPE, encoding='utf_8', check=True).stdout

for line in maybe_snap.splitlines():
  if line.startswith(' '):
    pkg = line.strip()
    if 'snap' in pkg:
      continue
    info = subprocess.run(['apt-cache', 'show', pkg], stdout=subprocess.PIPE, encoding='utf_8', check=True).stdout
    if re.search(r'Depends:.* snapd', info):
      print(pkg)
```

---

### Post by ruwolf on 2024-07-05
It correctly shows LightDM, but as dead:
```

$ systemctl status display-manager.service
&#9675; lightdm.service - Light Display Manager
     Loaded: loaded (/usr/lib/systemd/system/lightdm.service; indirect; preset: enabled)
     Active: inactive (dead)
       Docs: man:lightdm(1)

```
Not only in top command, lxdm-binary & lxdm-session are running:
```

$ systemctl status lxdm
&#9679; lxdm.service - LXDE Display Manager
     Loaded: loaded (/usr/lib/systemd/system/lxdm.service; static)
     Active: active (running) since Wed 2024-07-03 08:11:10 CEST; 2 days ago
       Docs: man:lxdm(1)
   Main PID: 2628 (lxdm-binary)
      Tasks: 18 (limit: 76382)
     Memory: 189.9M (peak: 225.3M)
        CPU: 1h 6min 2.080s
     CGroup: /system.slice/lxdm.service
             &#9500;&#9472;2628 /usr/sbin/lxdm-binary
             &#9492;&#9472;9223 /usr/lib/xorg/Xorg :0 vt07 -nolisten tcp -novtswitch -auth /var/run/lxdm/lxdm-:0.auth

```

---

