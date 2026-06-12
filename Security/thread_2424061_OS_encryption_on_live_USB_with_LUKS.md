---
title: "OS encryption on live USB with LUKS?"
date: 2019-08-02
forum: Security
---

### Post by mbassiouny33 on 2019-08-02
Hello,

I'm trying to create an encrypted live ubuntu version on portable USB.

I know how to customize ubuntu and add my own custom apps.

The usb has to be live without persistence so that each time it starts as a fresh new os, You don't store anything, clean, no traces.

[COLOR=#242729][FONT=Arial]Please note it has to be [/FONT][/COLOR]**live**[COLOR=#242729][FONT=Arial] loaded to the ram each time I start the OS, I don't want to install on an external usb drive.[/FONT][/COLOR]

[COLOR=#242729][FONT=Arial]I want to store the os on a bootable USB flash drive and I want to know if it's possible to encrypt this usb flash disk with **LUKS**, so when I boot it to run linux, before entering my user password it asks for the password to decrypt the whole flash disk in the following order:[/FONT][/COLOR]

[LIST=1]
[*]boot usb (load bootloader and grub?...etc)
[*]decrypt the os with the password
[*]normal linux login
[/LIST]
[COLOR=#242729][FONT=Arial]I know that I can't encrypt the whole drive as bios won't be able to read it, but I'm looking for way to leave the necessary files for boot unencrypted and encrypt everything else.

Can someone please help me with some explanations on how to achieve this?

Thanks in advance!
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]

---

### Post by sudodus on 2019-08-02
Would it be 'enough' to have a read-only iso9660 file system with standard live Ubuntu and behind that a partition with an encrypted file system?

In that case you can boot the live-only Ubuntu and after that unlock your encrypted file system. I have tested that it works with 18.04.1 LTS.

-o-

- Clone from an Ubuntu (or Ubuntu family: Kubuntu, Lubuntu ... Xubuntu) iso file to a USB flash drive.
- Create a new partition after the cloned image with fdisk (let it use all remaining space in the flash drive).
- Create a file system in this new partition (after the cloned image).

When running live booted from the USB flash drive, you can loop mount the file system in this new partition. (Please notice that it will probably not mount 'as usual'.)

```

sudo mount -o loop /dev/sdx3 /mnt

```

- If you wish, you can create an ext4 file system, where you can use chown and chmod to manage ownership and permissions on individual directory and file level.

- If you wish, you can mount a Microsoft file system with flags to allow the regular live user, 999, to read and write.

*Finally, you can encrypt the file system in this new partition. *

---

### Post by mbassiouny33 on 2019-08-03
Hey,

Thanks a lot for you answer!
Actually the read only approach seems very interesting, but I believe it might have some limitations, right? Please correct me if I'm mistaken. With read-only your OS files are still visible, so for example if I'm creating a super secret custom OS with custom apps you can't prevent people from seeing if they steal the flash drive and insert it as non-boot secondary drive in any pc. I know I can still put the apps I want to protect the in the encrypted partition, but what if I wish to "hide" the entire OS?

I'm actually wondering is the idea I explained in my first post theoretically possible to achieve?

---

### Post by C.S.Cameron on 2019-08-04
Add a Guest User to Ubuntu 18.04

- Install lightdm:

        sudo apt-get install lightdm

- At popup select lightdm as display manager.

- After install run:

        sudo gedit /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf

- Change: allow-guest=true.

- On next boot there will be a guest user, no changes will be saved during the session.

- The administrator may change settings and add programs.

Customize Guest Session:
[https://help.ubuntu.com/community/CustomizeGuestSession](https://help.ubuntu.com/community/CustomizeGuestSession)

---

### Post by mbassiouny33 on 2019-08-04
Sorry,  I'm not trying to be rude but how does that even answer my question?  Did you read the title?  I'm talking about LUKS and encryption. You're answering with how to add a user. I already know how to add a user and I didn't even ask for this in my first post...
Thanks though?

---

### Post by sudodus on 2019-08-06
> **mbassiouny33 said:**
> Hey,

Thanks a lot for you answer!
Actually the read only approach seems very interesting, but I believe it might have some limitations, right? Please correct me if I'm mistaken. With read-only your OS files are still visible, so for example if I'm creating a super secret custom OS with custom apps you can't prevent people from seeing if they steal the flash drive and insert it as non-boot secondary drive in any pc. I know I can still put the apps I want to protect the in the encrypted partition, but what if I wish to "hide" the entire OS?

I'm actually wondering is the idea I explained in my first post theoretically possible to achieve?

Most things are possible with linux, but some of them are rather difficult. I would recommend something else:

- Install Ubuntu with **encrypted disk** (LVM with LUKS encryption). Install like into an internal drive, but into the USB drive. It helps if you do this in a computer, where you can remove or disconnect the internal drive to avoid confusion where to put the bootloader.

or

- Use [**Tails**](https://tails.boum.org/)

---

### Post by mbassiouny33 on 2019-08-06
Installing is not an option for me because:
1- I simply want to do it the unusual way (for the hobby of it)
2- if somehow someone manages to break the encryption: in the installation context, they have your apps + the traces (data in the apps, browsing history...etc) while in the live context they will only get access to the apps with no data.

Tails is great, I considered it, but still it doesn't prevent from knowing/reading my os files.

So far I've had some success achieving My goal. In theory it should be feasible since grub IS able to read luks volumes.

I'm able to load the linux kernel, it asks for the decryption password but for some reason it hangs right after displaying the ubuntu logo.

---

### Post by sudodus on 2019-08-06
If you like the challenge and you have the time, fine. Good luck :KS

---

### Post by mbassiouny33 on 2019-08-06
> **sudodus said:**
> If you like the challenge and you have the time, fine. Good luck :KS
Thanks :)

---

### Post by C.S.Cameron on 2019-08-07
I think Full Disk Encryption on a Live/Persistent drive is like trying to run proprietary video drivers on a persistent drive.
You can't put the cart before the horse.
Full disc encryption is easy with a Full install to USB.
You can encrypt everything except the Boot partition, and by using a Guest User there is no need to write to disk.

See: [https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption/1086314#1086314](https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption/1086314#1086314)

---

