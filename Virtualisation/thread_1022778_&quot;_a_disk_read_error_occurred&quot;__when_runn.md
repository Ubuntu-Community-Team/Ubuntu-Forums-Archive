---
title: "&quot; a disk read error occurred&quot;  when running cloned .vdi"
date: 2008-12-27
forum: Virtualisation
---

### Post by falkob on 2008-12-27
Hi

i'm brand new to ubuntu and virtual box so please bear with me.

i installed virtualbox yesterday and created a virtual HD for my guest windows xp system.
after much effort i managed to clone the hard disk or .vdi file using the VboxManage clonevdi command in the terminal.

in virtual machine i selected this hard disk as an existing hard disk and started the cloned virtual machine but i get a black screen with an error message " a disk read error occurred" press ctrl+alt+del  and that's it.

i already tried googling it but didn't find anything very useful.

has anyone encountered this and can suggest a solution or a direction?

cheers
falkob

---

### Post by falkob on 2008-12-28
anyone care to lend a hand?

---

### Post by formerwindowspoweruser on 2008-12-28
Hello. I had this same problem yesterday with the newest version of virtualbox.  If I understand correctly, it's an issue due to the upgrade of virtualbox. I'm using 
$ VBoxManage -v
2.1.0r41146
on Ubuntu 8.10 (fresh host install too)

First, try clonevdi command:
$ VBoxManage clonevdi WinXP_gaming.vdi WinXP_using_clonevdi.vdi -format VDI

Since we can't seem to get that to work, there's clonehd:
$ VBoxManage clonehd WinXP_gaming.vdi WinXP_using_clonehd.vdi -format VDI

When that didn't work, I tried running the same two commands from within a Windows XP install, same effect when I tried to start the cloned drives in the Ubuntu host virtualbox (NOTE: I didn't try starting the cloned drives in Windows virtualbox.)

Lastly, the SOLUTION!
see [http://forums.virtualbox.org/viewtopic.php?p=50761&sid=259e31af6ebcb27e2b9c527908487e10]("http://forums.virtualbox.org/viewtopic.php?p=50761&sid=259e31af6ebcb27e2b9c527908487e10")

There's an "internalcommand" that allows you to simply change the disk UUID. To use this, copy the desired vdi, then run
$ VBoxManage internalcommands setvdiuuid <filename>.vdi

I was able to use this copied vdi along side the original, since the UUID had been changed.

Please let me know if this worked for you.

---

### Post by falkob on 2008-12-29
Hi,

Thank you for your help, i did the change uuid command and it changed the uuid, however i still get the exact same error message.

if this problem happens only in the latest virtual box 2.1.0  and not in 2.0.6, how can i uninstall the current virtual box and try the older version?

cheers
falkob

---

### Post by albinootje on 2008-12-29
> **falkob said:**
>  if this problem happens only in the latest virtual box 2.1.0  and not in 2.0.6, how can i uninstall the current virtual box and try the older version? 

Are you using the OSE (Included in Ubuntu repositories) or PUEL version (From the VirtualBox website) of VirtualBox ?

What file-system are you using ?
I had some problems in the past in Ubuntu with vdi files which were in a NTFS-partition.

---

### Post by falkob on 2008-12-29
Hi

i use the virtualbox i loaded from the virtualbox website so i guess it's puel.

i have no idea which filesystem i use and how to check it, i know ext3 is the default but i couldn't see what i have anywhere.

cheers
falkob

---

### Post by albinootje on 2008-12-29
> **falkob said:**
>  i use the virtualbox i loaded from the virtualbox website so i guess it's puel.

i have no idea which filesystem i use and how to check it, i know ext3 is the default but i couldn't see what i have anywhere.


Okay, then it's probably not a problem related to the filesystem.
If you really want to remove VirtualBox to use an older version

Check the version with this :
```

dpkg -l|grep -i virtualbox

```

On my machine it looks like this, the ii means that 2.1 is installed.

rc  virtualbox-2.0  2.0.6-39765_Ubuntu_intrepid Sun xVM VirtualBox
ii  virtualbox-2.1  2.1.0-41146_Ubuntu_intrepid Sun xVM VirtualBox

Removing it :
```

apt-get remove --purge virtualbox-2.1

```

---

