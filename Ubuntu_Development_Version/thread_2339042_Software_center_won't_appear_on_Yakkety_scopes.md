---
title: "Software center won't appear on Yakkety scopes"
date: 2016-10-04
forum: Ubuntu Development Version
---

### Post by poiel-gb on 2016-10-04
Hey pals, I installed Ubuntu Xenial on my laptop, updated to Yakkety and installed Unity8 with Mir, now when I log into Unity 8, scopes only shows the Browser and Settings icons, but the software center isn't there. Someone knows how to fix it? And btw, there is any way to install firefox 49 on Unity 8 or use the default browser to watch Netflix?

---

### Post by mc4man on 2016-10-04
If you glanced thru here you'd probably get the idea on how to install deb based apps for 'use' in unity8
[https://ubuntuforums.org/showthread.php?t=2338565](https://ubuntuforums.org/showthread.php?t=2338565)
As far as ubuntu-software, no point really as it wouldn't be able to do anything (or even run

---

### Post by ventrical on 2016-10-05
> **mc4man said:**
> If you glanced thru here you'd probably get the idea on how to install deb based apps for 'use' in unity8
[https://ubuntuforums.org/showthread.php?t=2338565](https://ubuntuforums.org/showthread.php?t=2338565)
As far as ubuntu-software, no point really as it wouldn't be able to do anything (or even run

Libertine is still busted.

---

### Post by poiel-gb on 2016-10-06
May be not usefull, but I would like to have it

---

### Post by ventrical on 2016-10-07
Libertine is now fixed (along with the release candidate iso).  You have to experiment with what types of apps you want to use. There are a lot of threads here where I experimented with Libertine as an early adopter and you will see some of the apps that work and some that will not. The apps store is no longer. Ubuntu  is moving towards a snap based repository system so we will be able to install xapps with snaps or through libertine/containers. Programs like firefox, nautilus, xterm, gedit, libreoffice and abiword to mention a few work very well through  xapps after they are installe via libertine.

Programs like gnome-system-monitor will not work but you can install mesa-utils and run glxgears in the click.terminal or xterm. Remember, each container is isolated from the others so if you install , lets say, mesa-utils into a container called  "Container1" through xterm and you run glxgears, you will only be able to run glxgears within that container. However, if you create another container called "Container2", install xterm through Libertine and then :
```

sudo apt-get install mesa-utils

```

you will be able to run glxgears from that container also, simutaneously.
 It is an awesome sandbox. :)

regards..

---

### Post by poiel-gb on 2016-10-07
I installed qterminal and chrome, it's working well, the only problem is that they close from nothing sometimes

---

### Post by ventrical on 2016-10-08
> **poiel-gb said:**
> I installed qterminal and chrome, it's working well, the only problem is that they close from nothing sometimes

Some apps will crash .. others will not. I do not know if there is actually a list of approved xapps that will work stable. Eventually we will be able to snap them in.

regards..

---

