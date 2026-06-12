---
title: "does ssh protect my ubuntu installation?"
date: 2017-06-11
forum: Security
---

### Post by blender12 on 2017-06-11
hello i followed this tutorial
[https://help.ubuntu.com/community/StricterDefaults](https://help.ubuntu.com/community/StricterDefaults)

i want to know if my ubuntu installation (home folder, root) are protected and nobody can acces my computer or my files in it if they don't know the passphrase:confused:

---

### Post by blender12 on 2017-06-12
Anyone?

---

### Post by again? on 2017-06-12
As stated in that article the best security is to use public key authentication and not passwords.
> Disable Password Authentication
One may also tighten security by forcing public key authentication and disabling password authentication entirely. While this greatly enhances security and completely defeats brute-force attacks, it will lock you out of the machine if you lose your private key. Use with caution.

---

### Post by Habitual on 2017-06-12
Most of the "tutorial" I have found is for forward facing hosts

If you install openssh-server locally, this tutorial would apply.
If you have not installed openssh-server this tutorial does not apply.
If you have a router, this tutorial may not apply.

None of that applies if I can walk up to your system and pop in an "Evil Maid" disk, or other bootable media.
Secure things in layers.

---

### Post by blender12 on 2017-06-12
oh so i should use criptfs
i already tried from a tutorial posted somewhere here it didn't worked
it was filled with errors
i need to know how to transfer without creating temporary admin account
if there any "on the fly" solution?

---

### Post by Habitual on 2017-06-12
I utilizse ssh-keys and scp.

criptfs for what?

Please have a read of the [Ubuntu Security]("https://ubuntuforums.org/showthread.php?t=510812") Thread
for recommendations, I guess.

and additionally, 
[https://help.ubuntu.com/community/SSH/TransferFiles](https://help.ubuntu.com/community/SSH/TransferFiles)
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by HermanAB on 2017-06-13
To answer the original question:
The SSH daemon provides secure remote access to your computer, IIF it is configured properly.

By default Ubuntu allows you to create very short nonsensical passwords.  If your password is 4 characters, then your machine will not be secure.  If your password is longer than 12 characters, then it is good.  The longer the better.

When you expose SSH to the world, your machine will be found by script kiddies who will run programs to scan thousands of passwords per hour.  One simple way to avoid this is to configure SSH to run on a different port, eg 2222, instead of 22.  Another way is to disable password access completely and only allow key access.  A key is a much longer thing, that is impossible to type by human beings and impractical to add to brute force scripts.

---

