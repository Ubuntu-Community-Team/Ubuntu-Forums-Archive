---
title: "The update manager needs work"
date: 2006-06-15
forum: The Cafe
---

### Post by MKR. on 2006-06-15
The update manager tells me there are updates available. I load it, let it check, and I see a list of 16 updates.

I see several updates for my kernel, and an older kernel. Three updates for 386, 3 for 686; all look almost identical to me, and the boxes that should say what's different are either empty or give a generic description of the package.

 I see that one of the 686 packages has a version number incrementally higher than my current kernel; the rest are the same version, or for a version I've never even had (or so it appears; with no changelog I can't know). Looking it up would be difficult since I can't copy+paste and google it, but then I still wouldn't know if there was a reason I'm being presented with what appears to be an old package.

There's an update for "xorg-driver-fglrx"; is that the proprietary one or the OSS one? The proprietary one makes my sound go nuts, and the OSS one (which I use) uses fake OpenGL acceleration. I can't risk having to go and undo this since everything works fine right now. Or...gasp, maybe I'm being presented with it because it supports real 3d accel now...or maybe not.

How am I supposed to know what to do with these? Why is it showing updates for a kernel I'm not using (and why would I want it to touch something that's only there as a failsafe?)?

I've elected not to install any of them since none appear to relate to security, though I can't be sure since there's no information on any of the packages.

Is anyone working on improving this? This seems like a very important part of Ubuntu's goal (opening Linux to the average person). If this is stumping an experienced computer user (not "I'm an expert at MS word" experienced; the real kind), imagine how rough it must be for people that wouldn't even know what half these packages are. The average person likely wouldn't even be able to assess the security risks involved with not updating.

The average user would have already been back in their comfort zone by this point (Windows or mac), and that seems counterproductive.

](*,)

---

### Post by Kvark on 2006-06-15
Just configure the update manager to automatically install all updates without telling you anything. There is no point in knowing what it updates since you have already knowlingly installed the packages and it is just installing new versions of what you already have.



The xorg-driver-fglrx package is the one you have installed of course since it won't update packages you don't have. So just install the update. If you have forgotten which one you have then search for the package in synaptic or type "apt-cache show xorg-driver-fglrx" in a terminal to see a description of it.

If I understood the kernel stuff correctly... Each version of the kernel is it's own package so that you still have the old version if the new version wouldn't work for some reason. So the update with the same version number as your current kernel is probably a security update for your current kernel. The update with a higher version number is a whole new kernel (because an update to the linux-686 metapackage caused the meta package to depend on the new kernel). The 386 ones are still installed and thus they should still be updated. If you don't like having multiple kernels you can uninstall the 386 kernels or the old kernel versions if you think you don't need them as failsafes.

So it is working just as it should and is just updating all the packages that needs to be updated.

---

### Post by bruce89 on 2006-06-15
[QUOTE=MKR.](or so it appears; with no changelog I can't know)[/QUOTE]
There is a changelog, you have to open the Show Details panel at the bottom.

The new kernel (2.6.15-25.43, assuming this is Dapper) is to fix security flaws - [http://www.ubuntu.com/usn/usn-302-1](http://www.ubuntu.com/usn/usn-302-1)

---

