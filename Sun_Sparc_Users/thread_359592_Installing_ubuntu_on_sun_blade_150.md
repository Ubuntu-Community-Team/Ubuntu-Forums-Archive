---
title: "Installing ubuntu on sun blade 150"
date: 2007-02-12
forum: Sun Sparc Users
---

### Post by capricorn80 on 2007-02-12
Hi !
     I got sun blade 150 with 256 Mb Ram. I want to install ubuntu on it. I have downloaded it from [http://us.releases.ubuntu.com/releases/6.06/ubuntu-6.06.1-server-sparc.iso](http://us.releases.ubuntu.com/releases/6.06/ubuntu-6.06.1-server-sparc.iso) . 
Please tell me how i can install it and is this the right version to install.
Regards.

---

### Post by mips on 2007-02-12
I don't own a sun but I would suggest starting to read other peoples threads here. I personally would also do a google search for ubuntu+sun

---

### Post by Delta_Farce on 2007-02-12
Yep, that's the right release for the Sun Blade.

To get you started with the install, have a look at the following links:

Sun OBP commands (Sun's BIOS):
[Open Boot PROM Commands]("http://www.sunshack.org/data/sh/1.1/wcd00001/wcd00119.htm")

[Sun OBP Reference Card]("http://www.unixzone.dk/unix/sun/resources/SunOBP_Quick_Ref.pdf")

Booting Ubuntu on a Sunblade:

[Booting with ide=nodma]("http://www.ubuntuforums.org/showthread.php?t=240420&highlight=SunBlade")

Getting X to work:

> **rimtech said:**
> if you are going to desktop route and installing the GUI (ie by running apt-get install ubuntu-desktop), you will have to manually edit /etc/X11/xorg.conf and add

```
Option "ReferenceClock" "29.500"
```

into the Device section.

That should get you started. There are lots more useful threads here for things like updating the OBP, configuring netboot etc etc...

Have a look around and best of luck,

Mark

---

### Post by capricorn80 on 2007-02-14
i read all ur reply but need some more help 

1: I am not sure where to edit this file /boot/silo.conf with 

 Code:
        image=/vmlinuz
        label=Linux
        append="ide=nodma"
        initrd=/initrd.img



I have this file in ubuntu-6.06.1-server-sparc iso . My sun blade system is crash.
    
2. wat i m doing is inserting the dvd and issuing command boot cdrom i get ubuntu prompt i.e boot: 
I press Enter and it do some processing and then give me error Illegal Instruction.

Just tell me where i should append the Code: given above. Please mention in simple way as i m new to this thing. 
Regards.

---

### Post by Delta_Farce on 2007-02-14
Ok,

What you need to do is boot Ubuntu and wait for it to reach the 'enter' prompt. At this point press the 'tab' key and you will see a list of all the available boot/install options *(I can't actually remember what the options are, but pressing 'tab' will show them to you)*.

What you need to do is choose the install option you want, and then add the line ide=nodma next to it.

ie. Type something like this:
```

ok> Linux ide=nodma

```

or for a LAMP server it might be:
```

ok> LAMP ide=nodma

```

That will enable you to install Ubuntu. Once installed you can follow the instructions to edit silo.conf and append the ide=nodma string to your kernels:

```

image=/vmlinuz
label=Linux
append="ide=nodma"
initrd=/initrd.img

```

Cheers,

Mark

---

### Post by capricorn80 on 2007-02-15
Hi !
     Thanks for your quick reply but the problem is still there . Now this time i followed your instructions.
When i do boot cdrom i got boot: prompt . On this i press tab and got these options
Install      Expert     Server     Server-Expert    Rescue    Check  Lamp-server Lamp-server-expert , then i did 

boot: install ide=nodma 
n following processing occured
Allocated 8 Megs of memory 0 * 40000000 for kernal
Loaded kernal version 2.6.15
Loading initial ramdisk ( 4861231 bytes at 0 * F802000 phys, 0 * 40C00000 virt) ...
illegal instruction
Ok

I did try options like boot: server ide=nodma and few others but same problem.

Regards.

---

### Post by Delta_Farce on 2007-02-15
This sounds like it might be a problem with the OBP version of your Sunblade. 

Boot the machien to the ok> prompt and type:

```
.version
```

I think the latest version is 4.17, so it might be worth updating the OBP if you have an older version.

There are instructions at Sun.com and [in this thread]("http://ubuntuforums.org/showthread.php?t=200603") for upgrading the OBP. It can be a tricky process but is worth doing.

Let us know how you go,

Mark

---

### Post by capricorn80 on 2007-02-16
hi !
     thx for your reply again. My OBP version is 4.10.6 but i m not getting any thing from that thread of upgrading OBP. 
It will be good if u just post me the steps of upgrading it.

Regards.

---

### Post by capricorn80 on 2007-02-19
hi Delta_farce : 
         can u plz help me and tell me the steps to upgrade OBP.

Regards.

---

### Post by Delta_Farce on 2007-02-19
These are the steps I had to use to upgrade my OBP:

1) Zero the hard disk (get rid of existing Linux and BSD partitions)
2) Boot into OBP and install Solaris (use the ok boot cdrom -s command for single user mode)
3) At the prompt use format -e /dev/rdsk/c0t0d0s0 (for ide drives - not sure what scsi is called)
4) Set the drive type and you should be ok to install Solaris
5) Upgrade OBP using instructions from Sun

