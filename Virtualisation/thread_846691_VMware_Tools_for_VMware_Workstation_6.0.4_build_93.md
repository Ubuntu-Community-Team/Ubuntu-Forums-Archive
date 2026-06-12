---
title: "VMware Tools for VMware Workstation 6.0.4 build 93057 on Ubuntu 8.04 guest"
date: 2008-07-01
forum: Virtualisation
---

### Post by Keithel on 2008-07-01
So, you've gone and upgraded to or installed Ubuntu 8.04 Hardy Heron to a VMware virtual machine, but you find that the guest-host directory sharing doesn't work, amongst other things.

You've gone on to do the usual VMware tools install/upgrade via the VM->Install VMware Tools... feature in VMware Workstation, but you run into the following error when compiling the vmhgfs module:
```
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/tmp/vmhgfs-only/backdoor.o
  CC [M]  /tmp/tmp/vmhgfs-only/backdoorGcc32.o
  CC [M]  /tmp/tmp/vmhgfs-only/bdhandler.o
  CC [M]  /tmp/tmp/vmhgfs-only/cpName.o
In file included from include/linux/string.h:11,
                 from /tmp/tmp/vmhgfs-only/cpName.h:18,
                 from /tmp/tmp/vmhgfs-only/cpName.c:18:
include/linux/types.h:40: error: conflicting types for ‘uintptr_t’
/tmp/tmp/vmhgfs-only/vm_basic_types.h:170: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/tmp/tmp/vmhgfs-only/cpName.o] Error 1
make[1]: *** [_module_/tmp/tmp/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmhgfs.ko] Error 2

```

Below paragraph is some technical info that most users can skip over:
Well, it seems that VMware has not updated their tools to work well with Linux kernel 2.6.24, and the Linux kernel team threw in a definition of uintptr_t outside the usual place it's defined -- in stdint.h.  This may mean that they determined that inclusion of stdint.h is not safe to include in kernel code.


Here are the steps to fixing this:
[LIST=1]
[*]Perform the VM->Install VMware Tools... action in VMware to get the VMware Tools virtual CD mounted in Ubuntu.
[*]Bring up a terminal window, existing user is fine (does not have to be root).
[*]Make sure build-essential package, and the patch package are installed using:
```
sudo aptitude install build-essential
sudo aptitude install patch
```
(I put them separately so you could more easily tell if one or the other failed)
[*]Change to a temporary directory: 
```
cd /tmp
```
[*]expand the VMware Tools: 
```
tar zxvf /media/cdrom/VMwareTools-6.0.4-93057.tar.gz
```
[*]expand the vmhgfs source code also in the current temp directory using: 
```
tar xvf vmware-tools-distrib/lib/modules/source/vmhgfs.tar
```
You should now have a directory called vmhgfs-only which was expanded from the vmhgfs.tar file.
[*]Now, download the patch file I have put together and attached to this post.  This patch file fixes the vmhgfs module sources so they properly compile for kernel 2.6.24.  

NOTE: This will only apply to the tools package included with Workstation 6.0.4 build 93057.  YMMV with other VMware products and versions.

[*]Apply the patch file to the sources we just expanded.  From the directory where vmhgfs-only resides, execute: 
```
patch -p1 < /path/to/vmhgfs_6.0.4-93057__linux-2.6.24_fix.patch.txt
```

[*]Force remove the old vmhgfs.tar file from the extracted tools install files, as the permissions on this file are read-only.
```
rm -f vmware-tools-distrib/lib/modules/source/vmhgfs.tar
```
[*]Package the modified sources up back into a tar file, replacing the original removed vmhgfs.tar file in vmware-tools-distrib:
```
tar cvf vmware-tools-distrib/lib/modules/source/vmhgfs.tar vmhgfs-only
```
[*]Make the permissions of the vmhgfs.tar file the same as the original one -- which I see as being -r--r--r-- (444 octal) (this is optional)
```
chmod 444 vmware-tools-distrib/lib/modules/source/vmhgfs.tar
```
[*]Now all that is left to do is execute the VMware tools installer from the vmware-tools-distrib directory, just like you would normally when installing VMware tools.  This time, however, the vmhgfs module should compile successfully when configuring.
```
cd vmware-tools-distrib
sudo ./vmware-install.pl
```
[/LIST]

NOTE: The patch file has been named with a .txt extension so that it will properly upload to the Ubuntu forums.  This should have no effect on the way the patch file applies.

---

### Post by Zenyatta13 on 2008-07-02
Great job on the patch!  It worked perfectly.  Thanks!

---

### Post by Keithel on 2008-07-02
> **Zenyatta13 said:**
> Great job on the patch!  It worked perfectly.  Thanks!

Glad to be of help!

I found that the existing solutions posted around the net didn't fit what I wanted to do -- all the other solutions involve using non-vmware open tools, and the any-any patch.  I've never used those, nor do I feel I really need them, so I instead just patched up VMware's existing tools.

---

### Post by evanb on 2008-07-06
> **Keithel said:**
> NOTE: This will only apply to the tools package included with Workstation 6.0.4 build 93057.  YMMV with other VMware products and versions.The patches also worked with Vmware Server 1.0.6 build-91891, although I couldn't apply them directly because Server doesn't have the following files:

cpNameLite.c
kernelStubs.h

I just applied the patches for the files it DOES have manually, although you could probably edit the patch file to remove the non-applicable patches and run it through patch.

