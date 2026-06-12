---
title: "universal pendrive encryption solution"
date: 2009-07-03
forum: Security
---

### Post by amarantus on 2009-07-03
I need truecrypt solution on a pendrive that works in any system and doesn't require admin rights. I don't have admin rights in company computer (obviously). Truecrypt needs admin rights to run a driver. Does any good solution come to your minds guys?

---

### Post by komputes on 2009-07-03
I have another solution although you need admin access to install cryptsetup on both the machine you use to create the encrypted partition, and the computer which will use it.

* Install the packages 'cryptsetup' and 'gparted'.
 * Make your partitions in gparted
 * Create an encrypted partition on the target partition:
    sudo luksformat /dev/sdb1
  (or sda2 if you want to format the second partition, and so on - check gparted table to see which partition relates to which device file).

You will be asked to write yes in upper case YES

This will ask you for a passphrase.

now when you plug into any ubuntu computer with cryptsetup, you will be asked for your password before the encrypted partition is mounted.

---

### Post by HermanAB on 2009-07-03
You will always need admin rights to install stuff, but FreeOTFE Explorer may work for you:
[http://www.freeotfe.org/main_explorer_differences.html](http://www.freeotfe.org/main_explorer_differences.html)

LUKS and FreeOTFE is the best solution.

See this:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)
[http://aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf](http://aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf)

---

### Post by juancarlospaco on 2009-07-04
Ubuntu Portable and store que private key on UbuntuOne. *(?)*

Check This:
[**http://www.tamalin.org/panther/**]("http://www.tamalin.org/panther/")

---

### Post by amarantus on 2009-07-07
Thanks for replies.

komputes:

that would be a great solution and I tried that. However I need a solution for my work - company only has windows, and I have no chance for getting admin rights. Windows only sees one partition in a pendrive.

My perfect solution would be 200 mb unencrypted partition on a pendrive with encryption software like FreeOFTE, and another partition which is encrypted, with portable apps, documents, etc.

HermanAB:
Again, this means 2 partitions on Win and Windows sees only one. 

juancarlospaco:
interesting, i must get a pendrive bigger than 2gb (right now mine shows 1.91 and Ubuntu Portable didnt install coz of lack of space on a device

---

### Post by HermanAB on 2009-07-07
Hmmm??? "Again, this means 2 partitions on Win and Windows sees only one."

I think you are missing something.

Windows needs to have a Primary partition on a USB disk.  My wizards are designed to work portably with Windows and Linux.

To work with Windows, a USB disk should show up as device /dev/sdb with primary partition /dev/sdb1 in Linux.  Windows will then use the partition that corresponds to /dev/sdb1.

---

### Post by leorolla on 2010-06-07
Hi Herman,
Can FreeOTFE work with an ext4 partition under Windows?
Thanks.

---

### Post by FuturePilot on 2010-06-07
> **leorolla said:**
> Hi Herman,
Can FreeOTFE work with an ext4 partition under Windows?
Thanks.

[http://www.freeotfe.org/docs/Main/FAQ.htm#ad]("http://www.freeotfe.org/docs/Main/FAQ.htm#ad")

---

### Post by leorolla on 2010-06-07
Thanks!

Is there a good software for reading ext4 in Windows?

---

### Post by leorolla on 2010-06-07
By the way, when you say LUKS/dm-crypt, is it the same thing as installing cryptsetup package and just checking "encrypt volume" in palimpsest ?

---

### Post by FuturePilot on 2010-06-07
> **leorolla said:**
> Thanks!

Is there a good software for reading ext4 in Windows?
no. nothing exists to read Ext4 on Windows I'm afraid.

> **leorolla said:**
> By the way, when you say LUKS/dm-crypt, is it the same thing as installing cryptsetup package and just checking "encrypt volume" in palimpsest ?

yes

---

### Post by leorolla on 2010-06-25
I have just realized that, despite what it claims twice in the documentation pages, FreeOTFE Explorer does *not* support encrypted device/partition.

So... as far as I know there is no universal plug-and-play solution for encryption.

You will need admin priviledges to access your data on someone else's computer.

The only solution is to have a file container rather than a partition. I don't like it. It's so convenient to have the partition automatically mounted on Ubuntu. But if portability is really important it might be the solution for you.

---

### Post by anomie on 2010-06-25
[QUOTE=amarantus]I need truecrypt solution on a pendrive that works in any system and doesn't require admin rights. I don't have admin rights in company computer (obviously). Truecrypt needs admin rights to run a driver. Does any good solution come to your minds guys?[/QUOTE]

Have you considered any of the IronKey drives - e.g. [IronKey Basic](https://www.ironkey.com/basic)? (I don't work for them / don't get paid to ask that.)

---

