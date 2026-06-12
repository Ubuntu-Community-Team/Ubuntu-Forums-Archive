---
title: "encrypting the whole disk"
date: 2019-12-25
forum: Security
---

### Post by Skaperen on 2019-12-25
i want to work on a scheme, maybe a derivative of *ubuntu* that keeps as much as possible encrypted.  the bootloader has to be clear (and this is technically risky) in order for the booting to run, unless the BIOS knows how to decrypt it.  this is a different kind of problem to work on.  for now, i'll approach this with common hardware and BIOS.  so there will need to be a clear bootloader (that the evil maid could replace).

that bootloader will need to load a kernel and initial ramdisk image.  the kernel and image will be encrypted so the bootloader has to know how to decrypt and you will need to give it your passphrase (and/or wave your secret hand gestures in front of the camera with your recognizable smiling face).  at that point everything else is encrypted.  all that free open source software will be encrypted, too, not to keep it secret from anyone, but to prevent anyone from changing it.

people often think that all they need to encrypt is their secrets.  if the computer software is given access to their secrets, can it be trusted to not send it over the network to Alice?  that's the ultimate reason everything needs to be encrypted.  but it is possible to make an evil bootloader that adds some evil software in with the initial ramdisk as it decrypts and loads it.  or at a minimum, if it can't fit all that in, it will encrypt your passphrase with Alice's public key (her secret key not included), and store the result somewhere. then when you leave youR "well encrypted" computer alone for an hour, Alice becomes the evil maid.

we even need encrypted BIOS and a CPU with EEPROM with inalterable code to decrypt the bootloader or maybe even something beyond that.  and that needs to be soldered in or Alice can just plug in her own CPU.  i'm sure Alice can get around that.

but, for now, i'll just depend on Alice being uninterested in my computer and all my crazy software and Mandelbrot images, and see what more i can encrypt beyond just /home.

i'll start with /usr being encrypted.  i'd like to encrypt /var, too.

any initial thoughts?

---

### Post by TheFu on 2019-12-25
[https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)

The solution to the evil maid attack is to boot from a flash drive that you keep with you, always.

---

### Post by Skaperen on 2019-12-26
then i need to work on my scheme of pre-loading the system into RAM so the flash booting device is not the long term system device, so you can, eventually, put it back in your secret pocket, when the pre-loading is complete.  it should run in the background so you can get to work as soon as the system is up.

but there is still the risk of being attacked and knocked out for a while after Alice observes you enough to discover that you are using a flash device.  or she could conclude you are doing that when it becomes a common practice (she might even be doing the same thing).

isn't this a lovely world that we live in that we even need to have encryption and door locks.

---

