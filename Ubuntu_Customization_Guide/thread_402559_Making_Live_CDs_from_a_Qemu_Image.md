---
title: "Making Live CDs from a Qemu Image"
date: 2007-04-05
forum: Ubuntu Customization Guide
---

### Post by LaurelLynn on 2007-04-05
Hello everyone,

I have been using Qemu to test out various configurations and customizations of Ubuntu, so I´m very comfortable with it. Also it´s as simple to customize the image as a normal install.

I´ve seen guides that use Qemu to test their isos before burning. But, going back and forth between   chrooted shell image and the iso in Qemu is very time consumming.

So, I was wondering if there was some way, once I have everything set up the way I like in Qemu, I could remaster from the Qemu image to CD or USB memory stick.

That way I could use it to show others just how friendly Ubuntu can be by running it on their own computers.

Laurel Lynn

---

### Post by linux_kid on 2007-05-01
Take this as a wondering idea (qemu literally hates me, so I script badly in it)
> sudo qemu-img convert hdd.img -f iso newisoname.iso
Again, this may not work.... but good luck =)

---

