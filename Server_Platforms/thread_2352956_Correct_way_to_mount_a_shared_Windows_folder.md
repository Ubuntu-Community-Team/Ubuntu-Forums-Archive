---
title: "Correct way to mount a shared Windows folder?"
date: 2017-02-17
forum: Server Platforms
---

### Post by voyto on 2017-02-17
Hi all!

I'm fairly inexperienced when it comes to Ubuntu / Lubuntu, however I've managed to work out most things I've needed with the help of these forums - thanks!

One thing I am struggling with however, is setting up a reliable mount from a Windows 2003 Server. Here is what I've done so far....

We have a Windows network with Server 2003 as our Domain Controller. On here, I have a folder C:/Users being shared.

I have VirtualBox on a Windows 7 host, running Lubuntu 16.10, on the same LAN. Lubuntu has a local IP address 192.168._._ by setting VirtualBox's network adapter into Bridged mode. Unlike the Windows machines, this Lubuntu setup hasn't joined the domain - I'm not sure if this is a thing with Linux? Should I be joining the domain?

OK, next up, I've installed the cifs-utils on Lubuntu and edited the /etc/fstab file to include the line below.....

```
//aimsserver/users    /mnt/Users    cifs    credentials=/home/email/.smbcredentials,defaults,users,uid=1000,rw  0  0
```

When I boot Lubuntu, I get a successful mount in /mnt/Users and it all works perfectly. I've created bookmarks to subfolders within this mount to make life easier for me when i navigate to common folders, by right clicking the folder and "+ Add Bookmark".

The issue I'm having is Lubuntu seems to drop the mount and cause the machine to hang. I have to reboot Lubuntu around 4-5 times a day to restore the mount. When the machine hangs, it's pretty unusable until I reboot. 

Does anyone have any idea's on what might be giving me this issue, or a better way to mount the shared folder?

Thank you in advance! :)

---

### Post by SeijiSensei on 2017-02-17
Sounds like a network problem of some sort.  You could run a simple script on the Lubuntu machine to keep the connection alive.  Here's a quick attempt:
```

#!/bin/bash

# script to check on remote connection and restart it as needed
CHECK=$(mount | grep /mnt/Users)

if [ "$CHECK" = "" ]
then
     mount -t cifs -a
fi
exit 0

```

Run this from /etc/crontab by adding a line like this
```

*/5 * * * * root /path/to/script

```
That runs "/path/to/script" every five minutes.  If you replace "*/5" with just "*" it will run every minute.

---

### Post by voyto on 2017-02-17
Thanks - should I try running [COLOR=#000000][FONT=&quot]mount -t cifs -o remount -a[/FONT][/COLOR] from terminal when it happens, before implementing this, to see if it fixes the issue?

---

### Post by SeijiSensei on 2017-02-17
Yes, though you'll need to use "sudo mount ..." and leave out the "-o remount".  I edited my post to remove it because I realized that if the share isn't mounted at all, remount should not apply.

Commands invoked from /etc/crontab run with root privileges so sudo isn't required.

---

### Post by voyto on 2017-02-20
Thank you for this. It's half solved my issue.....

If I run "sudo umount -a" when the issue happens, it will hang for about 30 seconds with the message "umount: /run/user/1000: target is busy" followed by some more busy messages. However it eventually works.

Then I run your "sudo mount -t cifs -a" and the connection is restored.

Would it just be a case of including the umount command in the script you helped me with? (If so, would you mind helping me with that?)

Thank you again!

---

