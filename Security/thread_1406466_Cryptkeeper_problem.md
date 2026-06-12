---
title: "Cryptkeeper problem"
date: 2010-02-14
forum: Security
---

### Post by iamBrach on 2010-02-14
My wife was using cryptkeeper fine, then she right-clicked the keys on the panel and did something, I'm not sure what.  Anyway, the keys you click on to open the encrypted folder are gone and I can't figure out how to get them back.  System monitor shows cryptkeeper running.  I can kill it and re-start it, but the keys don't show on the panel.  I'm running ubuntu 9.10.

---

### Post by yogesh.girikumar on 2010-02-15
Hi,

Hit Alt+F2 and type "cryptkeeper" and hit enter to bring the Applet to the panel.

       Alternatively, you can start it by going to : Applications -> System Tools -> Cryptkeeper

   If this doesn't work, you can try uninstalling and reinstalling Cryptkeeper

```
$ sudo apt-get remove cryptkeeper && apt-get install cryptkeeper
```      Your setting will be preserved.
       If this happens often, it might be due to a bug: [https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/201348](https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/201348)

---

