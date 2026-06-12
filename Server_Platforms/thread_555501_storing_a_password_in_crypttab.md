---
title: "storing a password in crypttab"
date: 2007-09-20
forum: Server Platforms
---

### Post by Xbehave on 2007-09-20
I was wondering if its possible to store my LUKS password in my crypttab and how secure it would be?
why? well ive only encrypted my root partition to prevent liveCD based attacks, as long as my system is booting normally i don't mind the fact the system will decrypt itself.
as crypttab is on the encrypted file system, and .'. not readable from the live CD this shouldn't cause any security problems
would you be able to get the password from the kernel?
even if yes id still give up my security(which is overkill based on the fact that i went oooo encrypted root partition that sounds cool) for a system that boots itself without having to enter the password.

---

### Post by jetole on 2007-10-20
What you are suggesting might work but it shouldn't and I wouldn't. In ubuntu you can create a new file based key for a luks based encryption scheme. I have four for a LVM to /home and as I am supposed to do, I have stored them in /etc/keys which is under a passphrase based encryption of / . Now for what you are asking, you can do this, however you can't store the key in a encrypted place. 

Here is why: You / partition is encrypted, you store the key in /etc/keys, you specify this key in crypttab. What happens when you boot? initrd has the keyfile name stored in it when you run update-initramfs so it knows where the key is, it looks in /etc/keys, Well this file is encrypted so what it is basically doing is trying to receive a key for an encrypted file from inside an encrypted file to open the encrypted file. You know have a FUBAR worthy catch 22.

Now I mentioned this could work although it shouldn't. Well I just don't see a point, if you want protection against disc based attacks, well then, turn disk based booting off in the bios and apply a setup password. Now no cd will be able to boot and your problem is solved without having to completly circumvent the purpose of encryption, in fact with this method and not wanting a password on encryption, well you just don't need encryption then.

That being stated, if you want to have the encryption disabled automatically by a key, store it in /boot, this way the key is never encrypted and when you specify it in /etc/crypttab then initrd will know where to find it. I really don't see the point of this method either because since your key is in plain sight, I can boot off a CD find your key and decrypt your hard drive from within the CD using the key that you left around for anyone to find.

Good Luck to you.

---