The important thing is that if you have Solaris on your Sunblade - the OBP update will work. Download Solaris from [Sun]("http://www.sun.com") and you'll automatically get a trial support contract that will let you download OBP updates (it's free too).

You only need to zero the hard drive if you've had another OS on there first. Zero means completely wiped. I had to remove my hard drive and zero it in a pc to get it to work. You can do this with a dd command or by using any zero program ([try killdisk]("http://www.killdisk.com/")).

After that, install Solaris and download the OBP patch. Then follow the instructions from Sun and you should be right to go.

There are other ways to do it, but this will work for sure (although it is long winded). The most important thing is to zero (ie completely wipe) your hard Sunblade hard drive if you've had any linux or BSD systems on it.

Cheers,

Mark

---

### Post by capricorn80 on 2007-03-13
As u mentione here 
The important thing is that if you have Solaris on your Sunblade - the OBP update will work. Download Solaris from Sun and you'll automatically get a trial support contract that will let you download OBP updates (it's free too).

This seems to be easy coz the process of upgrading OBP is little difficult. I als tried to install ubuntu-6.06.1-server-sparc on sun blade 1500 but its monitor get black after some processing when i run install command .

Wat should i do.

Regards.

---

### Post by nemonoid on 2007-03-19
I was never able to get my Blade 150 to install off the CD even using the latest OBP. It was a beta of Dapper at the time though.

I had to install via netboot. You should be able to use the image here:

> [http://uk.archive.ubuntu.com/ubuntu/dists/edgy/main/installer-sparc/current/images/sparc64/netboot/2.6/]("http://uk.archive.ubuntu.com/ubuntu/dists/edgy/main/installer-sparc/current/images/sparc64/netboot/2.6/")

You can find some instructions for Debian [here]("http://www.hermann-uwe.de/blog/help-how-do-i-boot-debian-on-a-sun-sparc-ultra-10") on setting up TFTP for netboot which should work. Just make sure you rename the boot.img to the hex of the ip address that the blade is assigned via DHCP. For example, 192.168.1.100 is C0A80164.

--
nem

---

### Post by jcastill on 2007-03-20
> **nemonoid said:**
> I was never able to get my Blade 150 to install off the CD even using the latest OBP. It was a beta of Dapper at the time though.


I have just been able to install Ubuntu Dapper using server cd image on my Sunblade 150; I haven't tried netinstall although, but Edgy and Feisty "dist-upgrade" make my sunblade stop working on the "Booting Linux" message on Silo. I don't know if it's the kernel not working or something else.

The sunblade 150 I tested is a UltraSparc II 550MHz with 256MB RAM and 80GB IDE HDD, the CD-ROM is also IDE.

The performance is "OK" but the machine does cries for more RAM and 2 CPU's (got some Ultra60 runnign with 2GB RAM and 2x360MHz CPU and they are far faster than the Sunblade) the Xorg service eats like 50% of the resources when "working on it"
I haven't tried OpenGL or something intensive on the machine, but I will get it back for more testing and help around.

Jose

---

### Post by matheusber on 2007-04-04
hi,

I'm trying to install 6.10 on a sunblade 150 and after the installide=nodma step the machine just freeze. I can see the Loading Linux line and the one after that, the screen blink once and that's the end of the line.

OBP is 4.6.something here, and FreeBSD boots great ...

if anyone has any clue ;)

thanks in advance

matheus

---

