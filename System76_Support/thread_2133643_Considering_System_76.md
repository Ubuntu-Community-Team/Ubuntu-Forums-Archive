---
title: "Considering System 76"
date: 2013-04-08
forum: System76 Support
---

### Post by TheMTtakeover on 2013-04-08
I  was looking into System 76. My only concern is with drivers. Say I purchase a laptop, and then next year you quit selling that model, how long will you continue to upgrade the driver to work with the current version of Ubuntu?

If the one I purchase comes with 13.04 and then you stop selling it after 13.10 will I receive driver updates for 14.04 and 14.10?

---

### Post by 3Miro on 2013-04-08
Other than the Bonobo, all System76 laptops come with free and open source drivers, hence they are not dependent on support from System76. The so called System76 driver is just a utility to gather support information and I think it fixes couple of quirks, but it does not install any actual drivers. In the case of Bonobo, you will probably need the Nvidia proprietary driver. While Nvidia technically can decide to drop support for the driver tomorrow, in practice, they support video cards that are many years old.

In short, if you purchase a System76 laptop, you will have full driver support in he foreseeable future. (Also, I don't work for the company)

---

### Post by Carborundum on 2013-04-10
> **3Miro said:**
> Other than the Bonobo, all System76 laptops come with free and open source drivers, hence they are not dependent on support from System76. The so called System76 driver is just a utility to gather support information and I think it fixes couple of quirks, but it does not install any actual drivers. In the case of Bonobo, you will probably need the Nvidia proprietary driver. While Nvidia technically can decide to drop support for the driver tomorrow, in practice, they support video cards that are many years old.

In short, if you purchase a System76 laptop, you will have full driver support in he foreseeable future. (Also, I don't work for the company)

Actually, all current-gen System76 laptops require the (Ubuntu-only) System76 driver to work properly. Without it, the SD-card reader and the brightness keys do not work.

---

### Post by isantop on 2013-04-10
> **Carborundum said:**
> Actually, all current-gen System76 laptops require the (Ubuntu-only) System76 driver to work properly. Without it, the SD-card reader and the brightness keys do not work.

It sounds to me like the OP is asking if he'll be able to use future Ubuntu versions, to which the answer is yes because A) We will be releasing a new version of the driver with support for new Ubuntu versions, and B) our laptops tend to work better with newer versions of Ubuntu. While our laptops now require fixes for the brightness keys and card reader, this won't always be the case.

---

### Post by 3Miro on 2013-04-10
> **Carborundum said:**
> Actually, all current-gen System76 laptops require the (Ubuntu-only) System76 driver to work properly. Without it, the SD-card reader and the brightness keys do not work.

The brightness keys are nothing than a boot time acpi option, they only modify one line in the grub settings. They do it automatically for Ubuntu and you can do it manually on other distributions.

I have not tested the card reader, but I doubt they are compiling a separate kernel module just for that. Even if they are using a kernel module, the driver is still open source, which means that you can get the source and compile it yourself.

---

### Post by TheMTtakeover on 2013-04-15
Alright, thank you. I greatly appreciate everyone's time here. I know where I will be going :).

---

