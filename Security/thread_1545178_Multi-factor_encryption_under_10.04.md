---
title: "Multi-factor encryption under 10.04"
date: 2010-08-03
forum: Security
---

### Post by allaboutsam on 2010-08-03
I am currently running 8.10 with full-disk (excluding /boot) encryption. I am going to be installing 10.04 on a new laptop, and I was wondering whether it supports multi-factor authentication. Specifically, I would like to have a keyfile on USB/SD memory that is required, in addition to the password, to decrypt the disk. Possible? Anyone know of a guide out there? So far my searches have turned up nil.

Thx,
allaboutsam

---

### Post by rookcifer on 2010-08-03
Nope.  To my knowledge LUKS does not allow two-factor yet.  However, I don't find using a key file all that great for increasing security since you can make a password that's as difficult to break as a key file would be.  Now, fingerprints on the other hand would be nice for laptop users but it's not here yet.

Just use a strong password and you're good to go. LUKS already uses PBKDF2 which is a password strengthening algorithm, so a 20 character password should make your crypto uncrackable by even the most powerful adversaries.

There is still no good solution to the evil maid attack, even when a TPM chip is present.  So, again, just be sure your machine is in a safe place where no adversary can plant a bootloader rootkit or keylogger on it and be sure to use a strong password.  That's all that can be done as of now.

---

### Post by iceman_ch on 2010-08-03
> **allaboutsam said:**
> I am currently running 8.10 with full-disk (excluding /boot) encryption. I am going to be installing 10.04 on a new laptop, and I was wondering whether it supports multi-factor authentication. Specifically, I would like to have a keyfile on USB/SD memory that is required, in addition to the password, to decrypt the disk. Possible? Anyone know of a guide out there? So far my searches have turned up nil.

Thx,
allaboutsam


I'm actually working on setting something like this up right now.  I'm using pamusb for additional authentication. I'm also using truecrypt to accomplish the encryption.  Truecrypt is looking for a key on the USB in order to decrypt the volume.  The goal is that when I plug in the USB it logs in and decrypts the volume.  Right now I'm stuck.  My scripts are running certain commands that need to be run as root.  I can't get the scripts to run without asking the user for the sudo password.  Once I get that down I should be able to get everything set up.  I'll post how I did every thing once I get it done.  I might switch to using ecrypts because it can athenticate through the user password and a key file.

---

### Post by Agent ME on 2010-08-03
> **rookcifer said:**
> However, I don't find using a key file all that great for increasing security since you can make a password that's as difficult to break as a key file would be.
I think a key file could be at least kilobytes, much more than any memorable password. And a key file adds a bit more security to a password: someone who happens to see you enter the password can't get in, and if someone is interrogating you for access to the system, you may be required to give the password but you can truthfully say you don't have the key file (Maybe you gave it to a friend or destroyed it).

---

### Post by allaboutsam on 2010-08-03
Thanks, everyone.

A variant of iceman's solution might do it, maybe this:

/boot - unencrypted
/bin, /usr, and so forth - dmcrypt/luks - password-protected
/home, /swap, /tmp - truecrypt - usb/sd keyfile bound to dmcrypt/luks password or ubuntu login password

Any idea how to do it?

---

### Post by iceman_ch on 2010-08-03
> **allaboutsam said:**
> Thanks, everyone.

A variant of iceman's solution might do it, maybe this:

/boot - unencrypted
/bin, /usr, and so forth - dmcrypt/luks - password-protected
/home, /swap, /tmp - truecrypt - usb/sd keyfile bound to dmcrypt/luks password or ubuntu login password

Any idea how to do it?

Google ecrypts or how to encrypt home.  There is a tutorial out there that walks through how to set up a key.  The nice thing about ecrypts is that if your user password is changed you can no longer decrypt home unless you change the ecrypts password.  If you use truecrypt then if you can log in then home becomes decrypted.  So if someone logs into root and changes your password they can then decrypt your home folder provided they have already obtained the key.  

I don't have the tutorial for ecrypts but I do have one for truecrypt.

