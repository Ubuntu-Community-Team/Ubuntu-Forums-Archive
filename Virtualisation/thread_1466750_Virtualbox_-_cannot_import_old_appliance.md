---
title: "Virtualbox - cannot import old appliance"
date: 2010-04-30
forum: Virtualisation
---

### Post by Warthaug on 2010-04-30
I just upgraded to ubutnu 10.04.  I installed the 64bit ubuntu virtualbox from the vbox website, and attempted to import my old (winxp) vbox.  I cannot do it - the import gets stuck at 0% and after a few minutes throws an error (see thumbnail).

The error itself says it cannot register the hard disk, as a hard disk with the same UUID already is entered in VirtualBox.xml.  I tried clearing and deleting this file, but I get the same error every time.

Any ideas as to what is happening, and how to make this work?

Thanx

Bryan

---

### Post by Warthaug on 2010-04-30
To add to what I have above.  I found what seemed like the fix on the vbox forums: [http://forums.virtualbox.org/viewtopic.php?f=6&t=30180](http://forums.virtualbox.org/viewtopic.php?f=6&t=30180)

But upon doing the fix, I got a new error which I cannot seem to find an answer to. The error I get is:

```

Filed to import applioance /home/bryan/tmp/VBox_20100428.ovf
The SHA1 digest f "WinXP pro.mdk" does not match the one in VBox_20100428.mf
```


Under the details drop-down window, I have the error:

```

Result Code: VBOX_E_FILE_ERROR (0x80BB0004)
Component: Appliance
Interface: IAppliance {e3ba9ab9-ac2c-4266-8bd2-91c4bf721ceb}

```

As far as I can tell this may be a checksum problem. Is that right, and if so is there any chance of recovery? And if I'm wrong, anyone know how to fix the problem I am having?

Thanx

Bryan

---

