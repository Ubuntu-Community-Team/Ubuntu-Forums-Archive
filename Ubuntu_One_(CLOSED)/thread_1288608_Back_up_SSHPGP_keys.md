---
title: "Back up SSH/PGP keys"
date: 2009-10-11
forum: Ubuntu One (CLOSED)
---

### Post by mac9416 on 2009-10-11
Hey,

I am constantly trying to make Ubuntu do more than it is meant to, so I end up doing a lot of reinstalls. Every time I do, I lose the PGP and SSH keys I use with Launchpad. Is there a way to back the keys up with my Ubuntu One account? How can I restore them when I reinstall?

Thanks!

---

### Post by joshuahoover on 2009-10-15
> **mac9416 said:**
> Hey,

I am constantly trying to make Ubuntu do more than it is meant to, so I end up doing a lot of reinstalls. Every time I do, I lose the PGP and SSH keys I use with Launchpad. Is there a way to back the keys up with my Ubuntu One account? How can I restore them when I reinstall?

Thanks!

Hi,

We don't recommend users store sensitive information in Ubuntu One without encrypting it using solutions like Karmic's encrypted home directory or other similar solutions (True Crypt, etc.) While your data is safely transported (encrypted), we do not store your data encrypted unless you have encrypted it on your local computer.

Thank you,

Joshua

---

### Post by mac9416 on 2009-10-15
Hey, Joshua, thanks for the information.

If I encrypted the keys to back them up on Ubuntu One, I would have another key to back up, and I suddenly find myself in an infinite loop.

Since I can't use Ubuntu One, is there a way to back up/restore my keys to/from a flash drive? That would be secure as long as it stays in my hands.

Thanks again!

---

### Post by ProfDecoy on 2009-10-15
My suggestion would be to install Truecrypt and create a container that you back up your keys into and then sync the encrypted container file to Ubuntu One.  That way you only have to remember your passphrase to your TC container.

If you haven't taken a look at it before, go to:
[http://www.truecrypt.org](http://www.truecrypt.org)

With a sufficiently long passphrase, anything you store in the TC container is well protected.

---

### Post by mac9416 on 2009-10-15
I've heard of Truecrypt before, but never tried it. I downloaded the x86 deb from their website and tried to install it with gdebi, but I get this error:

> dpkg: unable to read filedescriptor flags for <package status and progress file
descriptor>: Bad file descriptor

Assuming I get Truecrypt installed, what files do I encrypt to sync with Ubuntu One? I know I should probably get /home/mac9416/.ssh/id_rsa and /home/mac9416/.ssh/id_rsa.pub. What about my PGP keys?

Then, once I have them backed up, how do I restore them after a reinstall? Simply copy the files back into place?

If you only know the answer to one or two questions, feel free to tackle just those. No need to try them all at once. :)

---

### Post by mac9416 on 2009-10-15
> dpkg: unable to read filedescriptor flags for <package status and progress file
descriptor>: Bad file descriptor 

Last post here fixed it: [http://ubuntuforums.org/showthread.php?t=1190053](http://ubuntuforums.org/showthread.php?t=1190053)

> Instead, just select Extract .deb Package File, then:
```
cd /tmp
sudo dpkg -i truecrypt_6.2a-0_i386.deb
```


Now on to knowing what files to encrypt. :)

---

### Post by ProfDecoy on 2009-10-16
For your PGP keys, you'll want to back up the ~/.gnupg folder for your GNUPG keys and the ~/.gnome2/keyrings folder, which contains your keyrings for seahorse.

However, I'm not certain if there's any other directories you'll want to back up as well.

---

### Post by zekopeko on 2009-10-16
> **joshuahoover said:**
> Hi,

We don't recommend users store sensitive information in Ubuntu One without encrypting it using solutions like Karmic's encrypted home directory or other similar solutions (True Crypt, etc.) While your data is safely transported (encrypted), we do not store your data encrypted unless you have encrypted it on your local computer.

Thank you,

Joshua

Why don't you encrypt on the server side?

---

### Post by wojox on 2009-10-16
Just go to Applications > Accessories > Passwords and Encryption 

Then Find remote keys and import them.

---

### Post by mac9416 on 2009-10-16
Thank y'all for your help! I have exported my PGP and SSH keys to .asc files; put ~/.ssh/, ~/.gnupg/, and ~/.gnome2/keyrings/ into tar.bz2s; and put all those into a Truecrypt volume to send to Ubuntu One. If I can't restore my keys after a reinstall now, no one can say I didn't try.  ;)

When I have to reinstall, I will carefully chronicle the process to restore the keys and post the instructions here.

Thanks again!

---

