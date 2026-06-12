---
title: "Dapper on Sun Blade 100"
date: 2006-07-07
forum: Sun Sparc Users
---

### Post by g-a-c on 2006-07-07
Any gotchas? I have a Blade 100, with 2 x 15Gb drives, and a gig of RAM. It has the latest OBP installed on it, and currently no OS. Would this work? I prefer Linux to Solaris and currently Ubuntu is my preferred distro, so I'd like to get it working if possible. 

I've tried Debian on it previously, but a lot of the text based installation screens were displaying as corrupt, and there seemed to be a lot of interference on the screen (which only showed itself during the installer, the OBP screen was fine). Anyone else had this and know if it's still a problem?

---

### Post by torches on 2006-08-13
Did you have any luck installing dapper on your blade 100? 

THX

---

### Post by jbirch on 2006-08-13
I had some install isuues related to ide/dma.  User Delta_Farce passed along the boot up tip "append ide=nodma" to get my Sunblade100 install going. 

[http://www.ubuntuforums.org/showpost.php?p=1343899&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1343899&postcount=3)

---

### Post by torches on 2006-08-14
I hate to ask but where does this parameter go, I tried 
install append ide=nodma 
install ide=nodma 

as well as server .... ; expert .... 
neither worked.

---

### Post by jbirch on 2006-08-14
Well if you changed your Blade to boot from cdrom it should sit at the boot:  prompt waiting for you to hit enter.

Instead of enter hit tab - it will give you a choice of install types. I believe hitting enter just does the "server" install.  

When you've choosen the type just stick it at the end.  Type in the type of install then add the append statement. 

server append ide=nodma ( then hit enter ) 
or
lamp-server append ide=nodma ( then hit enter )

Now after the install you need to modify the bootup or you still have problems. See this post for how to do that.
 [http://www.ubuntuforums.org/showpost...99&postcount=3](http://www.ubuntuforums.org/showpost...99&postcount=3)

And then if this isn't working for you then you must have other issues.

---

### Post by Delta_Farce on 2006-08-14
Hi,

To add to jbirch's comments above, the Sunblade 100 and 150 have trouble booting without the string ide=nodma being passed to them at some stage.

If you're booting from cd, try this:

```

ok boot cdrom

```

This should load SILO and give you a prompt. You need to press the <Tab> key to see all available boot options.

Assuming we're using Ubuntu Server 6.06 and that we want a standard installation (ie not a LAMP server). The standard image is called "Linux" and we need to add ide=nodma to that image name to get it to boot properly.

```

SILO> Linux ide=nodma

```

Please note that when booting from the CD SILO promt, you just type the string after the image name. 

Once Ubunut is installed, you need to modify silo.conf so that the ide=nodma string is passed to the kernel during loading (otherwise the machine will crash).

You need to do this either before restarting the machine or, if you must restart, you need to modify the boot options when the machine loads with the newly installed system.

If the machine has been rebooted, you'll get the system's SILO prompt and need to add the same string as you did to the CD SILO prompt.

```

SILO> Linux ide=nodma

```

If that line doesn't work, your kernel may not be referred to as "Linux"

I think the standard Unbuntu install will name the kernel vmlinuz, so you can refer to that.

```

SILO> /boot/vmlinuz ide=nodma

```

Once you're in the system, just use an editor to change your silo.conf setting.

```

nano -w /boot/silo.conf

```

In silo.conf you will find a section for each of your images (or kernels). This is where you need to add the append="ide=nodma" string.

```

image=/vmlinuz
        label=Linux
        append="ide=nodma"
        initrd=/initrd.img

```

So to summarise - If you're booting from CD, use the syntax: <image-name> ide=nodma

And when you edit your silo.conf, use the syntax: append="ide=nodma"

---

### Post by g1zmo on 2006-08-15
This is what I get on my Sun Blade 100 when I boot from the Dapper install CD (with or without the nodma argument):

```

boot:
install             expert                   server
server-expert       rescue                   check
lamp-server         lamp-server-expert
boot: server ide=nodma
Allocated 8 Megs of memory at 0x40000000 for kernel
Loaded kernel version 2.6.15
Loading initial ramdisk (4821666 bytes at 0x4F802000 phys, 0x40C00000 virt)...
     ERROR: Last Trap: Illegal Instruction

Error -256
     ERROR: Last Trap: Fast Data Access MMU Miss

Error -256
Stack Underflow


```

---

### Post by Delta_Farce on 2006-08-15
What OBP version are you running?

I know you've said it's the latest version but I got this error before I upgraded mine (was 4.6).

The latest for Sunblade 100 and 150 is 4.17. 

Another trick may be to try removing half the RAM or issuing the mem=512 (I think that's what it was?) statement. Have a look at the thread below for some info on the RAM disk problems:

[http://ubuntuforums.org/showthread.php?t=219746]("http://ubuntuforums.org/showthread.php?t=219746")

Mark

---

### Post by arkham on 2006-08-16
There is one other gotcha, if you attempt to run an X Server several people (including me on a Sun Blade 150) have sync problems with their monitors or messages that the video mode cannot be displayed, regardless of the resolution and bit depth used.  I believe this is an issue only if you use the built in PGX64 (ATI Rage based) graphics.

To solve this, you need to add the following line to the Device section of the xorg.conf:

Option “ReferenceClock” “29.500MHz”

Other than that (and the afore mentioned memory issues) everything has gone pretty smoothly :)

---

### Post by goreo95033 on 2006-09-27
> **Delta_Farce said:**
> What OBP version are you running?

I know you've said it's the latest version but I got this error before I upgraded mine (was 4.6).

The latest for Sunblade 100 and 150 is 4.17. 

Another trick may be to try removing half the RAM or issuing the mem=512 (I think that's what it was?) statement. Have a look at the thread below for some info on the RAM disk problems:

[http://ubuntuforums.org/showthread.php?t=219746]("http://ubuntuforums.org/showthread.php?t=219746")

Mark

Any suggestions for aquiring updated OBP for those without a service contract from $un?  A service contract will probably cost more than I paid for this box.

---

### Post by mips on 2006-09-28
> **goreo95033 said:**
> Any suggestions for aquiring updated OBP for those without a service contract from $un?  A service contract will probably cost more than I paid for this box.

Not to familiar with sun stuff but did a bit of browsing. If the OBP is part of the flash PROM then look here;

[http://sunsolve.sun.com/search/advsearch.do?collection=PATCH&type=collections&queryKey5=119235&toDocument=yes](http://sunsolve.sun.com/search/advsearch.do?collection=PATCH&type=collections&queryKey5=119235&toDocument=yes)
[http://developers.sun.com/solaris/articles/openboot_sparc.html](http://developers.sun.com/solaris/articles/openboot_sparc.html)
[http://developers.sun.com/solaris/articles/openboot_sparc.html](http://developers.sun.com/solaris/articles/openboot_sparc.html)

---

### Post by shawnerz on 2006-09-28
I have a Sunblade 100 running OpenBoot 4.5.  I installed it with no problems.
At the prompt, I entered 'halt.'
Then, 'boot cdrom.'
The machine rebooted and everything proceeded normally.
-Shawn

---

### Post by goreo95033 on 2006-09-28
Okay, $un let me download the OBP update without a service contract.  I suppose I got a little spooked there when I got the registration prompt.  So I'm all good there.

But, alas, I got all the typical problems (most) everyone else has had with the stack underflow errors even though I used the ide=nodma option.

Since this box only has one 128MB DIMM installed, removing half the memory trick that worked for those with 1GB or more memory wasn't really an option for me.  Oh well...

Net boot/install seems to be working now.  At least I have a fast Internet connection.

I suppose I can park my coffee cup on this CD-R of the Ubuntu-6.06.1-sparc image.  :wink:

---

### Post by theBlackDragon on 2006-10-17
I'm also having boot problems with a Sun Blade 100 but the OpenBoot version is pretty old (4.0) so I figured I'd update it, but all instrutions are for  putting the image on a Solaris partition on the harddrive, but I don't have any Solaris on the disk (it's blank) and I don't have any installation media either (and I don't really feel like just downloading Solaris to upgrade OpenBoot).

So I wondered if putting the image on a CD  instead of on a harddisk would work? I'd rather not nuke the system with a failed update...

---

### Post by shawnerz on 2006-10-17
Dragon,

What are your boot problems?

Does the system have a hard drive?

I'm running 6.06 on a SunBlade 100, OpenBoot 4.5, 128 MB RAM, 20GB IDE hard drive.

---

### Post by theBlackDragon on 2006-10-17
> **shawnerz said:**
> Dragon,

What are your boot problems?

Does the system have a hard drive?

I'm running 6.06 on a SunBlade 100, OpenBoot 4.5, 128 MB RAM, 20GB IDE hard drive.

The system does have a hardrive (Seagate 15G), OpenBoot 4.0 and 256MB RAM.

It just hangs on "Loading Linux...", passing "ide=nodma" doesn't seem to have any effect, I've left it hanging like that for 15min but it doesn't pull through.

---

### Post by shoki on 2007-02-17
Good info!

Thanks!

---

### Post by shoki on 2007-02-20
Hello All,

So should I use ide=nodma even still? I have this machine up and running and it seems like all is working. I used the ide=nodma when I installed haven't edited my silo boot setting to append it.

Will it run fine like this or am I asking for trouble down the line?

Thank you,
--Shoki

---

