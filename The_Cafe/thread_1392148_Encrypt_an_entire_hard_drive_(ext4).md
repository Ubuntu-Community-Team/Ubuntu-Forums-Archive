---
title: "Encrypt an entire hard drive? (ext4)"
date: 2010-01-27
forum: The Cafe
---

### Post by Dark Aspect on 2010-01-27
Due to a long story that no one really cares to hear about, I need to encrypt my entire hard drive. I am not very interested in TrueCrypt as versions tend to not be backwards compatible and it may be a very long time before I have physical access to the drive again (year+). So I am thinking RSA or PGP encryption, something that would take a while to get into. Is there anyone here that might be able to point me in the right direction?

I am using Arch Linux but if someone gives me an Ubuntu guide I can work with that.

---

### Post by nrs on 2010-01-27
cryptsetup -c aes-xts-plain -s 512 -y luksFormat /dev/sdxx
[http://wiki.archlinux.org/index.php/System_Encryption_with_LUKS_for_dm-crypt](http://wiki.archlinux.org/index.php/System_Encryption_with_LUKS_for_dm-crypt)

Ubuntu's alternate installer has support for it, but not the livecd for some reason.

---

### Post by Dark Aspect on 2010-01-27
> **nrs said:**
> cryptsetup -c aes-xts-plain -s 512 -y luksFormat /dev/sdxx
[http://wiki.archlinux.org/index.php/System_Encryption_with_LUKS_for_dm-crypt](http://wiki.archlinux.org/index.php/System_Encryption_with_LUKS_for_dm-crypt)

Ubuntu's alternate installer has support for it, but not the livecd for some reason.

Doesn't that break the filesystem?

---

### Post by Rainstride on 2010-01-27
> **Dark Aspect said:**
> Due to a long story that no one really cares to hear about, I need to encrypt my entire hard drive. I am not very interested in TrueCrypt as versions tend to not be backwards compatible and it may be a very long time before I have physical access to the drive again (year+). So I am thinking RSA or PGP encryption, something that would take a while to get into. Is there anyone here that might be able to point me in the right direction?

I am using Arch Linux but if someone gives me an Ubuntu guide I can work with that.

is it your main drive your OS is on? or a secondary? I can tell you how to do ether.

---

### Post by nrs on 2010-01-27
> **Dark Aspect said:**
> Doesn't that break the filesystem?
So you're looking to encrypt an already existing filesystem? I think you may be SOL.

---

### Post by AugeIN on 2010-01-27
> **Dark Aspect said:**
> Due to a long story that no one really cares to hear about, I need to encrypt my entire hard drive.

Trying to hide something illegal?

---

### Post by k64 on 2010-01-28
How is it possible to encrypt the Ubuntu system drive? Can you do it with GNUPG or something?

---

### Post by FuturePilot on 2010-01-28
LUKS. It's an option in the Alternate installer.

---

### Post by Dark Aspect on 2010-01-28
> **Rainstride said:**
> is it your main drive your OS is on? or a secondary? I can tell you how to do ether.

Main drive with my OS and files, in fact I could probably get away with just encrypting the home folder really.

> **nrs said:**
> So you're looking to encrypt an already existing filesystem? I think you may be SOL.

Yep, it’s my main 1TB hard drive which is an ext4 filesystem with Arch Linux.

> **AugeIN said:**
> Trying to hide something illegal?

Sort of, I am sure I've broken a few copyright rules but I am not really worried about that. It’s a little more complicated than that, it has more to do with someone having access to my computer that I do not trust completely. So my plan is to use my old 200 GB hard drive for now and encrypt my 1 TB and give it to a friend. The good news is I'll use Ubuntu 9.04 on the 200 GB hard drive since I need a quick OS up and running to make it look like its the OS I normally use. 

In fact, its not just my computer its all my belongings actually but like I said its complicated ;)

---

### Post by Dark Aspect on 2010-01-28
> **k64 said:**
> How is it possible to encrypt the Ubuntu system drive? Can you do it with GNUPG or something?

I am looking for the [same thing]("http://ubuntuforums.org/showthread.php?t=1392148") actually, however, if you just need to do a few files you can use [GPG]("http://www.gnupg.org/").

---

### Post by Rainstride on 2010-01-28
> **Dark Aspect said:**
> Main drive with my OS and files, in fact I could probably get away with just encrypting the home folder really.
hmm... I don't know how to encrypt an already installed system, and even if I did, chances are there is a big risk of breakage anyway. but if you want full system encryption and have an external or something to backup your files to, first backup your home folder and open synaptic and make a copy of you install list by choosing "save markings as" from the "File" list and save it to the back up location, that way you can just use that and your system will reinstall itself later(if your using PPA's you need to add then back before using that file.).

now download a copy of the alt-install disk for your system.
[ubuntu-9.10-alternate-amd64.iso.torrent]("http://releases.ubuntu.com/9.10/ubuntu-9.10-alternate-amd64.iso.torrent")
[ubuntu-9.10-alternate-i386.iso.torrent]("http://releases.ubuntu.com/9.10/ubuntu-9.10-alternate-i386.iso.torrent")

once you have it burned and ready to go, restart with it in the drive like a normal install (make sure the disk is fine before hand). choose "install ubuntu" and start the install. it an easy text based installer, so make sure you read whats going on.

first thing it will ask for is your language, then what variation of that language (just select you country). it will have you choose your keyboard layout next, just choose "NO" when it asks to detect your keyboard layout, its much faster to just pick it from a list. if you are in the US with a standard keyboard, just pick USA and then USA again. it will try to then auto setup your network, you can skip this if you want. then you pick your host name (name it whatever you what, doesn't matter.). then select your timezone (for your clock.).

Now is then important part! choose "Guided - use entire disk and setup encrypted LVM". then pick the harddrive to install on. then it will ask you to confirm, choose yes. you now have to choose your encryption passphrase, this is the password you have to type at boot to be able to boot your system. pick something good. when it asks for the amount of volume to use, just hit enter. then you will be asked to confirm you partition settings, choose yes. it will then install the base of the system. once then finishes it will ask for your user name and password also whether you want to encrypt you home directory or not, pick no, the harddrive is already encrypted so there is no need. it will ask if you use an http proxy when setting up the apt stuff, if you don't just hit enter. it will then finish the install and it will be done. 

then just boot your system and restore your stuff. to use the file for synaptic just use "read markings from" under the "file" menu. it should just mark all the stuff the same under synaptic, then just click apply.

----------------------------------------

for external drives or secondary drives. just run run the disk utility under system>administration.(back up your stuff first) then find the drive you want to encrypt and delete the partitions off of it by selecting the drive and clicking the last icon to the right at the top, when you hover you should see "erase the contents of the device".you should now just see the device and a single item on it in the tree to the left something like "2.1GB unrecognised" or whatever the size of your drive is. just select that and then to the right click the check box that says "Encrypt underlying device" and choose you filesystem from the drop down list (ext4 or whatever). you can also name the filesystem if you want in the label field. then just click the "create" button. A small window will popup and ask for the password for the volume(you password you need to access the new file system). just type what you want the password to be and click "create". optionally you can add the password to your keyring so you don't have to type your password every time. just click the radio button that says "Remember forever" that way when you plug it in while logged into your user name it will automatically mount. this is just for your username, if other people use your system, make sure you unmount the drive when done. or just turn the computer off so it unmounts. otherwise people can access it.

-------------------------------------------------------------
on a side note, if you don't want people analysing the drive for deleted files, you need to do a secure wipe.at least 7wipes(35-guttman ftw:D) before installing with encryption.

---

