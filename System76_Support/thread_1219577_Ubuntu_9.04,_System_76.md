---
title: "Ubuntu 9.04, System 76"
date: 2009-07-21
forum: System76 Support
---

### Post by kidguayas on 2009-07-21
I have recently install System 76 in my laptop which has Ubuntu 9.04. Every time that I'm trying to run it, I have a message that says: that it is only for version 8.10. Is there a way to install it in 9.04?

Thanks,

kidguayas

---

### Post by gila_monster on 2009-07-22
I presume you are talking about the System76 driver. Which version did you install?

---

### Post by thomasaaron on 2009-07-22
You need the latest version of the driver. Please see below for information/instructions.

> The System76 Driver comes installed on your system and is located in your menu at System > Administration > System76 Driver. Any updates to the System76 Driver will be detected by Update Manager. 

If you have performed a fresh Ubuntu installation, you will need to install and run the System76 Driver. To install it, go to...

[http://planet76.com/repositories](http://planet76.com/repositories)

...and download the latest driver .deb package. The latest driver will always be the second link from the bottom. Save it to your Desktop.
Once it has downloaded, double-click the icon on your desktop and follow the prompts to install it. Once you are finished, it will appear at System > Administration > System76 Driver.

The first time you run the driver after a fresh installation, you will need to click the Restore System tab and the Restore button. This will modify your software sources file so that any future driver updates will be available via Update Manager.

After running the driver the first time, you no longer need to use its restore fucntionality. You can just use the Install Drivers tab and the Install button to install any necessary drivers.

If for some reason you get a GPG Key error when trying to update, open a terminal (Applications > Accessories > Terminal) and run this command to fix it.

wget -q [http://planet76.com/repositories/system76_dev.pub](http://planet76.com/repositories/system76_dev.pub) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by kidguayas on 2009-07-22
Thanks for the help, however, after download system 76 2.3.6 I still have the message that says:This driver is designed for System 76 machines running ubuntu versions 6.06 through 8.10. If you have a System 76 machine running one of the above ubuntu versions please file a bug report at [https://launchpad.net/system76](https://launchpad.net/system76).
 
I think there is not system 76 driver for 9.04, but if I have install the wrong version please tell me how to uninstall it and install the right version.

Thanks,

kidguayas

---

### Post by gila_monster on 2009-07-22
> **kidguayas said:**
> Thanks for the help, however, after download system 76 2.3.6 I still have the message that says:This driver is designed for System 76 machines running ubuntu versions 6.06 through 8.10. If you have a System 76 machine running one of the above ubuntu versions please file a bug report at [https://launchpad.net/system76](https://launchpad.net/system76).
 
I think there is not system 76 driver for 9.04, but if I have install the wrong version please tell me how to uninstall it and install the right version.

Thanks,

kidguayas

Actually, that should work for 9.04. It worked for me when I had 9.04 installed. I'm using Linux Mint at the moment (that may change soon), and the driver wasn't working for that, but I presumed that it was because I was using Mint. Now I'm wondering if that's not the case.

Tom, I'm posting that mainly just to give you additional data that may be helpful. I did think it odd that the driver didn't mention 9.04, even if I wouldn't expect it to work with Mint.

---

### Post by Scotty Bones on 2009-07-22
> **gila_monster said:**
> Actually, that should work for 9.04. It worked for me when I had 9.04 installed. I'm using Linux Mint at the moment (that may change soon), and the driver wasn't working for that, but I presumed that it was because I was using Mint. Now I'm wondering if that's not the case.

Tom, I'm posting that mainly just to give you additional data that may be helpful. I did think it odd that the driver didn't mention 9.04, even if I wouldn't expect it to work with Mint.

I have reinstalled 9.04 on an occasion or two and have not experienced any issues reinstalling the S76 drivers (pan5). I've even installed the drivers in Mint without issue (small tweak required).  I believe I have read, in here somewhere, that the issue can be caused by having the wrong BIOS version installed. I don't know if that is what you are experiencing, but it might be worth a look.

---

### Post by thomasaaron on 2009-07-23
kidguayas, are you using a computer purchased from system76.com? What system76 model do you have?

---

### Post by kidguayas on 2009-07-23
I have not bought any system 76 I am using an old laptop

---

### Post by thomasaaron on 2009-07-23
That's why the System76 driver doesn't work. It is made to work on System76 computers.

On this forum, we support System76 machines.

---

