---
title: "is 200mhz cpu and 64mb ram enough for a file server?"
date: 2007-10-03
forum: Server Platforms
---

### Post by uknowho008 on 2007-10-03
i want to know if i should bother installing ubuntu server on an old dell i have. basically just to share movie iso's and music mp3's on my home network. possibly even a web file server just so i have access to programs and such wherever i am. but im sure thats really pushing it.

so how would this system hold up as a simple media server?

maybe just as a command line with ssh, although i dont yet know how to set up ssh or share files with command line.

oh.. also any good how to's on adding additional hard drives to appear as one large hard drive for more space.

thanks.

---

### Post by galeron on 2007-10-03
Right. For basic file sharing, that's fine. But on the web server's end, your RAM might not be sufficient and your processor definitely won't be able to run processor-intensive scripts, like image encoding for Gallery.

For sharing, you would want to look into Samba (if there're Windows boxes), or NFS if its a full Linux shop.

For multiple hard drives appearing as one, you should check out either LVM or RAID0 on mdadm.

You need to do further Googling with the information I've given here to get a more complete picture.

---

### Post by uknowho008 on 2007-10-03
cool, thanks for the reply. i know about samba and nfs. i just dont know how to set it up with cli. but i can do a search for that. ill have to look into lvm a little more but it seems to be what im looking for. so as long as this machine really can handle serving these files im all good i think. thanks again.

---

### Post by Brazen on 2007-10-03
That machine would be just fine for sharing files and running a web server.  As galeron said though, the webserver will probably only be able to handle static files and simple php scripts, nothing to fancy or it will probably crash and burn.  And of course, you will have to go without a gui, cli only.

LVM is what you need for combining the drives.  I would suggest install webmin and configure the lvm on the hardware tab in the webmin web interface.  As for finding guides to do the other things, start here: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html)

I seriously don't know why people don't think to check the official Ubuntu documentation first.  It's the easiest to follow guides I've found.  I even use them when I'm setting up services on RedHat machines.

---

### Post by netlogic on 2007-10-03
Yes. It will be slow, but it will work. 2.6 is a bit more bloated than 2.4, but there is a howto for shrinking it down more. I believe there is an article on HowtoForge about compiling kernel Debian way. You should read it. If you that isn't your direction, blacklist some unnecessary modules from loading up. I have done it with 32megs, so it shouldn't be a problem. However, it will be a slow server. Samba and NFS should be fine, but Apache with PHP will be grinding your drive. If this is a simple Samba server, you are good to go. Have fun making it work. Tweaking old machine to run and function are always fun. Also, don't set your ram to Turbo. Set it to run Normal. It will make the system slow down a bit to catch up when the ram is a bit small.

---

### Post by uknowho008 on 2007-10-03
cool, thanks guys. ill set that up when i get a chance then.

---

### Post by uknowho008 on 2007-10-03
its worse than i thought. its only 32mb of ram. but im gonna give it a shot anyway.

---

### Post by tgalati4 on 2007-10-04
Damn Small Linux is about the only thing that will run on those specs.  I set up a DSL server using a 166 MHz Pentium with 96 MB.  140 days and counting:

pbook:~ Gman$ ruptime  
homeserver    up 140+11:35,     0 users,  load 0.00, 0.00, 0.00
hpubuntu      up 15+12:09,     0 users,  load 0.02, 0.11, 0.14
pbook         up 46+10:08,     0 users,  load 0.27, 0.24, 0.25
tubuntu2      up 134+00:06,     1 user,   load 0.00, 0.00, 0.00

---

