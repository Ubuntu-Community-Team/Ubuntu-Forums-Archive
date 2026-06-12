---
title: "U1 not syncing Tomboy Notes"
date: 2009-11-08
forum: Ubuntu One (CLOSED)
---

### Post by jondecker76 on 2009-11-08
U1 is finally working for me as far as file backup, but one of the bigger features that I wanted to use was Tomboy syncing and backup - but it doesn't appear to work at all.

Any idea when and if this will be working again?

I'm very excited to see U1 working and stable - its a service that both my wife and I will gladly be paying for once its all ironed out!

---

### Post by Merovius on 2009-11-09
I have to tell mine to synch. Tools, synchronize.

---

### Post by joshuahoover on 2009-11-09
> **jondecker76 said:**
> U1 is finally working for me as far as file backup, but one of the bigger features that I wanted to use was Tomboy syncing and backup - but it doesn't appear to work at all.

Any idea when and if this will be working again?

I'm very excited to see U1 working and stable - its a service that both my wife and I will gladly be paying for once its all ironed out!

Have you tried following the tutorial on how to setup Tomboy sync? [https://wiki.ubuntu.com/UbuntuOne/Tutorials/Notes](https://wiki.ubuntu.com/UbuntuOne/Tutorials/Notes)  If sync is still not working, then please do the following:

1) Quit Tomboy
2) From Applications->Accessories->Terminal, run: tomboy --debug > ~/tomboy-debug.log
3) Right-click on the Tomboy applet in your task bar and select "Synchronize Notes"
4) File a bug report here: [https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug](https://bugs.edge.launchpad.net/ubuntuone-servers/+filebug) and be sure to attach your ~/tomboy-debug.log file

Thank you,

Joshua

---

### Post by jondecker76 on 2009-11-09
Thanks - submitted the bug report!

[https://bugs.edge.launchpad.net/ubuntuone-servers/+bug/479417]("https://bugs.edge.launchpad.net/ubuntuone-servers/+bug/479417")

---

