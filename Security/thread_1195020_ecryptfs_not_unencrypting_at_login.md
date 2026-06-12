---
title: "ecryptfs not unencrypting at login"
date: 2009-06-23
forum: Security
---

### Post by dpatel on 2009-06-23
Hi All -

For some time now I've been using ecryptfs to create an encrypted Private folder in my home directory.

Not sure what I did (maybe after an upgrade), but it no longer mounted automatically on login to Ubuntu (I login using a username/password -- not auto login). I can see all the folders and filenames but they are encrypted (try to open and get random data).

Consequently, I have to mount manually.

It remains mounted/unencrypted after a suspend. Maybe it's designed like that?

Any ideas of what the issue is at the login stage or should I just delete my Private folder and re-install ecryptfs-utils?

---

### Post by Kobalt on 2009-06-23
Hello,

Did you record your mount passphrase ? 
```
$ ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase
```

---

### Post by Agent ME on 2009-06-23
Out of curiosity, what version of Ubuntu are you on? It sounds like you're on 8.* or below, since the filenames aren't encrypted.

Post the output of "ls -a ~/.ecryptfs". By default, the blank files auto-mount and auto-umount should be in this directory, controlling the filesystem's behavior.

---

### Post by dpatel on 2009-06-23
Hi - 

Kobalt - yes I did keep my mount passphrase. How can I use that?

Agent ME - Output of command:

```

.            Private.sig.20081031164404  wrapped-passphrase.20081031164404
..           Private.sig.20081116152008  wrapped-passphrase.20081116152008
auto-mount   Private.sig.20081116152604  wrapped-passphrase.20081116152604
auto-umount  Private.sig.20081116152648  wrapped-passphrase.20081116152648
Private.sig  wrapped-passphrase          .wrapped-passphrase.recorded

```

Edit: I am on Ubuntu 9.04

---

### Post by dpatel on 2009-06-25
Where did everybody go? :)

---

### Post by Agent ME on 2009-06-25
When you run 'ecryptfs-mount-private', are there any error messages or anything?

---

### Post by dpatel on 2009-06-25
No errors directly but in the user log (see below) there are errors. It doesn't actually mount the private folder either!


```
Jun 25 21:20:00 davesh-laptop gnome-screensaver-dialog: Passphrase key already in keyring; rc = [1] 
Jun 25 21:20:00 davesh-laptop gnome-screensaver-dialog: ecryptfs_add_passphrase_key_to_keyring: Error adding auth tok with sig [35e5a***********] to the keyring; rc = [1] 
Jun 25 21:20:00 davesh-laptop gnome-screensaver-dialog: Error attempting to add passphrase key to user session keyring; rc = [1] 
Jun 25 21:20:00 davesh-laptop gnome-screensaver-dialog: There is already a key in the user session keyring for the given passphrase.
```


Not sure if I needed to but I put the '*'s in the output above.

---

### Post by dpatel on 2009-07-06
Bump?!

---

### Post by lotwook on 2009-07-17
Have you had any luck? I am experiencing the same errors. Many times (perhaps every time) when they appear X crashes out with a signal 11 and boots me back to the login screen. This is reproducable if I launch Firefox or synaptic for example. I've done some digging and no luck thus far. Any help would be greatly appreciated!

---

### Post by dpatel on 2009-07-18
Well I ultimately re-installed ecrptfs utilities and re-created the Private folder (obviously copied the contents first as this action will completely delete the folder and all content).

Your problem sounds different to mine. Your issue seems to be not completely related to ecryptfs since Firefox and Synaptic can cause a crash. Could be related to X or graphics driver not correctly configured.

I'd suggest posting a new thread with full details of your problem. I usually get good help in these forums.

---

