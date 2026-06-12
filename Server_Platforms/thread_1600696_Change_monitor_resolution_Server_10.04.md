---
title: "Change monitor resolution Server 10.04"
date: 2010-10-19
forum: Server Platforms
---

### Post by Ed_Ziffel on 2010-10-19
Help!  I'm going blind!

Installed server 10.04 using an old Sony 19" multi scan 400ps CRT monitor.  The command line font is less than 1/8" high:  something on the order of a large 4pt or small 5pt font. Made several attempts to locate the correct info using the man functions and searching the archives, but so far have not been unable to find the needed information. The eye strain is about to make me eligible for a white cane with a red tip.  

Could someone point me in the right direction with this?

---

### Post by arrrghhh on 2010-10-19
> To add custom boot options to your boot linux from grub 2, you need to edit

/etc/default/grub

find the line that reads
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and change it to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=ask"
```

if you know your exact vga= number is, then put that in instead of "ask"

After you edit any of grubs files in /etc you should run
```
update-grub2
```

to apply the changes


Pulled from [here](http://superuser.com/questions/66428/how-can-i-change-console-shells-resolution-in-ubuntu-9-10)

---

### Post by Ed_Ziffel on 2010-10-21
Thanks for the reply.  

> if you know your exact vga= number is, then put that in instead of "ask"

When you refer to exact vga= number are you referring to the a specific resolution that I know that my monitor is capable of?

---

### Post by arrrghhh on 2010-10-21
> **Ed_Ziffel said:**
> When you refer to exact vga= number are you referring to the a specific resolution that I know that my monitor is capable of?

Yea, but evidently the numbers are specific.  I'll see if I can find a list, that link had another link that supposedly had the numbers are their corresponding resolution, but that link was dead...

Oh google how I love thee...

[VGA Resolutions List for GRUB & LILO](http://www.linuxquestions.org/questions/blog/lifeforce4-30748/a-more-complete-vga-resolutions-list-for-grub-and-lilo-2000/)

---

### Post by bdemers on 2010-12-05
So, I followed and messed up everything I inserted vga=771 which is 800x600x8, certainly well with the capabilities of my monitor.  Guess what, big sign "Not supported"  Now what?  Is there an "F" key that'll bypass and let me fix this thing?

---

