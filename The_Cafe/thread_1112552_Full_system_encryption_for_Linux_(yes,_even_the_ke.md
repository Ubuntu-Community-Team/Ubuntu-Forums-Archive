---
title: "Full system encryption for Linux (yes, even the kernel)"
date: 2009-03-31
forum: The Cafe
---

### Post by mrsteveman1 on 2009-03-31
[http://tech.xerces.com/full-system-encryption-for-linux.geek]("http://tech.xerces.com/full-system-encryption-for-linux.geek")

I wasn't sure where to stick this one, but the Cafe is pretty open. If moderators feel it fits better somewhere else, by all means move it wherever you want :)

The concept is simple, the work is fairly complicated and involved, but there are screenshots and general (very looong) directions on the page.

Basically what I did is modify an existing encrypted Ubuntu setup such that the kernel and all files in /boot are part of the main encrypted filesystem instead of a separate unencrypted /boot partition, by using a set of patches to the GRUB2 bootloader that support luks encryption directly. When grub boots it can find the luks partition, ask you for a password and load the kernel. From there it boots like normal.

There will no longer be an unencrypted kernel or initrd anywhere on the system, all that remains unencrypted is the MBR, and around 60KB of grub2 bootloader code. Functionally this makes the system similar to how Truecrypt system encryption works on Windows. You don't actually gain much if anything in security terms doing this, but i hate separate boot partitions, and this was really fun to setup and play with :)

It is however useful in some situations, for instance if you wish to boot an encrypted system using a small USB key, this is a better fit than sticking all of /boot on the USB stick, since all files are actually in the same encrypted filesystem and not on the stick, you can remove the stick after booting.

Again this is not trivial to setup, but it does work. If you don't know your way around a Linux system you might be able to get it to work, but probably not. The grub developers are in discussions to get this stuff merged into the main development tree for grub2, after that it should be much easier to setup and maintain. Who knows, maybe a future release of Ubuntu will allow us to do what i did here by simply checking a box in the installer.

---

### Post by Polygon on 2009-04-01
this would be a lot easier then what current solutions are out there, and hell, even truecrypt and other programs can just use the grub code to manage the encryption. I shall check it out.

---

### Post by FuturePilot on 2009-04-01
Wow, sounds cool. I hope this can get merged upstream. :)

---

