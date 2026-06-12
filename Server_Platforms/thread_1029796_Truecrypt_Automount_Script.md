---
title: "Truecrypt Automount Script"
date: 2009-01-03
forum: Server Platforms
---

### Post by zenmatrix on 2009-01-03
I created a script called auto_mount_datastore and placed it in /etc/init.d/ there script contains
*****
truecrypt /dev/sdb --password="Passwordhere" /media/tc --protect-hidden=no -k=
*****
I made it a executable by doing chmod +x auto_mount_datastore.
Then I ran update-rc.d auto_mount_datastore. I restart I try going to /media/tc get permisson denied, as root no problem. I dismount the volume, then run it as root. the exit out of root I can access it, but If I restart the same thing happens again. Am I missing a step here.Thanks for any help.

---

### Post by _madman_ on 2009-08-17
Hello.

Do you have this issue on truecrypt usage [http://forums.truecrypt.org/viewtopic.php?t=15761](http://forums.truecrypt.org/viewtopic.php?t=15761) ?

---

