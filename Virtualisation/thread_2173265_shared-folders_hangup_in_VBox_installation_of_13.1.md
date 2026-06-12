---
title: "shared-folders hangup in VBox installation of 13.10 beta1"
date: 2013-09-08
forum: Virtualisation
---

### Post by jamzen on 2013-09-08
I guess the title says it all.  It's the recent 4.2.18 release of VBox.

     sudo mount -t vboxsf [sharename] [mountpoint]

completes without an error, and

     df

shows the mount, but

    ls [mountpoint]

hangs.  Anybody else see this behavior?  Find a fix?

---

### Post by TheFu on 2013-09-08
Verify that the correct version of the guest additions matches 100% to the VM host virtualbox release. 
If in doubt, reinstall the guest additions and reboot the VM.

Sometimes a new kernel will not relink with the vbox guest additions automatically or we might forget to update them with the new vbox host version update.  I know that I forget.

---

### Post by jamzen on 2013-09-08
Uh-huh, I've done that.  Two or three times.

---

### Post by TheFu on 2013-09-08
> **jamzen said:**
> Uh-huh, I've done that.  Two or three times.

Seems like time to open a bug against the alpha code.  Anything interesting in the logs to share?

---

### Post by jamzen on 2013-09-08
> **TheFu said:**
> Seems like time to open a bug against the alpha code.  Anything interesting in the logs to share?

Nothing in the logs on the 13.10 VM.  Nothing odd in the [guestnode].xml under VB.  Nothing in the host logs.  Just the guest hangup at any attempt to access the shared mount.

How to open a bug?  Against VirtualBox, or against Ubuntu 13.10 beta1?

Come to think of it, when this problem first showed up yesterday (anxious to try out the beta1), I was running VB 4.2.16.  There was a thread on one of the VB forums: the shared-folder Guest Additions module wouldn't compile for me.  That was 'fixed' in 4.2.18, but then we arrived at the problem I'm posting about.

I'm going to assume this is a problem in VB.

Thanks for your help.

---

### Post by TheFu on 2013-09-09
Let's step back for a second.

You are running an alpha version of Ubuntu and think that opening a bug against VB is correct?
I just had to ask.

---

### Post by jamzen on 2013-09-09
Uh, well, when you put it that way... .

How would I open a bug here against 13.10?

---

### Post by TheFu on 2013-09-09
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) - google found it, BTW.  Ubuntu Forums **is not** a bug reporting tool.

I take it you've not looked at my signature about running an LTS?

---

### Post by jamzen on 2013-09-11
> **TheFu said:**
> [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) - google found it, BTW.  Ubuntu Forums **is not** a bug reporting tool.

I take it you've not looked at my signature about running an LTS?

The VirtualBox 4.2.18 which I alluded to in my original posting is running under Ubuntu 12.04.

I test new Ubuntu releases on one or more of the dozen VM's I've configured.  That's the context in which I started this thread.

---

### Post by Morbius1 on 2013-09-11
May I ask why you are mounting something with a "sudo mount -t vboxsf [sharename] [mountpoint]" when it's already mounted for you at /media/sf_sharename.

---

### Post by jamzen on 2013-09-12
> **Morbius1 said:**
> May I ask why you are mounting something with a "sudo mount -t vboxsf [sharename] [mountpoint]" when it's already mounted for you at /media/sf_sharename.

Uh -- it isn't.  I believe that happens only when one requests 'auto-mount' for a shared folder.  I don't usually do that.

I just now tried configuring it that way, to see whether it makes any difference in the behavior I'm reporting.

It doesn't.

---

### Post by rooijan on 2013-09-14
I am seeing the same issue.  Can mount the shared folder but not able to list anything in there as root or my own user.  And I am part of the vboxsf group.   
# df -h | grep DATA
DATA            239G  226G   13G  95% /media/sf_DATA

And yes we all understand it's **beta** and not supposed to work.  Just reporting it so we can help get ahead of the problem before released.

