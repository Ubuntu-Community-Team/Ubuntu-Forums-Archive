---
title: "How Do I Prevent Users From Running &quot;VirtualBox&quot; command?"
date: 2010-10-24
forum: Virtualisation
---

### Post by AlexanderDGreat on 2010-10-24
Hi!

I have an Ubuntu HOST Lucid Lynx 32bit, but there are multiple users in this machine.

Now, I noticed:

**They can type _VirtualBox_ from the command line.**

And they'd be given full access to the Virtualbox GUI and thus manipulate guest machines, do something malicious like boot from the cd, create hard drives, etc...

I want to be the only one to tinker with my Virtualbox settings because I'm the Sudoer, but I find this difficult to do. :confused:

How do I prevent users from running "VirtualBox" or the Virtualbox GUI entirely?

Is there another way to solve the problem?

Please help! Thanks.

---

### Post by mikewhatever on 2010-10-24
Look at the permissions of "VirtualBox" with "ls -l /usr/bin/VirtualBox". If all the other users are not sudoers, denying the executable bit to 'others may work'

sudo chmod o-x /usr/bin/VirtualBox

---

### Post by AlexanderDGreat on 2010-10-24
Hi mikewhatever! Thanks for replying.

If I TAKE AWAY the **Executable Permission of Virtualbox.**

Other uses won't be able to AutoRun their Virtualboxes.

Because I autorun the Virtualbox by

```
VBoxManage startvm Microsoft\ Windows\ XP
```

Try taking away the executable of VirtualBox, and there's _practically NOTHING YOU CAN DO TO LAUNCH_ other Virtualbox commands!

I think it's a BIG SECURITY ISSUE in the part of VirtualBox! :(

---

### Post by mikewhatever on 2010-10-24
Do your users need to have Terminal access at all? If not, take that away.

---

### Post by Manifest on 2010-10-24
> **mikewhatever said:**
> Do your users need to have Terminal access at all? If not, take that away.
How?

---

### Post by AlexanderDGreat on 2010-10-24
@Manifest - Just go to System > Administration > Users & Groups >

Click on the user, Advanced Settings > Advanced

Set the terminal to /bin/false

Yes I agree, all workstations should not be allowed a Command Line, it's practically access to the whole system! In Windows I also disabled the Command Line, however in Ubuntu, for some strange reason, I've disabled the Terminal Bash, But right click on the desktop > Make a Launcher, and type there VirtualBox,

And VirtualBox GUI rears its Ugly Head! What a shame, don't worry, I've found a Quick & Dirty Step:

> Backup first your VirtualBox command, it's found in /usr/bin/

sudo cp /usr/bin/VirtualBox /home/username

Then remove it entirely:

sudo rm /usr/bin/VirtualBox

There!

PS I hope someday they will make a feature to password protect the VirtualBox GUI! It makes sense.

---

### Post by AlexanderDGreat on 2010-10-24
Finally, to launch the VirtualBox GUI again, you must login as the SUDOER or where you put the file.

From that folder, launch ./VirtualBox

You must also chmod 700 VirtualBox - so only the owner of the file can launch the Command and thus MANIPULATE the GUI.

PS You can also Delete the VirtualBox CDROM drive from the GUI Settings, to prevent your VirtualBox Guest OS'es from booting to Live CD's / DVD's.

VirtualBox... why didn't you think of such security issues? Does VMware have these?

---

