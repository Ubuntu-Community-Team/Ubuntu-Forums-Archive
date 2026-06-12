---
title: "Jackd artsshell terminate/server socket error"
date: 2010-07-13
forum: Ubuntu Studio
---

### Post by Peter7K on 2010-07-13
Hi.  I've been successfully running qjackctl, the following happens:

The jackd message window pops up with this stuff visible:

```
artsshell -q terminate
Cannot connect to server socket err = No such file in directory
Cannot connect to server socket err
jack server is not running or cannot be started
     ALSA connection graph change
sh: artsshell: not found
```

And then my system completely freezes (I've *never* had this happen in ubuntu).  Any ideas?

EDIT:[http://www.backports.ubuntuforums.org/showthread.php?t=1515680&highlight=artsshell+terminate]("http://www.backports.ubuntuforums.org/showthread.php?t=1515680&highlight=artsshell+terminate") did find this thread but I think I have a different problem from this guy, not sure though.

---

### Post by Pablo_F on 2010-07-14
Hi, 

I am sure you don't have the artsshell command in your system (because it is deprecated) and you can safely disable "Execute script at startup" in the Options tab in the setup.

I don't think this has something to do with the freeze though. But then I don't know what the problem can be.

Cheers! Pablo

---

### Post by Peter7K on 2010-07-14
> **Pablo_F said:**
> Hi, 

I am sure you don't have the artsshell command in your system (because it is deprecated) and you can safely disable "Execute script at startup" in the Options tab in the setup.

I don't think this has something to do with the freeze though. But then I don't know what the problem can be.

Cheers! Pablo

I can't even access the options tab, because it freezes.  :(

---

### Post by Pablo_F on 2010-07-15
Hi, 

Then, you can manually edit the qjackctl conf file before you launch it.

gedit /home/user/.config/rncbc.org/QjackCtl.conf

Under the [Options] header turn to false the option:

StartupScript

And, if the value is true, try with false also in:

PostStartupScript

Please report back, 

Cheers! Pablo

---

### Post by Peter7K on 2010-07-16
Ah, should have known I could have just gedited the config.  Worked like a charm.  Thank you very much Pablo!  Marking as solved.

---

### Post by Pablo_F on 2010-07-16
Cool :D

That conf file is so hidden. Linux-like marketing, I guess

---

