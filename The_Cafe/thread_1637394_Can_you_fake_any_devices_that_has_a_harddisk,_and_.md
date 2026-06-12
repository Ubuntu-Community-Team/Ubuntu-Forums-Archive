---
title: "Can you fake any devices that has a harddisk, and boot linux?"
date: 2010-12-04
forum: The Cafe
---

### Post by honeybear on 2010-12-04
So procedure, for any machine, here we go ... -ok we live in the future, installing Ubuntu or Linux on anything possible, let's take an [I-robot ]("http://www.hamaraforums.com/uploads/post-6518-1185559882.jpg")

You then override the booting MBR of it, - could be applied with e.g. a regular tomtom, by installing grub, after doing dd if=/dev/XX of=/boot/grub/mbr-original.bin bs=512 count=1
then, you mount and install linux, then after reboot, the grub can be launched at power on of the device and with the grub menu, to let you boot either run Ubuntu, or alternatively the previous Operating System. So you have linux booted;..

no? Then you can install Ubuntu on anything you like, 

:popcorn: 

Here you may practice before ... but well, this is not really allowed to installed linux on anything you'd like [here]("http://strangehorizons.com/2004/20040405/badger.shtml") - This HowTo is not recommended however ;)

---

### Post by SlackerD on 2010-12-04
What the heck is this? Are you trolling?

---

### Post by Doctor Mike on 2010-12-04
> **SlackerD said:**
> What the heck is this? Are you trolling?That's not nice. And faking harddisks and other hardware is an old trick, but this is not the proper venue for that kind of discussion.

---

### Post by alexan on 2010-12-04
more simple put a micro computer in a usb3-flash-drive and have a super fast live distro linux capable to boot on every PC (your OS in your keyring)

---

### Post by xircon on 2010-12-04
Assuming the I-Robot ran on a processor architecture that Linux has been ported to then yes. But you would have to re-write all of the other firmware and software required to handle all of the functions, such as controlling the movement of the limbs etc.

So installing Linux on a dead badger would be easier ;)

---

### Post by Doctor Mike on 2010-12-04
> **xircon said:**
> 
So installing Linux on a dead badger would be easier ;)But? Could it be done???

---

### Post by xircon on 2010-12-04
Depends see 

[http://strangehorizons.com/2004/20040405/badger.shtml](http://strangehorizons.com/2004/20040405/badger.shtml)

Old, but still amusing. But remember:

Do not taunt zombie badgers. Prolonged use of a zombie badger may cause acne, insomnia, leprosy, unusual weather, or the end of time. Please dispose of your zombie badgers properly; consult your local recycling company for proper disposal protocols.

---