Also, I had to set the files to be writable before I made the changes:
```
chmod a+w vmware-tools-distrib/lib/modules/source/vmhgfs.tar
``` and
```
chmod a+w vmhgfs-only/*
```

Finally
```
tar uvf vmware-tools-distrib/lib/modules/source/vmhgfs.tar vmhgfs-only/
```

will update the existing tar file with just the changes, rather than replacing the entire file.

Many thanks to Keithel for this thread. I would never have figured out how to get vmhgfs compiled on my own.

---

### Post by ceac on 2008-07-10
Thank you! Your solution worked perfectly too for the version 6.0.3, build 80004, of Vmware Workstation, except that the "sources" directory in the tar path is actually called source. Regards!

---

### Post by storkman78 on 2008-07-10
You da man (or wo-man)!

Thanks a million for making the effort to put together this solution for us!

Storkman

---

### Post by Stumpy842 on 2008-07-12
@Keithel, this is great! If you would just modify your OP to include the advice from evanb to make the necessary files writable, it would be perfect! :)

Thanks a million!

---

### Post by Keithel on 2008-07-14
Ahh! I missed that.  Thanks Stumpy and evanb -- I overlooked that.
I have fixed the permissions problem with my instructions now -- it should work good now.

If more people find this useful, I'll try to find some time to fix up the post so it's in a nicer HowTo format with sections and better formatting of steps.

---

### Post by jung-kreidler on 2008-07-15
[SIZE="6"]COOL![/SIZE] You're such a crack! Worked like a charm. Thanks!:guitar:

---

### Post by benplanet on 2008-07-15
why is it telling me that it cannot find the command "patch" I am stock at step 8, somebody please help the noob!! 

I tried sudo apt-get install patch, and it says there is not such app.

---

### Post by Keithel on 2008-07-15
Ok, I did see that 'patch' is not in my instructions to install -- the people that have had success probably already had it installed.  I was thinking it was installed with the 'build-essential' package, but I investigated that, and it appears that it is not.

Now, you did say that you tried doing 'sudo apt-get install patch' --
That really should work -- There is a 'patch' package in Ubuntu Hardy Heron that provides the /usr/bin/patch command, which I use in the script.

Have you tried updating your list of packages from the sources? (Click the 'Reload' button from synaptic package manager, or type 'sudo apt-get update' from the command line)

---

### Post by Mountaingod on 2008-07-17
At step 8, I get the following error:

> patch: **** strip count l is not a number


I have checked as per step 1, and the program 'patch' is installed.

EDIT: My mistake, for some reason the patch command wasn't copying over into the console properly. I had to manually type in the '-p1' bit.

The patch is much appreciated, VMware tools appears to have installed properly now. Time to see if sharing works...

---

### Post by skm665 on 2008-08-13
I have the same problem.  At step-8.  There is a prompt saying file to patch.  Also step-3 it said not find build-essentials.

---

### Post by Keithel on 2008-08-13
Ahh you spotted a typo in step 3 -- the package is not named 'build-essentials', but 'build-essential' --
So the command would be:

```
apt-get install build-essential
```

So, clean up all that you've done sofar, and try the steps again with this change.

Subsequent steps after 3 depend on the build tools being installed, and thus will fail.

---

### Post by cyberDrake on 2008-08-19
Just wanted to say THANKS!

Worked like a charm for me. I just wish I would have found these instructions sooner.

~the cyberDrake

---

### Post by twoseids on 2008-08-21
I'm stuck on step 1!
> Perform the VM->Install VMware Tools... action in VMware to get the VMware Tools virtual CD mounted in Ubuntu.

This doesn't do anything for me. I get:
```
tar: /media/cdrom/VMwareTools-6.0.4-93057.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

What am I doing wrong?

---

### Post by BurekUSvemiru on 2008-08-23
thanks! works perfectly!

---

### Post by Mike21 on 2008-08-26
Works fine. Easy to use.
Thanks a lot!!!!!
Mike :)

---

### Post by Keithel on 2008-08-26
> **twoseids said:**
> This doesn't do anything for me. I get:
```
tar: /media/cdrom/VMwareTools-6.0.4-93057.tar.gz: Cannot open: No such file or directory
```

What am I doing wrong?

It's quite possible you're not using VMware Workstation 6.0.4 **build 93057**.  If you want to try with a different build of VMware workstation, the patches may not apply cleanly (because they may have changed the VMware tools sources), however, you can try applying the patches to a different VMware tools build..

Just alter the initial tar command I have listed with the VMwareTools-*.tar.gz that is actually present on your virtual vmware tools CD that gets mounted when you "Install VMware Tools" from the vmware menu, and follow the rest of the instructions.

Again, I do say that the patches I have provided in all likelihood will not work with different builds of VMware Tools, however it might, so it's worth a try.

---

### Post by SamStone33 on 2008-09-02
Thanks for the great info, it worked like a charm.

---

### Post by ckong on 2008-09-03
AWESOME! You're such a crack! 
Your patch works well with my VMwareTools-6.0.3-80004, and I don't know why VMware team don't fix it during 80004 to 93057, you should give them a hand:)
Thanks a lot again!

---

### Post by LaAmiGoo on 2008-10-02
Works like a charm. Thanks!

---

### Post by linkey_liu on 2009-09-26
thanks a lot.
I'v just downloaded it .

---

