---
title: "partimage restore into vmware"
date: 2008-09-22
forum: Virtualisation
---

### Post by malanco on 2008-09-22
hey guys, is it possible to restore a partimage of my hardy box into a vmware box?, is there any issue about the hardware?

THANKS! :guitar:

---

### Post by malanco on 2008-09-23
bumpppppppppppppp

---

### Post by veloce on 2008-09-23
I suggest you try it and see if it works.

The key question I have is how would you go about it.  Do you need a running linux machine to restore an image?  If so, you'll need to bootstrap your system somehow.

eg:
[LIST=1]
[*]Create a tiny ubuntu install.
[*]Add an appropriately sized virtual disk to the image
[*]restore your partimage to the new virtual disk
[*]shut down the bootstrapping vm
[*]Create a new vm that uses the disk just created
[*]Try starting the new vm
[/LIST]

Yes, there will be hardware issues. The network card, video card, ... have changed - see how well the os copes.

Another issue is the size of the virtual disk you are creating - have you enough disk space?

---

