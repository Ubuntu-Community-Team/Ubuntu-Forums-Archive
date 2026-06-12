---
title: "Bios Problem, USB or DVD don't show up in boot menu"
date: 2015-09-09
forum: Windows
---

### Post by gabrielandersson18 on 2015-09-09
Hello!

I Have an ASUS R505CB laptop, bought it with windows 8 installed, i have an windows 8 upgrade key

Installed windows 10 just for testing, the system crashed and i successfully installed linux 15.04 which works just perfect
Though i want to go back to windows 7 and have a dual boot, and i've heard that it best to go from windows to linux in a dual boot?

And now to the problem,

i've tried to create a bootable USB drive, burned discs with windows, but it won't show up in bios at all. And if it shows up, i can't boot with it
Called asus and microsoft and they had no idea what to do

anyone who can help?

---

### Post by yancek on 2015-09-09
> i've tried to create a bootable USB drive, burned discs with windows,  but it won't show up in bios at all. And if it shows up, i can't boot  with it

A bootable USB of what, windows 7?  Burned discs of what with windows?  Did you use the windows iso file to create a bootable disk?  Do you not have a windows 7 installation disk?  I don't know if/how you would downgrade to windows 7, I would think you would need to install it.

How did you create the bootable usb, what software did you use?  It is possible to boot a windows iso extracted and copied to a flash drive and boot it from Grub.  More details on what you did, how you did it and the results.

---

### Post by jerrylamos on 2015-09-09
I'm having fits with Windows 10 boot.

Hard drive /dev/sda dual boots Win 10 pro and Win 10 Enterprise which was upgraded from Win 10 preview.

USB SSD Wily Ubuntu, LTS, etc.  All along I boot USB for Linux, hard drive for Win 7 no problem.

Lenovo M58p 3 GHZ dual processor 4 G

Now with Win 10 every boot the hardware reports illegal unauthorized @#$% attempt to change Bios.
I had to reset boot order to 
USB
CD
Hard Drive

several times.  

Finally to the point power up, BIOS claims unauthorized change - that's Windows 10 screwing around.
F12 to select boot choice
Reboots, BIOS complains some more
F2 to get by
Select USB SSD ubuntu
Reboots, BIOS complains some more
F2 again
Then finally boots USB Wily ubuntu.

That's Microsoft's desperate conniving to make sure only Microsoft products boot.

Now I've an Acer laptop with same setup, 
hard drive Win 10 home upgraded from Win 7
USB SSD drive Wily ubuntu, LTS, etc.

BIOS Startup sequence 
USB
CD
hard drive

No problem.  F12 select boot device.

Go figure.

---

