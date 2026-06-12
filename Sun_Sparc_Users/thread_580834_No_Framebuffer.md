---
title: "No Framebuffer?"
date: 2007-10-19
forum: Sun Sparc Users
---

### Post by trmentry on 2007-10-19
I have an interesting problem with 2 Ultra 5s that I have.  

One Ultra5 has 256m ram and I can't remember the CPU speed (box1) but it is slower than the other I have with 512 ram and 333mhz (box2).

Box1 will boot the Ubuntu 7.10 sparc cd with no issues and I can get to the install... however it will get to 88% on copy the files and locks up.  No errors given.

Box2 will boot the cd, and when I press enter for "Boot Install" my monitor goes wacked with "out of sync, range" etc.  But I know it can display what the cd is doing as Box1 doesn't have this issue.  So figure there is somethign wacked with Box2, but it ran OpenBSD fine for a long time, but no framebuffer on it.

So I'm stuck.   I'd like to see if I can get Box2 running as it has better cpu and more memory.  But I can't see the screen for what its doing.

Is there a way to boot the cd without using framebuffer?  

Thanks

---

### Post by netztier on 2007-10-19
> **trmentry said:**
> 

Is there a way to boot the cd without using framebuffer?  

Thanks

Not all U5s are the same, as far as I know - there were versions with different amount of video memory, different graphics chipset revisions, etc.

Check and try the atyfb=..... kernel parameter:

[http://ubuntuforums.org/showthread.php?t=536188&highlight=atyfb](http://ubuntuforums.org/showthread.php?t=536188&highlight=atyfb)

best regards

Marc

---

### Post by trmentry on 2007-10-19
thanks netztier.

and yes, I'm still trying to get these 2 Ultra5s up with Ubuntu from last year.  ](*,)

I'll give this a try when I got home (oh the fun in working graveyard shifts).  I completely forgot about that parm to pass to kernel at boot.

I'm guessing at the 
Press Enter - Boot Install prompt that I would just enter the
video=atyfb:1024x768@60 and then hit enter right?
or is it more 'install video=atyfb:1024x768@60"

thanks

---

### Post by trmentry on 2007-10-19
Ok.. bit more of a problem.  <sigh>  

I was able to 
ok> boot cdrom
then at the prompt 

install video=atyfb:1024x768@60 

I then was able to get Ubuntu installed. 

However now when the machine boots, it does a boot disk that I expect and drops me to a

boot:  

I hit return and get the same framebuffer issue that I had before.  All out of wack for my monitor.

I tried the 'setenv output-device screen:......' command and reseting but that didn't help.

If I knew what the boot: was looking for to boot Ubuntu I would pass the atyfb on to it... but I have no idea.

So can someone please help and let me know what Silo is loading with just a <cr> at the boot: so that I can enter it and the parm I need to get the framebuffer working right.  

Thanks.

---

### Post by netztier on 2007-10-20
> **trmentry said:**
> 
So can someone please help and let me know what Silo is loading with just a <cr> at the boot: so that I can enter it and the parm I need to get the framebuffer working right.  


Check **/etc/silo.conf **

```
marc@grill:/etc$ more silo.conf
# root=/dev/sda2
root=/dev/disk/by-uuid/c5ea121a-6843-4a0d-917b-1d248fddb33b
partition=1
[COLOR="Red"]default=Linux[/COLOR]
read-only
timeout=100
append="quiet splash"

image=/vmlinuz
        [COLOR="Red"]label=Linux[/COLOR]
        initrd=/initrd.img

image=/vmlinuz.old
        [COLOR="Red"]label=LinuxOLD[/COLOR]
        initrd=/initrd.img.old

```

See the "label" lines - here's what you type at the boot prompt.

So at first boot, what you type at the boot prompt is "Linux atyfb=...."

Once you have successfully booted the machine, edit **/etc/silo.conf**. For "global" kernel options, add "atyfb=..." to the "append" line. If you wanted to define individual kernel options for the different images, add an append="..." line to each image=... section.

That should be it. According to it's manpage, unlike LILO or grub, SILO does not need some update-script to be run after changing /etc/silo.conf, so edit and save the file and reboot the machine.

best regards

Marc

---

### Post by trmentry on 2007-10-20
That did the trick.  Thank you very much for the help.

---

