---
title: "How do I complete remove and reinstall Ubuntu One"
date: 2011-08-26
forum: Ubuntu One (CLOSED)
---

### Post by frogotronic on 2011-08-26
in Lucid.

---

### Post by ajgreeny on 2011-08-26
How did you install the first time, wubi or partitioned disk install?

If you used wubi you uninstall with the windows control centre add/remove utility then reinstall.

If you did a proper partitioned install choose manual partitioning when you get to the partitioning stage, and use the same partitions as before.  There is no need to uninstall first if you install this way.

---

### Post by frogotronic on 2011-08-28
> **ajgreeny said:**
> How did you install the first time, wubi or partitioned disk install?

If you used wubi you uninstall with the windows control centre add/remove utility then reinstall.

If you did a proper partitioned install choose manual partitioning when you get to the partitioning stage, and use the same partitions as before.  There is no need to uninstall first if you install this way.

OMG, sorry complete remove and re-install UbuntuOne.

---

### Post by haqking on 2011-08-28
Synaptic i imagine.

Ubuntuone-client and its dependencies then a reinstall of the same.

or from terminal

Guess by the way

---

### Post by ajgreeny on 2011-08-28
Sorry, I didn't notice this was about ubuntu-one.  (Have you edited the tread title now?)

Haqking has it right, but make sure you mark for **complete removal** in synaptic, not just **removal** or configurations may remain.  

Also note what else is removed when you remove the ubuntu-one packages as other dependent packages may also go and need replacing.

---

### Post by HarrisonNapper on 2011-08-29
Note: review what will be removed with complete removal. Sometimes, if it's packaged with the OS, it will try and remove the metapackage for everything ubuntu (not good). First, I would recommend opening a terminal and:

```
sudo dpkg-reconfigure ubuntuone-client; sudo dpkg-reconfigure ubuntuone-client-gnome
```

Then if that doesn't work:

```
sudo apt-get remove ubuntuone-client ubuntuone-client-gnome; sudo apt-get install ubuntuone-client ubuntuone-client-gnome
```

You can optionally do the first apt-get remove command, delete your Ubuntu One directory from home AND delete the hidden .Ubuntu-One (don't know exactly what it's called actually, so "ls -a ~/ |grep -i one" to double check) THEN do the apt-get install command.

Cheers.

---

