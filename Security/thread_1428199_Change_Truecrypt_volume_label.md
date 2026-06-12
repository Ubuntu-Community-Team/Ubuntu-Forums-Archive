---
title: "Change Truecrypt volume label"
date: 2010-03-12
forum: Security
---

### Post by nh2 on 2010-03-12
Hi,

is it possible to change a truecrypt volume label so that appears not as "truecrypt1" but rather as "myStick"?

Thanks!

---

### Post by 2hot6ft2 on 2010-03-12
Not that I could find

---

### Post by bodhi.zazen on 2010-03-12
From here:

[http://www.truecrypt.org/docs/?s=troubleshooting](http://www.truecrypt.org/docs/?s=troubleshooting)

> **Problem:**  *The label of a filesystem within a TrueCrypt volume cannot be  changed under Windows Vista or a later version of Windows.*
 **  Cause: **
 A Windows issue causes the label to be written only to the Windows  registry file, instead of being written to the filesystem.
 ** Possible Solutions: **
  
[LIST]
[*]This issue affects only volumes that are not mounted as removable.  Hence, if you want to change the label reliably, make sure the option '*Mount  volume as removable medium*' in the [Mount  Options]("http://www.truecrypt.org/docs/mounting-truecrypt-volumes") is enabled (or that the option '*Mount volumes as  removable media*' in the Preferences is enabled) when mounting the  volume.
[*]This issue affects only labels set via the Windows GUI. Hence, if  you want to change the label reliably, you can use the label command to do so.
[/LIST]

So you can try setting the label from the window command line (use the command label) or you can try from Linux :

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by DragonDon on 2010-06-08
> **bodhi.zazen said:**
> From here:

[http://www.truecrypt.org/docs/?s=troubleshooting](http://www.truecrypt.org/docs/?s=troubleshooting)


So you can try setting the label from the window command line (use the command label) or you can try from Linux :

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Ok, I gotta ask, what does "TrueCrypt volume cannot be changed under Windows Vista or a later version of Windows." have to do with Ubuntu?  That quote just kinda confused me as I see no relevance.

GParted initially seemed to be a good suggestion but does not recognize the partition.

And it seems that it's not so much the name but the mounting point.  Once I understand how to change the mounting point, then the name will change :)

---

### Post by bodhi.zazen on 2010-06-09
> **DragonDon said:**
> Ok, I gotta ask, what does "TrueCrypt volume cannot be changed under Windows Vista or a later version of Windows." have to do with Ubuntu?  That quote just kinda confused me as I see no relevance.

GParted initially seemed to be a good suggestion but does not recognize the partition.

And it seems that it's not so much the name but the mounting point.  Once I understand how to change the mounting point, then the name will change :)

The OP did not specify what OS s/he is using, so I gave an answer that should work in either OS.

What problem are you having ? The "solution" varies, are you trying to set a mount point, change a file system label, or change the truecrypt label ?

If you need assistance, I highly suggest you start your own thread. Hard to know how a thread from another person from a month ago is relevant to your problem, which may be why the advice does not apply to your situation. Be sure to specify the problem you are having.

---

### Post by Ordes on 2012-03-02
might be late,.. but perhaps usefull for other people that come over this post...

if you want to make your volume appear under your custom label, you need to mount it on that folder.

# create a mystick folder in /media
# when mounting, choose options, and select mount folder (/media/mystick)
# your volume should now appear under mystick, instead of truecryptX

---