[http://blog.littleimpact.de/index.php/2009/09/14/automatic-encryption-of-home-directories-using-truecrypt-62-and-pam_exec/](http://blog.littleimpact.de/index.php/2009/09/14/automatic-encryption-of-home-directories-using-truecrypt-62-and-pam_exec/)

You will need to change it a bit to get it to work with a keyfile but, it is doable.  The other thing to look at is make sure that it requires the key.  I believe that truecrypt uses either the password or the key file not both.

---

### Post by rookcifer on 2010-08-04
> **Agent ME said:**
> I think a key file could be at least kilobytes, much more than any memorable password. And a key file adds a bit more security to a password: someone who happens to see you enter the password can't get in, and if someone is interrogating you for access to the system, you may be required to give the password but you can truthfully say you don't have the key file (Maybe you gave it to a friend or destroyed it).

How do you think the machine recognizes the key file?  It hashes it (this is a simplified explanation but accurate for our purposes).  And if it's SHA-1, the hash will be a hexadecimal string of 40 characters in length.

My point is a keyfile itself can be brute forced just like a password.  Make a strong enough password and there's no need for a keyfile at all.  This is especially true when PBKDF2 is in use by the encryption program (I know LUKS uses it).  I will concede, however, that a keyfile might help one defend against rubber-hose cryptanalysis.

---

### Post by no.human.being on 2011-03-30
I'd love to see this implemented as well.

Using something like a MicroSD into a card reader on your notebook for storing your LUKS encryption key is just a great idea.

There is a script on the internet, which does just that. It reads a key from a memory card and pipes it into some utility mounting the root file system during the boot process, but you have to manually set this up for yourself. There is no support from the installer (even the alternate installer) and the script is embedded into the initrd, so when there is a system update changing something on your initrd, you might lose the script and find yourself unable to mount your root file system (which means that you have just locked yourself out of your own system).

I find the idea pretty sweet. They cannot watch you entering your password, because you don't have to. You can choose a really strong and random key and in case you need to render your data unavailable, you have the option of physically destroying the memory card (e. g. you could use a Bunsen burner to melt it up) and the key is really gone. No one can force you to tell him the key, because you simply don't know it. I'd love to see more support for this, as it is a great problem with full disk encryption.

Like our professor for IT security said: "Every password you can remember is weak, when it's being used for deriving a cryptographic key. The only purpose a password should ever serve is authentication with a remote system." This is because when used for authentication, you can slow the attacker down or even ban him on multiple wrong attempts. But if you use it for deriving a cryptographic key, the attacker will usually have physical access to the machine, on which the encrypted data is stored, which enables him to try out an amazing amount of passwords during a very short period of time. Storing a REALLY strong key on an external medium solves this problem.

---

### Post by rookcifer on 2011-03-30
> **no.human.being said:**
> I'd love to see this implemented as well.

Using something like a MicroSD into a card reader on your notebook for storing your LUKS encryption key is just a great idea.

I believe LUKS has support for crypto cards now.  This would do the equivalnet of what you're suggesting with an SD card except it would be more secure since a smartcard is tamper resistant.

> But if you use it for deriving a cryptographic key, the attacker will usually have physical access to the machine, on which the encrypted data is stored, which enables him to try out an amazing amount of passwords during a very short period of time. 

It depends on two things:

1) How strong is the password?

2) Is the key strengthened?

If the password is, say, 20 random ASCII characters, then no one is going to brute-force it, even with supercomputers.  If the key is strengthened (like with PBKDF2 which LUKS and TC both use) then a shorter password will be much stronger than it would otherwise be.

---

### Post by BkkBonanza on 2011-03-30
> **allaboutsam said:**
> Thanks, everyone.

A variant of iceman's solution might do it, maybe this:

/boot - unencrypted
/bin, /usr, and so forth - dmcrypt/luks - password-protected
/home, /swap, /tmp - truecrypt - usb/sd keyfile bound to dmcrypt/luks password or ubuntu login password

Any idea how to do it?

Just use encrypted home for this. It already uses your login password to unlock a key file and the key file can be put on a usb stick for two-factor. For that you just move it manually and replace the original with a symlink to the usb location. You need to make sure the usb stick always mounts at the same place (use UUID) so it can be found reliably.

If you want to add encrypted home after there is a command to migrate now.

See...
[http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html#comment-form](http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html#comment-form)
[http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

---

### Post by no.human.being on 2011-03-31
> **rookcifer said:**
> I believe LUKS has support for crypto cards now.  This would do the equivalnet of what you're suggesting with an SD card except it would be more secure since a smartcard is tamper resistant.

Sound nice. Is it actually **supported** by LUKS/dm-crypt? If so, can you tell me how to set it up? The only pages I found had quite experimental solutions for this.

---

