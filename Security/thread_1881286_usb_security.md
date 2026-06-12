---
title: "usb security"
date: 2011-11-15
forum: Security
---

### Post by mallesh453 on 2011-11-15
hello, i'm mallesh.

i want to know

how to give security to usb device in linux?

i mean i want to give read/write only options to my usb mass storage device(eg: pendrive)

---

### Post by jerrrys on 2011-11-16
here's a link

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=usb+security&sa=Search&cof=FORID:9#821](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=usb+security&sa=Search&cof=FORID:9#821)

---

### Post by mallesh453 on 2011-11-17
thank you for ur reply.
i dont want to protect data on usb mass storage.
i want to protect my pc from usb mass storage.

i mean, in case of pendrive attach to my pc,
 i should handle(accept/reject)
file transfer to/from my pc to pendrive.

---

### Post by jerrrys on 2011-11-17
Linux does not need virus protection.  If you want to protect MSwindows in linux:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=virus+protection&as_qdr=all&sa=Google+Search&lang=en#827](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=virus+protection&as_qdr=all&sa=Google+Search&lang=en#827)

---

### Post by DogMatix on 2011-11-17
You could use [truecrypt]("http://www.truecrypt.org/") to encrypt the data on it. If thats what you intend to do.

---

### Post by CharlesA on 2011-11-17
> **mallesh453 said:**
> thank you for ur reply.
i dont want to protect data on usb mass storage.
i want to protect my pc from usb mass storage.

i mean, in case of pendrive attach to my pc,
 i should handle(accept/reject)
file transfer to/from my pc to pendrive.

If you plug a usb stick in, it gets automounted. Did you not want that to occur?

---

### Post by DogMatix on 2011-11-17
You could try [PySDM]("http://pysdm.sourceforge.net/")

I think password protecting your usb ports is a good idea there is an entry in the Ubuntu brainstorm.ubuntu site [idea 13225]("http://brainstorm.ubuntu.com/idea/13225/"). Perhaps we should get behind it.

---

### Post by aysiu on 2011-11-17
If you don't want programs to start when you plug in a USB stick, then go to **System Settings** and select **Removable Media**. Then check (or tick) the **Never prompt or start programs on media insertion**. (See attached screenshot for more details.)

Frankly, though, there isn't really anything like an *autorun.inf* file for Ubuntu and, even if there were, mounting the drive read-only wouldn't really protect you. Read-only protects the drive from what your computer could do to *it*. Read-only does *not* protect you from what the drive could do to your computer.

And if you don't want to read what's on the USB stick, what's the point of even inserting it into your computer?

If, for some strange reason, you know for a fact that a USB stick is infected with something, the best thing to do would be to find a computer you don't care about, disconnect it from the internet, boot up a live CD, plug in the USB, and *then* mount it.

---

### Post by mallesh453 on 2011-11-17
thank u for ur reply.

i'm able to block(accept)/unblock(reject) the device(pendrive) from my pc.
upto this it is working with the help of libusb api's..

in case of accepting also,
i want to give two opions to user.

1.write data into pc only
2.read data from pc only


i mean,if i give write only option to user after accepting device,he should not get data from my pc(no read permission) but he can copy data to pc(write only).



this is my problem.

---

