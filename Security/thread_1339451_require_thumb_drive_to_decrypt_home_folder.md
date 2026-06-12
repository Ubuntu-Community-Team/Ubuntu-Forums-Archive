---
title: "require thumb drive to decrypt home folder"
date: 2009-11-27
forum: Security
---

### Post by deadowl on 2009-11-27
I decided that I'd try encrypting my home folder since the option was there during installation. I was somewhat surprised that when I logged in, my home folder would automatically be decrypted without my using my passphrase. It's certainly convenient, but if my encryption passphrase is a lot stronger than my login passphrase, there is really no benefit to my encryption passphrase being stronger, or even being different.

I came up with an idea of what I might want to try instead: why not just have a ridiculously strong random passphrase that is automatically read in from external media? In essence, I could have my old 12MB USB thumb drive turn into a physical key that unlocks my computer, as well as create a very inexpensive copy that can be kept somewhere safe.

WARNING: this does NOT work, I am here to ask for help.

1. I inserted my thumb drive.
2. It automatically mounted.
3. Labelled and formatted the thumb drive to be an ext4 filesystem owned by me.
4. Moved the physical version of ~/.ecryptfs to my thumb drive.
5. Created a symbolic link to the .ecryptfs folder on my thumb drive.
6. Restarted my computer, and was unable to decrypt my home folder (thumb drive didn't mount).
7. Restored the old version.

The thumb drive was not mounted, and I have no idea how to properly use the mount command (though I learned a little bit by reading through the man page). GNOME also wouldn't load because the home folder was set to read-only by default.

I also don't know whether I'm going in the right direction with this at all.

---

### Post by User0123 on 2009-11-27
Why not just encrypt the whole disk and put /boot on a flash drive? Surely that would be even better, not to mention easier.

---

### Post by deadowl on 2009-11-27
It would be easier, but not as flexible.

---

### Post by scorp123 on 2009-11-27
[https://help.ubuntu.com/9.04/serverguide/C/ecryptfs.html](https://help.ubuntu.com/9.04/serverguide/C/ecryptfs.html)

---

### Post by deadowl on 2009-11-27
> **scorp123 said:**
> [https://help.ubuntu.com/9.04/serverguide/C/ecryptfs.html](https://help.ubuntu.com/9.04/serverguide/C/ecryptfs.html)

merci beaucoup

---

