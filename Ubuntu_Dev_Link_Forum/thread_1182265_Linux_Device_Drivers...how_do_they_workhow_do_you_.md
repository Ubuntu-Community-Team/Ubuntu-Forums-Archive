---
title: "Linux Device Drivers...how do they work/how do you find/edit them? Need it 4 Research"
date: 2009-06-08
forum: Ubuntu Dev Link Forum
---

### Post by Rbro on 2009-06-08
Hello,

I am an engineering student conducting research at a university this summer. In order to progress in this research, I need to develop some program that can interface with the driver to a cd burner so that I can control the laser manually. So before I develop a program that times the laser's movement accordingly, I need some way to communicate with the driver.

I know that I will need to start learning about linux device drivers. But I need more information, such as how Linux communicates with the dvd writers that a computer has and whatnot? Will I have to edit those drivers? Will I also have to develop a program to inferface with that driver? Does this program change depending on the writer of the cd writer hardware?

Does anyone know how I should go about doing this? Any input would be greatly appreciated.


Thanks!

---

### Post by jpkotta on 2009-06-09
I'm not sure how much control you can get of a commodity DVD drive.  It will probably be tricky.  AFAIK, the only control you have is through ATAPI commands, and they generally don't have anything to do with "put the laser here and pulse it for 2 ms" type commands.  But I'm not extremely familiar with that side of things.

If you want to learn about Linux drivers, for sure get Linux Device Drivers 3rd Ed.  It's available for free download (and purchase) at O'Reilly and is an excellent introduction.  Most drives would use libata these days,so have a look at that.  Finally, you can send ATA commands directly from userspace; have a look at hdparm.

---

