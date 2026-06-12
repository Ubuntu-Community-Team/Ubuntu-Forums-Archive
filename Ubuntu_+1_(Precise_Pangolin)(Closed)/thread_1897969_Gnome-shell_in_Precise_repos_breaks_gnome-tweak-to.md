---
title: "Gnome-shell in Precise repos breaks gnome-tweak-tool"
date: 2011-12-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-12-20
The newest update of Gnome-shell (3.2.1-8ubuntu1) in Precise repos breaks Gnome-tweak-tool (<3.2).
The version in Precise repos of gnome-tweak-tool is 3.2.2.1, which is not <3.2, however.

If you try to update (with Synaptic) gnome-shell (3.2.1-0ubuntu1), gnome-tweak-tool (3.2.2.1) is uninstalled.
This is not the intention, something is wrong here.

Edit: also, gnome-shell needs gnome-shell-common, which is not ready yet. We have to wait a bit.

Here:
[https://launchpad.net/ubuntu/+source/gnome-shell/3.2.1-8ubuntu1/+build/3024275](https://launchpad.net/ubuntu/+source/gnome-shell/3.2.1-8ubuntu1/+build/3024275)

---

### Post by dino99 on 2011-12-20
Compilation is done for GS, but seems to wait for additional packages

---

### Post by jbicha on 2011-12-20
Actually, the new gnome-shell conflicts against gnome-tweak-tool << 3.2. gnome-shell-common is in the [new queue]("https://launchpad.net/ubuntu/precise/+queue?queue_state=0"). Every time a new binary package gets uploaded, the archive admins have to manually approve it so just wait a bit longer. (Unfortunately many developers are already on holiday...)

---

### Post by Harry33 on 2011-12-20
> **jbicha said:**
> Actually, the new gnome-shell conflicts against gnome-tweak-tool << 3.2. gnome-shell-common is in the [new queue]("https://launchpad.net/ubuntu/precise/+queue?queue_state=0"). Every time a new binary package gets uploaded, the archive admins have to manually approve it so just wait a bit longer. (Unfortunately many developers are already on holiday...)

I think the package details actually say it breaks g-t-t:

> Breaks:
[LIST]
[*]                  [             fglrx-driver                            (<<                1:11-10)                       ]("https://launchpad.net/ubuntu/precise/amd64/fglrx-driver")
[*]                  [             gnome-control-center                            (<<                1:3.0)                       ]("https://launchpad.net/ubuntu/precise/amd64/gnome-control-center")
[*]                  [             gnome-session                            (<<                3.0)                       ]("https://launchpad.net/ubuntu/precise/amd64/gnome-session")
[*]                  [             gnome-tweak-tool                            (<<                3.2)                       ]("https://launchpad.net/ubuntu/precise/amd64/gnome-tweak-tool")
[/LIST]
  


---

### Post by jbicha on 2011-12-20
Yes, it breaks versions of gnome-tweak-tool less than 3.2 because gnome-tweak-tool 3.0 won't work with  gnome-shell 3.2. But it's not a problem because we're already using gnome-tweak-tool 3.2. I believe Synaptic is just confused because gnome-shell-common isn't available yet.

---

### Post by Harry33 on 2011-12-20
> **jbicha said:**
> yes, it breaks versions of gnome-tweak-tool less than 3.2 because gnome-tweak-tool 3.0 won't work with  gnome-shell 3.2. But it's not a problem because we're already using gnome-tweak-tool 3.2. I believe synaptic is just confused because gnome-shell-common isn't available yet.

ok

---

### Post by qwill on 2012-01-30
Well, I'm not even using Presice repos, and I just got the same problem this morning.

The latest update wants to instll gnome-shell; but displays a gazillion warning about dependencies etc. looking closer to it, I come to the same conclusion that it wants to install gnome-shell-common (which mean disinstalling an awfull lot of other packages ),

---

### Post by jbicha on 2012-01-30
Yes, but you're using oneiric-proposed. gnome-shell-common is waiting in the new queue but it should be fixed by tomorrow. Sorry for the inconvenience.

---

