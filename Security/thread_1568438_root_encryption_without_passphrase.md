---
title: "root encryption without passphrase?"
date: 2010-09-05
forum: Security
---

### Post by fbs777 on 2010-09-05
i have installed a ubuntu 10.04 (mini iso) w/ option of root encryption. 

Now i need to boot without ask for passphrase, but im trying to add a luks keyfile without success.

i want to use a keyfile in the /boot partition or inside the initrd (cant be in external pendrive), but ubuntu aparently dont accept a keyfile in /boot or initrd file.

I know, this way isnt very security, but i just need a basic encryption.

So, how to force the use of a keyfile in /boot or inside the initrd for a crypt root partition?

---

### Post by OpSecShellshock on 2010-09-05
I'm not sure I understand. The point of encryption is to protect data while it's not in use from those who would otherwise be able to physically access it. In order to use your system, the encryption needs to be undone during an active session. As such, there's not really any point to encrypting the data on the disk but then not requiring any sort of manual process (whether passphrase or external physical key) to decrypt. Files on disk are not encrypted during active use anyway.

What you seem to be trying to do here is full encryption of the file system (from root on down), which is fine as long as there's an external mechanism for decryption at boot. However, you're trying to put the key in a directory inside the root file system--which is encrypted. If it actually worked, then the key to unlock the encryption would itself be encrypted.

---

### Post by fbs777 on 2010-09-05
> Files on disk are not encrypted during active use anyway.
this will be an embeeded system, so after start, the system will auto run only a program, and is not possible to quit this program or change the terminal, so after start is not possible to access the terminal.

>  However, you're trying to put the key in a directory inside the root file system
no, im trying to put the key in the /boot (open partition) or inside the initrd, but the ubuntu isnt allowing...

---

### Post by Agent ME on 2010-09-05
What's the point of the encryption if the key is right there and easy to access?

---

### Post by anomie on 2010-09-05
@fbs777: Sorry mate, but I have to agree with the others. Having the key accessible alongside the encrypted files / filesystem is absurd. You've defeated your own encryption scheme.

---

### Post by fbs777 on 2010-09-05
ok, as i said before, i know this method is weak, but i just need a basic encryption w/ auto mount.

but ubuntu isnt allowing this...

when i try to add the key file w/ luksAddKey i have this:
```
cryptsetup: WARNING: target sda5_crypt uses a key file, skipped
```
after this i tryied 2 ways:
1- edit /etc/crypttab, then when i update the initramfs, the cryptroot file w/ the line about the keyfile is gone, and i have a kernel panic after reboot
2- edit initrd manually and then edit cryptroot file to include manually the key file. after remount the intrd i have a kernel panic

so, my question is: how to force the use of a keyfile in /boot or inside the initrd for a crypt root partition?

---

