---
title: "Make cryptsetup ask the same password only once at boot"
date: 2009-05-23
forum: Tutorials
---

### Post by atomnarf on 2009-05-23
I changed cryptsetup.functions for a friend to be able to mount several partitions which have been encrypted with the same password. It will basically try the last entered password for the "next" partition.

Tested with Ubuntu 9.04 (i386 in vbox with 2-3 encrypted logical volumes), only!

download [http://mitglied.lycos.de/specialistk/cryptsetup/cryptdisks.functions-k.tar.gz](http://mitglied.lycos.de/specialistk/cryptsetup/cryptdisks.functions-k.tar.gz)
extraxt and move to /lib/cryptsetup/cryptsetup.functions-k
chmod 644 /lib/cryptsetup/cryptsetup.functions-k
chown root:root /lib/cryptsetup/cryptsetup.functions-k
in /etc/init.d/cryptdisks-early (and possibly /etc/init.d/cryptdisks, but I don't think its nessesary):

around line 20, change

```
if [ -r /lib/cryptsetup/cryptdisks.functions ]; then
    . /lib/cryptsetup/cryptdisks.functions
else
```to

```
if [ -r /lib/cryptsetup/cryptdisks.functions-k ]; then
    . /lib/cryptsetup/cryptdisks.functions-k
else
```that's it. You can always undo the changes by changing /etc/init.d/cryptdisks-early back (or copy over a backup copy).
If your system is unable to boot, you can for example use the debian live rescue cd [1] (includes lvm support) to undo the changes. Good luck.

Use at your own risk.

[1] [http://cdimage.debian.org/cdimage/release/current-live/i386/iso-cd/debian-live-500-i386-rescue.iso](http://cdimage.debian.org/cdimage/release/current-live/i386/iso-cd/debian-live-500-i386-rescue.iso)

---

### Post by KubuntuKilledMe on 2009-05-28
To get only one prompt, use lvm. Set the whole encrypted container as one lvm physical volume and then create as many logical volumes as you want. The password only gets asked once to unlock the lvm physical volume. My root ran on this setup on 7.10 and 8.04.

---

### Post by shaggy999 on 2009-05-28
I just want to say same as the reply above. However, another way to do it (perhaps these seperate partitions are on seperate physical drives and some of them are removable, making lvm useless) another option is to store a keyfile on the first drive that you type your password into. Then for all subsequent drives use the keyfile stored on that partition as the password. What will happen is you type in one password to open up the primary partition and then the system will auto-decrypt the rest with the keyfile.

I use a combination of both. I have my computer set up w/ a password, but just in case I forget my password I have it set up to use a keyfile on a flash drive (you can set multiple passwords/keyfiles in dm-crypt) that I keep in a secure location.

---

### Post by atomnarf on 2009-06-11
Thank you for you comments. :)

The reason why the lvm solution ([#2]("http://ubuntuforums.org/showpost.php?p=7359619&postcount=2")) was not possible in this case is that the solution had to be developed ex post to an existing installation. The same applies for the (quite good) idea of the keyfile solution ([#3]("http://ubuntuforums.org/showpost.php?p=7361913&postcount=3")). 

> **shaggy999 said:**
> I have my computer set up w/ a password, but just in case I forget my password I have it set up to use a keyfile on a flash drive (you can set multiple passwords/keyfiles in dm-crypt) that I keep in a secure location.

This would mean that anybody who gets hold of the flash drive (how do you define "secure location"?) would be able to decrypt the partition - unacceptable.

paranoid regards

---

### Post by shaggy999 on 2009-06-12
> **atomnarf said:**
> Thank you for you comments. :)

The reason why the lvm solution ([#2]("http://ubuntuforums.org/showpost.php?p=7359619&postcount=2")) was not possible in this case is that the solution had to be developed ex post to an existing installation. The same applies for the (quite good) idea of the keyfile solution ([#3]("http://ubuntuforums.org/showpost.php?p=7361913&postcount=3")). 



This would mean that anybody who gets hold of the flash drive (how do you define "secure location"?) would be able to decrypt the partition - unacceptable.

paranoid regards

I keep it in a safety deposit box at a bank along with other important things that a designated family member can access upon my death.

Also, the fact of the matter is that almost nobody would even think that a file on a USB drive could be used as a key file to unlock a computer. Someone would have to KNOW that I actually employ this method and THEN run around trying to find all my USB keys. And since a keyfile can be ANYTHING - even a jpeg file, there really is no obvious way of stumbling across my key, looking at its contents and realizing that the contents are used to unlock a computer.

The only real likelyhood of anybody unlocking your computer is if they STUMBLE across the usb key (you did hide it, right?) and plug the key into the computer before it starts up.

In this increasingly digital age it's important to decide if you want family members to have access to your 'digital life' when you die and if so, how that will be done. Considering I'm the only technical-oriented person in my family I have to make further considerations on making things easy for family members. Having a keyfile on a usb key makes things really easy. Plus I keep other important things on that key like passwords to all my accounts, financial data, etc.

---

### Post by shaggy999 on 2009-06-12
> **atomnarf said:**
> Thank you for you comments. :)

The reason why the lvm solution ([#2]("http://ubuntuforums.org/showpost.php?p=7359619&postcount=2")) was not possible in this case is that the solution had to be developed ex post to an existing installation. The same applies for the (quite good) idea of the keyfile solution ([#3]("http://ubuntuforums.org/showpost.php?p=7361913&postcount=3")). 


The keyfile method CAN be implemented post-installation. In fact that's the ONLY way of doing it to my knowledge.

---

### Post by unutbu on 2009-06-12
> **shaggy999 said:**
> The keyfile method CAN be implemented post-installation. In fact that's the ONLY way of doing it to my knowledge.

Here are instructions on how to setup a keyfile post-installation:
[http://ubuntuforums.org/showthread.php?t=837416](http://ubuntuforums.org/showthread.php?t=837416)

---

### Post by sharkl on 2012-08-13
Thank you for sharing your solution with us. Sadly it does not work on my system. I use my Ubnuntu LTS 12.04 with a full system encryption via lvm and luks cryptsetup. 
I compared your /lib/cryptsetup/cryptdisks.functions-k with my /lib/cryptsetup/cryptdisks.functions and it seems a some code changed since Ubuntu 9.04 .  But your solution does not use LVM, so that can be a problem, too. 

i have different users on my system and all are able to boot the system with their own passhrase. i have multiple home sections in my crypttab and which have only the users passphrase. i want the system to try all and only encrypt the one with the correct password, the rest should fail silently. 

I have cryptsetup entries like this:
home    UUID=a       none    luks
home    UUID=b       none    luks
home    UUID=c       none    luks
. At the moment it asks for every partition. When i enter the password for a and ignore b, the system starts normally. 
Now it should just try the phrase before and everything would be perfect. 
Do you have any suggestions?

---

