---
title: "How secure is root password if a root password could be changed with no root?"
date: 2022-08-12
forum: Security
---

### Post by simsconsulting on 2022-08-12
So, I have a customers computer who is a older gentlemen that forgot or never knew his password on his Xubuntu system. As a mildly experienced Linux user I quickly pulled up a very quick step by step guide of how to change the root password (with no root or user password known), which then allowed me to change his user password as well. So the immediate question that came to my mind was. Wow, this isn't very secure at all. 

 Granted, I do the same thing with windows password pretty easily but that's only due to third party tools. This was quick with no third party intervention. How does one protect from this, I guess, is my main question? How do we make these passwords actually matter in Ubuntu?

Little more info:
How I did it was going to the boot window, press E, editing there to re-write as root, changed password, and logged in then used that root to change his user account. 

Is this something that can be done by someone remotely or is this purely a physical security issue? Even so, how do you protect against it?

I realize this is nice for my situation with customers who forget, and other legitimate uses, but if someone is nefarious they seem to already have the keys to the gates.

---

### Post by ajgreeny on 2022-08-13
Unless the disks are encrypted security is, as you found, completely non-existant for anyone with a little Linux knowledge who has physical access to the machine.
There are many ways to harden the security with extra passwords, eg on BIOS, etc, etc, but it can never be 100% without encryption.

Using a separate root password as many distros do adds nothing.

---

### Post by simsconsulting on 2022-08-13
But even if it had encryption if you're logging in with your password it gets unencrypted. Bios passwords are more of an annoyance because you can slap the hard drive into another machine to avoid it. This is all seeming extremely broken to me right now.

---

### Post by ajgreeny on 2022-08-13
Yes agreed! Though I would not suggest it is broken!

Of course an encrypted file/disk has to be unencrypted before it can be used or read; there is no way out of that, and to the best of my knowledge, that would also be the situation in any or all computer operating systems.

As I said, and you seemed to be agreeing with, physical access removes security, and if you have access to a computer that has an OS actually running from an encrypted disk, again there is not much security.  Only if the OS is shutdown will an encrypted disk give you the security you appear to be looking for.

---

### Post by simsconsulting on 2022-08-14
> **ajgreeny said:**
> Yes agreed! Though I would not suggest it is broken!

Of course an encrypted file/disk has to be unencrypted before it can be used or read; there is no way out of that, and to the best of my knowledge, that would also be the situation in any or all computer operating systems.

As I said, and you seemed to be agreeing with, physical access removes security, and if you have access to a computer that has an OS actually running from an encrypted disk, again there is not much security.  Only if the OS is shutdown will an encrypted disk give you the security you appear to be looking for.

Okay so if I understand correctly we're talking about an encrypted disk with encryption key that isn't automatically used when logging in with the changed password, it would be a separate key that could be kept safe. Is this correct?

---

### Post by ajgreeny on 2022-08-15
Never having needed to use encryption on my computers I can't give you a proper answer to that question but I am pretty sure that the encryption passphrase will usually be different from the login password and is a separate key.

---

### Post by SeijiSensei on 2022-08-15
Many things are possible if you have physical control of the machine and can boot into recovery mode. 

External attackers obviously have no such power.

Unix has used the shadow password system for decades. There are alternatives if you want to look deeper. [https://www.redhat.com/sysadmin/pluggable-authentication-modules-pam](https://www.redhat.com/sysadmin/pluggable-authentication-modules-pam)

---

### Post by QIII on 2022-08-15
Physical access is the mother of all security weaknesses.  

If I had a *nix OS on a bootable thumb drive and access to a Windows computer, nobody would ever know I had been there if I did my dirtiest.

---

### Post by ActionParsnip on 2022-08-18
If you have physical access to the system (or console access as a VM) then you have the server. You can also boot USB Ubuntu then mount the disks and chroot into the OS and change passwords as well.

Also +1 to what QIII says

---

### Post by TheFu on 2022-08-18
If physical access is possible for any device, there can be no assured security. This applies to all computers and has always applied.

> **simsconsulting said:**
> Okay so if I understand correctly we're talking about an encrypted disk with encryption key that isn't automatically used when logging in with the changed password, it would be a separate key that could be kept safe. Is this correct?

Yes.  The old system what mounted encrypted HOME directories per userid was flawed and has been deprecated.
Since at least 2010, the LUKS dm-crypt system has been available.  This is system-wide and not tied to any specific username.  There are 8 "slots" which can be used to open the LUKS container(s). The best practice is to have 1 for the Admin, and 1 for each individual user.  I've been encrypting my laptops with LUKS for a while now.  There are attacks possible, like the evil maid attack, but when I'm really worried, I have the boot media around my neck always, which thwarts evil maids.

And it cannot be said often enough.  Encryption works only when the encryption container is closed and the system is powered off, not suspended or hibernated. In that situation, I doubt the FBI could crack into my laptop storage using any method short of beating me and me having the 2FA device required to gain access.  Without that device, I'm not getting in.  I have a challenge-response setup with a yubikey Neo and another with a yubikey 5c.  The devices take a passphrase that gets entered, which runs through some calculations and spits out the LUKS decryption passphrase. I have a very long, backup, passphrase that it stored in a relatives home (which they don't know about) for emergency needs.  Even with it, I doubt I'll be able to enter it correctly. It is long and random, full of every possible character on the keyboards in this locale.

But if I'm in a cafe, step away to get another coffee for 60 seconds and don't shutdown the system, completely, all my security setup is useless should someone have 10 seconds with the laptop and a flash drive with a device driver that runs a specific hacking program. Doing 10,000 things correctly can be undone by 60 seconds of being careless.

Also remember that automatic mounting of external storage is a huge security risk. The power to mount is the power to destroy.  Next time you plug in a flash drive and it opens in a file manager, think about that.  Maybe disabling automatic mounting for unknown storage devices would be smart?  That's why we have autofs - so we can mount known storage to specific locations, with specific options.  Mount options can bring a new level of security to an OS, BTW.  The default options can be bad for security.

---

### Post by QIII on 2022-08-18
The Fu reminds me of an expression we used in the Army, and it applies very well to computer security:

One "Oh, Snap!" immediately wipes out 100 "Atta-boys". 

It was a bit saltier than that of course, so I've given you a polite version.

---

