---
title: "Need help editing vista registry"
date: 2008-11-23
forum: Windows
---

### Post by dontgvadamn on 2008-11-23
I run both ubuntu and vista on my system. And Vista Screwed up big time after I did a uninstall of a app the other day. Basically the 3 user accounts I have. Guest, "true" admin and my normal account now all show up as a guest account. So I can not log in with admin privliges right now. I need to edit the registry to fix this. 

I am pretty new with ubuntu. So all the help I can get would be appreciated. I have some registry backups....and have my windows partition mounted in ubuntu. I am running ubuntu ultimate(version of herdy huron with bunch of stuff preinstalled.) 


What else do I need to do....and what steps?

---

### Post by mdurham on 2008-11-23
Is there a way to start Windows in so called 'safe mode'? Maybe this gives you admin privileges? I'm not a Windows person so I'm not really sure about this but you could try it.

---

### Post by p_quarles on 2008-11-23
Moved to Windows Discussions.

---

### Post by ITAndrew on 2008-11-23
You can run regedit in wine and open the hives manually. As far as where you need to go to repair the damage that has been done, I have no clue.

Have you tried safe-mode (Mash F8 after post). Are you able to view the local accounts there?

I know if it was corruption, you may be able to repair by running a: 
chkdsk /r
but you will need to be able to log in as an admin first.

I also know most of these problems occour when the ProfileGuid key was corrupted or deleted. You may want to google this to find a resolution.

---

### Post by dontgvadamn on 2008-11-23
Yes I tried safe mode...the problem is safe mode wont even start because the administrator account is now a guest account as well. only one that comes up even on the safe mode is guest...and it wont start because the accounts are guest instead of admin.

I looked in the registry and the profiles are all still there...so they didnt get deleted. It's somewhere in the securities...But I have some old registry backups that I can put back into vista through ubuntu...I am just not sure how to get to the path via the terminal...

---

### Post by ITAndrew on 2008-11-23
most hives are located in %SystemRoot%\System32\Config

For example, you would need to mount the drive/partition that has Windows installed on it. If it was mounted automaticly is is most likely located at /media/heresomewhere

So if you want to restore a hive you would:
1) First make another backup of your hives
2) replace the hives using your backup hives
3) try booting up again.

Need any further explanation?

---

### Post by dontgvadamn on 2008-11-23
nope I think I can get it from that...thanks...hopefully it works.

---

### Post by TeXtonyx on 2008-11-23
> **ITAndrew said:**
> most hives are located in %SystemRoot%\System32\Config

For example, you would need to mount the drive/partition that has Windows installed on it. If it was mounted automaticly is is most likely located at /media/heresomewhere

So if you want to restore a hive you would:
1) First make another backup of your hives
2) replace the hives using your backup hives
3) try booting up again.
Need any further explanation? 

In principle this is a good explanation. But Windows only does a
good registry backup during system restore. I doubt if he used ERUNT.
So I don't think he can run System Restore and choose an earlier
time. He might try F8 and use 'last known good configuration'.

It's likely Windows hasn't shut down properly, so one can't mount
the Windows partition to backup key data. So I think OP would need
to shut down Windows cleanly for mounting the Windows partition
from Ubuntu to work. 

I think OP should do as much backup as possible before trying to
fix the registry or he may lose even his ability to login as guest,
so making backup more difficult. I thought that the guest account
wouldn't have sufficient permissions to backup or restore the hives?

I don't think the registry backup restore will work. OP may be able to
do a non-destructive reinstall to C:\Windows.000 which will save
his data except My Documents but will lose most of the applications.
They will have to be reinstalled. That's in case he has tried
the registry restore and it failed and he can't do backups from
Ubuntu because Windows won't boot at all, not even to guest.

---

### Post by TeXtonyx on 2008-11-23
I seem to recall that after you login as guest and it loads, that 
there is an option to switch user. Is that available to guest?

Try switching users and logging in with your regular username
that usually has admin privileges. This might be broken also
but then again it might be separate from the damaged part of
the registry, anyway it's worth trying. I think you may not be
able to change the registry from the permissions available to
you from the guest account. 

I think it it time to do backups. Boot to guest and cleanly
shutdown windows so that Ubuntu will allow the Vista partition
to be mounted. Then you can copy some stuff over and write it
to a cd or dvd or usb stick. If this fails ...

Try first a repair install. Then next an install which is called
non-destructive which writes to C:\>Windows.000 
The data is mostly safe but you lose the applications. 
After Vista repairs/reinstalls which may write to the MBR,
you will need to reinstall grub to the MBR unless you use
Easybcd to boot Ubuntu. Oh, and try last know good configuration
an option available from the F8 bootup first. You are going to
need a Vista install disk, not an OEM recovery disk for the
non-destructive reinstall. There is a Vista recovery disk (only)
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Erunt and ntregopt will work for Vista and x64 bit also. Read the 
report below and you'll see why I'm pessimistic about your chances, 
so don't spend a lot of time trying to restore the registry. 

[http://www.larshederer.homepage.t-online.de/erunt/erunt.txt](http://www.larshederer.homepage.t-online.de/erunt/erunt.txt)

"Note: The "Export registry" function in Regedit is USELESS (!) for
making a complete backup of the registry. Neither does it export the
whole registry (for example, no information from the "SECURITY" hive
is saved), nor can the exported file be used later to replace the
current registry with the old one. Instead, if you re-import the 
file, it is merged with the current registry without deleting anything 
that has been added since the export, leaving you with 
an absolute mess of old and new entries."

---

