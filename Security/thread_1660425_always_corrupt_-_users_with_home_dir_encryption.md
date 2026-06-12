---
title: "always corrupt - users with home dir encryption"
date: 2011-01-05
forum: Security
---

### Post by Unhackmee on 2011-01-05
Hey guys,

I installed lubuntu from the alternate disk to a Toshiba NB205 netbook today... (GUI installer got stuck)

Before this, i had UNR with a home encrypted user, so i selected home encryption on lubuntu too.. but when i logged in (lxde), the menu had no other option except "*Run*" and "*Log-off*".. The chrome and minimize shortcuts in the bottom panel don't do anything when clicked.

logging into the **ctrl+alt+F1** thing (*sorry i have no idea what its called*) - I was able to create another user, but to no avail. 

It took me a while to discover that users with unencrypted home DIRs are fine. I tried to take a screenshot to attach, but it doesnt seem to work either...

The only files that seem to be in the home folder of an encrypted home DIR is:
**_.bash_logout  .bashrc  .ecryptfs  .Private  .profile_**

So how can i create a working user with an encrypted home dir, and has this happened to anyone else... (i did try searching)

Sorry if i lost you half way there, but hey- i couldn't take a picture to show you a thousand words... :-(

Thank-you

[COLOR="Red"]Edit>>[/COLOR]
```
ecryptfs-migrate-home
``` doesnt seem to work... so i guess it isnt to do with the incorrect setup of the account..

---

### Post by Unhackmee on 2011-01-05
[COLOR="Red"]Update:[/COLOR] [*I have got this far*]

Okay, so i created another ***test*** admin user. and after logging off , i switched to a tty console, and then logged in.
```
$sudo ecryptfs-migrate-home
```

This creates a user, which has all the ciphered stuff in ~/.private .. and after issuing:
 ```
ecryptfs-insert-wrapped-passphrase-into-keyring
```
I switched back to the graphical mode and logged in to find the sadly familiar little non-working desktop. So after logging out i issued:
```
ecryptfs-mount-private
```
this mounted the right files at the right place supposedly, because my unencrypted files have now been encrypted and are exactly where i left them.

Now i have to manually run the mount-private command. The auto mounting feature doesn't seem to be working. Can a security expert or someone with the right know-how please point me in the correct direction? 

Thankyou

---

### Post by joris1977 on 2011-01-21
Same issue here. Would be cool if someone has a solution. Maybe there should be a bug report about this, but I don't feel experienced enough to create one.

---

### Post by joris1977 on 2011-01-21
Ok it seems to be a known issue...
[URL="https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/LucidLynx"]
https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/LucidLynx[/URL]
> 
Encrypted partitions must be listed in /etc/fstab

Users who have configured any encrypted partitions in /etc/crypttab to start at boot time (i.e., not using the noauto option) should make sure that the filesystems on these volumes are listed in /etc/fstab. Otherwise, the passphrase prompt is not guaranteed to be displayed at boot time. 

But I have no clue how to do this. If I can figure it out I will post here...

---

