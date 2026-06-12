---
title: "[SOLVED] Virtual box software sources"
date: 2008-06-23
forum: Virtualisation
---

### Post by Robbyx on 2008-06-23
I am getting an error message in synaptic as follows:

> Failed to fetch 

[http://www.virtualbox.org/debian/dists/hardy/non-free/binary-i386/Packages.gz](http://www.virtualbox.org/debian/dists/hardy/non-free/binary-i386/Packages.gz)
ie
.org/debian/dists/hardy/non-free/binary-i386/Packages.gz


  403 Forbidden
Some index files failed to download, they have been ignored, or old ones used instead.

I am running Hardy, but can not see a VB repository for it. How should I change the software sources to correct the error.

Robin

---

### Post by pytheas22 on 2008-06-23
If you go to just [http://www.virtualbox.org/debian/](http://www.virtualbox.org/debian/) , you get a message that sounds like they've removed their repositories and want you to use Sun's servers instead (I think Sun acquired VirtualBox not too long ago).  But the link provided to Sun doesn't make sense to me.

I'm wondering however what you're trying to download in the first place.  I've used VirtualBox for a while and don't remember ever adding a repository for it.  I know they have a closed-source version of VB available on their site, but I thought I was able to download it directly from their web page; I didn't need to use apt.  I could be wrong though.

---

### Post by bijeeshvs on 2008-06-23
you can download and install virtual box from here..............

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

i did it from here and it works just fine for me...............

---

### Post by Robbyx on 2008-06-23
Do you know how to uninstall an old version. It is easy to do through the repositories, but as they do not work for VB how do I do it?

Robin

---

### Post by pytheas22 on 2008-06-23
> Do you know how to uninstall an old version. It is easy to do through the repositories, but as they do not work for VB how do I do it?

As long as you installed it via a package (regardless of whether the repository still works or not), you should just be able to:
```

sudo apt-get remove virtualbox*
```

If you installed from source it would be harder, but you didn't do that did you?

---

### Post by Yuki_Nagato on 2008-06-23
Because it is not connected to the repositories, the program will be (Linux is annoying like this) difficult to completely uninstall.  The best place to start is /usr and remove the VirtualBox files.  Remove the icon from the Application menu if it is in there.  Perhaps there are a few more places, but I am unaware of them.  That is uninstalling in Linux.

In Linux, a program isn't really "installed;" the binaries and executables are just placed in the correct places.  On a Windows machine, registries must be made and updated, and other stuff, and dropping files somewhere will get you nothing.

I got Virtual Box working with the guide in my signature.

---

### Post by pytheas22 on 2008-06-23
> Because it is not connected to the repositories, the program will be (Linux is annoying like this) difficult to completely uninstall. The best place to start is /usr and remove the VirtualBox files. Remove the icon from the Application menu if it is in there. Perhaps there are a few more places, but I am unaware of them. That is uninstalling in Linux.

In Linux, a program isn't really "installed;" the binaries and executables are just placed in the correct places. On a Windows machine, registries must be made and updated, and other stuff, and dropping files somewhere will get you nothing.

This is all true if you compile something from source, but if you install it using a package, you don't need to do this.  Just use apt-get from the command line, or Synaptic, or the Add/Remove programs utility, and you can uninstall very easily.  The absence of a convoluted, binary nightmare like the Windows registry doesn't mean that adding and removing software in Linux has to be hard.

---

### Post by Yuki_Nagato on 2008-06-23
Absolutely true.

But that only applies because I installed the binaries without Synaptic (because Derek told me to.)

---

### Post by Robbyx on 2008-06-23
> **pytheas22 said:**
> As long as you installed it via a package (regardless of whether the repository still works or not), you should just be able to:
```

sudo apt-get remove virtualbox*
```

If you installed from source it would be harder, but you didn't do that did you?

I removed the old version by  following your command line and then installed the latest version. I am unable to load VB. This is the error message:

> 
The VirtualBox support driver which is running is from a different version of VirtualBox. You can correct this by stopping all running instances of VirtualBox and reinstalling the software..
VBox status code: -1912 (VERR_VM_DRIVER_VERSION_MISMATCH).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

 

At the end of the installation process VB found my old vdi and wanted to convert it to the new version. It failed. When  I clicked to start the conversion to make it compatable with the new version it reported it was unable to make the change.


What should I do?

Robin

---

### Post by pytheas22 on 2008-06-23
How did you install the "binaries?"  You don't necessarily need to use Synaptic.  You could have just downloaded the Debian package onto your desktop or wherever and double-clicked on it to install it with gdebi, or through the command-line with dpkg.  Either way it would still be uninstallable through Synaptic.  In other words, you don't need to install something from a repository to make it easy to uninstall.  You just need to use a package even if it's a stand-alone one.

If you downloaded a tarball (.tar.gz file) and compiled it from source, that's where it gets messy.  There are also some applications where you get a tarball and have to copy the binaries into place appropriately, usually because the vendor doesn't bother to build a package and doesn't want to release the source.  But that's luckily increasingly rare, as almost everyone offers .deb's now if they're in any way serious about supporting Linux.

---

### Post by pytheas22 on 2008-06-23
Robin,

Try:
```

sudo rmmod vboxdrv
sudo /etc/init.d/vboxdrv setup
sudo modprobe vboxdrv
```

this should pull out the old driver and build a new one, which I think is the problem.  If it doesn't work let us know.

---

### Post by Robbyx on 2008-06-23
> **pytheas22 said:**
> Robin,

Try:
```

sudo rmmod vboxdrv
sudo /etc/init.d/vboxdrv setup
sudo modprobe vboxdrv
```

this should pull out the old driver and build a new one, which I think is the problem.  If it doesn't work let us know.

I followed the above and there were no error messages. I then opened the VB program and found that although the vdi is showing there as powered off it will not load as settings, start and discard are all greyed out.

I tried creating a new vdi but when I came to choosing the existing vdi as the hard disk the select button is greyed out.

Robin

---

### Post by pytheas22 on 2008-06-24
This all seems very strange.  Could you try:
```

sudo apt-get remove --purge virtualbox
```

and then reinstall using the .deb on VirtualBox's site?  Make sure to use the right build for your system (32 or 64 bit).  Does the problem still occur after all this?

The command above will remove virtual box and all configuration files, so hopefully it will get rid of whichever incompatibilities are causing you problems (it shouldn't delete your vdi--in fact I'm almost certain that it won't--but just in case, you could back it up if it would be a major problem to lose it).  I'm sorry things aren't going as smoothly as they could but I think you're close to getting this solved.

---

### Post by Robbyx on 2008-06-24
> **pytheas22 said:**
> This all seems very strange.  Could you try:
```

sudo apt-get remove --purge virtualbox
```

and then reinstall using the .deb on VirtualBox's site?  Make sure to use the right build for your system (32 or 64 bit).  Does the problem still occur after all this?

The command above will remove virtual box and all configuration files, so hopefully it will get rid of whichever incompatibilities are causing you problems (it shouldn't delete your vdi--in fact I'm almost certain that it won't--but just in case, you could back it up if it would be a major problem to lose it).  I'm sorry things aren't going as smoothly as they could but I think you're close to getting this solved.

Thank you very much. This worked and it was not necessary to back up the vdi files but I did just in case.

Robin

---

