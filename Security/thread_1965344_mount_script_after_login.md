---
title: "mount script after login"
date: 2012-04-25
forum: Security
---

### Post by paulwall on 2012-04-25
Hi @ll,

I need to run a script after user login to auto-mount a shared folder.

The password for the shared folder is located in the encrypted user directory (/home/user) and therefore only accessible after login.

How would you setup this to work? :guitar:

---

### Post by papibe on 2012-04-25
Hi paulwall.

Then it looks like the best place is to set a task on 'Startup Application' under your system menu. The task defined there are executed right after you login into the GUI.

I hope that helps. Tell us if you need more help with that.
Regards.

---

### Post by paulwall on 2012-04-25
Yes, it would start after login, but I cant mount a share in my script if I have no root permissions..

---

### Post by jerome1232 on 2012-04-25
Would putting it in fstab, with the noauto and user option work? noauto would make it not mount at boot time, user would allow a regular use to mount it.

---

### Post by paulwall on 2012-04-25
thank you.. this is what I've found after over 4 hours of search ;)

This seems to work but files are created with root as owner and I can't edit them on the shared folder..

Permissions for unmounted shared folder on **/mnt/mysharedfolder** are set to **chown myuser:myuser /mnt/mysharedfolder**.

The **user **option in **/etc/fstab** seems to be the problem, because if I set the options to **uid=myuser,gid=users,rw,noauto,exec,sync** and mount it with root permissions it will work.

With the **user **option it will mount without root permission but files are created as root user?

---

### Post by oklokl on 2012-04-26
Try this application.
I autorun
I do not know how it works
sorry..





udisks man


#!/bin/bash
udisks --mount /dev/sdbx


#!/bin/bash

udisks --unmount /dev/sdbx

---

### Post by jamvaru on 2012-10-14
Hi, sorry to raise an old thread, but I'm having trouble finding an answer to my question, which is almost answered here.

Where would be the place to find an answer like the one I need?

I wish to add automount to my fstab (i guess, so a disc is mounted at boot) but also to add 'inherit' to the modifiers, so all the files inherit the parent directory permissions.  I would also like to know how to add this modification to a setting so any time I mount the drive after boot, say I unmounted it, then it mounts with the 'inherit' option.

I read somewhere that this is the answer to removing the $SECURIY_DESCRIPTOR from the files on an ntfs drive, so the defragmenter doesn't freak out so much, and they are unmovable

Can you give me a sample fstab listing?

---

