---
title: "LUKS unlocking via file on USB Key / partition alignment"
date: 2015-12-25
forum: Security
---

### Post by stuartbh2 on 2015-12-25
ALL,

I recently installed Ubuntu GNOME from bare bones install on up (I am migrating from an installation that was Unity based then GNOME-ized to Ubuntu GNOME). In so doing, I instantiated full disk encryption using LUKS (which worked fine). I do have a few questions though:

1) I want to use an USB key containing a LUKS key on it (such as is suggested here: [http://possiblelossofprecision.net/?p=300](http://possiblelossofprecision.net/?p=300)), to unlock the newly encrypted drive (whilst still leaving me the option to enter a LUKS key via the keyboard as well). I followed the steps in the previously mentioned website up to and inclusive of step 4 (which seems reasonable to me).

Thus, now I want to configure Ubuntu to take notice of the USB key whence it is instantiated, and use the file thereupon avoiding the prompting for the key via keyboard. However, in the absence of the presentation of the USB key containing the secret key file, I'd like for Ubuntu to revert to asking for the pass phrase as normal. It is instructive that I have added the secret key in slot 1, thus leaving the keyboard pass phrase in slot 0. I know cryptsetup can use a key file, and I want to be careful to be as minimally invasive with my solution so that it does not impact the ability for me to easily upgrade Ubuntu in the future without disabling the boot process or this capability.

I have encrypted all but /boot

I am curious what clever or even obviously simple solutions others might have tried and what their results have been.


2) Is LUKS using AES whence it is installed by Unbutu's installer and if so, AES-128 or AES-256? If not, how hard would it be for me to change to AES after the fact?


3) I do not expect a full answer to this question second question, but I want to get a better understanding of partition alignment so that I can customize it a bit better than I did (which was to just accept Ubuntu's choosing of partition styling). Some people say everything needs to start on a 2048 block alignment, some say otherwise, etc... I am using an external USB3 2TB HD, so perhaps the speed gain or loss is so minimal its irrelevant? Sometimes it is connected to a system that uses USB3 and sometimes a USB2 based system.


This is kind of a bonus question...:)

4) I use a very simple system of copying a system file to ".org" before I modify it, so later I can search for all the ".org" files on my HD and know what I modified since installation. Anyone else has any better ideas for change control on a desktop system?


Thanks,

Stuart

---

### Post by TheFu on 2015-12-26
I've never used a key-file for LUKs. Interesting. Currently using a Yubikey with a passphrase tacked on.
LUKS can use different cyphers. The options control what is used. Don't know how easy or hard changing is, but I would expect that complete data loss would be expected. If you don't want to loose the data, have a good backup.  With any solution that includes encryption, excellent backups are mandatory.

Managing config files has been solved for years-decades.  Versioned backups, etckeeper, or just use any source code version control system that every programmer uses like git.  /etc is tiny, so having daily backups for a year really doesn't take much space with a tool like rsnapshot or rdiff-backup. Maybe 2MB total?

---

### Post by HermanAB on 2015-12-28
According to the cryptsetup man page:
the default is for plain dm-crypt and LUKS mappings "aes-cbc-essiv:sha256"

The best guide is here:
[https://wiki.archlinux.org/index.php/Dm-crypt/Device_encryption](https://wiki.archlinux.org/index.php/Dm-crypt/Device_encryption)

Scroll down and look for: "With a keyfile stored on an external media"

---

