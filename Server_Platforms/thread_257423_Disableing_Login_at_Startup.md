---
title: "Disableing Login at Startup"
date: 2006-09-14
forum: Server Platforms
---

### Post by apocalypsefalcon on 2006-09-14
When ubuntu server starts, it requires a password to log in to the system. I was wondering if there was a way to remove this. I usually configure a server so that I can have the bios boot the server and it will start itself up, so I dont have to configure it myself. Also, I may need the startup file that runs programs for example like /bin/apache start in order to make apache start when the computer boots from the bios.

---

### Post by crane on 2006-09-14
Most of the time a server does not log in a user when it starts or is running. Do you have some user specific reason for it to log you in automaticly?
Also do a search for start up scripts for info on getting Apache to start automaticly. Although I thought apache ran automaticly when then system started (default setting). Not real sure about that though.

---

### Post by lamego on 2006-09-14
apocalypsefalcon,
starting services on system boot does not required any user login.

If you install those services from APT the service will be installed to startup during boot.
You can read about the boot process:
[http://www.debianhelp.co.uk/boot.htm](http://www.debianhelp.co.uk/boot.htm)

---

### Post by apocalypsefalcon on 2006-09-14
have the server so it starts itself in the morning before i go to school so me and my friends can use it. dont have time in the morning to start it manually, and i dont want to leave the noisy thing on all night. thats why i was wondering whether it would work before i had to log in, because if i did it would defeat the purpose of the bios boot i had it on with another linux distro

---

### Post by Maylar on 2006-09-14
I can tell you for a fact, Apache2, gnump3d, ssh, proftp and so on are running by the time the login prompt is displayed. no need to login. having a server to auto log you in is not a good idea from a security stand point.

---

### Post by apocalypsefalcon on 2006-09-14
4)Kernel

initialise devices

(optionally loads initrd, see below)

mounts root filesystem

specified by lilo or loadin with root= parameter

kernel prints: VFS: Mounted root (ext2 filesystem) readonly.

runs /sbin/init which is process number 1 (PID=1)

init prints: INIT: version 2.76 booting

can be changed with boot= parameter to lilo, eg boot=/bin/sh can be useful to rescue a system which is having trouble booting.

initrd

Allows setup to be performed before root FS is mounted

lilo or loadlin loads ram disk image

kernel runs /linuxrc

load modules

initialise devices

/linuxrc exits

"real" root is mounted

kernel runs /sbin/init

Details in /usr/src/linux/Documentation/initrd.txt (part of the kernel source).

5) /sbin/init

reads /etc/inittab (see man inittab which specifies the scripts below for manpage click here)

Run boot scripts:

debian: run /etc/init.d/rcS which runs:

/etc/rcS.d/S* scripts

/etc/rc.boot/* (depreciated)

run programs specified in /etc/inittab 

found this, and so i can edit /sbin/init in order to run the processes. that way i can autorun the server and have everything the way that i want it. just install ssh and then ssh with my lapotop, and mod everything on the server that i need to in order for it to work. will post here once i get it running

---

