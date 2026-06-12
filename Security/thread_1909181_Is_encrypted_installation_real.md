---
title: "Is encrypted installation real?"
date: 2012-01-14
forum: Security
---

### Post by giantpc on 2012-01-14
So lets say I run the "Ubuntu Encrypted Installation" (LVM) to install Ubuntu, and then I boost into my encrypted installation.

I then install 5 programs and add 5 files to my home directory which I also set to "Encrypt Home Directory".

1) Are the 5 programs encrypted too? Or are new programs that are installed never encrypted?

2) Are the 5 files that I put into my home directory automatically encrypted without me doing anything?

3) Are all new files added to the system encrypted too, and if yes, then when are these files actually encrypted? When the new files are created? If I create a text file and put it in my home directory -- when is that text file encrypted? Right then and there, after reboot, after log-in/log-out? When?

---

### Post by Dangertux on 2012-01-14
> **giantpc said:**
> So lets say I run the "Ubuntu Encrypted Installation" (LVM) to install Ubuntu, and then I boost into my encrypted installation.

I then install 5 programs and add 5 files to my home directory which I also set to "Encrypt Home Directory".

1) Are the 5 programs encrypted too? Or are new programs that are installed never encrypted?

2) Are the 5 files that I put into my home directory automatically encrypted without me doing anything?

3) Are all new files added to the system encrypted too, and if yes, then when are these files actually encrypted? When the new files are created? If I create a text file and put it in my home directory -- when is that text file encrypted? Right then and there, after reboot, after log-in/log-out? When?

I already explained this in your other thread but I'll do it here too.

When you encrypt a filesystem using Logical Volume Manager this is what happens.

The data on that volume is encrypted. It remains encrypted until the volume is mounted. When the volume is mounted the key (passphrase) is provided. If the correct passphrase is provided it is unencrypted. It remains plain text while the file system is mounted (this usually happens at boot time, there is an exception which I will explain in a moment). All files written are written in plain text. When the volume is unmounted (usually at shutdown or reboot, or a forced unmount) the data is re-encrypted, and will remain that way until it is remounted. Thus any data added during mount  time becomes encrypted at unmount.

Now the exception I told you about is home directory encryption through ecryptfs. This is unencrypted at login of the user. So if user bob and user jill both have encrypted home directories but only user jill is logged in, user bob's home directory remains encrypted. When Jill logs out her directory will be encrypted again. The catch here is that both users could be logged in simultaneously, and both their home directories would be unencrypted. Thus if permissions were set wrong , they could read eachothers home directory.

Hope this explains this for you

Same caveat as the other thread. When I say it "becomes encrypted" or "unencrpted" I am talking about the point at which the data is visible in an unencrypted state. NOT the time at which the cryptographic cipher is applied to the data stored POST dm-crypt. If that makes sense.

---

### Post by tubbygweilo on 2012-01-15
giantpc, would it be possible for you to turn you machine off and then boot with an Ubuntu Live cd? Give it a go and then see if you can read your home file or indeed any other user's home file.

Your kit/data is encrypted when the machine is switched off and it remains encrypted until things happen as explained in Dangertux's posting.

---

