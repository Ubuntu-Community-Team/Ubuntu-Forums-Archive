---
title: "fake directx"
date: 2009-05-04
forum: Wine
---

### Post by steeler on 2009-05-04
i tried to install need for speed most wanted but the installator terminates because it needs directx 9.0c

is there a way to actuallly make the installer think that directx is installed without installing it..in other words to fake it?

---

### Post by akoskm on 2009-05-04
> **steeler said:**
> i tried to install need for speed most wanted but the installator terminates because it needs directx 9.0c

is there a way to actuallly make the installer think that directx is installed without installing it..in other words to fake it?

I don't know anything about making fake directx entries in the regedit, but why don't you try to install it?
Take a look to this site:
[http://directxwine.sourceforge.net/]("http://directxwine.sourceforge.net/").
Hope that helps.

---

### Post by steeler on 2009-05-04
> **akoskm said:**
> I don't know anything about making fake directx entries in the regedit, but why don't you try to install it?
Take a look to this site:
[http://directxwine.sourceforge.net/]("http://directxwine.sourceforge.net/").
Hope that helps.

i've read that it might actually break wine so i'd prefer to avoid it..but thanks..

---

### Post by akoskm on 2009-05-04
> **steeler said:**
> i've read that it might actually break wine so i'd prefer to avoid it..but thanks..

I don't have any other idea to install DirectX. Before a few months ago I'm installed it with wine-doors, try that.

---

### Post by garythegoth on 2009-05-04
I always install DirectX when I install WINE. It has NEVER broken functionality....

---

### Post by cogadh on 2009-05-04
> **steeler said:**
> i tried to install need for speed most wanted but the installator terminates because it needs directx 9.0c

is there a way to actuallly make the installer think that directx is installed without installing it..in other words to fake it?

You can get around NFS:MW's DirectX installation requirement by copying the content of the install DVD to your hard drive and editing the AutoRun.conf. Change these two line to read like this:
```
DirectXVersion=0
StartMenuDXEULA=0
```
After that, run the install from that directory and it should complete without demanding that DX be installed.


> **garythegoth said:**
> I always install DirectX when I install WINE. It has NEVER broken functionality....
It might not have broken functionality that you have used, but it does definitely break some things in Wine and it really should not be done. It also does not add anything at all to Wine that you couldn't get by simply copying the few DLLs that Wine doesn't already have and applying overrides for them.
From the Wine [FAQ]("http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2"):
> **8.1. Does Wine support DirectX? Can I install Microsoft's DirectX under Wine?**

Wine itself provides a DirectX implementation that, although it has a few bugs left, should run fine. Wine supports DirectX 9.0c at this time. Plans for DirectX 10 are underway.

**If you attempt to install Microsoft's DirectX, you will run into problems.** It is not recommended nor supported by Wine HQ to attempt this. You can install the runtime, but it will not run. The runtime needs access to the Windows drivers, and Wine cannot access them for obvious reasons. The only native Microsoft DLLs that could be useful anyway are the d3dx9_xx.dll type ones, and these require you to accept Microsoft's license. Additionally these DLLs are now part of the Wine tree. So, as Wine improves these DLLs will only become less relevant.

That said, there are some guides out there which describe how you can install Microsoft's DirectX. I reiterate: It is not recommended nor supported by Wine HQ to attempt this. Furthermore it is considered off topic in Wine HQ support mediums (such as the forums). Please use a clean Wine configuration folder before seeking help. (You may need to rm -rf ~/.wine and re-install your Windows applications.)

---