---

### Post by rooijan on 2013-09-14
Update:  I can actually see and even copy a single file.  So the problem is related to expanding the list of files / dirs.  Be carefull leaving your system trying to access that shared folder, I think its in a loop at that stage and may affect performance.

$ ls -lh /media/sf_DATA/dell_warranty.py
-rwxrwx--- 1 root vboxsf 1.6K May 21 08:06 /media/sf_DATA/dell_warranty.py

---

### Post by entangled on 2013-09-15
I agree rooijan. I have kubuntu 13.10 b1 installed on virtualbox 4.2.18 r88780 on my iMac. 
I can set up a shared folder, and it auto mounts, but I can't list files or folders inside a folder. I can 'ls' a single file, as long as I give ls the full path.
I noticed the automount sets gid=1001 (an unknown group), whereas my user has gid=1000.
I have tried a manual mount at /mnt/share, using gid=1000. No different.
The same shared folder works well from Arch, also running in another virtual image on the same machine, but not simultaneously. This implies the mac side of things is OK.
One of us should report this bug. It could be for virtualbox or for ubuntu, but also the 3.11 kernel was just introduced, so...?
Do you know how this bug should be raised?

---

### Post by bearnard on 2013-09-21
Same issue here with Ubuntu 13.10b1 guest on osx, VBOX 4.2.18r88780, I'm going to try with a 12.04 guest and report back.

---

### Post by chaat on 2013-09-30
I can confirm that this issue happens with Lubuntu 13.10 but works correctly with Lubuntu 13.04 both with VirtualBox 4.2.18

is there a bug report on this ?

I'm a noob when it comes to linux, so I'm probably not the best person to report this.

it appears that this may be related to VirtualBox, see the link below

[https://forums.virtualbox.org/viewtopic.php?f=15&t=57437&p=267725#p267725](https://forums.virtualbox.org/viewtopic.php?f=15&t=57437&p=267725#p267725)

it appears to be fixed with virtualbox 4.3 beta3

---

### Post by rooijan on 2013-10-03
As people mentioned its a bug for the 3.11 kernels.  If you absolutely can't wait for virtualbox to be patched you can try temporarily fixing it by updating **dirops.c** source and recompiling.  I saw the patch here [https://www.virtualbox.org/changeset/48529/vbox](https://www.virtualbox.org/changeset/48529/vbox)

root@rrosso-VirtualBox:/opt/VBoxGuestAdditions-4.2.18/src/vboxguest-4.2.18/vboxsf# diff dirops.c dirops.c.orig
285,289c285
< 	if (!dir_emit(ctx, d_name, strlen(d_name), fake_ino, DT_UNKNOWN)) 
< 	{ 
< 		LogFunc(("dir_emit failed\n")); 
< 		return 0; 
<  	}
---
>         err = dir_emit(ctx, d_name, strlen(d_name), fake_ino, DT_UNKNOWN);
291a288
> #endif
299c296
< #endif
---
> 

root@rrosso-VirtualBox:~# /etc/init.d/vboxadd setup
...
Removing existing VirtualBox non-DKMS kernel modules ...done.
Building the VirtualBox Guest Additions kernel modules ...done.
Doing non-kernel setup of the Guest Additions ...done.
You should restart your guest to make sure the new modules are actually used

---

### Post by entangled on 2013-10-03
If you happen to be using Arch the problem has been fixed already in the rolling update of virtualbox_guest_modules_4.2.18-4.

---

### Post by DbhTPnx on 2013-10-19
Virtualbox 4.3 is out, which resolves this issue on Ubuntu 13.10. "Check for updates" doesn't indicate 4.3 available, but grab it from the downloads page.

---

### Post by Harry_Percival on 2013-10-24
what [**[COLOR=#000000]DbhTPnx[/COLOR]**]("http://ubuntuforums.org/member.php?u=1872256") said.  New Virtualbox 4.3 fixes it :)

---