### Post by netlogic on 2007-10-04
> **uknowho008 said:**
> its worse than i thought. its only 32mb of ram. but im gonna give it a shot anyway.
soon as you do an install, start yanking stop out like crazy.
1. use one getty (it is server. you don't need multiple)
2. check dmesg, do lsmod and see any extra modules are loaded. blacklist anything you don't want. you can create a blacklist in 
/etc/modprobe.d/blacklist
3. do ps aux and see if you are running any process you might not need. get rid of them. 
4. dpkg -l and look for package you don't want...
5. yank them out
6. only install sshd and samba, dnsmasq (smaller than bind and dhcpd combined)
you are done for service. don't try to run anymore. hopefully, you got 1meg cache to work with.
7.good luck. just remember... don't give up and yank things out.
==============================
if the performance isn't good enough, you can recompile, but on your machine it will take very LONG time.

---

### Post by galeron on 2007-10-04
With that kind of RAM size, you want to look into recompiling your own kernel to slim it down as much as possible. Start by pulling out any kernel modules that you don't need, so that you just get the essentials. As a bonus, you have the ability to compile it on another machine, so it'll be faster.

But a word of advice, you might be enthusiastic right now, but I have a feeling that you'll tire of its speed soon. Do look into upgrading the RAM at least.

---

### Post by netlogic on 2007-10-04
If you are having issues yanking stuff out, just use debian. Look for debian-40r0-i386-netinst.iso at debian.org That will only install kernel and networking. after that install ssh, sshd, samba, dnsmasq. Don't use bind and dhcpd, they will eat up too much ram.

---

### Post by uknowho008 on 2007-10-04
wow thanks for all the tips guys. im working on installing right now. i downloaded the alt cd thinking it would give me an option to install a command line system but its not giving me the option. is it default? or do i have to use the regular cd for command line? i guess ill find out.....

---

### Post by netlogic on 2007-10-04
> **uknowho008 said:**
> wow thanks for all the tips guys. im working on installing right now. i downloaded the alt cd thinking it would give me an option to install a command line system but its not giving me the option. is it default? or do i have to use the regular cd for command line? i guess ill find out.....

download the server version, not DESKTOP & avoid LAMP installation. i think you are better off with a Debian-net-install at this point.

---

### Post by kerry_s on 2007-10-04
go debian base, use aptitude to get what you need.
my friend set up a similar spec system, he did the base install then.
apt-get install mc links2
mc is a file manager and editor
links2 is a browser that doesn't need X(links2 -g google.com)

he use the browser to follow guides and read what to do, tips, tricks, etc...he has no X installed.

[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

---

### Post by uknowho008 on 2007-10-04
hmm... well i installed it and right after POST it says loading grub or whatever then the computer just restarts. i installed it once with lvm and then once without. both using the whole disk. and i get the same problem. so i dont know whats up.

---

### Post by kerry_s on 2007-10-04
> **uknowho008 said:**
> hmm... well i installed it and right after POST it says loading grub or whatever then the computer just restarts. i installed it once with lvm and then once without. both using the whole disk. and i get the same problem. so i dont know whats up.

could be a bad install or bad hd.
you make a swap for extra memory? 
ext2 is best for old slow rigs, faster than all the others.

---

### Post by uknowho008 on 2007-10-05
im pretty sure the hard drive is fine. i used the default "use entire disk" to install so there should be a swap right? i guess i can try a different hard drive but i dont think that is the problem. the last time i used the hd i was running xp on it and it worked perfect.

---

### Post by netlogic on 2007-10-05
> **uknowho008 said:**
> hmm... well i installed it and right after POST it says loading grub or whatever then the computer just restarts. i installed it once with lvm and then once without. both using the whole disk. and i get the same problem. so i dont know whats up.

same error = what is this mean?
explain the error.

---

### Post by uknowho008 on 2007-10-05
well i tried a different hard drive and still have the same problem. the computer gets through post says loading grub. then it says "starting up" on the top left corner then it suddenly restarts. does it everytime. i dont know whats up

i also checked the integrity of the disk and it says its fine.

---

### Post by netlogic on 2007-10-05
are you completely sure you have placed grub at the mbr and not at the beginning of partition? Have you tried editing your grub? Have you looked at your menu.lst?
Post your menu.lst

---

### Post by uknowho008 on 2007-10-05
i installed it the way i always do i dont know why it would install grub to the first partition. but no i havent looked at the menu list and im not sure how.

but i just realized whne i select install to hard drive from the cd menu it says acpi something unable to locate rsdp

---

### Post by netlogic on 2007-10-05
> **uknowho008 said:**
> i installed it the way i always do i dont know why it would install grub to the first partition. but no i havent looked at the menu list and im not sure how.

but i just realized whne i select install to hard drive from the cd menu it says acpi something unable to locate rsdp

turn off ACPI
acpi=off
put this on it next to end of kernel line.
example
=======================================
default=0
timeout=5

title           Ubuntu, kernel 2.6.15-29-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-29-386 root=/dev/hde1 ro quiet splash **acpi=off**
initrd          /boot/initrd.img-2.6.15-29-386
savedefault
boot
=======================================
when it asks you for the grub menu count down, choose the grub menu... chose the kernel path and hit "e" to edit and make sure acpi is turned off. **Also, make sure your kernel is located on the partition you installed on.** Since, your board is old, it might not recognize it and turning on the acpi even it should turned it off or it can't find your kernel. You must installed at the wrong place and mis-configured the grub. at this point, a live cd will come in handy if you are not used to editing grub from the boot. look for a live cd that supports 2.6 kernel and option to choose not to boot the window manager. the lightest one i can think of that is based around 2.6 kernel is INSERT. DSL is 2.4. It will not properly work if you need to chroot, but you probably don't need that function at this time, so if you have one, you can use DSL. However, insert live cd has an option to not boot window manager. and you can mount the file system and look at your menu.lst  and edit it that way.

Look on-line for how to edit grub.

---

### Post by uknowho008 on 2007-10-05
on my machine on the kernal line root="UUID=fsodbb........" 

is this the problem? i tried setting it to /dev/hde1 with no success as well as /dev/hda1 and /dev/hdb1 still didnt work.

---

### Post by netlogic on 2007-10-05
if you don't know where you installed the kernel, you need a live cd.

sudo fdisk /dev/your-hard-drive-number
on m:
press p
look for the Linux partition
go to that partition if your kernel is in there.

also read the articles
[http://www.gnu.org/software/grub/manual/html_node/Troubleshooting.html](http://www.gnu.org/software/grub/manual/html_node/Troubleshooting.html)
[http://www.wlug.org.nz/TroubleshootingStartUp](http://www.wlug.org.nz/TroubleshootingStartUp)

---

### Post by uknowho008 on 2007-10-05
i just installed it on a different computer and it worked perfect. with all the same selections except this time it asked if i wanted to install lamp or dns which im guessing is because this system is much more powerfull. but anyway that means the disk is fine and its not because im configuring something wrong. its something else..... if its not something simple i think im just gonna give up on this machine. i dont know if its worth the hassle.

---

### Post by netlogic on 2007-10-05
it is probably loading  a wrong module for the controller, wrong grub config, can't find the kernel,  acpi is triggering, your bios settings are set to plug and play... etc.... Old machines are AT based... That is APM or no APM. If you are not comfortable with an old hardware, I say pass on it. Old hardware isn't plug and play. Don't assume your OS will handle everything for you. That includes Windows too. You have to know your hardware before you start. The newer hardwares have a better standard such as PCI, ACPI, APCI, improved IRQ and INT routing, etc. I have installed Linux on 486 with 16megs with 2.4 kernel.

---

### Post by uknowho008 on 2007-10-05
well it runs windows 2000.... awfully slow. but it works. so i guess ill just leave it at that. thanks for all the help though. maybe once im a little more used to linux ill give this pc another shot.

---

