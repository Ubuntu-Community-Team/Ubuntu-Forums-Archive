---
title: "[SOLVED] Maya and environment variables"
date: 2008-08-23
forum: Ubuntu Studio
---

### Post by csa3d on 2008-08-23
I'm a windows user, slowly making the switch over to full time Ubuntu.

In my Maya.env, i typically point the MAYA_APP_DIR to an external drive which my system sees as "i:/Maya"

In my Ubuntu setup, my external drive gets a path of "/media/sdb2/my drive", and yes, there's a space in the name of the drive name.

I don't seem to be able to edit the ~/maya/2008/Maya.env to have it load the settings from my external device.  I've tried the following with no luck:
```
MAYA_APP_DIR=/media/sdb2/my\ drive/Maya
```

and also

```
MAYA_APP_DIR=/media/sdb2/my drive/Maya
```

nothing I do seems to work by editing the .env file.  That being said, if I load up a Terminal window and type
```
export MAYA_APP_DIR=/media/sdb2/my\ drive/Maya
maya
```

Then Maya loads using the settings properly from the external drive.  My question is:

1.  What am I doing wrong which prevents my edited Maya.env from working?

2.  Seeing that I have made an "Applications" menu entry for maya using Sessions, where do I need to place an "export MAYA..." entry so that Maya loads using the variable.

Any help clarifying this would be super helpful!

---

### Post by unutbu on 2008-08-23
Edit your ~/.profile to include
```

export MAYA_APP_DIR=/media/sdb2/my\ drive/Maya

```
The ~/.profile is read every time you log in. So log out, log in, and you should be good to go.

I don't know anything specific about Maya (except that it's a cool program), but it seems that at least under Ubuntu, the Maya.env file is not getting read.

---

### Post by csa3d on 2008-08-23
> **unutbu said:**
> Edit your ~/.profile to include
```

export MAYA_APP_DIR=/media/sdb2/my\ drive/Maya

```
The ~/.profile is read every time you log in. So log out, log in, and you should be good to go.
getting read.

Thanks so much!  This worked perfectly.  I also discovered that if you type

```
env
``` in a terminal window you can verify that the variable has registered.

-csa

---

