---
title: "Disk imaging program"
date: 2008-12-11
forum: The Cafe
---

### Post by grazed on 2008-12-11
Hey guys, are they any decent imaging programs to back up my hard drive? I'm looking for something like Norton Ghost, and if possible, be able to save the image to a separate partition, and back up if need be from there.

thanks guys!

---

### Post by Bungo Pony on 2008-12-11
I've used the Parted Magic live CD:

[http://www.download.com/Parted-Magic-LiveCD/3000-2094_4-10663999.html](http://www.download.com/Parted-Magic-LiveCD/3000-2094_4-10663999.html)

---

### Post by grazed on 2008-12-11
ok that is somewhat awesome, I knew about system rescue CD, but not that one. thanks. =)

the only issue though is that I wont be able to update the saved image unless I boot the cd.

---

### Post by xc1024 on 2008-12-11
dd. the simplest, the most useful. makes a physical image of the disk. example use : dd if=/dev/sda of /dev/sdf. if probably stands for "input file" and of for "output file". the input is the file you want to copy, in this case the device file, the output file is where you want it copied. as linux handles the devices as normal files (see /dev), there is no problem with copying one to another.

let's make a simple backup. we assume that you want to do a copy of whole sda4, which is 4 gb to your 20 gig external usb disk partition sdf2.
first mount the sdf2, we will write to .img file, just in case.
then, to backup do dd if=/dev/sda4 of=/mnt/sdf2/backup.img. to restore, you just reverse of with if, eg. dd if=/mnt/sdf2/backup.img of=/dev/sda4.

as simple as that. used it only few times, but should work. now i try to work out how to use it to make backup of my cds.

---

### Post by JohnFH on 2008-12-11
Yes, I second that recommendation of dd!  It's simple and very powerful, but be careful - it is VERY powerful.  Learn how to use it on a spare PC first or a virtual machine.  One easy mistake with dd and you could kiss all your data goodbye.

---

### Post by Daveski on 2008-12-11
If you use dd and nc you can transfer the image directly to a file on another Linux machine.

On the machine where you want the file:
```
nc -l -p 10000 | dd of=/home/me/mybackups/diskimage.img
```

(nc, listen on port 10000 -pipe- dd outputfile diskimage.img in your home folder)

Boot to a LiveCD on the machine you want to image:
```
dd conv=noerror if=/dev/hda | nc <IP_Address_of_other_machine> 10000
```

(dd, cont on read errors, input hda device -pipe- nc to other machine on port 10000

---

### Post by mips on 2008-12-12
> **grazed said:**
> Hey guys, are they any decent imaging programs to back up my hard drive? I'm looking for something like Norton Ghost...

[Clonezilla]("http://clonezilla.org/")

---

### Post by Vince4Amy on 2008-12-12
PING (Partimage Is Not Ghost)

[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

Works great for me, even when restoring from a network, very fast and reliable, couldn't ask for more where PING is concerned.

---

### Post by Swagman on 2008-12-12
> **Vince4Amy said:**
> PING (Partimage Is Not Ghost)

[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

Works great for me, even when restoring from a network, very fast and reliable, couldn't ask for more where PING is concerned.

Yeah I [ ** PING**](http://ping.windowsdream.com) The Penguin too.

---

### Post by grazed on 2008-12-12
didn't notice all of the replies until now. thanks guys. 

I'll make sure to research dd before I use it since a mishap could = lost data. I read into clonezilla and ping, they look a little more user friendly . =P

clonezilla actually uses dd, from what I understand.

I'll report back soon. thanks again!

---

