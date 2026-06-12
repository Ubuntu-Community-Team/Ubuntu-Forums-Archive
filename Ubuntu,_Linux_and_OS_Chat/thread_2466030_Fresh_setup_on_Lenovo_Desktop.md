---
title: "Fresh setup on Lenovo Desktop"
date: 2021-08-18
forum: Ubuntu, Linux and OS Chat
---

### Post by peter-1984 on 2021-08-18
Hi,
Before this, I had Virtualbox guest machine running Ubuntu server 18.04 and everything was fine there.


I now expect to use one other Lenovo machine to set up Ubuntu server from scratch. Do I need to create USB boot disk by extracting Ubuntu server ISO file into such USB boot disk? Can I have details steps towards this?

---

### Post by sudodus on 2021-08-18
You can clone from an Ubuntu Server iso file to a USB drive and get a working boot drive, that can be used to install Ubuntu Server in a computer either in UEFI mode or the old BIOS mode (alias CSM alias legacy mode).

There are also extracting tools that can create a USB boot drive with Ubuntu Server.

There are many cloning tools. The standard cloning tool in Ubuntu is the **Ubuntu Startup Disk Creator**, alias [FONT=Courier New]**usb-creator-gtk**[/FONT], but all true cloning tools do the same (copy every bit without modification from one file or device to another file or device).

In Windows **Rufus** is the recommended tool. Its standard mode is extracting, not cloning, but there is also 'DD-mode' which is cloning. Both methods in Rufus work with Ubuntu, can create a working USB boot drive.

Edit: Links

[Link to Ubuntu's own instructions](https://ubuntu.com/download/server)

[url=https://help.ubuntu.com/community/Installation/FromUSBStick] Installation/FromUSBStick
[/url]

---

### Post by peter-1984 on 2021-08-18
Good day Sudodus,
Many thanks to your update. Regarding the hardware, is it better to choose one Desktop machine or Notebook?


Regards,
Peter

---

### Post by mastablasta on 2021-08-18
server is a computer running one or more services for it's client computers. it is usually headless -  has no monitor, but you can add one if you wish. 

depends what you intend to use the computer for:

[LIST]
[*]desktop PC has non-ecc ram and various desktop PC components you might not need in server (such as GPU). it can still be used a server. depends what you want to acomplish and how much money you have. an old desktop can be a good server.
[*]servers usually have more robust hardware, they have ECC ram to protect your data, maybe built in RAID, various other server features (hot swap disk option, easy disk access), and usually very basic GPU. they can have power saving CPU or multiple power hungry CPU.
[*]laptops are designed to be portable. as such they usually do not lats as long as dekstops. those that do are a lot more expensive. they have various work arrounds to reduce the heat and power consumption. i would not recomend it as a 24h on server, but it can be used.
[/LIST]

mini ITX, small form factor PC... they can actually all be used a server, but each has some limits, so it depends what you need the server to do. for example my media server is old RaspberyPi. small, low power, a bit slow, but works quite well for it's role.

my data backup device is HP MicroServer N40L. It has ECC ram, low power CPU and is running slower and more robust WD red drives in software RAID1 configuration. big fans in the box keep it quiet over night. small factor saves space on the cupboard.

---

