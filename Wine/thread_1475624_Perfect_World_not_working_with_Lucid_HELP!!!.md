---
title: "Perfect World not working with Lucid: HELP!!!"
date: 2010-05-07
forum: Wine
---

### Post by Rehdon on 2010-05-07
Hi all,
I've been running PWI under Ubuntu + Wine for about one and half year with only a few minor glitches, after updating to Ubuntu 10.04 I discovered it doesn't work anymore :(

**Problems**: PWI runs very slowly, is jerky; graphics are messed up in such a way to make the game unplayable anyway: only the basic terrain is rendered well, anything else (buildings, other objects) are invisible or expanded in such a way to prevent viewing everything else.

**Hardware**: Sony Vaio laptop VGN-FW21E, ATI Radeon Mobility HD 3400 series video card, Intel(R) Core(TM)2 Duo CPU P8400 @ 2.26GHz

**Software**: Ubuntu 10.04 Lucid Lynx (clean install), ATI proprietary drivers, Wine 1.1.42, PWI latest version (319); dual boot possible with Windows Vista (where the game works fine).

**What I did**: just to be sure I used a new .wine directory, moved PWI into it, installed the necessary fonts, then tried first the registry settings posted on the PWI forums ([http://pwi-forum.perfectworld.com/showthread.php?t=579982&highlight=wine+ubuntu](http://pwi-forum.perfectworld.com/showthread.php?t=579982&highlight=wine+ubuntu)) then those suggested on the WineHQ site ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923)). Nothing worked.

Any idea about what could be the solution? I could try an older version of Wine, but I have a feeling that the problem lies in the ATI proprietary drivers coming with the Lucid release.

Please help!!! I don't want to boot Vista because of this problem :(

Thx in advance!

Rehdon



Please

---

### Post by darkforester67 on 2010-05-07
Did you try downloading the lastest drivers of ATI ??
Did you use 9.10 be you upgraded to 10.04?, if so what drivers did you have for your ATI graphics card? try downloading the driver's you had on the previous version of ubuntu

---

### Post by Rehdon on 2010-05-07
Hi and ty for replying. No, I didn't try download ATI's drivers directly because, as far as I know, they should be exactly the same version Ubuntu ships with. I've thought about downgrading to the 9.10 ones but, since they are handled by a special software, I don't know how to do that ... I guess I could compare the package names (assuming I get them right :))

Rehdon

---

### Post by Rehdon on 2010-05-09
Ok, I tried to downgrade the ATI drivers using Karmic's ones, but failed with this error message when installing the fglrx-kernel-source package:

```
Error! Bad return status for module build on kernel: 2.6.32-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.660/build/ for more information.
Done.

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.32-22-generic (i686) first.
```

And in fact glxinfo returns:

```
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14
```

Tried with the Catalyst package, producing Ubuntu debs, and likewise failed.

Any idea about what I should do? why is it so difficult to handle drivers in Ubuntu Linux?

Rehdon

---

### Post by cogadh on 2010-05-09
Its not Ubuntu that is the problem, its just the ATI drivers themselves; they are a pain in the *** to deal with. Try uninstalling whatever drivers you may have installed then simply use the Restricted Drivers Manager to install the current ATI drivers correctly.

---

### Post by Rehdon on 2010-05-10
> **cogadh said:**
> Its not Ubuntu that is the problem, its just the ATI drivers themselves; they are a pain in the *** to deal with. Try uninstalling whatever drivers you may have installed then simply use the Restricted Drivers Manager to install the current ATI drivers correctly.

Hmm, I did a fresh install, that is I wiped clean the / partition. The current ATI drivers as shipped with Ubuntu 10.04 don't seem to work with PW, which is why I was looking for a downgrade (Karmic's ones were working just fine). Do you know how to solve the error the previous drivers give?

OTOH I didn't try to downgrade the Wine version, but I'm convinced the problem lies in the drivers, as you were saying ... should I try that too?

Rehdon

---

### Post by cogadh on 2010-05-10
The previous driver package really can't be used in 10.04 as it was built against a previous version of the Linux kernel and modules, hence the error you got. If you want the older drivers, don't bother trying to create an Ubuntu .deb package, just get the .run file and run it normally (assuming you are going to go with the Catalyst package). If you want to go with the Open Source driver, follow these instructions:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Rehdon on 2010-05-10
Installed the ATI Catalyst drivers as per your suggestion, but still it doesn't work, getting the same error message:

```
glxinfo
name of display: :1.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
```

I'm pretty sure I managed to install those some time ago in Karmic, I wonder what I did wrong since I followed the instructions faithfully :(

Unfortunately I can't go with the open source driver until 3D is supported.

Rehdon

---

### Post by jvdurme on 2010-05-10
I have exactly the same problem here with Lucid. I have to go back to Jaunty or so if it doesn't work. For me, SwapScreens is not xworking in the latest ati drivers, so I have to downgrade. I used the runfile of the 9.10 version and of course, this fails and the output is:

Creating symlink /var/lib/dkms/fglrx/8.661/source ->
                 /usr/src/fglrx-8.661

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.661/build; sh make.sh --nohints --norootcheck....(bad exit status: 1)
0
0
[Error] Kernel Module : Failed to build fglrx-8.661 with DKMS
[Error] Kernel Module : Removing fglrx-8.661 from DKMS


Anyone knows a workaround or am I lost? Thanks!

---

### Post by Rehdon on 2010-05-11
I guess at this point the question is: how do I downgrade my graphics drivers in Ubuntu 10.04? which has little to do with Wine.

BTW I noticed that in the full error message there's this line:

```
dlopen: /usr/lib/xorg/modules/drivers/fglrx_drv.so: undefined symbol: UpdateSpriteForScreen
```

which doesn't seem like a major showstopper to me: installing the Catalyst drivers might work if we find a way around this "undefined symbol" :)

Rehdon

---

### Post by jvdurme on 2010-05-11
I gave up and went back to Karmic. I can't afford these hickups.

---

### Post by Rehdon on 2010-05-11
Might have to do the same unless I find a "cure" for the drivers ... sad :(

Rehdon

---

### Post by Rehdon on 2010-06-22
Hello again,
after actually going back to Karmic (argh!), I read about the updated ATI drivers: are those available for Ubuntu? there's been an update of xorg and proprietary drivers on my main box (nVidia based), so I'd say yes: has anyone tried again using those? any improvements?

If not, what about the very recent Catalyst update?

Rehdon

---

