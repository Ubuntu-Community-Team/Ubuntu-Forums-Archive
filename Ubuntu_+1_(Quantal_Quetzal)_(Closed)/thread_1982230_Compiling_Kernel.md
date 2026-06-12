---
title: "Compiling Kernel"
date: 2012-05-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Miykel on 2012-05-18
G'day guys; This may not be the right place to post this question, but it has to do with 12.10 and kernel rc.
 Ive been trying like mad to learn how to compile the kernel from the tar.gz file, just found out the instructions are actually in my PC already so I followed those instructions but I always get the same message at the end,

```
 LD      .tmp_vmlinux1
drivers/built-in.o: In function `gmux_probe':
apple-gmux.c:(.devinit.text+0x8c3e): undefined reference to `acpi_video_unregister'
drivers/built-in.o: In function `gmux_remove':
apple-gmux.c:(.devexit.text+0xbab): undefined reference to `acpi_video_register'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/home/miykel/Downloads/Linux-2.6/ubuntu-quantal'
make: *** [debian/stamp/build/kernel] Error 2

```
I'm under the impression that up to this point was to create .deb packages so I could install them, but by those errors I assume the packages were not created, or if they were, where would they be, I thought they would be where the source file was.
 Kind Regards Miykel

---

### Post by dino99 on 2012-05-18
are you following this howto ?

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Miykel on 2012-05-18
thanks Dino99, yep tried both them methods but ended up at the same error message, thne I found a readme in (I think, I can't check at the moment I'm in W7, Ubuntu just went bang) /usr/local/kernel, or something like that which gave me,basically the same as the second method in your link, but I always end up with the same error 1&2.
  When I rebooted there was an entry in grub for 2.6 but it only went to the Ubuntu splashscreen, tried the other kernel entries and they did the same so .... start again.
  Will be back on the road in the next few days so will not have much computer time until I go to ground again somewhere so it would be nice to have something to work on in the interim.
Regards Miykel

---

