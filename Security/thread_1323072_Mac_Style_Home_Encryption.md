---
title: "Mac Style Home Encryption"
date: 2009-11-11
forum: Security
---

### Post by sarloth on 2009-11-11
For a while I have been wondering if it was possible to combine login with hard drive encryption. I realize this means that you would have to have an unencrypted root partition, but I really don't see a need for encrypting data that should be relatively the same on everyone's machine.

Then recently I was reading some mac paraphernalia and noticed that evidently it can encrypt your home folder with your user password which may be exactly what I am looking for. Would it be possible to implement something like this in Ubuntu or any other distro?

Somewhat (un)related: I was also wondering if it was possible to make the operating system clear the encryption password from RAM after a certain amount of time, or at least after doing a sleep. This would keep the hard drive from being vulnerable when the computer is left in sleep mode or a certain time has passed without any disk read/writes.

(I do realize that combining login and decryption of the home directory eliminates a level of security, that is acceptable for me.)

---

### Post by Kelvin Gardiner on 2009-11-11
If I remember correctly Karmic offers the choice of encrypted home folders during the install, but not if you upgrade.

---

### Post by sarloth on 2009-11-11
> **Kelvin Gardiner said:**
> If I remember correctly Karmic offers the choice of encrypted home folders during the install, but not if you upgrade.

This has actually been available since Jaunty; I was looking for way to combine the decryption of the home drive with login. Basically I am lazy and only want to enter a password once ;)

Thanks for the reply though! :)

---

### Post by mr_steve on 2009-11-11
> **sarloth said:**
> This has actually been available since Jaunty; I was looking for way to combine the decryption of the home drive with login. Basically I am lazy and only want to enter a password once ;)

Thanks for the reply though! :)

That's exactly how it works, at least in Karmic for sure. I'm using it. On login, it uses your user password to decrypt a separately-stored decryption key, which then mounts your encrypted homedir. It's seamless.

It also prompts you the first time to copy down your actual (randomly-generated) encryption key, in case you ever have to access your encrypted home from another OS or whatever.

---

### Post by sarloth on 2009-11-11
> **mr_steve said:**
> That's exactly how it works, at least in Karmic for sure. I'm using it. On login, it uses your user password to decrypt a separately-stored decryption key, which then mounts your encrypted homedir. It's seamless.

It also prompts you the first time to copy down your actual (randomly-generated) encryption key, in case you ever have to access your encrypted home from another OS or whatever.

This is awesome, thank you much.

---

### Post by slumbergod on 2009-11-11
I've been using it since I did my clean install of Karmic. I have to say it is one of the things that is working perfectly for me. No problems at all with it. No perceptible performance loss either.

---

### Post by __p1n__ on 2009-11-11
Just to be clear, you don't want the snow-leopard-delete-home-folder-and-contents-after-guest-login behavior, right?

---

### Post by sarloth on 2009-11-11
> **__p1n__ said:**
> Just to be clear, you don't want the snow-leopard-delete-home-folder-and-contents-after-guest-login behavior, right?

Interesting feature, funny they wouldn't advertise something like that publicly! ;)

---

### Post by slumbergod on 2009-11-11
I unchecked that option when I did my clean install of Karmic. The option to delete all my files sounded too buggy to rely on as working properly given the bugs in Karmic. Wait til next release :P

---

