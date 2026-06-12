---
title: "How do I get cryptsetup to read a password from standard input?"
date: 2009-06-23
forum: Security
---

### Post by u-slayer on 2009-06-23
I'm re-doing my system's full disk encryption so that it requires both a password and key (multi-factor authentication) I've figured out how to add a script to the initrd image on the usb key. Now all I need to do is add a new password to luks before deleting the old one.

I want to cat the password and keyfile like this:

askpass "Enter Pass" | cat /ram/test - | cryptsetup luksAddKey /dev/ram0 -

But the problem is that cryptsetup needs the old password first and tries to read it from stdin when I do that.

The above method works just fine for luksFormat because it doesn't ask for the old password. But I need it to work for luksAddKey so I don't have to re-encrypt my entire system partition.

Any Ideas?

---

