---
title: "Script for mounting shares question"
date: 2009-01-29
forum: Server Platforms
---

### Post by MaindotC on 2009-01-29
How would you write a script to mount the shares listed at this website [http://helpdesk.morrisville.edu/DrivePaths.htm](http://helpdesk.morrisville.edu/DrivePaths.htm) (my college) using smb4k?

---

### Post by kidders on 2009-01-30
Hi there,

Personally, I would leave smb4k out of the picture ... I'm not sure involving it would do much more than increase the number of ways your script could fail. In theory, all you really need is something like ...```
for share in //CISNTS1/COURSES //CISNTS1/ACCT //CISNTS1/PUBLIC; do mount $share etc etc ...; done
```

In practice, you'd probably want to ...[LIST]
[*]Check your domain name or IP address to make sure you're on the right network before trying to mount loads of potentially non-existent shares.
[*]Before actually executing each mount, you could check that the share isn't already mounted somewhere. That way, if one of your shares fails to mount the first time around for some reason, you could safely re-run your script to try again.
[*]If you wanted to be really smart, you could try to establish whether any Windows shares mounted prior to running the script cause credentials conflicts.
[*]Either add each share to your /etc/fstab, or find a way of auto-generating mount point names. For example, **for share in //CISNTS1/COURSES //CISNTS1/ACCT //CISNTS1/PUBLIC; do echo /mnt/`echo $f | tail -c+3 | sed 's/\W/_/'`; done** would do a reasonably good job (ie basing the names of the mount points on the share paths).
[/LIST]

Anyhow, to answer the question you actually _asked_, smb4k is a KDE app, so dcop is your best bet. I don't have KDE installed on anything atm (so I can't check for you), but smb4k must surely expose a method for hooking into its share mounting feature. You would need to ...

[LIST]
[*]Find a reference to a pre-existing instance of smb4k, or instantiate a new one.
[*]Invoke the right method (a dcop browser will help you find it) repeatedly.
[*]Since your list of shares is quite long, you may want to experiment with what happens when smb4k can't access them, just in case you wind up writing a script that makes your machine unresponsive or spits 10 or 11 consecutive dialog boxes at you.
[/LIST]

I hope that helps.

---

### Post by MaindotC on 2009-01-31
The Places -> Connect to Server option doesn't work in 8.04 and is bug reported that's why I use smb4k :(  I don't know anything about scripting and I've not taken the time to google it and I was just hoping someone would post the script.  Thank you for the work that you did and I'll try and figure out the rest sometime.

---

