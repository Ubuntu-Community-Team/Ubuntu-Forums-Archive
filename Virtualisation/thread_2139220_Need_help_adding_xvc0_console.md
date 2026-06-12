---
title: "Need help adding xvc0 console"
date: 2013-04-26
forum: Virtualisation
---

### Post by tangi on 2013-04-26
hi, 
how can I make xenconsole xvc0 working on Ubuntu PV guest domu? 
Here is the message I received, it hangs on boot: 
```
Loading, please wait...
Begin: Loading essential drivers ... done.
[    1.768247] udevd[91]: starting version 175
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
[    1.824091] kjournald starting.  Commit interval 5 seconds
[    1.824113] EXT3-fs (xvda1): mounted filesystem with ordered data mode
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
[    3.574129] EXT3-fs (xvda1): using internal journal
 * Starting set console font                                             [ OK ]
 * Stopping set console font                                             [ OK ]
 * Starting userspace bootsplash                                         [ OK ]
```

---

### Post by tangi on 2013-04-26
please close the thread, I have to use hvc0 insteed of xvc0...

---

