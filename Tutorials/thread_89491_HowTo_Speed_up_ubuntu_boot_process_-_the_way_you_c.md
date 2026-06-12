---
title: "HowTo: Speed up ubuntu boot process - the way you can feel it."
date: 2005-11-12
forum: Tutorials
---

### Post by i3dmaster on 2005-11-12
This HowTo is for those who complaint ubuntu boot-up speed is pretty slow but not willing to install any alternative tools to speed up. The way I use here is not the altimate solution by any means but it does make differences and it does work. Everything done below is by tuning the boot process itself and because everyone's computer might be different, there is a little risk that something below might break your system. Take your own judgment before you perform a change and always good to do a backup for the /etc dir.

[COLOR="Red"]****This HowTo is mainly for laptops and desktops, not for servers.****[/COLOR]

**Due to Ubuntu Edgy Eft (6.10) is using upstart to manage the init process and it already has reducing boot time built in mind, many things have been changed. This thread is mainly for any ubuntu version older than 6.10. For how to customize upstart, please refer to upstart threads in this forum. The following is a very interesting and useful WiKi on how to further speed up the boot process by taking out some useless bootup/shutdown processes...**

[COLOR="Red"][wiki.ubuntu.com/Teardown]("http://wiki.ubuntu.com/Teardown")[/COLOR]

[COLOR="Red"]**Suggestions for this HowTo:**[/COLOR]
1. I hope you learn something from here but not just a simple copy. So please, **DO NOT** follow exactly what I did and copy to your box. Read the descriptions of services and use your own judgment to determine if you need to keep them on or not. For instance, I turned GDM off on mine to boot to console, but if you do not feel confortable to see console at all, you should keep GDM or KDM on to boot directly to GUI.
2. If you have a question about a boot up service and not really sure what it does, post a question here and see if anybody can help you. Ask before you do if you don't know. The bottom line to be safe is to leave a service on rather than turn it off if you do not understand.
3. If you see a boot up service that you have but not in here, let us know what it does just like what I did here - give some descriptions and suggestions on whether it should be on or off on a normal laptop or desktop environment.
 
Color reference : [COLOR="SeaGreen"]**service I turned on**[/COLOR]
                  [COLOR="Red"]**service I turned off**[/COLOR]

[color=blue]**Screen shots contrib'ed by domino for the initial bootup settings. A great reference for those who mess up on runlevels... Thanks!!**[/color]




I. Install a tool - sysv-rc-conf. It is a perl based boot process adjustment tool.
```

sudo apt-get update
sudo apt-get install sysv-rc-conf

```
It gives you a way to esaily config the boot process and runlevel configuration, but its not necessary if you want to do it manually by linking/unlinking the files... Its up to you.

II. Ok, that's all we need. Now let's fire it up by
```

sudo sysv-rc-conf

```
and analyze each service one by one. **Note:** Some services I have here you might not have, perfectly ok. If some you have but I don't, then you will need to investigate on your own or ask here... But this HowTo should cover most of them...

Throw a littel bit of runlevel knowledge here before we start messing them up.... All the boot processes are executed in sequence as following:
runlevel S: the first runlevel in boot process. /etc/init.d/rcS script will be invoked to start and all the processes underneath /etc/rcS.d will be executed.
runlevel 1: the single user mode. All processes underneath /etc/rc1.d will be executed.
runlevel 2,3,4,5: in debain system, the multi-user env, may not may not include GUI. The same, processes under each of the corresponding dirs will be run. **Note** this is different than RedHat, SuSE, and other RPM based systems.
runlevel 0: computer shutdown.
runlevel 6: computer reboot.

ok, back to sysv-rc-conf:

1. [COLOR="SeaGreen"]**acpi-support**[/COLOR]  - You'd better leave it on the default runlevel. The default is 2,3,4,5.
2. [COLOR="SeaGreen"]**acpid**[/COLOR]   - The acpi daemon. These two are for power management, quite important for laptop and desktop computers, so leave them on. The default is 2,3,4,5
3. [COLOR="Red"]**alsa**[/COLOR]  - If you use alsa sound subsystem, yes leave it on. But if you have the service below, its safe to be off. The default is off when alsa-utils is on.
4. [COLOR="SeaGreen"]**alsa-utils**[/COLOR]  - On my system, this service supercedes the alsa, so I turn off the alsa and turn this on at S level. **Note**, I mean "turn off" is to remove all "X" at all runlevels. If you don't have it on your system, no problem. Just keep going. The default is S runlevel.
5. [COLOR="Red"]**anacron**[/COLOR]  - A cron subsystem that executes any cron jobs not being executed when the time is on. Most likely you've probably turned your computer off when a certain cron job time is ready. For example, updatedb is scheduled at 2am everyday, but at that moment, you computer is off, then if anacron service is on, it will try to catch up that updatedb cron... I turn it off cause it didn't turn my laptop off very offen, but its totally up to you for this one. The default is 2,3,4,5
6. [COLOR="Red"]**apmd**[/COLOR] - This is the one that confused me a quite bit. I have acpid on already and what's the benefits of having apmd on too? If you computer is not that old which can't even support acpi, then you may try to turn this off. I did anyway. The default is 2,3,4,5
7. [COLOR="Red"]**atd**[/COLOR] - like cron, a job scheduler. I turned it off. The default is 2,3,4,5
8. [COLOR="SeaGreen"]**binfmt-support**[/COLOR] - Kernel supports other format of binary files. I left it on. The default is 2,3,4,5
9. [COLOR="Red"]**bluez-utiles**[/COLOR] - I turned it off. I don't have any bluetooth devices. The default is 2,3,4,5
10. [COLOR="SeaGreen"]**bootlogd**[/COLOR] - Leave it on. The default is S.
11. [COLOR="SeaGreen"]**cron**[/COLOR] - Leave it on. The default is 2,3,4,5
12. [COLOR="Red"]**cupsys**[/COLOR] - subsystem to manager your printer. I don't have so I turned it off, but if you do, just leave it on. The default is 2,3,4,5
13. [COLOR="SeaGreen"]**dbus**[/COLOR] - Message bus system. Very important, leave it on. The default is 2,3,4,5
14. [COLOR="Red"]**dns-clean**[/COLOR] - Mainly for cleaning up the dns info when using dial-up connection. I don't use dial up, so I turn it off. The default is S.
15. [COLOR="Red"]**evms**[/COLOR] -  Enterprise Volumn Management system. I turned it off.  The default is S.
16. [COLOR="Red"]**fetchmail**[/COLOR] - A mail receving daemon. I turned it off. The default is 2,3,4,5
17. [COLOR="SeaGreen"]**gdm**[/COLOR] - The gnome desktop manager. I turned it off anyway since I get use to boot to console first. This is up to you if you want to boot directly to GUI. The default is 2,3,4,5
18. [COLOR="Red"]**gdomap**[/COLOR] - Actually I have no idea why this one should on. I didn't see any other systems have this daemon, so I turned it off and  I don't feel I lose anything. Any benefits to have it on a loptop or desktop? The default is 2,3,4,5
19. [COLOR="SeaGreen"]**gpm**[/COLOR] - Mouse support for console. If you feel you'd better have a mouse on console, go turn it on at runlevel 1 and 2. That's all you need. The default is 2,3,4,5
20. [COLOR="SeaGreen"]**halt**[/COLOR] - Don't change it. The default is 0.
21. [COLOR="SeaGreen"]**hdparm**[/COLOR] - tuning harddisk script. I removed the 2,3,4,5 runlevel but add it to S runlevel. I feel that opening DMA, 32bit I/O, etc eariler will benefit the rest of the processes. Also I changed the original script to a very simple one that I made myself. I feel useless to put all those redundant checks if I know what I am doing. The configuration file is /etc/hdparm.conf. The default is 2,3,4,5
22. [COLOR="SeaGreen"]**hibernate**[/COLOR] - If your system support hibernate, leave it on. Otherwise, its useless for you. The default is S.
23. [COLOR="Red"]**hotkey-setup**[/COLOR] - This daemon setup some hotkey mappings for Laptop. Manufacturers supported are: HP, Acer, ASUS, Sony, Dell, and IBM. If you have a laptop in those brands, you can leave it on, otherwise, this might not have any benefits for you. The default is 2,3,4,5
24. [COLOR="Red"]**hotplug and hotplug-net**[/COLOR] #activating hotplug subsystems takes time. I'd consider to turn them off. I did some changes in my /etc/network/interfaces file. Instead of mapping my wireless card during hotplug process, I set it up to auto. So I can turn them off. I've tested even I turned them off, ubuntu can still detect my usb driver, my digital camera, etc. So I think its pretty safe to turn them off. [COLOR="SeaGreen"]****Note** If you find your sound card doesn't work after turning hotplug service off, you can turn it back. Or edit /etc/modules file to add your sound card's driver module.**[/COLOR] Tested out the later one is faster. The default is S.
25. [COLOR="Red"]**hplip**[/COLOR] - HP printing and Image subsystem. I turned it off. The default is S.
26. [COLOR="Red"]**ifrename**[/COLOR] - network interface rename script. Sounds pretty neat but I turned it off. Mainly for managing multiple network interfaces names. Since I have a wireless card and an ethernet card, they all assigned eth0 and ath0 from kernel, so its not really useful for me. The default is S.
27. [COLOR="SeaGreen"]**ifupdown and ifupdown-clean**[/COLOR] - Leave it on. They are network interfaces activation scripts for the boot time. ifupdown default is 0,6,S and ifupdown-clean is S.
28. [COLOR="Red"]**inetd or inetd.real**[/COLOR] - take a look your /etc/inetd.conf file and comment out any services that you don't need. If there aren't any services there, then its very safe to turn them off. The default is 2,3,4,5
29. [COLOR="SeaGreen"]**klogd**[/COLOR] - Leave it on. The default is 2,3,4,5
30. [COLOR="SeaGreen"]**laptop-mode**[/COLOR] - A service to tweak the battery utilization when using laptops. You can leave it on. The default is 2,3,4,5 
31. [COLOR="SeaGreen"]**linux-restricted-modules-common**[/COLOR] - You need to see if you really have any restricted modules loaded on your system. Since I need madwifi ath_pci module, so I left it on. The restricted modules can be found from /lib/linux-restricted-modules. If you find that you are not using any of the restricted modules, then its ok to turn it off. The default is 0,6, and S.
32. [COLOR="Red"]**lvm**[/COLOR] - I don't use it so I turned it off. Leave it on if you *DO* have lvm. The default is S.
33. [COLOR="SeaGreen"]**makedev**[/COLOR] - Leave it on. The default is 2,3,4,5
34. [COLOR="Red"]**mdamd**[/COLOR] - Raid management tool. I don't use it so I turned it off. The default is 2,3,4,5
35. [COLOR="Red"]**mdamd-raid**[/COLOR] - Raid tool. If you don't have Raid devices, turn it off. The default is S.
36. [COLOR="SeaGreen"]**module-init-tools**[/COLOR] - Load extra modules from /etc/modules file. You can investigate your /etc/modules file and see if there is any modules that you don't need. Normally, this is turned on. The default is S.
37. [COLOR="SeaGreen"]**mountvirtfs**[/COLOR] - mount virtual filesystems. Leave it on. The default is S.
38. [COLOR="SeaGreen"]**networking**[/COLOR] - bring up network interfaces and config dns info during boot time by scaning /etc/network/interfaces file. Leave it on. The default is 0,6,S
39. [COLOR="SeaGreen"]**ntpdate**[/COLOR] - Sync time with the ubuntu time server. The default is S. QUOTED: "If you are dual-booting with Windows, it is probably a good idea to leave ntpdate on. Windows can only deal with the hardware clock set to local (not UTC) and Linux needs ntpdate to correct this, otherwise your clock will increase an hour everytime you boot into Linux from Windows." [color=blue]Thanks dejitarob for the update!![/color] I don't have dual boot, so I turned it off, but if you have multiple systems, suggestion is to turn it on.
40. [COLOR="Red"]**nvidia-kernel**[/COLOR] - I compiled the nvidia driver by myself, so its useless for me now. If you use the ubuntu nvidia driver from the restrict modules, just leave it on. The default is 1,2,3,4,5
41. [COLOR="SeaGreen"]**pcmcia**[/COLOR] - Active pcmcia device. I changed it to start on 0,6,S runlevel instead of on each 2,3,4,5 cause I feel its better to have hardware device ready at first. Also, useless if you are using desktop which doesn't have pcmcia card. So in that case, turn it off please. The default is 2,3,4,5
42. [COLOR="Red"]**portmap**[/COLOR] - daemon for managing services like nis, nfs, etc. If your laptop or desktop is a pure client, then turn it off. The default is 2,3,4,5,0,6,S
43. [COLOR="SeaGreen"]**powernowd**[/COLOR] - client to manage cpufreq. Mainly for laptops that support CPU speed stepping technology. Normally, you should leave it on if you are configuring a laptop, but for desktop, it might be useless. The default is 2,3,4,5
44. [COLOR="Red"]**ppp and ppp-dns**[/COLOR] - Useless to me. I don't have dial-up. The default for ppp is 2,3,4,5 and pppd-dns is S.
45. [COLOR="Red"]**readahead**[/COLOR] - [color=blue]**Thanks mr_pouit!**[/color] It seems readahead is a kind of "preloader". It loads at startup some libs on memory, so that some programs will start faster. But it increases startup time for about 3-4 seconds. So, you can keep it... or not . **update**, I tested and I just didn't feel difference loading programs. So I decided to turn it off. If you have a reason to keep it on, please do so. The default is S
46. [COLOR="SeaGreen"]**reboot**[/COLOR] - Don't change it. The default is 6
47. [COLOR="SeaGreen"]**resolvconf**[/COLOR] - Automatically configuring DNS info according to your network status. I left it on. The default is S.
48. [COLOR="Red"]**rmnologin**[/COLOR] - Remove nologin if it finds it. It wouldn't happen on my laptop, so I got rid of it. The default is 2,3,4,5
49. [COLOR="Red"]**rsync**[/COLOR] - rsync daemon. I don't use it on my laptop, so turned it off. The default is 2,3,4,5
50. [COLOR="SeaGreen"]**sendsigs**[/COLOR] - send signals during reboot or shutdown. Leave it as it is. The default is 0,6
51. [COLOR="SeaGreen"]**single**[/COLOR] - Active single user mode. Leave it as it is. The default is 1
52. [COLOR="SeaGreen"]**ssh**[/COLOR] - ssh daemon. I need this so I turned it on. The default is 2,3,4,5
53. [COLOR="SeaGreen"]**stop-bootlogd**[/COLOR] - stop bootlogd from 2,3,4,5 runlevel. Leave it as it is. The default is 2,3,4,5
54. [COLOR="Red"]**sudo**[/COLOR] - check sudo stauts. I don't see any good to run it everytime on a laptop or desktop client, so I turned it off. The default is S
55. [COLOR="SeaGreen"]**sysklogd**[/COLOR] - Leave it as it is. The default is 2,3,4,5
56. [COLOR="SeaGreen"]**udev and udev-mab**[/COLOR] - Userspace dev filesystem. Good stuff, I left them on. The defaults are all S runlevels.
57. [COLOR="SeaGreen"]**umountfs**[/COLOR] - Leave it as it is. The default is 0,6
58. [COLOR="SeaGreen"]**urandom**[/COLOR] - Random number generator. Might not useful but I left it on. The default is 0,6,S
59. [COLOR="Red"]**usplash**[/COLOR] - Well, if you really want to see the nice boot up screen, leave it as it is. I just turned it off anyway. If you want to turn it off, you also need to edit /boot/grub/menu. lst file to comment out the splashimage line and get rid of the splash kernel boot option. The default is 2,3,4,5
60. [COLOR="SeaGreen"]**vbesave**[/COLOR] - video card BIOS configuration tool. Its able to save your video card status. I left it on. The default is 2,3,4,5
61. [COLOR="SeaGreen"]**xorg-common**[/COLOR] - setup X server ICE socket. I moved it from starting at runlevel S to runlevel 2,3,4,5. Since I don't need this if I boot to single user mode. This way it wouldn't occupy time during the initial booting. The default is 2,3,4,5
============ My bootup services end up here============

============ Some services from others================
62. [COLOR="Red"]**adjtimex**[/COLOR] - This is a kernel hw clock time adjusting too. Normally, you shouldn't see this on your boot up list. In very rare case if you do see its on your boot up process, then there might be a reason why it is on, so better leave it that way. In my case, it is off.
63. [COLOR="Red"]**dirmngr**[/COLOR] - A certification lists management tool. Work with gnupg. You will have to see if you need it or not. In my case, I turned it off. Default runlevel 2,3,4,5
64. [COLOR="Red"]**hwtools**[/COLOR] - A tool to optimize irqs. Not sure what's the benefits of turning it on. In my case, I turned it off.
65. [COLOR="SeaGreen"]**libpam-devperm**[/COLOR] - A daemon to fix device files permissions after a system crash. Sounds pretty good, so I left it on.
66. [COLOR="Red"]**lm-sensors**[/COLOR] - If you matherboard has builtin some sensor chips, it might be helpful to see hw status via userspace. I ran it and it said "No sensors found", so I turned it off.
67. [COLOR="SeaGreen"]**screen-cleanup**[/COLOR]  - A script to cleanup the boot up screen. Well, turn on or off is up to you. In my case, I left it on. The default is S
68. [COLOR="Red"]**xinetd**[/COLOR] - A inetd super daemon to manage other damons. In my system, the xinetd is managing chargen, daytime, echo and time (find them from /etc/xinetd.d dir), I care none of them, so I turned it off. If you do have some important services configured under xinetd, then leave it on.

III. Alter the /etc/inittab file
```
vi /etc/inittab
```then comment out tty4,tty5, and tty6. Just leave tty1, tty2, and tty3. Three vts should be enough for a laptop or desktop user. Save the file.

IV. Ok, now, we can reboot our box and see how it goes. From what I've tested, before I got tons of services stopped, the whole process is about 85 secs to 90 secs to boot to console. (At that time, I also has samba and nfs services turned on which I shouldn't. Apparently, I turned them off too). After this change, the whole boot up process took about 50 secs. I have a P4M 1.8G CPU laptop. Some of the high-end desktops or laptops should take even less time.

[COLOR="Red"]****UPDATE**: speed up/clean system reboot or shutdown process.**[/COLOR]
1. start sysv-rc-conf by issuing:```
sudo sysv-rc-conf
```
2. ok, open your eyes and look very carefully for those [color=red]SERVICES THAT DO NOT HAVE A "X" ON _ANY_ RUNLEVELS[/color] (Any runlevel means 1,2,3,4,5,6, and S), write them down one by one. Don't make mistakes here. Double check after you've done. [color=blue]Thanks ice60 for wording recommendation![/color]
3. quit sysv-rc-conf.
4. ```
cd /etc/rc0.d
``` - This is for the system shutdown process.
5. ok, now, ```
 ls K*
``` will list all links starting from UPPERCASE letter "K". Compare with your list, change each of the filename containing the service name in your list to start from a lowercase "k". For example, in your list, you have ppp service (which means ppp is turned off at all runlevels), then you can do like: ```
sudo mv K00ppp k00ppp
```. You just change the UPPERCASE K to lowercase k, keep the rest the same. Do this on all of the services in your list.
6. ```
cd ../rc6.d
``` - This is for the system reboot process.
7. ok, you should see similar things here too. So do the same thing here as you did on rc0.d.
8. Now, you reboot and shutdown process should be cleaned up and faster.

The explanation for what you did is pretty simple. The /etc/rc and /etc/rcS scripts run start on each link on each runlevel by scaning if it is starting with a UPPERCASE "S" and run stop on each by scaning if it is starting with a UPPERCASE "K". So for reboot and shutdown runlevels, the most thing we care is the "K" links cause for those services not running on all runlevels, its just not needed to stop them. They are not runing at all.  If some day you want to turn some of the services back on, just change the lowercase "k" to UPPERCASE "K". That's all.

Anyway, it is not intend to work on servers, but I did try on one of my servers has 2.7G P4 and 1.5G mem. It brought the boot process down to 31 secs. I calc'ed it with my watch. Besides, this is with my ftp server and nfs server started on boot time.

[COLOR="Red"]****Note****[/COLOR]
For all of those that having HAL failure problem, try this:
1. change acpi-support from S to 2,3,4,5
2. change acpid from S to 2,3,4,5
3. change dbus from S to 2,3,4,5
4. Reboot. Go to the console and do ```
ps -aef|grep hald
```. If hald service is up, then your dbus subsystem is running fine now. Try it.

[color=blue]**Great comments added by bodhi.zazen. Thanks!!**[/color]
First we should make sure we are left with a bootable system and have backups.

Since we are changing our boot process:

Step 1- Make a bootable GRUB floppy.

[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

Step 2- Backup
Is there any need to back up more then menu.1st, /etc/init.d, /etc/rcS.d, and /etc/rc*.c ( *= 0,1,2,3,4,5,6)?
mkdir /~/bakup.files
sudo cp -P /etc/init.d /~/backup.files
sudo cp -P /boot/grub/menu.1st /~/backup.files
sudo cp -P /etc/rc*.d /~/backup.files
Although a backup of /etc is nice, is it not overkill for this exercise?

Setp 3- Know you Ubuntu Root device (hda1, hdb1, hda2,) and kernel (the numbers in "vmlinuz").
Location of kernel is /boot

Step 4- Modify runlevels.
DO NOT MODIFY DEFAULT RUN LEVELS 0,1, OR 6
MODIFY ONLY 1 RUN LEVEL AT A TIME
RUN LEVEL "S" IS RUN AT EACH RUN LEVEL PRIOR TO OTHERS
ie as system boots (at default) the scritps in rcS.d are run first, then rc2.d

Therefore, if you disable a script in "S", enable the script in runlevel 2
This should guarantee your system will remain bootable to the default run level (2)

In Ubuntu the default run level is 2
Modify only 1 test run level at a time. Choose a custom run level (I will use 3 for the rest of this post, you can use 3,4, or 5).
After modifying the runlevel test without re-booting
sudo init 3
This will change to run level 3
Now check your system.
Problems? Return to default run level and re-configure run level 3
sudo init 2
No problem -> Boot from floppy
No problem, boot from floppy.
When booting (from diskette) to the default run level, the "kernel" line looks like:
kernel=/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
In menu.1st this looks like this:
kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
To boot to run 3 (from GRUB diskette), add a "3" at the end of the line
kernel=/boot/vmlinuz.... root=/dev/..... ro quiet splash 3
Note: the number 3 was added at the end (without quotes)
time boot process.
If OK boot again from floppy (to default run level)
kernel=/boot/vmlinuz..... root=/dev/....
Note: no number 3 at the end of this line
time boot process
This is the default boot and you can measure any time savings.
booting from a floppy to compair apples to apples
If OK you can now change the default run level (or not)
There is more then 1 way to do this
My preferance is to leave the default runlevel unmodified
This leaves the default boot process as a future referance
Change the default boot level
sudo nano /boot/grub/menu.1st
add init=3 to end of line

kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash 3

Or create 2 Ubuntu titles, one for each run level.

OR

Edit /etc/inittab

Step 4- Modify shutdown scripts if desired.

This process should guide users through a logical process of modifying boot scripts without generating a non-bootable system. Backups were made "just in case" but really should not be needed.

---

### Post by Jingo on 2005-11-13
Try InitNG

---

### Post by i3dmaster on 2005-11-13
InitNG is still needing some work, but its another way to try. The way I provided above is based on adjusting the native init process which I feel a little more confortable than replacing the whole thing.

---

### Post by mintcoffee on 2005-11-13
Very nice! I've always wondered what each one of those processes were... and now i've learned a little bit more about the boot process!

Thanks! :KS

---

### Post by i3dmaster on 2005-11-13
[QUOTE=mintcoffee]Very nice! I've always wondered what each one of those processes were... and now i've learned a little bit more about the boot process!

Thanks! :KS[/QUOTE]
Indeed! Its actually a way to learn how your system boots itself up and what you really need and what you don't.

---

### Post by MetalMusicAddict on 2005-11-13
Nice guide. Reminds me of BlackVipers guide for windows services. :)

I would like to see it a little cleaner though. Maybe something like this?

_OLD_
1. acpi-support #You'd better leave it on "X" at S runlevel.

_NEW_
1. **[COLOR="DarkGreen"]acpi-support[/COLOR]** - You'd better leave it on **X** at **S** runlevel.

2. **[COLOR="DarkGreen"]acpid[/COLOR]** **(The acpi daemon)** - These two are for power management, quite important for laptop and desktop computers, so leave them on.

I wouldnt mind organizing it this way if you dont mind. Maybe something we could put up on the WIKI?

---

### Post by mohaham on 2005-11-13
excellent job , Thanks.

---

### Post by Rob2687 on 2005-11-13
Nice work, I'll have to go through all this later.

---

### Post by Heliode on 2005-11-13
Thanks for this guide. I didn't do any benchmarks, but I think its faster now. Plus it feels better to have services disabled that I'm not using anyway, like bluez and ppp... the descriptions and the sysv-rc-conf tool were very helpful as well.

---

### Post by i3dmaster on 2005-11-13
[QUOTE=MetalMusicAddict]Nice guide. Reminds me of BlackVipers guide for windows services. :)

I would like to see it a little cleaner though. Maybe something like this?

_OLD_
1. acpi-support #You'd better leave it on "X" at S runlevel.

_NEW_
1. **[COLOR="DarkGreen"]acpi-support[/COLOR]** - You'd better leave it on **X** at **S** runlevel.

2. **[COLOR="DarkGreen"]acpid[/COLOR]** **(The acpi daemon)** - These two are for power management, quite important for laptop and desktop computers, so leave them on.

I wouldnt mind organizing it this way if you dont mind. Maybe something we could put up on the WIKI?[/QUOTE]
Its a good idea. I will get it updated. Thanks very much!

---

### Post by sailor420 on 2005-11-13
[QUOTE=i3dmaster]III. Alter the /etc/inittab file
```
vi /etc/inittab
```then comment out tty4,tty5, and tty6. Just leave tty1, tty2, and tty3. Three vts should be enough for a laptop or desktop user. Save the file.[/QUOTE]

I'm a bit confused about this part here... Are these the lines that look like:

```
l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
```

Or the ones that look like this:

```

1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6
```

Thanks for the help--looks like a great guide, and like was said, it's nice to know that there's nothing running you don't need.

---

### Post by benplaut on 2005-11-13
you might want to green GDM... i know that some people will go down the list, doing exactly what you did, then reboot to CLI, not knowing what to do...

---

### Post by MetalMusicAddict on 2005-11-13
i3dmaster. Can we list other services that "we" have that "you" may not and get them added to the guide? 

**ie**:855resolu, mdamd-raid (I know related to mdamd),  mountvirt, screen-cl and so on.

I dont really know what all of them are but we could get the definitions together for the list. :)

---

### Post by i3dmaster on 2005-11-13
[QUOTE=MetalMusicAddict]i3dmaster. Can we list other services that "we" have that "you" may not and get them added to the guide? 

**ie**:855resolu, mdamd-raid (I know related to mdamd),  mountvirt, screen-cl and so on.

I dont really know what all of them are but we could get the definitions together for the list. :)[/QUOTE]
Yes, definitely. That's something we all should do to get this list useful for more people.

---

### Post by i3dmaster on 2005-11-13
[QUOTE=sailor420]I'm a bit confused about this part here... Are these the lines that look like:

```
l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
```

Or the ones that look like this:

```

1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6
```

Thanks for the help--looks like a great guide, and like was said, it's nice to know that there's nothing running you don't need.[/QUOTE]
The one with tty1,tty2... at the end. Don't touch the rc ones.

---

### Post by i3dmaster on 2005-11-13
[QUOTE=benplaut]you might want to green GDM... i know that some people will go down the list, doing exactly what you did, then reboot to CLI, not knowing what to do...[/QUOTE]
hmm... ok. I can see what you mean on that... I will update the HowTo.

---

### Post by Jack_S on 2005-11-14
Hi everybody,

In my case turning off Hotplug, sound and correct ATI driver modules are nor loaded. Fujitsu-Siemens Amilo A1630.

Regards,
Jack

---

### Post by mr_pouit on 2005-11-14
It seems readahead is a kind of "preloader". It loads at startup some libs on memory, so that some programs will start faster. But it increases startup time for about 3-4 seconds. So, you can keep it... or not :lol:

---

### Post by i3dmaster on 2005-11-14
[QUOTE=Jack_S]Hi everybody,

In my case turning off Hotplug, sound and correct ATI driver modules are nor loaded. Fujitsu-Siemens Amilo A1630.

Regards,
Jack[/QUOTE]
Another way to load your sound card driver is to add the module to the /etc/modules (the module-init-tool boot up process will load modules in that file) file but you need to know the chip set name of your sound card. ```
lspci -v
```should tell you.
As far as the ATI driver, I am not quite sure why it need hotplug subsystem. Did you compile the driver yourself? If the driver is in the correct place (/lib/modules/$KERNEL-VER/kernel/drivers/video). If you see it, take a look the /etc/modprobe.d/alias file and see if it is added. Also, take a look another thread here talking about how to get ATI driver to work...

---

### Post by i3dmaster on 2005-11-14
[QUOTE=mr_pouit]It seems readahead is a kind of "preloader". It loads at startup some libs on memory, so that some programs will start faster. But it increases startup time for about 3-4 seconds. So, you can keep it... or not :lol:[/QUOTE]
Yes, it looks that way. I will try and see if there is any benefits to load it on boot time. Thanks very much and I will update the HowTo on this.

---

### Post by GoA on 2005-11-14
Here's my opinion. I had disabled some services through BUM which is easier method. With this thread I stopped few more services and the result was that I didn't have no sound (hotkey is needed for that, using regular computer). After fixing sound everything worked but the speed difference was so minimal with modern computer that the whole thing was quite a useless. I don't actually feel any difference with or wothout using the bum to disable services. Using athlon 2800+ and 1 gig of memory with sata hd.

---

### Post by i3dmaster on 2005-11-14
[QUOTE=GoA]Here's my opinion. I had disabled some services through BUM which is easier method. With this thread I stopped few more services and the result was that I didn't have no sound (hotkey is needed for that, using regular computer). After fixing sound everything worked but the speed difference was so minimal with modern computer that the whole thing was quite a useless. I don't actually feel any difference with or wothout using the bum to disable services. Using athlon 2800+ and 1 gig of memory with sata hd.[/QUOTE]
It may be a stupid question but what's BUM? Anyway, you should know there is always more than one way to do things in Linux, so I am glad you are satisfied with BUM, but knowing more of each daemon and what they are doing wouldn't be a bad thing all at. And I am pretty sure some will get a dramatic difference and some don't after adjusting it cause you might have already disabled most of the services that you don't need. I didn't say this will benefit for everyone.

---

### Post by GoA on 2005-11-14
Bum is boot-up-manager. You can find a lot of information about it from here by using search. Actually, it's developing forum is in here. And like I said, I don't notice the difference with all the services on or most of them shutdown. Because they require so little power with modern computers. Of course with older ones this can effect a lot on the performance.

link to bum: [http://www.ubuntuforums.org/forumdisplay.php?s=&daysprune=30&f=75](http://www.ubuntuforums.org/forumdisplay.php?s=&daysprune=30&f=75)

---

### Post by Caboto on 2005-11-14
The first time i tried this howto, my sound didn't work anymore. Even if i turn alsa on. So i tried to turn on some other things, but it seems i put 'em to the wrong runlevel. My PC crashed everytime the x server started.
Happily i've got a backup from my /etc folder. This time I just turned off the things, which i was sure of, that i don't need 'em. Now it all works out.

But i would suggest before turning something completly off, write down what runlevel they are in.

And I've always wondered how I can modify the shutdown sequence. It tries to shut down things, which aren't even there anymore. This don't really reduce the shutdown-time (at least i guess so), but it would be nice to know and it would look a little bit nicer as when there are tons of red "failed".


Nevertheless, i always wanted to know what things are in the boot sequence. Thanks for your information! :)

---

### Post by Sionide on 2005-11-14
Regardless of bootup speed gains, it seems worthwhile to get rid of any services you won't ever use. Thanks for this..

---

### Post by i3dmaster on 2005-11-14
[QUOTE=Caboto]The first time i tried this howto, my sound didn't work anymore. Even if i turn alsa on. So i tried to turn on some other things, but it seems i put 'em to the wrong runlevel. My PC crashed everytime the x server started.
Happily i've got a backup from my /etc folder. This time I just turned off the things, which i was sure of, that i don't need 'em. Now it all works out.

But i would suggest before turning something completly off, write down what runlevel they are in.

And I've always wondered how I can modify the shutdown sequence. It tries to shut down things, which aren't even there anymore. This don't really reduce the shutdown-time (at least i guess so), but it would be nice to know and it would look a little bit nicer as when there are tons of red "failed".


Nevertheless, i always wanted to know what things are in the boot sequence. Thanks for your information! :)[/QUOTE]
Thanks for your feedback! The shutdown part is coming soon and its easier than configuring bootup processes.

---

### Post by i3dmaster on 2005-11-14
[QUOTE=Sionide]Regardless of bootup speed gains, it seems worthwhile to get rid of any services you won't ever use. Thanks for this..[/QUOTE]
Yes indeed! Knowing what you need and what you don't is always better and safer.

---

### Post by adamb10 on 2005-11-14
A regular Ubuntu system boots in about 44 seconds to the logins screen for me on a Athlon XP 2100.  After using this Howto, I feel it chopped 5 seconds off the boot time.  :)

Good Work.

PS Is there a way to speed up the network part in the boot?  It's the slowest for me.

---

### Post by GoldBuggie on 2005-11-15
Really nice guide...I love the tool you recommended to use. I used the tool BUM(boot-up-mgr) before but I can't turn everything off and it isn't nearly as flexible. Thank you.

About readahead...the project is called readahead-list and it preloads files into the page cache to accelerate program loading. The files it caches are stored in */etc/readahead/readahead*.

Maybe experimenting with it can make firefox load faster hmmm...something to check into for me I think.

Anyway...thx again for a nicely written guide. I like it cause it tweaks  the existing system to your needs instead of replacing it with something new.

---

### Post by i3dmaster on 2005-11-15
[QUOTE=adamb10]A regular Ubuntu system boots in about 44 seconds to the logins screen for me on a Athlon XP 2100.  After using this Howto, I feel it chopped 5 seconds off the boot time.  :)

Good Work.

PS Is there a way to speed up the network part in the boot?  It's the slowest for me.[/QUOTE]
The way I changed was not let the hotplug system to detect my pcmcia card and activate the network but change it to auto from the /etc/network/interfaces file. You will see on the file there is a portion to mapping hotplug devices.. I commented that out and add my ath0 after the "auto lo", so its "auto lo ath0". Also, I changed the pcmcia service start runlevel from 2,3,4,5 to S, so it loads it first and then networking script loads my network configuration. Its faster than use the hotplug subsystem. If you don't use pcmcia and have an internal ethernet card, you don't even need to bother opening that service.

---

### Post by i3dmaster on 2005-11-15
[QUOTE=GoldBuggie]Really nice guide...I love the tool you recommended to use. I used the tool BUM(boot-up-mgr) before but I can't turn everything off and it isn't nearly as flexible. Thank you.

About readahead...the project is called readahead-list and it preloads files into the page cache to accelerate program loading. The files it caches are stored in */etc/readahead/readahead*.

Maybe experimenting with it can make firefox load faster hmmm...something to check into for me I think.

Anyway...thx again for a nicely written guide. I like it cause it tweaks  the existing system to your needs instead of replacing it with something new.[/QUOTE]
Yes, the readahead thing is something that I am not sure. I didn't feel a whole lot faster though by stopping or starting it... so I am not sure if it really that promising...

---

### Post by manicka on 2005-11-15
I have added this how-to to the Ubuntu Document Storage Facility

[http://doc.gwos.org/index.php/Speed_up_boot](http://doc.gwos.org/index.php/Speed_up_boot)

---

### Post by i3dmaster on 2005-11-15
[QUOTE=manicka]I have added this how-to to the Ubuntu Document Storage Facility

[http://doc.gwos.org/index.php/Speed_up_boot](http://doc.gwos.org/index.php/Speed_up_boot)[/QUOTE]
Thank you very much sir!

---

### Post by crispingatiesa on 2005-11-15
I made the suggested changes and it gave an error , unable to start halt, so I went bacjk and enable it and when rebooted happens that the process starts ok  but after passing the part of "loading extra binaries" in the splash boot the computers goes off all the time. Bottom line is I cannot acces the ubuntu box anymore, any thoughs in how to rollback someway?

---

### Post by i3dmaster on 2005-11-15
[QUOTE=crispingatiesa]I made the suggested changes and it gave an error , unable to start halt, so I went bacjk and enable it and when rebooted happens that the process starts ok  but after passing the part of "loading extra binaries" in the splash boot the computers goes off all the time. Bottom line is I cannot acces the ubuntu box anymore, any thoughs in how to rollback someway?[/QUOTE]
Ok, sounds like you enabled halt on all runlevels. The halt service can only be enabled at runlevel 0 which is to shutdown the computer. You can use Live CD to change it back but let's try to boot to single mode first. When you see the grub menu, hit "e" to edit the default boot line. After you hit "e", you will see the detail boot options. Go to the kernel line and hit "e" again, then you can edit the kernel options, at the end of the line, input "single", then "enter", after that hit "b" to boot. If you can boot to the single mode, then try to run sysv-rc-conf again to change the halt to only start at runlevel "0". Let me know if this works or not.

---

### Post by domino on 2005-11-16
This was a good how-to and I'm sure it works for a lot of folks. But this is the only how-to I have gone through that actually broke gnome. Granted that it was partially my fault for not taking screenshots noting of all the runlevels I changed, it still should have been stated in the how-to about totally screwing up my perfect ubuntu install.

Now I'm stuck with this windows OS till I this ^%&% fixed. So damn frustrating. I thought I would safe at least 20 seconds of boot time, but ended up trying to fix what's broken for 5 damn hours.

Now to my problem, I back stepped the how-to and renamed all the k* back to K*, uncommitted this lines in the inittab file. The only thing I could not fix was the runlevel. I can boot all the way to gnome but the splash screen does not show and neither does the desktop. Only the brown Ubuntu background and the cursor. How do I set the runlevel back to default?

---

### Post by i3dmaster on 2005-11-16
[QUOTE=domino]This was a good how-to and I'm sure it works for a lot of folks. But this is the only how-to I have gone through that actually broke gnome. Granted that it was partially my fault for not taking screenshots noting of all the runlevels I changed, it still should have been stated in the how-to about totally screwing up my perfect ubuntu install.

Now I'm stuck with this windows OS till I this ^%&% fixed. So damn frustrating. I thought I would safe at least 20 seconds of boot time, but ended up trying to fix what's broken for 5 damn hours.

Now to my problem, I back stepped the how-to and renamed all the k* back to K*, uncommitted this lines in the inittab file. The only thing I could not fix was the runlevel. I can boot all the way to gnome but the splash screen does not show and neither does the desktop. Only the brown Ubuntu background and the cursor. How do I set the runlevel back to default?[/QUOTE]
Sorry to hear that your box was broken by tuning the boot process. I want to help you out to get it back. I am sure there must have some misconfigurations in the runlevels. Ok, your default GUI runlevel should be at 2. So check your xorg-common service and make sure its up at runlevel 2. Also, check to make sure your /home/yourname dir is not residing in any lvm or raid devices cause in my HowTo, those services were turned off since I don't use them, but it might be a different case in your situation. If you didn't backup your /etc dir, its hard now to back step to the original status. Post your problems here and I will try to help out as much as I can. And I can tell you that this can be fixed.

---

### Post by domino on 2005-11-16
I'm able to boot straight into user land by fallowing this how-to:

InitNG: [http://ubuntuforums.org/showthread.php?t=80423&highlight=boot+process](http://ubuntuforums.org/showthread.php?t=80423&highlight=boot+process)

Before that, I could only boot into root land via "recovery mode". I added InitNG to my boot menu. I still have the original boot options though. I'm having a lot of other issues with InitNG, more than I'd like to dedicate my time on. So, I just want to get my runlevels back to where they were and boot into user land as before.

> Sorry to hear that your box was broken by tuning the boot process.

My luck had to run out sooner or later. :)

> Ok, your default GUI runlevel should be at 2. So check your xorg-common service and make sure its up at runlevel 2.

My xorg-common service is set to S. I'll change to 2 and reboot. I'll post back with what ever happens.

> Also, check to make sure your /home/yourname dir is not residing in any lvm or raid devices cause in my HowTo, those services were turned off since I don't use them, but it might be a different case in your situation.

My home dir is still where it is at. I don't have raid or lvm set up.

> If you didn't backup your /etc dir, its hard now to back step to the original status. And I can tell you that this can be fixed.

That's the first thing I would have done had I known :(. I know better now.

If there is any information I can provide, let me know.

---

### Post by domino on 2005-11-16
After setting xorg-common service from S to 2, I still couldn't get into user destop. Still stuck at the brown background with only a pointer. I know most of the names I had changed runlevels on. Is there a list of default runlevels? Or does it vary between boxes on evry fresh install?

acpid
alsa / alsa-utils
apmd
bluez-util
cupsys
dbus
dns-clean
evms
fetchmail
hotkey-se$
hotplug / hotplug-n$
hplip
lvm
mdadm / mdadm-raid
pcmcia
powernowd
ppp / pppd-dns
readahead
rsync
xorg-common (was set to S, but I never touched it)

---

### Post by i3dmaster on 2005-11-16
[QUOTE=domino]After setting xorg-common service from S to 2, I still couldn't get into user destop. Still stuck at the brown background with only a pointer. I know most of the names I had changed runlevels on. Is there a list of default runlevels? Or does it vary between boxes on evry fresh install?

acpid
alsa / alsa-utils
apmd
bluez-util
cupsys
dbus
dns-clean
evms
fetchmail
hotkey-se$
hotplug / hotplug-n$
hplip
lvm
mdadm / mdadm-raid
pcmcia
powernowd
ppp / pppd-dns
readahead
rsync
xorg-common (was set to S, but I never touched it)[/QUOTE]

xorg-common turned on at runlevel S is fine. I just want to make sure its there. Also, turn on your favorite logon manger, either GDM or KDM, so that you can go directly to GUI. I don't see you cron daemon there, its bad to turn that off. I don't see any of your log daemons on, such as bootlogd, sysklogd, etc. If you don't have lvm and raid at all, no need to leave lvm and mdadm/mdadm-raid on.  I don't see udev/udev-mtab on, that's not good. I don't see vbesave on. Please look  carefully and make sure.

---

### Post by grizzly on 2005-11-16
I think i configured too much. 
Now it boots into a blank screen, both with the normal and recovery mode. Everything seems to go well then suddenly the three lights on my keyboard blink and and the harddisk goes dead.

Where exactly are the settings configured by sysv-rc-conf stored. I'll use a livecd to restore things.

Thanks for the nice tut by the way

---

### Post by i3dmaster on 2005-11-16
[QUOTE=grizzly]I think i configured too much. 
Now it boots into a blank screen, both with the normal and recovery mode. Everything seems to go well then suddenly the three lights on my keyboard blink and and the harddisk goes dead.

Where exactly are the settings configured by sysv-rc-conf stored. I'll use a livecd to restore things.

Thanks for the nice tut by the way[/QUOTE]
hmm... that's weird. Make sure you didn't touch the halt and reboot services. There are some services you shouldn't touch even just change the runlevels. All the boot up scripts are at /etc/init.d dir and they are also linked to /etc/rcx.d dir according to the sysv-rc-conf settings. If a certain service turned on at a certain runlevel, then you will see a Sxxname link, otherwise, you will see a Kxxname link.

---

### Post by grizzly on 2005-11-16
Oh i think its some other problem since i couldn't mount ext3( bad superblock). I guess that wouldn't happen due to services.

---

### Post by domino on 2005-11-16
> I don't see you cron daemon there, its bad to turn that off. I don't see any of your log daemons on, such as bootlogd, sysklogd, etc. If you don't have lvm and raid at all, no need to leave lvm and mdadm/mdadm-raid on. I don't see udev/udev-mtab on, that's not good. I don't see vbesave on. Please look carefully and make sure.
I didn't list the other you mentioned because I didn't touch/change the values. But they are lised and working (I think). The values I did change I listed above. 

Edit: Maybe images will help?

[[IMG]http://img83.imageshack.us/img83/8184/16rt.th.png[/IMG]](http://img83.imageshack.us/my.php?image=16rt.png) [[IMG]http://img83.imageshack.us/img83/2323/23xv.th.png[/IMG]](http://img83.imageshack.us/my.php?image=23xv.png)

---

### Post by crispingatiesa on 2005-11-16
[QUOTE=i3dmaster]Ok, sounds like you enabled halt on all runlevels. The halt service can only be enabled at runlevel 0 which is to shutdown the computer. You can use Live CD to change it back but let's try to boot to single mode first. When you see the grub menu, hit "e" to edit the default boot line. After you hit "e", you will see the detail boot options. Go to the kernel line and hit "e" again, then you can edit the kernel options, at the end of the line, input "single", then "enter", after that hit "b" to boot. If you can boot to the single mode, then try to run sysv-rc-conf again to change the halt to only start at runlevel "0". Let me know if this works or not.[/QUOTE]

Sorry for not answering before but I was travelling I just make it home.

I figure out that that's was the problem and the fact that english is not my mother tongue so, words don't jump at me telling me IDIOT DON't DO IT :???: 

I tried what you suggested but to no avail. There is something else I could do to fix it?

Thanks

---

### Post by crispingatiesa on 2005-11-16
Hi, guys thanks for the support, I manage to boot by renaming the halt file in the run level s.

---

### Post by jrincon87 on 2005-11-16
> 2. ok, open your eyes and _look very carefully for those SERVICES DO NOT HAVE "X" ON ALL RUNLEVELS_ (All runlevel means 1,2,3,4,5,6, and S), write them down one by one. Don't make mistakes here. Double check after you've done.

I'm confused about this part. It seems there is a small redaction mistake there. What do you mean: that I should write down all the services that has X in some runlevels, or those who have no X at all?

Thanks.

---

### Post by i3dmaster on 2005-11-16
[QUOTE=crispingatiesa]Hi, guys thanks for the support, I manage to boot by renaming the halt file in the run level s.[/QUOTE]
Great! You solved it by yourself. See, you just learned something.

---

### Post by i3dmaster on 2005-11-16
[QUOTE=jrincon87]I'm confused about this part. It seems there is a small redaction mistake there. What do you mean: that I should write down all the services that has X in some runlevels, or those who have no X at all?

Thanks.[/QUOTE]
You write down for services that has NO "X" at all runlevels. (NO "X" all all)

---

### Post by i3dmaster on 2005-11-17
[QUOTE=domino]I didn't list the other you mentioned because I didn't touch/change the values. But they are lised and working (I think). The values I did change I listed above. 

Edit: Maybe images will help?

[[IMG]http://img83.imageshack.us/img83/8184/16rt.th.png[/IMG]](http://img83.imageshack.us/my.php?image=16rt.png) [[IMG]http://img83.imageshack.us/img83/2323/23xv.th.png[/IMG]](http://img83.imageshack.us/my.php?image=23xv.png)[/QUOTE]
After you looked at you screen, I am getting confused. I am wondering if you are trying to configure a server or what? Can you tell me what you have some many server daemons turned on? Do you need to dial up to network? ... I am going to send you my laptop boot up process configuration. Ok, remember, its for laptop.

---

### Post by domino on 2005-11-17
> After you looked at you screen, I am getting confused. I am wondering if you are trying to configure a server or what?
This is not a production server. I use it as a sandbox (ISPConfig) and 70% of work done is in Ubuntu using wine and vmware. The rest is in native windows and OSx86, tri-boot.

When I changed the daemon settings, I was aware of what third party daemons were running and I didn't touch them. I listed the ones that I changed on page 5. I just need to figure out the default runlevel of those services prior to changing them. I'll checkout your config and see if anything possitive comes out of them.

> Do you need to dial up to network?
I don't have a dialp modem, but if wre turned on by default, that's the way I want it. Again,I don't know if it was on by default. Damn myself. Should have taken screenies before I started this.

Thanks for your time

---

### Post by domino on 2005-11-17
I visually diffed your config but it didn't work. So I pretty much got ballistic and just enable/disabled all kinds of tihs. I can't say I learned much from it because I didn't really know what I was doing. Luck was on my side the 3rd try. I think Hotplug or VMWare did the trick. I'm about 20% sure of it, and I'm not willing to test and see if it was the cause. Can you please look at the new visuals and see if something is out of wack?

[[IMG]http://img499.imageshack.us/img499/9544/w14qh.th.png[/IMG]](http://img499.imageshack.us/my.php?image=w14qh.png) [[IMG]http://img499.imageshack.us/img499/1214/w29jr.th.png[/IMG]](http://img499.imageshack.us/my.php?image=w29jr.png)

---

### Post by i3dmaster on 2005-11-17
[QUOTE=domino]I visually diffed your config but it didn't work. So I pretty much got ballistic and just enable/disabled all kinds of tihs. I can't say I learned much from it because I didn't really know what I was doing. Luck was on my side the 3rd try. I think Hotplug or VMWare did the trick. I'm about 20% sure of it, and I'm not willing to test and see if it was the cause. Can you please look at the new visuals and see if something is out of wack?

[[IMG]http://img499.imageshack.us/img499/9544/w14qh.th.png[/IMG]](http://img499.imageshack.us/my.php?image=w14qh.png) [[IMG]http://img499.imageshack.us/img499/1214/w29jr.th.png[/IMG]](http://img499.imageshack.us/my.php?image=w29jr.png)[/QUOTE]
I've said at the beginning that this HowTo was not intend to work on Servers cause it trys to turn off all unnecessary server daemons... Anyway, looks like you are still not sure what stuff that you don't need. Let me get through all of them by asking you questions.
1. acpi-support - you turned it on at 2,3,4,5 and S, which is wrong. If you turned it on at S runlevel, you can safely turn them of at 2,3,4,5. Or you keep them on at 2,3,4,5 but turn off S level.
2. acpid - The same as above.
3. alsa - you can turn it off at all runlevels.
4. alsa-utils - This one supercedes the alsa daemon, so just turn it on at S runlevel.
5. anacron - fine.
6. apache2 - web server. Do you need it?
7. apmd - fine.
8. atd - fine
9. bind9 - DNS server. Do you need it?
10. bluez-utiles - bluetooth daemon. Do you need it? Again, S and other runlevels shouldn't be turned on at the same time.
11. bootlogd - fine.
12. clamav-fr$ - Not sure what that is... No comments.
13. courier-* - Not sure what they are doing ... No comments.
14. cron - fine.
15. cupsys - Not turned on, which is ok
16. dbus - fine
17. ddclient - Looks like its DHCP client. Do you need it?
18. dns-clean - Should be at S runlevel.
19. evms - Enterprise Volume manager. Do you need this?
20. fetchmail - Not turned on. ok
21. gdm - fine
22. halt - fine
23. hdparm - Turn on at S runlevel. Turn off on all the others. 
24. Hotkey-setup - ok
25. hotplug - Either on 2,3,4,5 or on S runlevel. Same problem as before.
26. hotplug-net - ok
27. hplip - Not on, ok
28. ifrename - ok
29. ifupdown* - ok
30. ispconfig - 2,3,5. Should be ok
31. klogd - fine
32. linux-restrict-modules-common - ok
33. lvm - ok but do you use LVM at all?
34. makedev - ok
35. mdadm - RAID. Do you need it ?
36. mdadm-raid - Not on, ok. And you probably don't need mdadm either.
37. module-init-tool - ok
38. mountvirtfs - ok
39. mysql - database daemon. Do you need it?
40. networking - ok
41. ntpdate - sync time server. fine
42. pcmcia - Turned off. ok
43. postfix - MTA. Mail server. Do you need it?
44. powernowd - Not on, ok
45. ppp* - Not on. ok
46. proftpd - ftp server. Do you need it?
47. quota* - quota support. fine
48. readahead - fine
49. reboot - fine
50. rmnologin - fine
51. rsync and samba - All off. ok
52. saslauthd* - mail SASL auth daemon. fine
53. screen-cleanup - fine
54. sendsigs - fine
55. single - fine
56. ssh - fine
57. stop-bootlogd - fine
58. sudo - fine
59. sysklogd - fine
60. udev* - fine
61. umountfs - fine
62. urandom - fine
63. usplash - fine
64. vbesave - fine
65. vmware - fine
66. xorg-common - fine
Let me know what you think about..

---

### Post by GoldBuggie on 2005-11-17
Just to give some info here on the other end of boot, that is **shutdown**. I issued the command ```
sudo sysv-rc-conf -p
``` which gives you a table mych like before but with 3 states instead of 2. These 3 states are as follows:

*nothing:* the process is never used
*SXX: *The process will start during boot and XX denotes when. XX=10 means it gets started before S20.
*KXX:* The proces will be shutdown during shutdown.

Since I have removed alot of processes during boot I wanted to look at the shutdown process and I noticed that ALOT of processes are beeing shutdown that never are started. So I basically removed all the lines containing only *KXX* and **NO** *SXX*. This made a huge difference on reboot and shutdown.

---

### Post by twigsby on 2005-11-17
> Originally Posted by domino
I visually diffed your config but it didn...

Completely offtopic, but where could I find that terminal background?

---

### Post by domino on 2005-11-18
[QUOTE=i3dmaster]I've said at the beginning that this HowTo was not intend to work on Servers cause it trys to turn off all unnecessary server daemons... 
[/QUOTE]
I was fully aware that this how-to was geared towards non-servers. That's why I didn't touch the ones I knew I needed to develope websites. All of the web services, apache2, bind, clamav, dns, postfix, etc., ties in with ISPConfig. I didn't touch those. The only one which I "thought" I didn't touch was VMWare. The fonts is for the email server.

[QUOTE=i3dmaster]Let me know...
[/QUOTE]
Since I did all my backups and screenies, I did what you suggested on your last post and the boot time was trully noticable. Thank you for the personal time to get me through this. Now i'm off to rename those reboot and startup files.

OT: @twigsby, the terminal is transparent. You can set this by executing Terminal: Edit -> Current Profile --> Effects

Thank you

---

### Post by i3dmaster on 2005-11-18
[QUOTE=domino]I was fully aware that this how-to was geared towards non-servers. That's why I didn't touch the ones I knew I needed to develope websites. All of the web services, apache2, bind, clamav, dns, postfix, etc., ties in with ISPConfig. I didn't touch those. The only one which I "thought" I didn't touch was VMWare. The fonts is for the email server.


Since I did all my backups and screenies, I did what you suggested on your last post and the boot time was trully noticable. Thank you for the personal time to get me through this. Now i'm off to rename those reboot and startup files.

OT: @twigsby, the terminal is transparent. You can set this by executing Terminal: Edit -> Current Profile --> Effects

Thank you[/QUOTE]
Great! Glad to hear you've got things straighted out.

---

### Post by domino on 2005-11-18
[QUOTE=GoldBuggie]So I basically removed all the lines containing only *KXX* and **NO** *SXX*. This made a huge difference on reboot and shutdown.[/QUOTE]
Let me get this straight. For example, if alsa is disabled on startup, I can clear out 1,2,3,4,5,0,6,S? If not, please give an example. runlevels aren't something we see every day, and I get overwhelmed by these configurations.

Thanks

---

### Post by i3dmaster on 2005-11-18
[QUOTE=domino]Let me get this straight. For example, if alsa is disabled on startup, I can clear out 1,2,3,4,5,0,6,S? If not, please give an example. runlevels aren't something we see every day, and I get overwhelmed by these configurations.

Thanks[/QUOTE]
Go to your sysv-rc-conf, if you see alsa does not have "X" on ANY runlevel (1,2,3,4,5,6,0,S), its safe to go to /etc/rc0.d and /etc/rc6.d to mv Kxxalsa to kxxalsa. (Uppercase K to lowercase k)

---

### Post by domino on 2005-11-18
:) I read that on your original post. I just thought that comparing 2 term screens side by side, I would be less proned to making visual mistakes.

Edit: I see something strange with alsa and alsa-utils. Remember when you said this:

> 3. alsa - you can turn it off at all runlevels.
4. alsa-utils - This one supercedes the alsa daemon, so just turn it on at S runlevel.

I ran *sysv-rc-conf* and now both alsa and alsa-utils are cleared out, but can still listen to my internet radio though. I'm asuming that alsa is the sound server?

---

### Post by i3dmaster on 2005-11-18
[QUOTE=domino]:) I read that on your original post. I just thought that comparing 2 term screens side by side, I would be less proned to making visual mistakes.

Edit: I see something strange with alsa and alsa-utils. Remember when you said this:



I ran *sysv-rc-conf* and now both alsa and alsa-utils are cleared out, but can still listen to my internet radio though. I'm asuming that alsa is the sound server?[/QUOTE]
alsa driver database is compiled in kernel, so normally if you are not having a rare sound card, you will have it enabled by default. The alsa or alsa-utils is the bootup process to restore the alsa configuration settings, such as mixer level, channel level, etc...

---

### Post by domino on 2005-11-18
Gotcha. I'm done and very satisfied with my load time and runlevels. Cold boot dropped from 80sec. to 50secs. Shutdown dropped from 25sec. to 15sec. Thanks for all the assistance.

---

### Post by grizzly on 2005-11-18
Me again! 
This time i was carefull, but still managed to mess up :rolleyes: .
Now i can boot in the syatem, so all i want is info abt the default status of each services. Whether it was in runlevel 3 or S etc. That should be easy, i guess
And by default i mean original, that came with the installation, *not* after tweaking.
Then i can simply compare and correct.

Thanks

btw does it matter if a servcie say alsa starts in runlevel 2 or S?

---

### Post by i3dmaster on 2005-11-18
[QUOTE=grizzly]Me again! 
This time i was carefull, but still managed to mess up :rolleyes: .
Now i can boot in the syatem, so all i want is info abt the default status of each services. Whether it was in runlevel 3 or S etc. That should be easy, i guess
And by default i mean original, that came with the installation, *not* after tweaking.
Then i can simply compare and correct.

Thanks

btw does it matter if a servcie say alsa starts in runlevel 2 or S?[/QUOTE]
S is the first runlevel, then the runlevel defined in inittab. Typically, it shouldn't matter but the thing you need to consider is the sequence or dependency. Some services depend on other ones. For example, if you have a pcmcia network card, then the networking script MUST run after the pcmcia service. When you switch the runlevels, you need to be careful on this type of thing. From my point of view, runlevel S intends to be a level that enables all hardware related services, which means at this runlevel, all the hardware should be detected and modules loaded. When system goes to upper runlevels, it shouldn't worry about any hardware problems, then we can enable network, GUI, all different kind of server daemons, and such...

---

### Post by IdolizingStewie on 2005-11-22
I followed this How-To a couple days ago and, like an idiot, failed to note the specific changes I was making. I finally got around to rebooting today and when the computer starts back up it gives me an internal error "Failed to initialize HAL." Can anyone tell me which services I need for HAL and maybe what runlevels they need to be on? I suspect this is why I can no longer mount my external HDD which, while not vital, is extremely annoying since it has all my music.

---

### Post by i3dmaster on 2005-11-22
[QUOTE=IdolizingStewie]I followed this How-To a couple days ago and, like an idiot, failed to note the specific changes I was making. I finally got around to rebooting today and when the computer starts back up it gives me an internal error "Failed to initialize HAL." Can anyone tell me which services I need for HAL and maybe what runlevels they need to be on? I suspect this is why I can no longer mount my external HDD which, while not vital, is extremely annoying since it has all my music.[/QUOTE]
Enable hotplug at runlevel S and try again.

---

### Post by IdolizingStewie on 2005-11-23
[QUOTE=i3dmaster]Enable hotplug at runlevel S and try again.[/QUOTE]

Success! I had apparently left hotplug on, but when I looked at it again, I found a couple places where I'd goofed and started services in 2-5 and S. Fixing those fixed it.

Thanks for the how-to. The faster boot-up is nice, but given how rarely I reboot, I appreciate more what I've learned about the start-up process and the knowledge that services I'm not using are shut off.

---

### Post by mangocrazy on 2005-11-30
Hi - absolute newbie alert...

I'v read this thread and am keen to try and reduce boot times on an older system I have, but when I try the first step in the process (i.e. getting and installing the package) I get the following response:

jackie@jackie:~$ **sudo apt-get update**
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates Release [19.6kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Sources
Fetched 39.6kB in 0s (85.5kB/s)
Reading package lists... Done
jackie@jackie:~$ **sudo apt-get install sysv-rc-conf**
Reading package lists... Done
Building dependency tree... Done
Package sysv-rc-conf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sysv-rc-conf has no installation candidate
jackie@jackie:~$

Does this mean that the tool is no longer available or has been moved, or am I doing something dumb?

Thanks,

Graham

---

### Post by dolson on 2005-11-30
[QUOTE=mangocrazy]Hi - absolute newbie alert...

I'v read this thread and am keen to try and reduce boot times on an older system I have, but when I try the first step in the process (i.e. getting and installing the package) I get the following response:

jackie@jackie:~$ **sudo apt-get update**
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates Release [19.6kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Sources
Fetched 39.6kB in 0s (85.5kB/s)
Reading package lists... Done
jackie@jackie:~$ **sudo apt-get install sysv-rc-conf**
Reading package lists... Done
Building dependency tree... Done
Package sysv-rc-conf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sysv-rc-conf has no installation candidate
jackie@jackie:~$

Does this mean that the tool is no longer available or has been moved, or am I doing something dumb?

Thanks,

Graham[/QUOTE]

You need to enable the Universe repositories. I'd recommend you do so via Synaptic's UI.

---

### Post by veloct on 2005-11-30
Great How-To I3dmaster!!  I boot up about 5-10 secs faster and I'm not loading a bunch of things I'm not using.  Also my reboots and shutdowns are much cleaner and quicker.  Thanks for this. :)

---

### Post by i3dmaster on 2005-11-30
[QUOTE=veloct]Great How-To I3dmaster!!  I boot up about 5-10 secs faster and I'm not loading a bunch of things I'm not using.  Also my reboots and shutdowns are much cleaner and quicker.  Thanks for this. :)[/QUOTE]
Glad it helps. :)

---

### Post by KermitJr on 2005-11-30
[QUOTE=i3dmaster]InitNG is still needing some work, but its another way to try. The way I provided above is based on adjusting the native init process which I feel a little more confortable than replacing the whole thing.[/QUOTE]

What are the chances you could build an autoscripter like Automatix or EasyUbuntu to makes these changes via GUI?

THanks,
KJ

---

### Post by MetalMusicAddict on 2005-11-30
Do you know what theres are?

**bind9** (just related to network-manager?) Turned off. Stopped using network-manager
**linux-res$** (is this "linux-restricted-modules-common"?)
**mountvirt** (looked but cant find what it is. Related to WINE or VNC?)
**ntp-server** (a time server sync?) Turned off.
**samba** (Know what it is just not how to define it. :))
**sendmail** (related to "fetchmail"? Just for mail servers?) Turned off.

---

### Post by otake-tux on 2005-11-30
I hate it how at the boot up it searches for network connections. I'm dont know if using dissabeling it via the scrip you reccomend is the solution.  Anyone know how to do this.  of course I would like to start my connections manually.

btw-I use a laptop and for wireless I need ndiswrapper, just in case this affects anything.

---

### Post by arphe_el on 2005-11-30
i just want to uncheck the ntpdate on bootup since during the internet connection is off it takes too long to boot-up. But when i'm on the system >administration>bootup manager 

...startup and shutdown scripts and uncheck it it says "Editing in run level S is not allowed!  Playing with rcS.d symlinks is an administration activity requiring deep knowledge of the runlevel system."

is there anyway to edit it? 

also is there a way that my system is not dependent on updates over the internet and just update it manually if i want? so that whether connected online or offline my computer runs normally.

thanks any help are greatly appreciated. GODspeed!

---

### Post by i3dmaster on 2005-12-01
[QUOTE=KermitJr]What are the chances you could build an autoscripter like Automatix or EasyUbuntu to makes these changes via GUI?

THanks,
KJ[/QUOTE]
There is already a GUI app called services that you can use. Its simple and mainly for beginners. sysv-rc-conf can be considered a console GUI which is much more powerful. I don't see a need just for another GUI app. The most important thing is to learn and understand what those services are and what they do so that you can make up your mind whether you need it or not.

---

### Post by i3dmaster on 2005-12-01
[QUOTE=MetalMusicAddict]Do you know what theres are?

**bind9** (just related to network-manager?) Turned off. Stopped using network-manager
**linux-res$** (is this "linux-restricted-modules-common"?)
**mountvirt** (looked but cant find what it is. Related to WINE or VNC?)
**ntp-server** (a time server sync?) Turned off.
**samba** (Know what it is just not how to define it. :))
**sendmail** (related to "fetchmail"? Just for mail servers?) Turned off.[/QUOTE]
bind9 - The DNS server. If you don't provide DNS name resolution, there is no need to  turn it on.
linux-restrict-modules-common - All linux restrict modules made by ubuntu team. They are under /lib/linux-restrict-modules. You will probably need it on.
mountvirtfs - maintain Linux virtual filesystems, such as devpts, sysfs, usbfs, shm..., you need it.
ntp-server - a time server. you don't need it.
samba - a windows smb sharing server. The conf file is under /etc/samba/smb.conf
sendmail - a unix MTA, mail server.

---

### Post by i3dmaster on 2005-12-01
[QUOTE=otake-tux]I hate it how at the boot up it searches for network connections. I'm dont know if using dissabeling it via the scrip you reccomend is the solution.  Anyone know how to do this.  of course I would like to start my connections manually.

btw-I use a laptop and for wireless I need ndiswrapper, just in case this affects anything.[/QUOTE]
If you don't need network up during the boot time, turn off networking, hotplug-network.

---

### Post by i3dmaster on 2005-12-01
[QUOTE=arphe_el]i just want to uncheck the ntpdate on bootup since during the internet connection is off it takes too long to boot-up. But when i'm on the system >administration>bootup manager 

...startup and shutdown scripts and uncheck it it says "Editing in run level S is not allowed!  Playing with rcS.d symlinks is an administration activity requiring deep knowledge of the runlevel system."

is there anyway to edit it? 

also is there a way that my system is not dependent on updates over the internet and just update it manually if i want? so that whether connected online or offline my computer runs normally.

thanks any help are greatly appreciated. GODspeed![/QUOTE]
Please refer to my first thread. There is a tool I listed there for editing all runlevels. Its call sysv-rc-conf and you will need to be root to edit it.

---

### Post by mangocrazy on 2005-12-01
[QUOTE=dolson]You need to enable the Universe repositories. I'd recommend you do so via Synaptic's UI.[/QUOTE]

Thanks for the pointer, Dolson, I'll try it tonight or tomorrow. I had heard of the 'Universe' but wasn't aware of how to get to it, or that the tool I needed was to be found there. Thanks again.

Graham

---

### Post by MetalMusicAddict on 2005-12-01
[QUOTE=i3dmaster]bind9 - The DNS server. If you don't provide DNS name resolution, there is no need to  turn it on.
[/QUOTE]
So I would only need this if Im a server?

---

### Post by KermitJr on 2005-12-01
Mangocrazy,

If you select "Add new programs", click on Settings, Repositories.  Click on Advanced and "Show unused repositories" or something like that.  I enable all of the binary and disable the source usually.

---

### Post by i3dmaster on 2005-12-02
[QUOTE=MetalMusicAddict]So I would only need this if Im a server?[/QUOTE]
Yes, only if you provide a DNS service.

---

### Post by geearf on 2005-12-02
Thanks for this good howto, I'll reboot later to feel the difference :)

---

### Post by geearf on 2005-12-02
I had one problem with the hotplug : no sound and no network so I put it back, maybe later I'll do something like you I don't know.

Also, when I'm closing KDE / X like when shutting down, it stays a bit on a black screen before showing again the terminal.

Finally, when the computer is starting, after I see the alsa message, there is a little problem, the font thing is like written over the alsa message, and at the end I have like the beginning of the alsa message, some blank space, the end of the font message.

It's very strange, but it's way faster,

---

### Post by i3dmaster on 2005-12-04
[QUOTE=geearf]I had one problem with the hotplug : no sound and no network so I put it back, maybe later I'll do something like you I don't know.

Also, when I'm closing KDE / X like when shutting down, it stays a bit on a black screen before showing again the terminal.

Finally, when the computer is starting, after I see the alsa message, there is a little problem, the font thing is like written over the alsa message, and at the end I have like the beginning of the alsa message, some blank space, the end of the font message.

It's very strange, but it's way faster,[/QUOTE]
If you are using hotplug service to map the network devices (which is the default) then  network wouldn't start. The same, sound card is probed by hotplug subsystem. For network, you can take a look your /etc/network/interfaces file, comment out the hotplug mapping section and put whatever the device to the "auto" line. For your sound card, find out what module it uses and put it into /etc/modules file. btw, Dapper will drop hotplug and only use udev.

---

### Post by geearf on 2005-12-04
Hello,

well it's ok, it's already way faster, and maybe I'll need hotplug for a plug'n play thing later (like a mouse, camera, or else, maybe not )

---

### Post by metoo on 2005-12-04
Good job, nice summary of the meaning of all the services.

---

### Post by mangocrazy on 2005-12-07
KermitJr,

Thanks - I'm now "universe-aware" and my wife has a lot of new games to play on her machine... So that's alright.

In fact Ubuntu has effortlessly supplanted XP as my wife's choice of boot; there are more games and she can still surf/do email etc.

Result! :D 

Graham

---

### Post by pachequin on 2005-12-08
hi! everyone! I followed the instructions and the boot is faster but when I turn off my laptop asks me for the root passwd, do you know what service or what I did wrong?

Thank you so much!

---

### Post by petervk on 2005-12-09
[QUOTE=pachequin]hi! everyone! I followed the instructions and the boot is faster but when I turn off my laptop asks me for the root passwd, do you know what service or what I did wrong?[/QUOTE]

I am getting the exact same problem. Does anyone know a fix? 

Also, my laptop does not boot past the brown screen with a cusor (after login) unless I disconnect my network cable before booting. I think this has something to do with the "hotplug-networking" or "networking" service, but if I enable them, booting takes forever when I am not connected to a network. Any way to fix this?

---

### Post by zasf on 2005-12-09
[QUOTE=i3dmaster]If you are using hotplug service to map the network devices (which is the default) then  network wouldn't start. The same, sound card is probed by hotplug subsystem. For network, you can take a look your /etc/network/interfaces file, comment out the hotplug mapping section and put whatever the device to the "auto" line. For your sound card, find out what module it uses and put it into /etc/modules file. btw, Dapper will drop hotplug and only use udev.[/QUOTE]

I disabled hotplug and then sound and network wouldn't work any more. I normally deal with ifup/down, etc by myself, since the network GUI doesn't work (that is something i go proud since I'm a win user). Other than looking at /etc/network/interfaces and commenting hotplug out, is there a way to understand what fails with hotplug at startup?? It doesn't actually fails.. it takes a long time but no "fail" nor "ok" shows.

Thanks you for the nice howto

---

### Post by joergenlie on 2005-12-09
:confused: 
Allright, I think  I messed up here. My Lap turns off during boot. tried the things listed above but without sucsess. Is it possible to change the settings through the Live CD? If yes, how?
The only thing i can manage is to get into the grub command line. 

"I'm learning by doing it the hard way!"

Thanks!

Jørgen

---

### Post by i3dmaster on 2005-12-11
[QUOTE=zasf]I disabled hotplug and then sound and network wouldn't work any more. I normally deal with ifup/down, etc by myself, since the network GUI doesn't work (that is something i go proud since I'm a win user). Other than looking at /etc/network/interfaces and commenting hotplug out, is there a way to understand what fails with hotplug at startup?? It doesn't actually fails.. it takes a long time but no "fail" nor "ok" shows.

Thanks you for the nice howto[/QUOTE]
hotplug and hotplug-network are hotplug subsystems that used for enabling plug&play devices, such as pcmcia card, usb, 1394, sound card, etc. Its a pretty sophisticated system to explain, but in a short, hotplug will try to detect low level devices by using d-bus and udev message bus and load the necessary modules by scaning various module files. The udev will actually have the same type func as hotplug in the near future I think and that's why the hotplug will be replaced by udev... With these type of subsystems enabled, Linux is truly a plug&play OS. But, things always have two sides, the side effect of hotplug is known to be the slow loading during boot time. The way that I can think of to learn this subsystem is to look at the hotplug scripts.

---

### Post by i3dmaster on 2005-12-11
[QUOTE=petervk]I am getting the exact same problem. Does anyone know a fix? 

Also, my laptop does not boot past the brown screen with a cusor (after login) unless I disconnect my network cable before booting. I think this has something to do with the "hotplug-networking" or "networking" service, but if I enable them, booting takes forever when I am not connected to a network. Any way to fix this?[/QUOTE]
Hmm... I am not sure about this. If you have chance to take a screenshot of  your sysv-rc-conf output, I'd love to try.

---

### Post by i3dmaster on 2005-12-11
[QUOTE=joergenlie]:confused: 
Allright, I think  I messed up here. My Lap turns off during boot. tried the things listed above but without sucsess. Is it possible to change the settings through the Live CD? If yes, how?
The only thing i can manage is to get into the grub command line. 

"I'm learning by doing it the hard way!"

Thanks!

Jørgen[/QUOTE]
I think you've probably touched some services that I emphasized NOT to touch at all. Most likely would be the "halt" service since you said your laptop turned off when booting. If you use live CD, go there and mount your root file system and go to the /mount_point_of_rootfs/etc/rc*.d dirs and change the Sxxhalt to only exist under /etc/rc0.d, meaning delete all other Sxxhalt in other rc*.d dirs. Be careful when you do any changes.

---

### Post by joergenlie on 2005-12-12
Ok
How do I mount the root file system through the live cd? I get into root@ubuntu but the the only thing there is Desktop. 
Is there som advanced way to do this through the live cd?

J&#248;rgen

---

### Post by i3dmaster on 2005-12-12
[QUOTE=joergenlie]Ok
How do I mount the root file system through the live cd? I get into root@ubuntu but the the only thing there is Desktop. 
Is there som advanced way to do this through the live cd?

Jørgen[/QUOTE]
ok, you will need to open a terminal and do a ```
fdisk -l
```. In that list, you should see your local hard disk root filesystem. Then create a temp dir under /mnt and then mount the root filesystem underneath that temp dir.

---

### Post by Mr_J_ on 2005-12-12
I used this and I now can't get my network to boot at startup.
I don't mind it too much, except I have to remember to manually boot the network interface.
When i get home i will go over the things I turned off and post it around here.
If i'm not too mistakened I only turned things off like the howto. However i'm not too assured of it. I remember going over the things and starting them one by one booting and reebooting, and going over it over and over. Nothing worked and i gave up on it.

Only now to remember about it.

---

### Post by joergenlie on 2005-12-12
[QUOTE=i3dmaster]ok, you will need to open a terminal and do a ```
fdisk -l
```. In that list, you should see your local hard disk root filesystem. Then create a temp dir under /mnt and then mount the root filesystem underneath that temp dir.[/QUOTE]

Thanks alot man! som head scratching with the mount, but i got it at last!:D 


Jørgen

---

### Post by yaaarrrgg on 2005-12-12
also, here's a one line hack that worked good for me on breezy ... run startup scripts in parallel, merely by changing the startup script: /etc/init.d/rc

Changing the line:

```

startup $i start

```

to the following:

```

startup $i start &

```

from:
[http://www.debian-administration.org/articles/199](http://www.debian-administration.org/articles/199)
[http://www.hoeg.org/blog/2005/07/27/fast-booting-debian/](http://www.hoeg.org/blog/2005/07/27/fast-booting-debian/)

---

### Post by joergenlie on 2005-12-12
Quote:
Originally Posted by IdolizingStewie
I followed this How-To a couple days ago and, like an idiot, failed to note the specific changes I was making. I finally got around to rebooting today and when the computer starts back up it gives me an internal error "Failed to initialize HAL." Can anyone tell me which services I need for HAL and maybe what runlevels they need to be on? I suspect this is why I can no longer mount my external HDD which, while not vital, is extremely annoying since it has all my music.

Enable hotplug at runlevel S and try again.
  	
My hotplug runlevel is aat S, still I get "failed to initialize HAL" ?

Jørgen

---

### Post by i3dmaster on 2005-12-13
[QUOTE=Mr_J_]I used this and I now can't get my network to boot at startup.
I don't mind it too much, except I have to remember to manually boot the network interface.
When i get home i will go over the things I turned off and post it around here.
If i'm not too mistakened I only turned things off like the howto. However i'm not too assured of it. I remember going over the things and starting them one by one booting and reebooting, and going over it over and over. Nothing worked and i gave up on it.

Only now to remember about it.[/QUOTE]
If you laptop wouldn't bootup, then one way to fix it is just like the other guy here to use the liveCD. Please refer to the thread. Also, in order to learn a bit more not just fixing, a better place to look at what the hell was wrong is the system log. Go to /var/log dir and look at message, bootlog, dmesg, faillog, kern.log files, etc... for the timeline closest to the accident time and see if there is anything indicating what went wrong during the last boot.

---

### Post by i3dmaster on 2005-12-13
[QUOTE=joergenlie]Quote:
Originally Posted by IdolizingStewie
I followed this How-To a couple days ago and, like an idiot, failed to note the specific changes I was making. I finally got around to rebooting today and when the computer starts back up it gives me an internal error "Failed to initialize HAL." Can anyone tell me which services I need for HAL and maybe what runlevels they need to be on? I suspect this is why I can no longer mount my external HDD which, while not vital, is extremely annoying since it has all my music.

Enable hotplug at runlevel S and try again.
  	
My hotplug runlevel is aat S, still I get "failed to initialize HAL" ?

Jørgen[/QUOTE]
that's actually your dbus system. Check that out.

---

### Post by gilchris on 2005-12-14
I want to translate this HowTo into Korean.

already finished translation.

I want to upload this translated Howto on Korean Ubuntu users group([http://ubuntu.or.kr](http://ubuntu.or.kr)) if you don't mind this translation is uploaded.

---

### Post by sailor420 on 2005-12-15
[QUOTE=yaaarrrgg]also, here's a one line hack that worked good for me on breezy ... run startup scripts in parallel, merely by changing the startup script: /etc/init.d/rc

Changing the line:

```

startup $i start

```

to the following:

```

startup $i start &

```

from:
[http://www.debian-administration.org/articles/199](http://www.debian-administration.org/articles/199)
[http://www.hoeg.org/blog/2005/07/27/fast-booting-debian/](http://www.hoeg.org/blog/2005/07/27/fast-booting-debian/)[/QUOTE]


Nice. That knocked a few seconds off my boot time, beyond all the tweaking here. I don't think much anything else other than InitNG (which isn't working for me) is gonna get my boot time below 1 minute though--damn slow laptop hard drive.

---

### Post by i3dmaster on 2005-12-15
[QUOTE=sailor420]Nice. That knocked a few seconds off my boot time, beyond all the tweaking here. I don't think much anything else other than InitNG (which isn't working for me) is gonna get my boot time below 1 minute though--damn slow laptop hard drive.[/QUOTE]
That's acutally a pretty good point!

---

### Post by Sokraates on 2005-12-19
[QUOTE=yaaarrrgg]also, here's a one line hack that worked good for me on breezy ... run startup scripts in parallel, merely by changing the startup script: /etc/init.d/rc

Changing the line:

```

startup $i start

```

to the following:

```

startup $i start &

```

from:
[http://www.debian-administration.org/articles/199](http://www.debian-administration.org/articles/199)
[http://www.hoeg.org/blog/2005/07/27/fast-booting-debian/](http://www.hoeg.org/blog/2005/07/27/fast-booting-debian/)[/QUOTE]

Great idea. The only annoyance is, that CLI appears for about a second or two before KDM starts.

Not even a minor prob, simply cosmetics, but does anyone have an idea, how runlevels could be tweaked to avoid this?

---

### Post by ashrack on 2005-12-19
What was the original setting for "readahead"?

---

### Post by brainkilla on 2005-12-20
@i3dmaster
You, Sir, are a genius. Very good how-to. I used to use rcconf and recently I've discovered BUM, which does more or less the same but within a GUI. But I could not get rid of that damn raid sh*t starting and LVM and crap... this is a life saver, booting is now shorter for like 10 sec or more... thanx!

---

### Post by ashrack on 2005-12-21
[QUOTE=ashrack]What was the original setting for "readahead" deamon?[/QUOTE]
Ive disabled it. But now I would like to enable it again. But don't know on which INIT LEVEL

---

### Post by ShirishAg75 on 2005-12-21
Hi there,
          First of  all thanx to give such a guide. Would be reading the all the pages soon & if the questions that I've if not asked would ask. Couldn't just resist saying thank u. That's all. It's a pretty good tool. Much better than BUM, much more thorough or maybe I haven't checked out BUM quite enough. either way it's cool.

---

### Post by ShirishAg75 on 2005-12-21
Hi there,
           Got an  (Internal Error:Failed to initialize HAL) error. Here are my pics. Would try to first use the pictures themselves to see if I can see what I did wrong otherwise maybe u can point out.
[[IMG]http://img337.imageshack.us/img337/5424/screenshot4gk.th.png[/IMG]](http://img337.imageshack.us/my.php?image=screenshot4gk.png)
[[IMG]http://img276.imageshack.us/img276/3198/screenshot12wy.th.png[/IMG]](http://img276.imageshack.us/my.php?image=screenshot12wy.png)

        Another thing I have a realtek 8139c+ Fast Ethernet card which in turn is connected to a D-Link Modem. As a noob, had taken an advice of an knowledgable friend & did the following config:-

ifconfig eth0 192.168.1.2
route add default gw 192.168.1.1 - this is this web interface to tweak the settings of the router/modem.
 He also made couple of entries in /etc/resolv.conf 
      nameserver 61.1.96.69
      nameserver 61.1.96.71 - These are DNS servers of our ISP here
 looked at /etc/network/interfaces
     & then gave /etc/init.d/networking restart

---

### Post by ShirishAg75 on 2005-12-22
Hi there,
           Got the Internal Error: HAL failed to initialize. First of all can u clean the 1st post little bit more. At the end when u have put some more services, it has become harder to follow the list. Can u change the order so it follows the order as we see on the screen.
          Now for the services that I need to know/confirm more about :-

1. alsa - put them on at 2-5. Your recommendation was off
2. alsa-utils :- put them on S runlevel on.
3. **binfmt-support** :-  This is not there. Should it be or it's specific to one's machine.
4. dns-clean :- on at S runlevel. Do I need this? Refer to the entry above.
5. fetchmail :- Put if off. Do I need it as would be using Thunderbird later.
6. firestart$ :- It's a GUI interface to IPtables. A firewall basically.
7. **hdparm** :- In /etc/hdparm.conf had put the following line in the script.
                      hdparm -d1 -X69 -C1 -M192 -A1 -a64 -M16 /dev/hda after 
                  deselecting readahead remove -a64
8. hibernate :- How to know if the service is supported or not. Just run hibernate as 
                        ```
$:- hibenate
``` or something else.
9. hotplug & hotplug-net :- Both are on S runlevel on. I wanna have the ability to use a thumbdrive or digital camera whenever I want. Other than that no printer, no scanner so is this correct.
10. **linux-restricted-modules** :- This isn't listed. Although the kernel I'm running is in linux-restricted-modules  2.6.12.10-686. Should this one be listed.
11. module-in$ :- Looking at /etc/modules there it lists 
                             a. lp
                             b. mousedev
                             c. psmouse
                          I have a ps/2 mouse. So what should be done here. Right now its on runlevel S
12. mountvirt$ :- What is this & why it should be enabled. I didn't find any info. about this one. Have enabled it at Runlevel S
13. ppp & ppp-dns :-  Don't use dial-up as said before but still await u'r instruction on this one. Right now ppp is on from 2-5 while ppp-dns on runlevel S14.
14. rmlogin :- This one is for remote logins or what. have disabled it.No info til yet.
15. rsync :- Remote synchronization. Is this for when I do an apt-get update or for what? Although have disabled it but would like to know more.
16. ssh :- Secure shell. This AFAIK is used than telnet. I don't know much about telnet itself. So would like to know of some link or something which explains where this is used & then can make up my mind.
17. udev & udev-mtab :- Both are on at runlevel S
18. sysklogd :- I have 3 services by this name. syslogd, syslogd~ & syslog_b$. While syslogd is on from 2-5 the rest are off.
19.** x.org-common** :-  Put in on from 2-5. Saw domino putting at Runlevel S & u said fine to that. Could this be the problem?
        
           How do I checkout my dbus system?

              Thanx in advance.

---

### Post by i3dmaster on 2005-12-23
[QUOTE=ashrack]Ive disabled it. But now I would like to enable it again. But don't know on which INIT LEVEL[/QUOTE]
The default readahead is runlevel S.

---

### Post by i3dmaster on 2005-12-23
[QUOTE=shirishag75]Hi there,
           Got the Internal Error: HAL failed to initialize. First of all can u clean the 1st post little bit more. At the end when u have put some more services, it has become harder to follow the list. Can u change the order so it follows the order as we see on the screen.
          Now for the services that I need to know/confirm more about :-

1. alsa - put them on at 2-5. Your recommendation was off.  - [COLOR="SeaGreen"] See my note in the HowTo[/COLOR]
2. alsa-utils :- put them on S runlevel on. -[COLOR="SeaGreen"] See my note in the HowTo[/COLOR]
3. **binfmt-support** :-  This is not there. Should it be or it's specific to one's machine. - [COLOR="SeaGreen"]Its strange you don't have this service. You probably need to manually install it. The pkg is binfmt-support.[/COLOR]
4. dns-clean :- on at S runlevel. Do I need this? Refer to the entry above. - [COLOR="SeaGreen"] Yes if you use dial up, otherwise, you don't need it.[/COLOR]
5. fetchmail :- Put if off. Do I need it as would be using Thunderbird later. - [COLOR="SeaGreen"] Absolutely not. Nothing related with Thunderbird and fetchmail.[/COLOR]
6. firestart$ :- It's a GUI interface to IPtables. A firewall basically. - [COLOR="SeaGreen"] I don't have it. I'd rather use CLI[/COLOR]
7. **hdparm** :- In /etc/hdparm.conf had put the following line in the script.
                      hdparm -d1 -X69 -C1 -M192 -A1 -a64 -M16 /dev/hda after 
                  deselecting readahead remove -a64 - [COLOR="SeaGreen"]That's cool. I did this type of changes too[/COLOR]
8. hibernate :- How to know if the service is supported or not. Just run hibernate as 
                        ```
$:- hibenate
``` or something else. - [COLOR="SeaGreen"]Most likely depending on the hardware. I would assume that if your laptop supports acpi, then it should support hiernate. Anyway, /etc/hibernate has all the conf and module files that you can take a look.[/COLOR]
9. hotplug & hotplug-net :- Both are on S runlevel on. I wanna have the ability to use a thumbdrive or digital camera whenever I want. Other than that no printer, no scanner so is this correct. - [COLOR="SeaGreen"]Yes, that's the default runlevel[/COLOR]
10. **linux-restricted-modules** :- This isn't listed. Although the kernel I'm running is in linux-restricted-modules  2.6.12.10-686. Should this one be listed. - [COLOR="SeaGreen"] Another weird one. If you have restricted module installed, you should have it.[/COLOR]
11. module-in$ :- Looking at /etc/modules there it lists 
                             a. lp
                             b. mousedev
                             c. psmouse
                          I have a ps/2 mouse. So what should be done here. Right now its on runlevel S -  [COLOR="SeaGreen"]Almost nothing. Leave as it is. BTW, if you want to load any modules during boot time, you may add here.[/COLOR]
12. mountvirt$ :- What is this & why it should be enabled. I didn't find any info. about this one. Have enabled it at Runlevel S - [COLOR="SeaGreen"]Its important. Leave it on. It will mount all virtual fs's, such as sysfs, usbfs, shm, proc, pts, etc... Look at your df and you will see them.[/COLOR]
13. ppp & ppp-dns :-  Don't use dial-up as said before but still await u'r instruction on this one. Right now ppp is on from 2-5 while ppp-dns on runlevel S14. - [COLOR="SeaGreen"]Then turn them off. They are services to sync the network settings when dialing up or hanging up.[/COLOR]
14. rmlogin :- This one is for remote logins or what. have disabled it.No info til yet. -  [COLOR="SeaGreen"]Yes, if there is a /etc/nologin file in your box, then nobody other than root can get in. This will make sure there isn't such file existing. [/COLOR]
15. rsync :- Remote synchronization. Is this for when I do an apt-get update or for what? Although have disabled it but would like to know more. - [COLOR="SeaGreen"]No, nothing to do with apt. Mainly for sync b/w servers. Quite useful but not for clients.[/COLOR]
16. ssh :- Secure shell. This AFAIK is used than telnet. I don't know much about telnet itself. So would like to know of some link or something which explains where this is used & then can make up my mind. -  [COLOR="SeaGreen"]In nowadays Linux, ssh will supercede all telnet services. They all provides remote login ability, but ssh is much much secure than telnet. [/COLOR]
17. udev & udev-mtab :- Both are on at runlevel S - [COLOR="SeaGreen"]Fine.[/COLOR]
18. sysklogd :- I have 3 services by this name. syslogd, syslogd~ & syslog_b$. While syslogd is on from 2-5 the rest are off.  [COLOR="SeaGreen"]Fine and you should be able to delete syslogd~ safely since that's just a backup file.[/COLOR]
19.** x.org-common** :-  Put in on from 2-5. Saw domino putting at Runlevel S & u said fine to that. Could this be the problem? -  [COLOR="SeaGreen"]No, either way is ok.[/COLOR] 
        
           How do I checkout my dbus system?  - [COLOR="SeaGreen"]See my note[/COLOR]

              Thanx in advance.[/QUOTE]
Thanks. HowTo has been updated. Some of the services were from the others which means my own box doesn't have them, so I am not sure the default runlevel on them. If someone can tell me, I would like to get them updated. For all of those that having HAL failure problem, try this:
1. change acpi-support from S to 2,3,4,5
2. change acpid from S to 2,3,4,5
3. change dbus from S to 2,3,4,5
4. Reboot. Go to the console and do ```
ps -aef|grep hald
```. If hald service is up, then your dbus subsystem is running fine now. Try it.

---

### Post by AjaxDaKid on 2005-12-23
I tried to install and i get an error--
pbrown@plinux:~$ sudo apt-get install sysv-rc-conf
Reading package lists... Done
Building dependency tree... Done
Package sysv-rc-conf is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sysv-rc-conf has no installation candidate

Do you know why?

---

### Post by i3dmaster on 2005-12-23
[QUOTE=AjaxDaKid]I tried to install and i get an error--
pbrown@plinux:~$ sudo apt-get install sysv-rc-conf
Reading package lists... Done
Building dependency tree... Done
Package sysv-rc-conf is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sysv-rc-conf has no installation candidate

Do you know why?[/QUOTE]
You will need to enable your universe and multiverse repos.

---

### Post by ShirishAg75 on 2005-12-23
[quote=i3dmaster]Thanks. HowTo has been updated. Some of the services were from the others which means my own box doesn't have them, so I am not sure the default runlevel on them. If someone can tell me, I would like to get them updated. For all of those that having HAL failure problem, try this:
1. change acpi-support from S to 2,3,4,5
2. change acpid from S to 2,3,4,5
3. change dbus from S to 2,3,4,5
4. Reboot. Go to the console and do ```
ps -aef|grep hald
```. If hald service is up, then your dbus subsystem is running fine now. Try it.[/quote] 
 Thanx for the note. Was able to clear up the mess. Also understood small bit about ps. Here's the output from :-
ps -aef|grep hald
hal       6514     1  0 01:04 ?        00:00:00 /usr/sbin/hald
hal       6519  6514  0 01:04 ?        00:00:00 hald-addon-acpi
hal       6527  6514  0 01:04 ?        00:00:02 hald-addon-storage
1000      7812  7705  0 03:49 pts/1    00:00:00 grep hald

 Seems to be o.k. I guess. Slightly OT which I'll scrub later but do u/anybody know/s how to show the thumbnails in the same side. I saw in the forum somewhere people able to conserve space by putting thumbnails next to each other.

---

### Post by domino on 2005-12-23
Thanks for adding the default values. This will be handy on my future installs. I'll make I post defaults on my desktop after I wipe the entire drive and re-install.

---

### Post by i3dmaster on 2005-12-23
[QUOTE=shirishag75]Thanx for the note. Was able to clear up the mess. Also understood small bit about ps. Here's the output from :-
ps -aef|grep hald
hal       6514     1  0 01:04 ?        00:00:00 /usr/sbin/hald
hal       6519  6514  0 01:04 ?        00:00:00 hald-addon-acpi
hal       6527  6514  0 01:04 ?        00:00:02 hald-addon-storage
1000      7812  7705  0 03:49 pts/1    00:00:00 grep hald

 Seems to be o.k. I guess. Slightly OT which I'll scrub later but do u/anybody know/s how to show the thumbnails in the same side. I saw in the forum somewhere people able to conserve space by putting thumbnails next to each other.[/QUOTE]
Cool. Glad it worked out for ya. But for the thumbnail thing, sorry I don't know.

---

### Post by i3dmaster on 2005-12-23
[QUOTE=domino]Thanks for adding the default values. This will be handy on my future installs. I'll make I post defaults on my desktop after I wipe the entire drive and re-install.[/QUOTE]
np. Good luck man.

---

### Post by John.Michael.Kane on 2005-12-24
sudo mv Kxx to kxx did not seem to change the capatol K to lowercase.. any idea's why..

---

### Post by ShirishAg75 on 2005-12-24
That's weird because it did on mine atleast.  My query is different though. These processes are there on the startup script but have no entry in the shutdown /etc/rc.0d or /etc/rc6.d

1. dns-clean
2. lm-sensors
3. ntpdate
4. ppp-dns
5. rmlogin
6. syslogd~

[quote=idmaster]18. sysklogd :- I have 3 services by this name. syslogd, syslogd~ & syslog_b$. While syslogd is on from 2-5 the rest are off. [COLOR=SeaGreen]Fine and you should be able to delete syslogd~ safely since that's just a backup file. [/COLOR][/quote]
                What is this backup file & what does it do? Till when does it backup & what do the other 2 similar services do. I know that's not the scope of the Howto but if u can :)

---

### Post by ShirishAg75 on 2005-12-25
The issue being was looking at /var/log/syslog.0 & the last entry there was of 22nd December. Nothing after that. Any ideas how to generate the logs again?

---

### Post by Brando569 on 2005-12-28
i have the same audio problem that everyone else has, but its wierder. i disabled hotplug and hotplug-net and set up eth0 to work w/o hotplug-net and the internet works fine, when i rebooted the sound didnt work. so i was just gonna replace hotplug and i thought everything was gonna be fine, but somehow hotplug misteriously disappeared. i didnt worry about it and used my dads pc which i also installed kubuntu on, and used that for a day or two. i think i installed something from synaptic and restarted linux, when i got back into kde the sound worked, which i thought was odd cuz i didnt do anything. so i installed 2 new kernels (2.6.14 from vanilla sources and 2.6.12-smp) and went into the 2.6.14 and the sound didnt work! tried it in the smp one, same thing. went back into my normal kernel, same thing. the wierd thing is in atleast one of the kernels it gives me an ALSA error or something that it cant find the soundcard (its integrated into my mobo [ac97] ) and on the other two usplash says "starting the hotplug subsystem" and loads it then it says "ALSA card0  ok  ALSA card1   ok" then it says something about the network interface which i thought was wierd cuz i didnt enable hotplug again :confused: the best tool ive seen sofar for messing with the boot scripts is a program i found on kde-apps.org it was called debian services control panel or something liek that, and it allowed u to start/stop services and either add them or delete them from running at bootup. (im guessing it removed the links, i think thats what it did) but i cant find the .deb or anything on the site anymore and i have it saved on my hdd but it wont work :(

---

### Post by i3dmaster on 2005-12-30
[QUOTE=SD-Plissken]sudo mv Kxx to kxx did not seem to change the capatol K to lowercase.. any idea's why..[/QUOTE]
Not sure but it should. Try to specify the whole file name and see how it goes.

---

### Post by i3dmaster on 2005-12-30
[QUOTE=shirishag75]That's weird because it did on mine atleast.  My query is different though. These processes are there on the startup script but have no entry in the shutdown /etc/rc.0d or /etc/rc6.d

1. dns-clean
2. lm-sensors
3. ntpdate
4. ppp-dns
5. rmlogin
6. syslogd~


                What is this backup file & what does it do? Till when does it backup & what do the other 2 similar services do. I know that's not the scope of the Howto but if u can :)[/QUOTE]
Those are just running once when bootup. They don't need shutdown. As of syslogd~, sometimes it will be created when you are editing that file or the file has been updated. Do a ```
diff -burN syslogd syslogd~
``` and also ```
ls -latr
``` on those two files and see what's the differences and access time on them. The syslogd~ would probably be older than syslogd which can just be del'ed.

---

### Post by i3dmaster on 2005-12-30
[QUOTE=shirishag75]The issue being was looking at /var/log/syslog.0 & the last entry there was of 22nd December. Nothing after that. Any ideas how to generate the logs again?[/QUOTE]
The current is always named syslog not syslog.0. That is the last saved file since the syslog files are log rotated.

---

### Post by i3dmaster on 2005-12-30
[QUOTE=Brando569]i have the same audio problem that everyone else has, but its wierder. i disabled hotplug and hotplug-net and set up eth0 to work w/o hotplug-net and the internet works fine, when i rebooted the sound didnt work. so i was just gonna replace hotplug and i thought everything was gonna be fine, but somehow hotplug misteriously disappeared. i didnt worry about it and used my dads pc which i also installed kubuntu on, and used that for a day or two. i think i installed something from synaptic and restarted linux, when i got back into kde the sound worked, which i thought was odd cuz i didnt do anything. so i installed 2 new kernels (2.6.14 from vanilla sources and 2.6.12-smp) and went into the 2.6.14 and the sound didnt work! tried it in the smp one, same thing. went back into my normal kernel, same thing. the wierd thing is in atleast one of the kernels it gives me an ALSA error or something that it cant find the soundcard (its integrated into my mobo [ac97] ) and on the other two usplash says "starting the hotplug subsystem" and loads it then it says "ALSA card0  ok  ALSA card1   ok" then it says something about the network interface which i thought was wierd cuz i didnt enable hotplug again :confused: the best tool ive seen sofar for messing with the boot scripts is a program i found on kde-apps.org it was called debian services control panel or something liek that, and it allowed u to start/stop services and either add them or delete them from running at bootup. (im guessing it removed the links, i think thats what it did) but i cant find the .deb or anything on the site anymore and i have it saved on my hdd but it wont work :([/QUOTE]

A little messy here. After bootup to the system, do this and post it out:
```
 lsmod |grep -iE '(snd|ac97|pcm|oss|codec)'
```
See if there are any sound modules loaded at runtime.

---

### Post by Brando569 on 2005-12-30
I fixed the sound problem lastnight by reinstalling kubuntu cuz i got tired of not having sound :D

this is the output i get:

```

snd_usb_audio          76032  1
snd_usb_lib            16160  1 snd_usb_audio
snd_rawmidi            25952  1 snd_usb_lib
snd_seq_device          8716  1 snd_rawmidi
snd_hwdep               9248  1 snd_usb_audio
snd_intel8x0           34240  3
snd_ac97_codec         84508  1 snd_intel8x0
snd_pcm_oss            53760  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                92900  5 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25956  2 snd_pcm
snd                    57764  16 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10176  1 snd
snd_page_alloc         10824  2 snd_intel8x0,snd_pcm
usbcore               121308  7 snd_usb_audio,snd_usb_lib,pwc,usbhid,ehci_hcd,uhci_hcd

```

now what would i do to have these loaded at bootup w/o running hotplug? would i add them into modules.conf?

---

### Post by Sokraates on 2006-01-01
I just did a fresh install of Ubuntu Breezy on the new laptop of mine and some inits had different default-runlevels than written in the how-to.

dirmngr = 2-5
networking = 0, 6, S
pcimcia = 2-5
portmap = 2-5, 0, 6, S
readahead = S
screen-cleanup = S
usplash = 2-5
x-org-common = S

Happy New Year! :D

---

### Post by domino on 2006-01-01
As promised. Virgin Breezy PC install.

**Page 1:**

[[IMG]http://img485.imageshack.us/img485/9814/14ub.th.png[/IMG]](http://img485.imageshack.us/my.php?image=14ub.png)

**Page 2:**

[[IMG]http://img485.imageshack.us/img485/4586/25cr.th.png[/IMG]](http://img485.imageshack.us/my.php?image=25cr.png)

---

### Post by ashrack on 2006-01-01
tanx DOMINO,this should be verY usefull.
Perhaps the topic starter could add your 2picture to the original post so other ppl visiting this thread would know the original settings if something went fubar

---

### Post by Sokraates on 2006-01-01
Thx, domino.

Better than typing everything. ;)

---

### Post by dcstar on 2006-01-02
There is also a graphical boot up tool in the repositories called "bum" (Boot Up Manager).

Worth a look if you want to view/alter these things.

---

### Post by veloct on 2006-01-02
[QUOTE=dcstar]There is also a graphical boot up tool in the repositories called "bum" (Boot Up Manager).

Worth a look if you want to view/alter these things.[/QUOTE]

BUM is great but sysv-rc-conf is more flexible.

---

### Post by i3dmaster on 2006-01-02
[QUOTE=Brando569]I fixed the sound problem lastnight by reinstalling kubuntu cuz i got tired of not having sound :D

this is the output i get:

```

snd_usb_audio          76032  1
snd_usb_lib            16160  1 snd_usb_audio
snd_rawmidi            25952  1 snd_usb_lib
snd_seq_device          8716  1 snd_rawmidi
snd_hwdep               9248  1 snd_usb_audio
snd_intel8x0           34240  3
snd_ac97_codec         84508  1 snd_intel8x0
snd_pcm_oss            53760  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                92900  5 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25956  2 snd_pcm
snd                    57764  16 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10176  1 snd
snd_page_alloc         10824  2 snd_intel8x0,snd_pcm
usbcore               121308  7 snd_usb_audio,snd_usb_lib,pwc,usbhid,ehci_hcd,uhci_hcd

```

now what would i do to have these loaded at bootup w/o running hotplug? would i add them into modules.conf?[/QUOTE]
add snd_usb_audio and snd_intel8x0 into modules.conf file.

---

### Post by Brando569 on 2006-01-03
cool thanks

---

### Post by Brando569 on 2006-01-03
[QUOTE=dcstar]There is also a graphical boot up tool in the repositories called "bum" (Boot Up Manager).

Worth a look if you want to view/alter these things.[/QUOTE]

it looks great but its essentially pointless. it wont even let you do what the name says. the program doesnt allow you to edit ANY startup or shutdown scripts :mad:

---

### Post by ashrack on 2006-01-04
I 2 checked BUM about a week ago and it is nice and GUIish, but it doesn't allow any of the advance functions. Making it quite pointless for lesser n00bs

---

### Post by i3dmaster on 2006-01-04
[QUOTE=domino]As promised. Virgin Breezy PC install.

**Page 1:**

[[IMG]http://img485.imageshack.us/img485/9814/14ub.th.png[/IMG]](http://img485.imageshack.us/my.php?image=14ub.png)

**Page 2:**

[[IMG]http://img485.imageshack.us/img485/4586/25cr.th.png[/IMG]](http://img485.imageshack.us/my.php?image=25cr.png)[/QUOTE]
Thanks Domino! I will get your pics posted on the HowTo.

---

### Post by Brando569 on 2006-01-04
[QUOTE=ashrack]I 2 checked BUM about a week ago and it is nice and GUIish, but it doesn't allow any of the advance functions. Making it quite pointless for lesser n00bs[/QUOTE]

its quite pointless for anyone, i know how to use sysrc-conf to configure the services but its alot easier and quicker to do it with a GUI frontend...

---

### Post by Brando569 on 2006-01-05
[QUOTE=i3dmaster]add snd_usb_audio and snd_intel8x0 into modules.conf file.[/QUOTE]

just tried it, that didnt work :(

---

### Post by mrchadman on 2006-01-05
The apt-get doesn't work:

"Package sysv-rc-conf is not available, but is referred to by another package.
 This may mean that the package is missing, has been obsoleted, or
 is only available from another source
 E: Package sysv-rc-conf has no installation candidate"

Any help?

Thanks

---

### Post by skattman on 2006-01-05
It sounds like you may only be using the cdrom as your repository.  Check your list of repositories and see if this is the case.  If so, you'll need to add the ubuntu repositories as well.

---

### Post by i3dmaster on 2006-01-05
[QUOTE=mrchadman]The apt-get doesn't work:

"Package sysv-rc-conf is not available, but is referred to by another package.
 This may mean that the package is missing, has been obsoleted, or
 is only available from another source
 E: Package sysv-rc-conf has no installation candidate"

Any help?

Thanks[/QUOTE]
1. make sure you enable universe and multiverse repos in your sources.list file.
2. do a ```
apt-get update && apt-cache search sysv-rc-conf
```

---

### Post by i3dmaster on 2006-01-05
[QUOTE=Brando569]just tried it, that didnt work :([/QUOTE]
```

snd_usb_audio          76032  1
snd_usb_lib            16160  1 snd_usb_audio
snd_rawmidi            25952  1 snd_usb_lib
snd_seq_device          8716  1 snd_rawmidi
snd_hwdep               9248  1 snd_usb_audio
snd_intel8x0           34240  3
snd_ac97_codec         84508  1 snd_intel8x0
snd_pcm_oss            53760  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                92900  5 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25956  2 snd_pcm
snd                    57764  16 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10176  1 snd
snd_page_alloc         10824  2 snd_intel8x0,snd_pcm
usbcore               121308  7 snd_usb_audio,snd_usb_lib,pwc,usbhid,ehci_hcd,uhci_hcd

```
This is the lsmod output you posted before. It shows the relationship b/w these modules. We can do some tests here according to this.
1. After you bootup your system, su/sudo to root, then open a term and enter
```
modprobe snd_usb_audio
```. Then do a ```
lsmod |grep snd
``` to see how many snd related modules have been loaded. 
2. Then load snd_intel8x0 by ```
modprobe snd_intel8x0
```, after that, do a lsmod again to see how many snd modules have been loaded. 
3. Load another module that does not require dependent module(s), which means there is no module name(s) listed at the right hand side and do lsmod again to see how many snd related modules have been loaded. 
4. Do the above until you see full list of snd modules have loaded like the above list, then write the modules name that you manually loaded to the /etc/modules.conf file and reboot the box.
Let me know how it goes...

---

### Post by Brando569 on 2006-01-05
what was wierd after i posted that the sound did work even though i got the error box when i logged into kubuntu that said that it couldnt load the driver or whatever it says... odd...

---

### Post by i3dmaster on 2006-01-05
[QUOTE=Brando569]what was wierd after i posted that the sound did work even though i got the error box when i logged into kubuntu that said that it couldnt load the driver or whatever it says... odd...[/QUOTE]
Ah, ok. You might want to search the logs...

---

### Post by Brando569 on 2006-01-06
what logs specifically? also is there anyway to enable boot logging? it could be helpful at times...

---

### Post by i3dmaster on 2006-01-07
[QUOTE=Brando569]what logs specifically? also is there anyway to enable boot logging? it could be helpful at times...[/QUOTE]
/var/log/messages and /var/log/dmesg. messages takes all syslogd logs and dmesg is the one from bootlogd which logs all bootup messages.

---

### Post by Brando569 on 2006-01-08
as far as i can see there arent any errors, although when i did open up amarok and tried to play a song (which worked a few days ago with the same problem) it said at the bottom [GStreamer] ALSA device "default" not found but im using totem now to play music, amarok pisses me off sometimes now ever since ive upgraded from 0.3.5 or whatever it was, seems like since theyve switched from aRTs to GStreamer theres been ALOT more problems playing music. :mad:

---

### Post by optotron on 2006-01-14
what a nice guide!

---

### Post by Sokraates on 2006-01-14
Does anyone know, how to get rid of an entry in SysV after uninstalling an app?

I had upower with Hoary. Now its gone and the entries are set not to load aver, but they're still there. 

Here are some new entries for the list:

**autofs** = default are 2, 3, 4, 5.
Don't know how I got it nor why I need it but I don't dare turning it off, lest I break something. The Automounter HowTo didn't help to enlighten me.
**cnewsclean** = default ???
As far as I remember it has something to do with newsgroups. Turned it off.
**festival** = default ???
No idea. Turned it off.
 **lisa** = default are 2, 3, 4, 5.
A LAN browsing utility package. Part of KDE. Needs samba.
**rc~** = default ???
No idea. Turned it off.

---

### Post by encompass on 2006-01-16
I wanted to say thanks... You have created a wonderful, and informative howto.  I give you a 10 out of 10 in my book.:D

---

### Post by hk_2999 on 2006-01-17
Maybe they should try tweaking the boot process for speed automatically after installation in Dapper.

XP boots faster than my ubuntu and that's not good.

And maybe they should also include a program in the preferences to tweak the boot process manually.

---

### Post by dcstar on 2006-01-17
[QUOTE=Brando569]it looks great but its essentially pointless. it wont even let you do what the name says. the program doesnt allow you to edit ANY startup or shutdown scripts :mad:[/QUOTE]
The old version in the repositories isn't that useful, but the version 2.1.4 available from the developer site does have advanced features and looks quite handy:

[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by firehead on 2006-01-17
[QUOTE=Sokraates]
**festival** = default ???
No idea. Turned it off.
[/QUOTE]
afaik festival is a tool to read out text, so it should be save to turn it off - but i 'm not sure wether there are other "festivals" to start at bootup...

---

### Post by dcstar on 2006-01-17
And if you want to speed up the boot process even further - as well as speed up any general filesystem use - have a look at this HOWTO:

[http://ubuntuforums.org/showthread.php?t=107856](http://ubuntuforums.org/showthread.php?t=107856)

Just adding the "noatime" option to your /etc/fstab mount entries seems to make a difference to disk I/O (by not updating inode access time for each access), without compromising data integrity at all (and let's face it, how many of us use - or need - the "Last Accessed" attribute on files?).

Someone may want to do some some quantitative boot time comparisons with this enabled, but it seems faster on my system....

---

### Post by Brando569 on 2006-01-17
[QUOTE=dcstar]The old version in the repositories isn't that useful, but the version 2.1.4 available from the developer site does have advanced features and looks quite handy:

[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)[/QUOTE]

i tried the new version too, same thing i had a convo with the author on here if u want further info read here: 
[http://ubuntuforums.org/showthread.php?t=82783&page=2](http://ubuntuforums.org/showthread.php?t=82783&page=2)

read from post 54 to 60 he gives his explanation on why he doesnt allow editing the boot up scripts, even though he explained it, i think its a stupid reason...

---

### Post by dcstar on 2006-01-17
[QUOTE=Brando569]what logs specifically? also is there anyway to enable boot logging? it could be helpful at times...[/QUOTE]
Edit /etc/default/bootlogd

BOOTLOGD_ENABLE=Yes

---

### Post by dcstar on 2006-01-17
[QUOTE=Brando569]i tried the new version too, same thing i had a convo with the author on here if u want further info read here: 
[http://ubuntuforums.org/showthread.php?t=82783&page=2](http://ubuntuforums.org/showthread.php?t=82783&page=2)

read from post 54 to 60 he gives his explanation on why he doesnt allow editing the boot up scripts, even though he explained it, i think its a stupid reason...[/QUOTE]
Well, it says he doesn't allow GUI editing of the rcS.d services (which are the Single User mode services), he still allows editing of all the other run level scripts.

---

### Post by shade11 on 2006-01-20
Great guide. Made my startup go *alot* faster.

---

### Post by rippon on 2006-01-21
Very good work here.

I would like to note that by disabling Hotplug, and Hotplug Net, my wireless and sound were lost. The first time I took off (nearly) everything that you listed, and the boot time was 46 Seconds on my AMD Athlon 3000 (2GHz 64bit) with 7200 SATA drive and 1GB RAM.

Sadly, being forced to re-enable the two hotplug systems, my boot time went up to 56 Seconds. Thats eight seconds more! I would recomend that everyone turn it off if they don't know that they need it. If it turns out they do need it then they can turn it back on.

-Dan Rippon

---

### Post by engla on 2006-01-23
Just another thanks, this was great.

I've heard about Initng too, but I'm not sure I'm brave enough to try it -- I can't get it from the reps for my ppc and I don't want to mess with the kernel too much.

Is this hint orthogonal to using initng, or can you use both at once to get a super-duper-powered start?

---

### Post by i3dmaster on 2006-01-23
[QUOTE=dcstar]And if you want to speed up the boot process even further - as well as speed up any general filesystem use - have a look at this HOWTO:

[http://ubuntuforums.org/showthread.php?t=107856](http://ubuntuforums.org/showthread.php?t=107856)

Just adding the "noatime" option to your /etc/fstab mount entries seems to make a difference to disk I/O (by not updating inode access time for each access), without compromising data integrity at all (and let's face it, how many of us use - or need - the "Last Accessed" attribute on files?).

Someone may want to do some some quantitative boot time comparisons with this enabled, but it seems faster on my system....[/QUOTE]
Interesting, thanks for sharing. I am going to give it a try.

---

### Post by i3dmaster on 2006-01-23
[QUOTE=rippon]Very good work here.

I would like to note that by disabling Hotplug, and Hotplug Net, my wireless and sound were lost. The first time I took off (nearly) everything that you listed, and the boot time was 46 Seconds on my AMD Athlon 3000 (2GHz 64bit) with 7200 SATA drive and 1GB RAM.

Sadly, being forced to re-enable the two hotplug systems, my boot time went up to 56 Seconds. Thats eight seconds more! I would recomend that everyone turn it off if they don't know that they need it. If it turns out they do need it then they can turn it back on.

-Dan Rippon[/QUOTE]
Yes, hotplug subsystem takes quite amount of time to enable but don't worry, we will say bye-bye to it when dapper comes.

---

### Post by i3dmaster on 2006-01-24
[QUOTE=engla]Just another thanks, this was great.

I've heard about Initng too, but I'm not sure I'm brave enough to try it -- I can't get it from the reps for my ppc and I don't want to mess with the kernel too much.

Is this hint orthogonal to using initng, or can you use both at once to get a super-duper-powered start?[/QUOTE]
I believe initng is using another different concept of managing the bootup tasks, so they might not take any advantage from each other. btw, I couldn't get initng working but I am quite familiar with the current sysv rc structures, so that's why I had this howto as a record of what I did and share with everyone here...

---

### Post by Brando569 on 2006-01-26
[QUOTE=dcstar]Edit /etc/default/bootlogd

BOOTLOGD_ENABLE=Yes[/QUOTE]

i enabled it but when i boot up it says loading bootlog        failed.

ive seen other people have had this problem but none of them have a solution for it...

---

### Post by dcstar on 2006-01-26
[QUOTE=Brando569]i enabled it but when i boot up it says loading bootlog        failed.

ive seen other people have had this problem but none of them have a solution for it...[/QUOTE]
It's not really a "problem", it is a known bug in the bootlogd code that incorrectly returns that error even though it is working.

Apparently will be fixed in the next version, but too trivial to bother fixing now.

---

### Post by agapito on 2006-01-28
> 66. lm-sensors - If you matherboard has builtin some sensor chips, it might be helpful to see hw status via userspace. I ran it and it said "No sensors found", so I turned it off.

I haven't read the all the posts so I don't know if this has been said allready, but did you run *sensors-detect*? I belive you have to do that to get the sensors working...

---

### Post by i3dmaster on 2006-01-28
[QUOTE=agapito]I haven't read the all the posts so I don't know if this has been said allready, but did you run *sensors-detect*? I belive you have to do that to get the sensors working...[/QUOTE]
Ya, I ran that before, but it still said no sensors found... well no big deal, my laptop is quite old..
```

root@ubuntumoblie:~# sensors-detect
No i2c device files found. Use prog/mkdev/mkdev.sh to create them.
root@ubuntumoblie:~# sensors
No sensors found!

```

---

### Post by egodust on 2006-01-31
Like many, stopping the hotplug service stopped detection of my sound card plus network, which I easily fixed (loaded the right modules and made eth0 auto to get DHCP)

However, something I didn't notice! it also disabled AGP and DRI acceleration (Who checks Xorg logs anyway?) that's cos it also stopped inserting intel_agp which the drm+'card' modules need.

whoops :T

So if you see dmesg output something about drm and locks, then lack of hotplug has messed up acceleration and you need to fix that too.

---

### Post by i3dmaster on 2006-01-31
[QUOTE=egodust]Like many, stopping the hotplug service stopped detection of my sound card plus network, which I easily fixed (loaded the right modules and made eth0 auto to get DHCP)

However, something I didn't notice! it also disabled AGP and DRI acceleration (Who checks Xorg logs anyway?) that's cos it also stopped inserting intel_agp which the drm+'card' modules need.

whoops :T

So if you see dmesg output something about drm and locks, then lack of hotplug has messed up acceleration and you need to fix that too.[/QUOTE]
Thanks for checking that out! I would assume adding the necessary modules to /etc/modules file would temporary solve the problem. When we go to dapper, all these hotplug problems will be gone.

---

### Post by Sokraates on 2006-02-03
How do I remove an entry from systemstartup, when the corresponding app is removed?

E.g. I've disabled lisa and later purged it from my system.

Running 
```
sudo sysv-rc-conf
```
the entry for lisa is still present, though deactivated (no runlevels selected).

---

### Post by i3dmaster on 2006-02-03
[QUOTE=Sokraates]How do I remove an entry from systemstartup, when the corresponding app is removed?

E.g. I've disabled lisa and later purged it from my system.

Running 
```
sudo sysv-rc-conf
```
the entry for lisa is still present, though deactivated (no runlevels selected).[/QUOTE]
Look at /etc/rcX.d where X is 1,2,3,4,5,6,0 and S and find out where *lisa* link is located and delete it. Go to /etc/init.d dir, look at lisa script and delete it.

---

### Post by pedrotuga on 2006-02-10
does sysv run in text mode or does it need X?

I can only access my server through ssh... no physical access

---

### Post by dcstar on 2006-02-10
[QUOTE=pedrotuga]does sysv run in text mode or does it need X?

I can only access my server through ssh... no physical access[/QUOTE]
It is a text app.

---

### Post by i3dmaster on 2006-02-11
yep, as long as you can get a console, it'll work for ya.

---

### Post by R3linquish3r on 2006-02-28
Hey, it worked great for me but I jsut have one question....

Do you know which one I need to turn back on so I can have a desktop background instead of this ugly blue one? I turned off everything that I deemed not necessary and rebooted and my background was gone! I read carefully through everything, but I don't really see which one it is? I was thinking it could have been GDM but I use KDM anyway so I don't see why disabling GDM would effect my desktop. Any ideas?

PS- I think I shaved near 10 seconds on my  AMD 3200+, 2BG RAM :D

---

### Post by R3linquish3r on 2006-02-28
Ignore that post. I figured it out in the desktop settings :P For some reason it changed it all I had to do was change it back lol.

---

### Post by bluevoodoo1 on 2006-03-10
This is great! Thank you very much! 
I have a quick question. There is a service that loads and says "reading desktop files" or something similiar to that. Do you happen to know what service that is and if so, is it entirely necessary?? Thank you again! Boot time has significantly changed for the better!

---

### Post by i3dmaster on 2006-03-11
[QUOTE=R3linquish3r]Ignore that post. I figured it out in the desktop settings :P For some reason it changed it all I had to do was change it back lol.[/QUOTE]
Ya cool. I was gonna say it shouldn't have anything to do with bootup process...

---

### Post by i3dmaster on 2006-03-11
[QUOTE=bluevoodoo1]This is great! Thank you very much! 
I have a quick question. There is a service that loads and says "reading desktop files" or something similiar to that. Do you happen to know what service that is and if so, is it entirely necessary?? Thank you again! Boot time has significantly changed for the better![/QUOTE]
Im not familiar with this service, but its probably from the readahead service. You can view the readahead startup script from /etc/init.d/ dir and find out the detail.

---

### Post by bluevoodoo1 on 2006-03-11
[QUOTE=i3dmaster]Im not familiar with this service, but its probably from the readahead service. You can view the readahead startup script from /etc/init.d/ dir and find out the detail.[/QUOTE]

Ok, great. I will check that out.

---

### Post by stanz on 2006-03-15
Hi All,
Thanks for this howto info!
I've noticed some problems, on my end tho, i need more time to cruize around- but, right off...rythembox,xine &totem... when called- they kinda pop up a sec, then close. rythembox will stay up & i can load a auto play list- but none will play.
i noticed everything's 'sleeping', as i checked out my system monitor- looking for some kind of clue- but- i'm too new at this.
when i clicked in the panal, for the system monitor- it took some time to load in... my circling curser had left- so i thought it was broke too- but it popped open...45sec later- or so.
Aside from no 'usplash', bootup was better.
I'll wait till morning.. when my eyes work better & i can get used to this 'new forum look'.

---

### Post by stanz on 2006-03-15
Hi All...
Thought I should add: I'm Desktop...i386.
I've checked in: 'sys', 'prefs', 'sound', and find a blank- for default sound card.
I've added the 'auto' for eth0- which i guess is kewl-cause i'm online-no prob! I think ya mentioned doing the same for Scard? 
Post mentions placing 'modules' someplace- but- i'm clueless there...I'ld ask for post referance or some kind of help with that.
What I've added in session startup- works fine. I've lost usplash, and like to have it back...
Well, it's all good...Thanks again !
---------------------
I've tried to attach my etc/modules, and more info~ but this function isn't accepting Oo2 or text saves???  I've done it 'before' the forum changes..? 
Guess I'll jus` post it- some time later.
I'm wondering about; "*if/how*" adding, soundcard modules- to file.

---

### Post by Triton on 2006-03-15
Has anyone looked into doing this with paralell service loading?  I would be very interested in trying to do this.  I've kinda tried but I'm not knowledgable enought on ubuntu services.

---

### Post by i3dmaster on 2006-03-15
for usplash, make sure you have it in grub menu.lst file (the kernel option), also sys-rc-conf should have it turned on at level 2345. After that, do a update-grub, then reboot. See if you can have it back...

---

### Post by stanz on 2006-03-15
It's in grub menu, & turned on @ 2345...did update & reboot & nadda.
Can't fix sound... I don't know where to start & haven't read any simular
posts, so i thinks jus' "hotpplug" will get re-x'ed....
***WOW...instant load/find!! and the tunes are blaring...

---

### Post by i3dmaster on 2006-03-17
For scard, you either turn hotplug back on or you can add your scard module into /etc/modules file and it will be loaded on boot time. but you need to know what module is.

---

### Post by stanz on 2006-03-17
Hi All, Hi i3dmaster-
Yeah... i read about adding scard module to /etc/modules file, but i don´t know what i looking for- when it comes to stuff like that...so, it was easier & quicker for a newbie like me, to turn hotplug back on.
I would need ´very detailed´ instructs...for that! 
Well, i do notice an improvement...Thanks much!!

---

### Post by i3dmaster on 2006-03-18
can you do ```
lsmod | grep snd
``` using root and paste the output? I will see if I can tell what scard module you are using...

---

### Post by stanz on 2006-03-21
[COLOR=Red]~# lsmod | grep snd[/COLOR]
snd_emu10k1           104964  1
snd_rawmidi            25248  1 snd_emu10k1
snd_seq_device          8588  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         74616  1 snd_emu10k1
snd_pcm_oss            50976  0
snd_mixer_oss          18304  1 snd_pcm_oss
snd_pcm                89480  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              24964  2 snd_emu10k1,snd_pcm
snd_page_alloc          9860  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9248  1 snd_emu10k1
snd                    55172  11 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9696  1 snd

---

### Post by ncappel1 on 2006-03-26
iD3Master, you might also want to remind people about making a backupcopy of the inittab file. This could have saved my butt after I made a big mistake fiddling with the settings!

---

### Post by dejitarob on 2006-04-06
[QUOTE=i3dmaster]
39. [COLOR="Red"]**ntpdate**[/COLOR] - Sync time with the ubuntu time server. I don't need it on boot time so I turned it off. The default is S.[/QUOTE]
If you are dual-booting with Windows, it is probably a good idea to leave ntpdate on. Windows can only deal with the hardware clock set to local (not UTC) and Linux needs ntpdate to correct this, otherwise your clock will increase an hour everytime you boot into Linux from Windows. Thanks for the great how-to.

---

### Post by domino on 2006-04-06
And if you triple boot with OS X Tiger (GMT), Linux (UTC), and windows (Local time), you have a bigger headache :D

---

### Post by Sokraates on 2006-04-07
I've noticed those troubles after booting into XP. Now I know why. :D

---

### Post by DavidTangye on 2006-04-07
What's the diff between GMT and UTC?

---

### Post by i3dmaster on 2006-04-07
[QUOTE=dejitarob]If you are dual-booting with Windows, it is probably a good idea to leave ntpdate on. Windows can only deal with the hardware clock set to local (not UTC) and Linux needs ntpdate to correct this, otherwise your clock will increase an hour everytime you boot into Linux from Windows. Thanks for the great how-to.[/QUOTE]
Thanks very much! I will update this to the HowTo

---

### Post by DavidTangye on 2006-04-07
> Originally Posted by dejitaOriginally Posted by dejitarob
...
> Windows can only deal with the hardware clock set to local (not UTC) and Linux needs ntpdate to correct this,
... if your linux system is told that your hard clock is set to UTC. If your linux system is told (via setup) that the hard clock is set to local time, ntpdate is still useful to fine-tune the system time.

A more full explanation. I am 98% sure this is correct...

I believe linux can be set to accept the hardware clock being set to UTC or to your local time, whereas windoze only expects the hardware clock to be set to local time. If both linux and windows are expecting the hardware clock to be local time, the two systems will each happily read the local time off the hardware clock and set the system time to that time. However in the case that linux is set to expect the hardware clock to be utc, a prior session under windows will have set the hardware clock to local, so your time in your next linux session will be out of synch.

To explain more indepth:
At bootup, linux runs 'hwclock'. Hwclock sets the system time to what it finds on the hardware clock. If hwclock has picked up local time off the hardware clock, but is expecting (ie told in your linux setup) that it is picking up UTC time, then hwclock will set the system time incorrectly. This is because it reads the local time off the hardware clock, however it considers it to be utc, and applies local time conversion again to what is already local time. The nett result is that your system time is set for the timezone twice the distance that you actually are from utc, ie from Greenwich. 
However if you have ntpdate run in the bootup it sets the correct system time irrespective of what hwclock has done: your system time will be set to exactly the correct time for your stated timezone. This is because ntpdate runs after hwclock, so any incorrect time set by hwclock will be fixed. Plus if your hardware clock has lost or gained any time while your PC was off, ntpdate will cause this to be corrected too.

> otherwise your clock will increase an hour everytime you boot into Linux from Windows.
... assuming your local time is an hour ahead of utc. See above.

> If you are dual-booting with Windows, it is probably a good idea to leave ntpdate on.
... if your linux system is told that the hard clock is actually set to utc, and also to set the clock precisely. See above.

---

### Post by i3dmaster on 2006-04-08
Very nice! Good to know!

---

### Post by R3linquish3r on 2006-04-12
sysv-rc-conf isn't available in the repo's anymore :( I really enjoyed this my last install of Ubuntu I can't stand IinitNG. Do you know of another way to get sysv-rc-conf?

---

### Post by MetalMusicAddict on 2006-04-12
[QUOTE=R3linquish3r]sysv-rc-conf isn't available in the repo's anymore :( I really enjoyed this my last install of Ubuntu I can't stand IinitNG. Do you know of another way to get sysv-rc-conf?[/QUOTE]
Something might be wrong. Im on Breezy now and I see it in Synaptic. I just got it yesterday for Dapper.

---

### Post by R3linquish3r on 2006-04-12
Could be because I'm using 64 bit this time around :/

---

### Post by MetalMusicAddict on 2006-04-12
Ahh... Good to know when I build my new PC.

---

### Post by stanz on 2006-04-12
I just got it from the repo's....again! uni & multi are enabled.

---

### Post by R3linquish3r on 2006-04-12
[QUOTE=MetalMusicAddict]Ahh... Good to know when I build my new PC.[/QUOTE]

Don't let that push you away from AMD 64's. There hella fast. Just don't use Ubuntu x64 run x32 instead. It's not that much slower.

---

### Post by Mishal on 2006-04-14
Stupid question but how do you shutdown a process? By removing the X from all the runlevels?

Can anyone show me a screenshot of how a final modified sysv-rv-conf looks like? :)

And what is Logical Volume Manager and how do I know whether I need it or not?

---

### Post by Owdy on 2006-04-15
I followed this quide and now reboot jams. It jams that part when it says 'rebooting, please wait'. What service i put back on?

edit: my bad. sorry. Fixed.

---

### Post by i3dmaster on 2006-04-16
[QUOTE=Mishal]Stupid question but how do you shutdown a process? By removing the X from all the runlevels?

Can anyone show me a screenshot of how a final modified sysv-rv-conf looks like? :)

And what is Logical Volume Manager and how do I know whether I need it or not?[/QUOTE]
Yes, by removing the X from all runlevels will stop that service from startup in any case, and the first thread actually shows which service I turned on and off on my personal laptop. But even though, I've said that you need to look carefully into each of the services cause your pc is different than mine and you can't just copy and paste... LVM is a logic storage management software. You can run vgscan -v as root and see if it finds anything, if no vg has been found, you can safely turn it off.

---

### Post by bodhi.zazen on 2006-04-20
This is a great post.

I would like to submit some modifications to your "howto", but I have a question,

What is the default run level in Ubuntu? Is the default 5 or 2?

---

### Post by bodhi.zazen on 2006-04-20
Nice post. I would like to add my 2 cents.

First we should make sure we are left with a bootable system and have backups.

Since we are changing our boot process:

Step 1- Make a bootable GRUB floppy.

[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

Step 2- Backup
	Is there any need to back up more then menu.1st, /etc/init.d, /etc/rcS.d, and /etc/rc*.c ( *= 0,1,2,3,4,5,6)?
		mkdir /~/bakup.files
		sudo cp -P /etc/init.d /~/backup.files
		sudo cp -P /boot/grub/menu.1st /~/backup.files
		sudo cp -P /etc/rc*.d /~/backup.files
	Although a backup of /etc is nice, is it not overkill for this exercise?

Setp 3- Know you Ubuntu Root device (hda1, hdb1, hda2,) and kernel (the numbers in "vmlinuz").
	Location of kernel is /boot

Step 4- Modify runlevels.
	DO NOT MODIFY DEFAULT RUN LEVELS 0,1, OR 6
	MODIFY ONLY 1 RUN LEVEL AT A TIME
	RUN LEVEL "S" IS RUN AT EACH RUN LEVEL PRIOR TO OTHERS
		ie as system boots (at default) the scritps in rcS.d are run first, then rc2.d

	Therefore, if you disable a script in "S", enable the script in runlevel 2
		This should guarantee your system will remain bootable to the default run level (2)

	In Ubuntu the default run level is 2
	Modify only 1 test run level at a time. Choose a custom run level (I will use 3 for the rest of this post, you can use 3,4, or 5).
	After modifying the runlevel test without re-booting
		sudo init 3
		This will change to run level 3
	Now check your system.
		Problems? Return to default run level and re-configure run level 3
			sudo init 5
		No problem -> Boot from floppy
	No problem, boot from floppy.
		When booting (from diskette) to the default run level, the "kernel" line looks like:
			kernel=/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
		In menu.1st this looks like this:
			kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
		To boot to run 3 (from GRUB diskette), add a "3" at the end of the line
			kernel=/boot/vmlinuz.... root=/dev/..... ro quiet splash 3
				Note: the number 3 was added at the end (without quotes)
			time boot process.
		If OK boot again from floppy (to default run level)
			kernel=/boot/vmlinuz..... root=/dev/.... 
				Note: no number 3 at the end of this line
			time boot process
			This is the default boot and you can measure any time savings.
				booting from a floppy to compair apples to apples
	If OK you can now change the default run level (or not)
		There is more then 1 way to do this
		My preferance is to leave the default runlevel unmodified 
			This leaves the default boot process as a future referance
		Change the default boot level
			sudo nano /boot/grub/menu.1st
				add init=3 to end of line

			kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash 3

				Or create 2 Ubuntu titles, one for each run level.
		
		OR
		
		Edit /etc/inittab

Step 4- Modify shutdown scripts if desired.

This process should guide users through a logical process of modifying boot scripts without generating a non-bootable system. Backups were made "just in case" but really should not be needed.

---

### Post by leeyee on 2006-04-28
Aha...thank you!
You have done a really nice job! I love this kind howtos, tell you how and tell you why as well. 
Thanks again!

---

### Post by jckdnk111 on 2006-05-02
Would you mind explaining your /etc/network/interfaces setup ... everything is working great except my wireless card (eth1) is not being detected anymore and my nic (eth0) isn't being activated by default.

Thanks for the HowTo!!!

**_My interfaces file looks like this:_**

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth1 inet dhcp
wireless-essid someSID
wireless-key someWEPKey

iface eth0 inet dhcp

auto eth1

auto eth0

---

### Post by barbarian on 2006-05-02
extremely usefull howto, thanks!

---

### Post by i3dmaster on 2006-05-03
[QUOTE=jckdnk111]Would you mind explaining your /etc/network/interfaces setup ... everything is working great except my wireless card (eth1) is not being detected anymore and my nic (eth0) isn't being activated by default.

Thanks for the HowTo!!!

**_My interfaces file looks like this:_**

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth1 inet dhcp
wireless-essid someSID
wireless-key someWEPKey

iface eth0 inet dhcp

auto eth1

auto eth0[/QUOTE]
I guess you probably are not using dapper yet so you still have the hotplug in there. If you turned off your hotplug/hotplug-nt (I think... cause I haven't used it for a while) services, you can turn them back so that it will be able to manage your nic cards. The last "auth eth1" is not necessary, you can put after "auto lo", just like "auto lo eth1".

---

### Post by i3dmaster on 2006-05-03
[QUOTE=bodhi.zazen]Nice post. I would like to add my 2 cents.

First we should make sure we are left with a bootable system and have backups.

Since we are changing our boot process:

Step 1- Make a bootable GRUB floppy.

[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

Step 2- Backup
	Is there any need to back up more then menu.1st, /etc/init.d, /etc/rcS.d, and /etc/rc*.c ( *= 0,1,2,3,4,5,6)?
		mkdir /~/bakup.files
		sudo cp -P /etc/init.d /~/backup.files
		sudo cp -P /boot/grub/menu.1st /~/backup.files
		sudo cp -P /etc/rc*.d /~/backup.files
	Although a backup of /etc is nice, is it not overkill for this exercise?

Setp 3- Know you Ubuntu Root device (hda1, hdb1, hda2,) and kernel (the numbers in "vmlinuz").
	Location of kernel is /boot

Step 4- Modify runlevels.
	DO NOT MODIFY DEFAULT RUN LEVELS 0,1, OR 6
	MODIFY ONLY 1 RUN LEVEL AT A TIME
	RUN LEVEL "S" IS RUN AT EACH RUN LEVEL PRIOR TO OTHERS
		ie as system boots (at default) the scritps in rcS.d are run first, then rc2.d

	Therefore, if you disable a script in "S", enable the script in runlevel 2
		This should guarantee your system will remain bootable to the default run level (2)

	In Ubuntu the default run level is 2
	Modify only 1 test run level at a time. Choose a custom run level (I will use 3 for the rest of this post, you can use 3,4, or 5).
	After modifying the runlevel test without re-booting
		sudo init 3
		This will change to run level 3
	Now check your system.
		Problems? Return to default run level and re-configure run level 3
			sudo init 5
		No problem -> Boot from floppy
	No problem, boot from floppy.
		When booting (from diskette) to the default run level, the "kernel" line looks like:
			kernel=/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
		In menu.1st this looks like this:
			kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
		To boot to run 3 (from GRUB diskette), add a "3" at the end of the line
			kernel=/boot/vmlinuz.... root=/dev/..... ro quiet splash 3
				Note: the number 3 was added at the end (without quotes)
			time boot process.
		If OK boot again from floppy (to default run level)
			kernel=/boot/vmlinuz..... root=/dev/.... 
				Note: no number 3 at the end of this line
			time boot process
			This is the default boot and you can measure any time savings.
				booting from a floppy to compair apples to apples
	If OK you can now change the default run level (or not)
		There is more then 1 way to do this
		My preferance is to leave the default runlevel unmodified 
			This leaves the default boot process as a future referance
		Change the default boot level
			sudo nano /boot/grub/menu.1st
				add init=3 to end of line

			kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash 3

				Or create 2 Ubuntu titles, one for each run level.
		
		OR
		
		Edit /etc/inittab

Step 4- Modify shutdown scripts if desired.

This process should guide users through a logical process of modifying boot scripts without generating a non-bootable system. Backups were made "just in case" but really should not be needed.[/QUOTE]
Great Instruction! Add to the Howto and thanks for contribution!

---

### Post by bodhi.zazen on 2006-05-03
There is one error in my post:

In step 4:
"
Problems? Return to default run level and re-configure run level 3
sudo init 5
"

This should read:
"
Problems? Return to default run level and re-configure run level 3
sudo init 2
"

Sorry, I run a version of Linux that defaults to level 5

---

### Post by i3dmaster on 2006-05-04
[QUOTE=bodhi.zazen]There is one error in my post:

In step 4:
"
Problems? Return to default run level and re-configure run level 3
sudo init 5
"

This should read:
"
Problems? Return to default run level and re-configure run level 3
sudo init 2
"

Sorry, I run a version of Linux that defaults to level 5[/QUOTE]
np, just updated! You must run a rpm based Linux.

---

### Post by Onyros on 2006-05-08
I just followed your guide, but didn't really notice a very dramatic difference in the time it takes to boot (obviously it doesn't list the services I disabled at startup).

I noticed a BIG difference regarding reboot and shutdown, it trimmed down the time it takes to do both of those by a lot.

I kept the hotplug subsystem as I need it constantly, I'm always hotplugging lots of different devices, and I expect that to be the most significant difference in that list ;)

The biggest difference I noticed was with RAM usage. With Fluxbox I went from around 85MB of RAM used after a reboot, to 66MB, so that's pretty good in my book, thanks :D

Note: I'm using the gnome-volume-manager and that gobbles a bit of RAM by itself), but would really like a good suggestion for an alternative. Something in the likes of DSL's way of mounting/accessing removable drives? Any way to integrate a mounting solution with PCManFM?

I also noticed something strange (or maybe not): I have two gdm processes running. Is this normal?

Also, it might be an inverted placebo effect, but now amaroK seems to take more time to start. (yeah, I know... we're talking about speeding up the system, minimizing RAM usage and I'm using amaroK... I just love it :P Strange as it may seem, my favourite music player in Windows was foobar2000... from minimal to bloated... it was a long way)

Btw, with my tiny Mini-ITX system (on my sig) I now manage to boot under a minute into Fluxbox. :D

---

### Post by ice60 on 2006-05-08
hi, i'm not sure why but i have **postfix** too, i disabled it because it's a internet server which i can't think how it got there :confused: (maybe i'm owned :( )

[quote=i3dmaster]2. ok, open your eyes and look very carefully for those [color=red]SERVICES DO NOT HAVE "X" ON ALL RUNLEVELS[/color] (All runlevel means 1,2,3,4,5,6, and S), write them down one by one. Don't make mistakes here. Double check after you've done.[/quote]
you wrote the above. it's unclear to me what you mean, it sounds like you are saying a runlevel which is anything less then totally full. if you are saying services which have no 'X's and the line is blank, it might be better to say it this way -

2. ok, open your eyes and look very carefully for those [color=red]SERVICES THAT DO NOT HAVE A "X" ON _ANY_ RUNLEVELS[/color], write them down one by one. Don't make mistakes here. Double check after you're done.


i hope that makes sense, i've read it over so many times now i'm totally confused :-k lol. thanks for the post :D

---

### Post by i3dmaster on 2006-05-11
[QUOTE=ice60]hi, i'm not sure why but i have **postfix** too, i disabled it because it's a internet server which i can't think how it got there :confused: (maybe i'm owned :( )


you wrote the above. it's unclear to me what you mean, it sounds like you are saying a runlevel which is anything less then totally full. if you are saying services which have no 'X's and the line is blank, it might be better to say it this way -

2. ok, open your eyes and look very carefully for those [color=red]SERVICES THAT DO NOT HAVE A "X" ON _ANY_ RUNLEVELS[/color], write them down one by one. Don't make mistakes here. Double check after you're done.


i hope that makes sense, i've read it over so many times now i'm totally confused :-k lol. thanks for the post :D[/QUOTE]
Well it sounds pretty clean to me though but I will take your suggestion and update the HowTo. Thanks!!

---

### Post by orzechowskid on 2006-05-21
wonderful guide, thanks!

---

### Post by walding on 2006-05-28
I have a service called etc-setse$.  I can't find any info on this.  Can anyone here enlighten me?  I have an Asus A6VM laptop.

---

### Post by i3dmaster on 2006-05-28
[QUOTE=walding]I have a service called etc-setse$.  I can't find any info on this.  Can anyone here enlighten me?  I have an Asus A6VM laptop.[/QUOTE]
you can go to /etc/init.d dir and look for the script named like that. If you don't know how to read bash, paste the script here and I will take a look for you.

---

### Post by walding on 2006-05-29
Thanks.  I'm not a programmer and relatively new (18m) to linux, but learning fast at both!  Thankfully, the script is well annotated.

---

### Post by R3linquish3r on 2006-05-29
Well I turned off mdadm-raid, firestarter, and one other thing thats on the top of my head, after an upgrade to dapper. Now I get a black screen with one line that doesnt blink :( I'm pretty sure the problem is the raid but the weird thing is that I don't use it....

---

### Post by lzap on 2006-06-18
Dont switch the readahead off. Its not a daemon, it is run only once at the startup - it loads several files in the memory...

---

### Post by mixim on 2006-06-18
Maybe it's time for a Dapper Drake 6.06 LTS Update ??

---

### Post by Owdy on 2006-06-18
[quote=lzap]Dont switch the readahead off. Its not a daemon, it is run only once at the startup - it loads several files in the memory...[/quote] I have also readhead$ , whats that?

---

### Post by i3dmaster on 2006-06-19
[QUOTE=R3linquish3r]Well I turned off mdadm-raid, firestarter, and one other thing thats on the top of my head, after an upgrade to dapper. Now I get a black screen with one line that doesnt blink :( I'm pretty sure the problem is the raid but the weird thing is that I don't use it....[/QUOTE]
If you aren't using raid in your system, it should be safe to turn the service off. firestarter is just a firewall service, it shouldn't have anything to do with the black screen either. When you boot up, go to grub menu and take out splash and queit, maybe add debug in there and boot, there will be more useful info output from the console.

---

### Post by i3dmaster on 2006-06-19
[QUOTE=mixim]Maybe it's time for a Dapper Drake 6.06 LTS Update ??[/QUOTE]
Not really necessary for Dapper. init bootup process and daemons are pretty much the same.

---

### Post by i3dmaster on 2006-06-19
[QUOTE=Owdy]I have also readhead$ , whats that?[/QUOTE]
something like preload. Some will consider it useful to speed up loading programs.

---

### Post by Owdy on 2006-06-19
[quote=i3dmaster]something like preload. Some will consider it useful to speed up loading programs.[/quote] Yes, but whats the difference with readhead$ and readhead?

---

### Post by i3dmaster on 2006-06-19
[QUOTE=Owdy]Yes, but whats the difference with readhead$ and readhead?[/QUOTE]
the readahead$ is just because the filename is longer than what the sysv program predefined, so it got chopped off. The real name is readahead-desktop. All the init scripts are under /etc/init.d/ dir. The difference is readahead will read in /etc/readahead/boot list and readahead-desktop will read in the desktop list.

---

### Post by Owdy on 2006-06-19
[quote=i3dmaster]the readahead$ is just because the filename is longer than what the sysv program predefined, so it got chopped off. The real name is readahead-desktop. All the init scripts are under /etc/init.d/ dir. The difference is readahead will read in /etc/readahead/boot list and readahead-desktop will read in the desktop list.[/quote] Thanks. Do you know defaulöt value for readahead-desktop?

---

### Post by JMO707 on 2006-06-19
Is there a file where I can manually choose what daemons I want at boot?

MPD simply doesnt start. I've tryed all, and now I cant find any file for that purpose.

---

### Post by richbarna on 2006-06-20
[QUOTE=MetalMusicAddict]Nice guide. Reminds me of BlackVipers guide for windows services. :)

[/QUOTE]

I remember BlackVipers guide as well, But instead of manually shutting down services (which I ended up doing anyway) he had .reg files that you just double-clicked and it was all done for you.
I could do with something like that for Ubuntu, but for now I will follow this guide and have a tinker ;)

---

### Post by stanz on 2006-06-22
Hi All,
After my 6.06 upgrade, booting got slow again, so the tweaking & stumbling on to new stuff ~ began!
[quote=i3dmaster]readahead will read in /etc/readahead/boot list and readahead-desktop will read in the desktop list.[/quote] I've found a "*stopreadahead*", in "*rc2.d*" @ "*S99*",
 Will this conflict with hdparm adjustments on enabling readahead?
I made my own file, made it script, placed it in "*/etc/init.d*", and linked to, "*/etc/rcS.d/S07hdparm*".
 My Testing still continues...#-o
I know there are many of us, the tweak the "hdparm" file, so someone might know already.?
*_Other New Stuff, TO ME, includes..._*
rc2.d / K90powernowd.early
rc0.d / K20bittorrent
rcS.d /    S25brltty
rc0.d/K20festival  2,3,4,5
rcS.d/S08loopback
rcS.d/S22mtab
rc2.d/S99rc.local   2,3,4,5
        /stop-read   2
        /umountroot  0,6
        /x11-common
rcS.d/S80bootmisc.sh {was looking for bootlogd- found off in sys-rc-conf?}
I've not abunch of time to look, & offer more info to these...but, I figured if new things are included,
 this might help update this HowTo, and offer some answers to all us newbies.  :rolleyes: 
Has This **[B]"**[howto] General 5.10"[/B]  Been updated, Since we're all mostly using 6.06?

---

### Post by Mishal on 2006-06-22
Yeah...will there be a similar thread for the Dapper Drake release? :) It will be very useful...

---

### Post by stanz on 2006-06-22
[quote=domino]As promised. Virgin Breezy PC install. **Page 1:****Page 2:**[/quote] This may be a "Dhaaaa", question,~ but, am i the only one having trouble viewing these pics?
I've "saved as", and opened with Ffox, gimp, image viewer, etc..etc.. & cannot get those into focus!?
Aside from being labeled "png.jpeg", can someone pass me a clue..?   :-k

---

### Post by ashrack on 2006-06-22
```
rc0.d / K20bittorrent   
rcS.d / brltty   #ppl with special needs
rc0.d/K20festival 2,3,4,5   ###its for reporting something to CANONCIAL,cant remember what
```
these are safe to remove. Leave the others as they are

---

### Post by stanz on 2006-06-23
:-D
BUM (boot up manager) sez:
**loopback**: high level tools to configure network interfaces
"This package provides the tools ifup and ifdown which may be used to
 configure (or, respectively, deconfigure) network interfaces based on
 interface definitions in the file /etc/network/interfaces."
----------
**mtab**: Standard scripts needed for booting and shutting down
"These scripts are meant for standard Debian/GNU/Linux installations."
----------
 **readahead-list** is an updated and enhanced version of the original readahead
 utility.
 "It allows the user to specify a set of files to be read into the page cache
 to accelerate first time loading of programs, typically during the boot
 sequence."   ~ I'll be lookin' for that!
----------
**brltty:** Access software for a blind person using a soft braille terminal {niice}
----------
I just found this info while tweaking & pondering stuff,
I guess If more is enabled ~ it'll be in that list... pretty kewl, I think :rolleyes:

---

### Post by Owdy on 2006-06-23
[quote=stanz]:-D
----------
 **readahead-list** is an updated and enhanced version of the original readahead
 utility.
 "It allows the user to specify a set of files to be read into the page cache
 to accelerate first time loading of programs, typically during the boot
 sequence."   ~ I'll be lookin' for that![/quote] How do i conf that?

---

### Post by stanz on 2006-06-24
[FONT=Georgia][SIZE=2][quote=Owdy]How do i conf that?[/quote] That's something, I don't know...Might [/SIZE][/FONT][FONT=Georgia][SIZE=2]be simple ~ adding/removing files.[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Georgia][SIZE=2] I've found a readahead file in /etc,  & in it, is 4 others (including the readahead.new).[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Georgia][SIZE=2]Have a look-see at both readaheads.  :-k[/SIZE][/FONT][FONT=Georgia][SIZE=2]
[/SIZE][/FONT][FONT=Georgia][SIZE=2] If  I worked 'diff' right- their similar files.  Some quick searching, I've found::[/SIZE][/FONT][FONT=Georgia][SIZE=2]
[/SIZE][/FONT][FONT=Georgia][SIZE=2][The Topic in forums]("http://ubuntuforums.org/showthread.php?t=137599&highlight=readahead")[/SIZE][/FONT][FONT=Georgia][SIZE=2][U]
[Linux:  Adaptive Readahead]("http://kerneltrap.org/node/6642")
[/U][/SIZE][/FONT][FONT=Georgia][SIZE=2][Linux Programmer's Manual ]("http://www.phpman.info/index.php/man/readahead/2")[/SIZE][/FONT]

---

### Post by Bosonator on 2006-07-27
Someone please correct me if this is the wrong place to ask, but...

Q: How do you know if you use LVM or Enterprise Volume Management? I ask because I would turn them off if I'm not using them. I've never intentionally set these things up, but is there a chance my system might be using them by default? 

Thanks for any help on this.

P.S. Great guide.... nice and clear.

---

### Post by eXisor on 2006-08-02
Typically you select them when you install Ubuntu. If you're aksing it is unlikely you use them...

---

### Post by FarmerGiles on 2006-08-08
Thanks, worked fo me :D

---

### Post by ciscosurfer on 2006-08-09
> **DavidTangye said:**
> What's the diff between GMT and UTC?
A bit more info on the differences (not related to *nix):
[http://www.dxing.com/utcgmt.htm](http://www.dxing.com/utcgmt.htm)
[http://ubuntuforums.org/newreply.php?do=newreply&p=900481](http://ubuntuforums.org/newreply.php?do=newreply&p=900481)

> **dcstar said:**
> Well, it says he doesn't allow GUI editing of the rcS.d services (which are the Single User mode services), he still allows editing of all the other run level scripts.
rcS.d services are *startup *scripts -- they are executed once when booting the system, even when booting directly into single user mode.
rc1.d services are *single user mode* scripts.

> **ashrack said:**
> ```
rc0.d / K20bittorrent   
rcS.d / brltty   #ppl with special needs
rc0.d/K20festival 2,3,4,5   ###its for reporting something to CANONCIAL,cant remember what
``` these are safe to remove. Leave the others as they are

bittorrent >> [http://ubuntuforums.org/showthread.php?t=197127](http://ubuntuforums.org/showthread.php?t=197127)
                    [http://packages.ubuntu.com/dapper/net/bittorrent](http://packages.ubuntu.com/dapper/net/bittorrent)

brltty >> Access software for a blind person using a soft braille terminal 
              [http://packages.ubuntu.com/dapper/admin/brltty](http://packages.ubuntu.com/dapper/admin/brltty)

festival >> Doesn't report anything to Canonical.  It's a general multilingual speech synthesis system: [http://packages.ubuntu.com/dapper/sound/festival](http://packages.ubuntu.com/dapper/sound/festival)

---

### Post by lennox on 2006-08-10
There is a little typo in the Howto:

runlevel 2,3,4,5: in debain system, the multi-user env, **may not may not** include GUI. The same, processes under each of the corresponding dirs will be run. **Note** this is

---

### Post by ciscosurfer on 2006-08-13
Bootime is now ~19 seconds for me =D>; Shutdown is now ~15 seconds!  Hazzah! \\:D/

---

### Post by stanz on 2006-08-14
> **Mishal said:**
> Yeah...will there be a similar thread for the Dapper Drake release? :) It will be very useful...
Hi All...Has Mishal's question been answered?
I ask, cause I'm working on a 'Fresh Install' & have begun tweaking &
finding New & Different, files & such.
One new file ~ for ME - is a 'hdparm' script, in */etc/init.d*.
In Breezy - I made mine...then with UpGrade - mine stayed...nothing new.
But this script, I can't figure out! Me no code braker.. :mrgreen:
- Would tweaking the new Dapper file, be better? or might be a Must?
- Switching won't be a problem?

Any advice for us?
Thanks in Advance....:rolleyes:

---

### Post by iamhugeinjapan on 2006-08-15
> **yaaarrrgg said:**
> also, here's a one line hack that worked good for me on breezy ... run startup scripts in parallel, merely by changing the startup script: /etc/init.d/rc

Changing the line:

```

startup $i start

```

to the following:

```

startup $i start &

```

from:
[http://www.debian-administration.org/articles/199](http://www.debian-administration.org/articles/199)
[http://www.hoeg.org/blog/2005/07/27/fast-booting-debian/](http://www.hoeg.org/blog/2005/07/27/fast-booting-debian/)

The code in the file appears to be different in Dapper as the referenced line does not appear. There is however a comment that appears a few times that says:
"# Run all scripts with the same level in parallel"

So maybe it's already doing it? If not can someone point out the relevant bit to change? Thanks

---

### Post by ardchoille on 2006-08-15
This is one outstanding post! This information has helped me to get Ubuntu booting much faster. Thank you very much for taking the time to explain it all :)

---

### Post by LKRaider on 2006-08-20
Very useful thread!

I also found this page: [wiki.ubuntu.com/Teardown]("wiki.ubuntu.com/Teardown")
it lists several shutdown and reset services (rc0 & rc6) that can be safely removed because they will be finished by the term signal in the same manner.

I also made a nice little script that disables/enables the rc0/6 services for me very easily. I just input a list of services (by their names, no need to know the KXX stuff) and it changes their state to either enabled or disabled (renames the initial K as per first post instructions) ^_^

I am thinking of developing it further with a GUI and all... we'll see :P

---

### Post by ashrack on 2006-08-20
This TEARDOWN info is great. Should be the first post!!! As it makes certain options in the first post obsolete.

---

### Post by lassegs on 2006-08-29
Hi

I just wanted to say thanks for this great howto!

---

### Post by KhaaL on 2006-09-03
You can also cut down the boot time by change the sleep time in the sleep calls in /etc/init.d . enter the /etc/init.d directory and do "grep sleep *". note the filenames who makes the sleep calls, then edit them in a text editor and decrease the time. To what I've heard, you can cut down the time to 1, even 0.5 seconds, and the system will boot without a problem.

WARNING! I haven't tested this yet, according to the article this shouldn't cause any problems. Keep in mind that this isn't a ubuntu specific hack.

---

### Post by Rodrigo on 2006-09-08
Xcelent, thanks, Im goint to test it right away :D

---

### Post by geearf on 2006-09-09
Hey,

just a small message to maybe warn some of you, i don't relly know how this will work when you will update to edgy and use upstart. There is a compatiblity between sysv and upstart, but is there one with initng ?

---

### Post by Jeff D on 2006-09-11
Hi quick question, when I type "sudo sysv-rc-conf" into the terminal I'm getting "sysv-rc-conf: command not found" and I'm unable to procede any further.  Any reason why this would be happening?  Before my Grub/Windows failure a week earlier I had no problem editing the boot process!?!  Thanks in advance.

---

### Post by ciscosurfer on 2006-09-12
You need to install it first```
sudo aptitude update && sudo aptitude install sysv-rc-conf
```Then run it from a terminal like you tried to do before.

---

### Post by Jeff D on 2006-09-12
Tried that to no avail, here's what I'm getting...after Reading package lists... "sudo aptitude update" runs properly.

jeff@jeff-desktop:~$ sudo aptitude install sysv-rc-conf
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No candidate version found for sysv-rc-conf
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
jeff@jeff-desktop:~$ sudo sysv-rc-conf
sudo: sysv-rc-conf: command not found

---

### Post by i3dmaster on 2006-09-13
> **Jeff D said:**
> Tried that to no avail, here's what I'm getting...after Reading package lists... "sudo aptitude update" runs properly.

jeff@jeff-desktop:~$ sudo aptitude install sysv-rc-conf
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No candidate version found for sysv-rc-conf
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
jeff@jeff-desktop:~$ sudo sysv-rc-conf
sudo: sysv-rc-conf: command not found
You will need to enable the universal repo in your sources.list file. Its under /etc/apt/sources.list.

---

### Post by niko7865 on 2006-09-13
I removed a few things from boot and can no longer boot to my k7-smp kernel. Once the GUI Login screen (gdm?) is displayed it everything but the mouse will hang indefinitly after 5 seconds. I'm fairly sure I changed everything back to how it was but I still can't get intothe k7 (386 works fine, on it now). Should I ry removeing and then reinstalling my k7-smp kernel? Is there anyway to revert back to my old boot up? (I'm a noob and didn't write down how everything was before I started changing crap)

---

### Post by Richardky on 2006-09-13
thx for the nice guide my first post and a total newb ... was easy to follow ...no probs

---

### Post by Jeff D on 2006-09-13
> **i3dmaster said:**
> You will need to enable the universal repo in your sources.list file. Its under /etc/apt/sources.list.


  Thank you kindly!  That did it.

---

### Post by drakedog on 2006-09-14
Nice Tips, tnks. But how can i speed up the Filechecking, or skip it on startup?

---

### Post by ciscosurfer on 2006-09-14
@drakedog: this will help you >> [http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/](http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/)

---

### Post by obf213 on 2006-09-15
help. i changed only wht the guide told me to change, and now when i do a reboot my computer just shuts down. also, on shut down it doest go through the process of shutting down any of the processes any more. normally it would say stopping ....., then shutting down alsa, stopping bluetoothutils etc. now  the usplash comes up it says something like "configureing usplash time out" then it says will now halt and closes down in like 4 seconds. the it wont restart. hellllp wht did i do. i used the pictures and set everything back to default (according to the picture) but it still persists

---

### Post by ijjz on 2006-10-02
Thanks for the easy way of editing some start up processes.

---

### Post by TFrog on 2006-10-10
> **i3dmaster said:**
> This HowTo is for those who complaint ubuntu boot-up speed is pretty slow but not willing to install any alternative tools to speed up. The way I use here is not the altimate solution by any means but it does make differences and it does work. Everything done below is by tuning the boot process itself and because everyone's computer might be different, there is a little risk that something below might break your system. Take your own judgment before you perform a change and always good to do a backup for the /etc dir.

[COLOR="Red"]****This HowTo is mainly for laptops and desktops, not for servers.****[/COLOR]

[COLOR="Red"]**Suggestions for this HowTo:**[/COLOR]
1. I hope you learn something from here but not just a simple copy. So please, **DO NOT** follow exactly what I did and copy to your box. Read the descriptions of services and use your own judgment to determine if you need to keep them on or not. For instance, I turned GDM off on mine to boot to console, but if you do not feel confortable to see console at all, you should keep GDM or KDM on to boot directly to GUI.
2. If you have a question about a boot up service and not really sure what it does, post a question here and see if anybody can help you. Ask before you do if you don't know. The bottom line to be safe is to leave a service on rather than turn it off if you do not understand.
3. If you see a boot up service that you have but not in here, let us know what it does just like what I did here - give some descriptions and suggestions on whether it should be on or off on a normal laptop or desktop environment.
 
Color reference : [COLOR="SeaGreen"]**service I turned on**[/COLOR]
                  [COLOR="Red"]**service I turned off**[/COLOR]

[color=blue]**Screen shots contrib'ed by domino for the initial bootup settings. A great reference for those who mess up on runlevels... Thanks!!**[/color]

**Page 1:**
[[IMG]http://img485.imageshack.us/img485/9814/14ub.th.png[/IMG]](http://img485.imageshack.us/my.php?image=14ub.png)

**Page 2:**
[[IMG]http://img485.imageshack.us/img485/4586/25cr.th.png[/IMG]](http://img485.imageshack.us/my.php?image=25cr.png)


I. Install a tool - sysv-rc-conf. It is a perl based boot process adjustment tool.
```

sudo apt-get update
sudo apt-get install sysv-rc-conf

```
It gives you a way to esaily config the boot process and runlevel configuration, but its not necessary if you want to do it manually by linking/unlinking the files... Its up to you.

II. Ok, that's all we need. Now let's fire it up by
```

sudo sysv-rc-conf

```
and analyze each service one by one. **Note:** Some services I have here you might not have, perfectly ok. If some you have but I don't, then you will need to investigate on your own or ask here... But this HowTo should cover most of them...

Throw a littel bit of runlevel knowledge here before we start messing them up.... All the boot processes are executed in sequence as following:
runlevel S: the first runlevel in boot process. /etc/init.d/rcS script will be invoked to start and all the processes underneath /etc/rcS.d will be executed.
runlevel 1: the single user mode. All processes underneath /etc/rc1.d will be executed.
runlevel 2,3,4,5: in debain system, the multi-user env, may not may not include GUI. The same, processes under each of the corresponding dirs will be run. **Note** this is different than RedHat, SuSE, and other RPM based systems.
runlevel 0: computer shutdown.
runlevel 6: computer reboot.

ok, back to sysv-rc-conf:

1. [COLOR="SeaGreen"]**acpi-support**[/COLOR]  - You'd better leave it on the default runlevel. The default is 2,3,4,5.
2. [COLOR="SeaGreen"]**acpid**[/COLOR]   - The acpi daemon. These two are for power management, quite important for laptop and desktop computers, so leave them on. The default is 2,3,4,5
3. [COLOR="Red"]**alsa**[/COLOR]  - If you use alsa sound subsystem, yes leave it on. But if you have the service below, its safe to be off. The default is off when alsa-utils is on.
4. [COLOR="SeaGreen"]**alsa-utils**[/COLOR]  - On my system, this service supercedes the alsa, so I turn off the alsa and turn this on at S level. **Note**, I mean "turn off" is to remove all "X" at all runlevels. If you don't have it on your system, no problem. Just keep going. The default is S runlevel.
5. [COLOR="Red"]**anacron**[/COLOR]  - A cron subsystem that executes any cron jobs not being executed when the time is on. Most likely you've probably turned your computer off when a certain cron job time is ready. For example, updatedb is scheduled at 2am everyday, but at that moment, you computer is off, then if anacron service is on, it will try to catch up that updatedb cron... I turn it off cause it didn't turn my laptop off very offen, but its totally up to you for this one. The default is 2,3,4,5
6. [COLOR="Red"]**apmd**[/COLOR] - This is the one that confused me a quite bit. I have acpid on already and what's the benefits of having apmd on too? If you computer is not that old which can't even support acpi, then you may try to turn this off. I did anyway. The default is 2,3,4,5
7. [COLOR="Red"]**atd**[/COLOR] - like cron, a job scheduler. I turned it off. The default is 2,3,4,5
8. [COLOR="SeaGreen"]**binfmt-support**[/COLOR] - Kernel supports other format of binary files. I left it on. The default is 2,3,4,5
9. [COLOR="Red"]**bluez-utiles**[/COLOR] - I turned it off. I don't have any bluetooth devices. The default is 2,3,4,5
10. [COLOR="SeaGreen"]**bootlogd**[/COLOR] - Leave it on. The default is S.
11. [COLOR="SeaGreen"]**cron**[/COLOR] - Leave it on. The default is 2,3,4,5
12. [COLOR="Red"]**cupsys**[/COLOR] - subsystem to manager your printer. I don't have so I turned it off, but if you do, just leave it on. The default is 2,3,4,5
13. [COLOR="SeaGreen"]**dbus**[/COLOR] - Message bus system. Very important, leave it on. The default is 2,3,4,5
14. [COLOR="Red"]**dns-clean**[/COLOR] - Mainly for cleaning up the dns info when using dial-up connection. I don't use dial up, so I turn it off. The default is S.
15. [COLOR="Red"]**evms**[/COLOR] -  Enterprise Volumn Management system. I turned it off.  The default is S.
16. [COLOR="Red"]**fetchmail**[/COLOR] - A mail receving daemon. I turned it off. The default is 2,3,4,5
17. [COLOR="SeaGreen"]**gdm**[/COLOR] - The gnome desktop manager. I turned it off anyway since I get use to boot to console first. This is up to you if you want to boot directly to GUI. The default is 2,3,4,5
18. [COLOR="Red"]**gdomap**[/COLOR] - Actually I have no idea why this one should on. I didn't see any other systems have this daemon, so I turned it off and  I don't feel I lose anything. Any benefits to have it on a loptop or desktop? The default is 2,3,4,5
19. [COLOR="SeaGreen"]**gpm**[/COLOR] - Mouse support for console. If you feel you'd better have a mouse on console, go turn it on at runlevel 1 and 2. That's all you need. The default is 2,3,4,5
20. [COLOR="SeaGreen"]**halt**[/COLOR] - Don't change it. The default is 0.
21. [COLOR="SeaGreen"]**hdparm**[/COLOR] - tuning harddisk script. I removed the 2,3,4,5 runlevel but add it to S runlevel. I feel that opening DMA, 32bit I/O, etc eariler will benefit the rest of the processes. Also I changed the original script to a very simple one that I made myself. I feel useless to put all those redundant checks if I know what I am doing. The configuration file is /etc/hdparm.conf. The default is 2,3,4,5
22. [COLOR="SeaGreen"]**hibernate**[/COLOR] - If your system support hibernate, leave it on. Otherwise, its useless for you. The default is S.
23. [COLOR="Red"]**hotkey-setup**[/COLOR] - This daemon setup some hotkey mappings for Laptop. Manufacturers supported are: HP, Acer, ASUS, Sony, Dell, and IBM. If you have a laptop in those brands, you can leave it on, otherwise, this might not have any benefits for you. The default is 2,3,4,5
24. [COLOR="Red"]**hotplug and hotplug-net**[/COLOR] #activating hotplug subsystems takes time. I'd consider to turn them off. I did some changes in my /etc/network/interfaces file. Instead of mapping my wireless card during hotplug process, I set it up to auto. So I can turn them off. I've tested even I turned them off, ubuntu can still detect my usb driver, my digital camera, etc. So I think its pretty safe to turn them off. [COLOR="SeaGreen"]****Note** If you find your sound card doesn't work after turning hotplug service off, you can turn it back. Or edit /etc/modules file to add your sound card's driver module.**[/COLOR] Tested out the later one is faster. The default is S.
25. [COLOR="Red"]**hplip**[/COLOR] - HP printing and Image subsystem. I turned it off. The default is S.
26. [COLOR="Red"]**ifrename**[/COLOR] - network interface rename script. Sounds pretty neat but I turned it off. Mainly for managing multiple network interfaces names. Since I have a wireless card and an ethernet card, they all assigned eth0 and ath0 from kernel, so its not really useful for me. The default is S.
27. [COLOR="SeaGreen"]**ifupdown and ifupdown-clean**[/COLOR] - Leave it on. They are network interfaces activation scripts for the boot time. ifupdown default is 0,6,S and ifupdown-clean is S.
28. [COLOR="Red"]**inetd or inetd.real**[/COLOR] - take a look your /etc/inetd.conf file and comment out any services that you don't need. If there aren't any services there, then its very safe to turn them off. The default is 2,3,4,5
29. [COLOR="SeaGreen"]**klogd**[/COLOR] - Leave it on. The default is 2,3,4,5
30. [COLOR="SeaGreen"]**laptop-mode**[/COLOR] - A service to tweak the battery utilization when using laptops. You can leave it on. The default is 2,3,4,5 
31. [COLOR="SeaGreen"]**linux-restricted-modules-common**[/COLOR] - You need to see if you really have any restricted modules loaded on your system. Since I need madwifi ath_pci module, so I left it on. The restricted modules can be found from /lib/linux-restricted-modules. If you find that you are not using any of the restricted modules, then its ok to turn it off. The default is 0,6, and S.
32. [COLOR="Red"]**lvm**[/COLOR] - I don't use it so I turned it off. Leave it on if you *DO* have lvm. The default is S.
33. [COLOR="SeaGreen"]**makedev**[/COLOR] - Leave it on. The default is 2,3,4,5
34. [COLOR="Red"]**mdamd**[/COLOR] - Raid management tool. I don't use it so I turned it off. The default is 2,3,4,5
35. [COLOR="Red"]**mdamd-raid**[/COLOR] - Raid tool. If you don't have Raid devices, turn it off. The default is S.
36. [COLOR="SeaGreen"]**module-init-tools**[/COLOR] - Load extra modules from /etc/modules file. You can investigate your /etc/modules file and see if there is any modules that you don't need. Normally, this is turned on. The default is S.
37. [COLOR="SeaGreen"]**mountvirtfs**[/COLOR] - mount virtual filesystems. Leave it on. The default is S.
38. [COLOR="SeaGreen"]**networking**[/COLOR] - bring up network interfaces and config dns info during boot time by scaning /etc/network/interfaces file. Leave it on. The default is 0,6,S
39. [COLOR="SeaGreen"]**ntpdate**[/COLOR] - Sync time with the ubuntu time server. The default is S. QUOTED: "If you are dual-booting with Windows, it is probably a good idea to leave ntpdate on. Windows can only deal with the hardware clock set to local (not UTC) and Linux needs ntpdate to correct this, otherwise your clock will increase an hour everytime you boot into Linux from Windows." [color=blue]Thanks dejitarob for the update!![/color] I don't have dual boot, so I turned it off, but if you have multiple systems, suggestion is to turn it on.
40. [COLOR="Red"]**nvidia-kernel**[/COLOR] - I compiled the nvidia driver by myself, so its useless for me now. If you use the ubuntu nvidia driver from the restrict modules, just leave it on. The default is 1,2,3,4,5
41. [COLOR="SeaGreen"]**pcmcia**[/COLOR] - Active pcmcia device. I changed it to start on 0,6,S runlevel instead of on each 2,3,4,5 cause I feel its better to have hardware device ready at first. Also, useless if you are using desktop which doesn't have pcmcia card. So in that case, turn it off please. The default is 2,3,4,5
42. [COLOR="Red"]**portmap**[/COLOR] - daemon for managing services like nis, nfs, etc. If your laptop or desktop is a pure client, then turn it off. The default is 2,3,4,5,0,6,S
43. [COLOR="SeaGreen"]**powernowd**[/COLOR] - client to manage cpufreq. Mainly for laptops that support CPU speed stepping technology. Normally, you should leave it on if you are configuring a laptop, but for desktop, it might be useless. The default is 2,3,4,5
44. [COLOR="Red"]**ppp and ppp-dns**[/COLOR] - Useless to me. I don't have dial-up. The default for ppp is 2,3,4,5 and pppd-dns is S.
45. [COLOR="Red"]**readahead**[/COLOR] - [color=blue]**Thanks mr_pouit!**[/color] It seems readahead is a kind of "preloader". It loads at startup some libs on memory, so that some programs will start faster. But it increases startup time for about 3-4 seconds. So, you can keep it... or not . **update**, I tested and I just didn't feel difference loading programs. So I decided to turn it off. If you have a reason to keep it on, please do so. The default is S
46. [COLOR="SeaGreen"]**reboot**[/COLOR] - Don't change it. The default is 6
47. [COLOR="SeaGreen"]**resolvconf**[/COLOR] - Automatically configuring DNS info according to your network status. I left it on. The default is S.
48. [COLOR="Red"]**rmnologin**[/COLOR] - Remove nologin if it finds it. It wouldn't happen on my laptop, so I got rid of it. The default is 2,3,4,5
49. [COLOR="Red"]**rsync**[/COLOR] - rsync daemon. I don't use it on my laptop, so turned it off. The default is 2,3,4,5
50. [COLOR="SeaGreen"]**sendsigs**[/COLOR] - send signals during reboot or shutdown. Leave it as it is. The default is 0,6
51. [COLOR="SeaGreen"]**single**[/COLOR] - Active single user mode. Leave it as it is. The default is 1
52. [COLOR="SeaGreen"]**ssh**[/COLOR] - ssh daemon. I need this so I turned it on. The default is 2,3,4,5
53. [COLOR="SeaGreen"]**stop-bootlogd**[/COLOR] - stop bootlogd from 2,3,4,5 runlevel. Leave it as it is. The default is 2,3,4,5
54. [COLOR="Red"]**sudo**[/COLOR] - check sudo stauts. I don't see any good to run it everytime on a laptop or desktop client, so I turned it off. The default is S
55. [COLOR="SeaGreen"]**sysklogd**[/COLOR] - Leave it as it is. The default is 2,3,4,5
56. [COLOR="SeaGreen"]**udev and udev-mab**[/COLOR] - Userspace dev filesystem. Good stuff, I left them on. The defaults are all S runlevels.
57. [COLOR="SeaGreen"]**umountfs**[/COLOR] - Leave it as it is. The default is 0,6
58. [COLOR="SeaGreen"]**urandom**[/COLOR] - Random number generator. Might not useful but I left it on. The default is 0,6,S
59. [COLOR="Red"]**usplash**[/COLOR] - Well, if you really want to see the nice boot up screen, leave it as it is. I just turned it off anyway. If you want to turn it off, you also need to edit /boot/grub/menu. lst file to comment out the splashimage line and get rid of the splash kernel boot option. The default is 2,3,4,5
60. [COLOR="SeaGreen"]**vbesave**[/COLOR] - video card BIOS configuration tool. Its able to save your video card status. I left it on. The default is 2,3,4,5
61. [COLOR="SeaGreen"]**xorg-common**[/COLOR] - setup X server ICE socket. I moved it from starting at runlevel S to runlevel 2,3,4,5. Since I don't need this if I boot to single user mode. This way it wouldn't occupy time during the initial booting. The default is 2,3,4,5
============ My bootup services end up here============

============ Some services from others================
62. [COLOR="Red"]**adjtimex**[/COLOR] - This is a kernel hw clock time adjusting too. Normally, you shouldn't see this on your boot up list. In very rare case if you do see its on your boot up process, then there might be a reason why it is on, so better leave it that way. In my case, it is off.
63. [COLOR="Red"]**dirmngr**[/COLOR] - A certification lists management tool. Work with gnupg. You will have to see if you need it or not. In my case, I turned it off. Default runlevel 2,3,4,5
64. [COLOR="Red"]**hwtools**[/COLOR] - A tool to optimize irqs. Not sure what's the benefits of turning it on. In my case, I turned it off.
65. [COLOR="SeaGreen"]**libpam-devperm**[/COLOR] - A daemon to fix device files permissions after a system crash. Sounds pretty good, so I left it on.
66. [COLOR="Red"]**lm-sensors**[/COLOR] - If you matherboard has builtin some sensor chips, it might be helpful to see hw status via userspace. I ran it and it said "No sensors found", so I turned it off.
67. [COLOR="SeaGreen"]**screen-cleanup**[/COLOR]  - A script to cleanup the boot up screen. Well, turn on or off is up to you. In my case, I left it on. The default is S
68. [COLOR="Red"]**xinetd**[/COLOR] - A inetd super daemon to manage other damons. In my system, the xinetd is managing chargen, daytime, echo and time (find them from /etc/xinetd.d dir), I care none of them, so I turned it off. If you do have some important services configured under xinetd, then leave it on.

III. Alter the /etc/inittab file
```
vi /etc/inittab
```then comment out tty4,tty5, and tty6. Just leave tty1, tty2, and tty3. Three vts should be enough for a laptop or desktop user. Save the file.

IV. Ok, now, we can reboot our box and see how it goes. From what I've tested, before I got tons of services stopped, the whole process is about 85 secs to 90 secs to boot to console. (At that time, I also has samba and nfs services turned on which I shouldn't. Apparently, I turned them off too). After this change, the whole boot up process took about 50 secs. I have a P4M 1.8G CPU laptop. Some of the high-end desktops or laptops should take even less time.

[COLOR="Red"]****UPDATE**: speed up/clean system reboot or shutdown process.**[/COLOR]
1. start sysv-rc-conf by issuing:```
sudo sysv-rc-conf
```
2. ok, open your eyes and look very carefully for those [color=red]SERVICES THAT DO NOT HAVE A "X" ON _ANY_ RUNLEVELS[/color] (Any runlevel means 1,2,3,4,5,6, and S), write them down one by one. Don't make mistakes here. Double check after you've done. [color=blue]Thanks ice60 for wording recommendation![/color]
3. quit sysv-rc-conf.
4. ```
cd /etc/rc0.d
``` - This is for the system shutdown process.
5. ok, now, ```
 ls K*
``` will list all links starting from UPPERCASE letter "K". Compare with your list, change each of the filename containing the service name in your list to start from a lowercase "k". For example, in your list, you have ppp service (which means ppp is turned off at all runlevels), then you can do like: ```
sudo mv K00ppp k00ppp
```. You just change the UPPERCASE K to lowercase k, keep the rest the same. Do this on all of the services in your list.
6. ```
cd ../rc6.d
``` - This is for the system reboot process.
7. ok, you should see similar things here too. So do the same thing here as you did on rc0.d.
8. Now, you reboot and shutdown process should be cleaned up and faster.

The explanation for what you did is pretty simple. The /etc/rc and /etc/rcS scripts run start on each link on each runlevel by scaning if it is starting with a UPPERCASE "S" and run stop on each by scaning if it is starting with a UPPERCASE "K". So for reboot and shutdown runlevels, the most thing we care is the "K" links cause for those services not running on all runlevels, its just not needed to stop them. They are not runing at all.  If some day you want to turn some of the services back on, just change the lowercase "k" to UPPERCASE "K". That's all.

Anyway, it is not intend to work on servers, but I did try on one of my servers has 2.7G P4 and 1.5G mem. It brought the boot process down to 31 secs. I calc'ed it with my watch. Besides, this is with my ftp server and nfs server started on boot time.

[COLOR="Red"]****Note****[/COLOR]
For all of those that having HAL failure problem, try this:
1. change acpi-support from S to 2,3,4,5
2. change acpid from S to 2,3,4,5
3. change dbus from S to 2,3,4,5
4. Reboot. Go to the console and do ```
ps -aef|grep hald
```. If hald service is up, then your dbus subsystem is running fine now. Try it.

[color=blue]**Great comments added by bodhi.zazen. Thanks!!**[/color]
First we should make sure we are left with a bootable system and have backups.

Since we are changing our boot process:

Step 1- Make a bootable GRUB floppy.

[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

Step 2- Backup
Is there any need to back up more then menu.1st, /etc/init.d, /etc/rcS.d, and /etc/rc*.c ( *= 0,1,2,3,4,5,6)?
mkdir /~/bakup.files
sudo cp -P /etc/init.d /~/backup.files
sudo cp -P /boot/grub/menu.1st /~/backup.files
sudo cp -P /etc/rc*.d /~/backup.files
Although a backup of /etc is nice, is it not overkill for this exercise?

Setp 3- Know you Ubuntu Root device (hda1, hdb1, hda2,) and kernel (the numbers in "vmlinuz").
Location of kernel is /boot

Step 4- Modify runlevels.
DO NOT MODIFY DEFAULT RUN LEVELS 0,1, OR 6
MODIFY ONLY 1 RUN LEVEL AT A TIME
RUN LEVEL "S" IS RUN AT EACH RUN LEVEL PRIOR TO OTHERS
ie as system boots (at default) the scritps in rcS.d are run first, then rc2.d

Therefore, if you disable a script in "S", enable the script in runlevel 2
This should guarantee your system will remain bootable to the default run level (2)

In Ubuntu the default run level is 2
Modify only 1 test run level at a time. Choose a custom run level (I will use 3 for the rest of this post, you can use 3,4, or 5).
After modifying the runlevel test without re-booting
sudo init 3
This will change to run level 3
Now check your system.
Problems? Return to default run level and re-configure run level 3
sudo init 2
No problem -> Boot from floppy
No problem, boot from floppy.
When booting (from diskette) to the default run level, the "kernel" line looks like:
kernel=/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
In menu.1st this looks like this:
kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
To boot to run 3 (from GRUB diskette), add a "3" at the end of the line
kernel=/boot/vmlinuz.... root=/dev/..... ro quiet splash 3
Note: the number 3 was added at the end (without quotes)
time boot process.
If OK boot again from floppy (to default run level)
kernel=/boot/vmlinuz..... root=/dev/....
Note: no number 3 at the end of this line
time boot process
This is the default boot and you can measure any time savings.
booting from a floppy to compair apples to apples
If OK you can now change the default run level (or not)
There is more then 1 way to do this
My preferance is to leave the default runlevel unmodified
This leaves the default boot process as a future referance
Change the default boot level
sudo nano /boot/grub/menu.1st
add init=3 to end of line

kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash 3

Or create 2 Ubuntu titles, one for each run level.

OR

Edit /etc/inittab

Step 4- Modify shutdown scripts if desired.

This process should guide users through a logical process of modifying boot scripts without generating a non-bootable system. Backups were made "just in case" but really should not be needed.

Works great for Dapper.  However, they've changed some things in Edgy Eft.  Though quick to boot up it still holds the tty4, tty5, and tty6 open and I've yet to figure out where to turn them off in Edgy Eft.  However, the rest of your how to works for Edgy even :D

---

### Post by emarkay on 2006-10-15
Interesting. 

How up-to-date is the first post (have all the changes in the following 27 pages been edited in?)

Would it be possible to get this into a document or an actual HTML page for easy printing?

Thanks!

---

### Post by CoffeeAddict on 2006-10-18
Hello All,


I used this guide to speed up my boot process and mostly, it was fine.
The process is quite a bit quicker now. 

Unfortunately, my network card doesn't seem to get activated on startup 
anymore. If I start up network-admin and activate it, everything works fine, so it's not a huge deal, but it's still annoying. I don't really know what did this since I deactivated neither networking nor any kernel modules or pcmcia or anything. I did initally deactivated ppp and dns-clean, but I already tried reactivating it and that didn't help.

I only really deactivated bluetooth and raid support and cupsys and festival (a text-to-speech system).

Does anyone have an idea what could have caused this ( or how I can correct it, in any case) ?  :-k 


Thanks in advance,

CoffeeAddict

---

### Post by Malakia on 2006-10-20
Can somebody please help me.I followed the guide exactly but when it restarts its says Alert! /dev/hda1 doesn't exist . Dropping to shell, where it goes into an ash shell. I can boot with recovery option but not reguarly. I have looked everywhere else and haven't found a solution.

---

### Post by Malakia on 2006-10-20
Whatever the problem was the kink got worked out. Thanks anyway.

---

### Post by learning on 2006-10-27
This made a big difference for me in edgy.  Thank you!

---

### Post by domino on 2006-10-28
I've only managed shave off ~3 seconds when trying this on Edgy. From 35 to 32. I don't think it make much difference trying this in Edgy unless Edgy has a totally different way to reducing boot time. I would like to get down to 15-20 seconds on a fresh install :).

---

### Post by jamescbjr on 2006-10-29
Can someone help me please, my pc stalls at boot up because I get disconnected from the systems message bus. I can not find the cause.](*,)    My boot chart. Might help in diagnostic. Thanks In advance for any assistance.

daemon.log

Oct 29 09:07:56 -panama hcid[4577]: Got disconnected from the system message bus

messages

Oct 29 09:01:25 -panama kernel: [17179597.608000] IPv6 over IPv4 tunneling driver
Oct 29 09:07:56 -panama exiting on signal 15
Oct 29 09:09:44 -panama syslogd 1.4.1#18ubuntu6: restart.

---

### Post by paul6 on 2006-10-31
Does this guide still work with Edgy? Now that (I think) they have replaced Sysvinit with Upstart?

---

### Post by Azerthoth on 2006-11-02
Boot process is changed and the documentation for the changes is horrid. There is a README in the /etc/init.d/ section or somewhere further down that branch that referance a document on the debian website. Problem is it doesnt give any info for what init is calling on. No clue what they changed initab to ](*,)

---

### Post by TFrog on 2006-11-07
I haven't seen any info on the Edgy boot process either.  Bits and pieces of this "How To" do work but it's very little.  Thus my request that this be updated.

---

### Post by elettronicha on 2006-11-07
Indeed this how-to is unsuitable to Edgy, since Edgy replaced the init system with 'upstart' that's faster than the old init.

---

### Post by Sokraates on 2006-11-07
Upstart in this early stage still relies on init-scripts. So this how-to still works (at least it does for me).

What errors or problems do you see when applying this how-to to edgy?

---

### Post by morzzzan on 2006-11-08
Helo! Your site niconux.free.fr is cool. See my bookmarks 
 
 
[Advanced Genome Mountain Rocky](http://advanced-genome-mountain-rocky.0catch.com)  
[Agent High Street Travel](http://agenthighstreettravel.0moola.com)  
[Tabernacle Church](http://besthost2.4000webs.com/tabernacle-church/index.html)  
[Online Accounting Degree](http://crazyhost.topfreewebhosting.com/online-accounting-degree/index.html)  
[Com Discount Hotel](http://betnews.digitalzones.com/com-discount-hotel/index.html)  
[4000 Juicer Omega](http://4000-juicer-omega.0catch.com)  
[Air In Levitate Secret](http://air-in-levitate-secret.125mb.com)  
[Upholstery Cleaning San Francisco](http://betnews.digitalzones.com/upholstery-cleaning-san-francisco/index.html)  
[Baby Carriage Shower Favor](http://besthost3.4000webs.com/baby-carriage-shower-favor/index.html)  
[Mountain Bike Shorts](http://crewcrew.somee.com/mountain-bike-shorts/index.html)  
[Account Half Robert Temps](http://account-half-robert-temps.0catch.com)  
[Money Filling Survey](http://crazyhost.topfreewebhosting.com/money-filling-survey/index.html)  
[2106 Federal Form Tax](http://2106-federal-form-tax.0moola.com)  
[6 Jumbo Month Mortgage](http://6-jumbo-month-mortgage.1sweethost.com)  
[Aids Hearing Sale Toronto](http://aids-hearing-sale-toronto.1sweethost.com)  
[East Wind Catering](http://aria.555mb.net/east-wind-catering/index.html)  
[2006 Destination Globals Imagination](http://2006-destination-globals-imagination.0catch.com)  
[Office Massage Chair](http://crewcrew.somee.com/office-massage-chair/index.html)  
[Advice Business Legal Small](http://advice-business-legal-small.1sweethost.com)  
[Advantage Bypass Genuine Window](http://advantage-bypass-genuine-window.150m.com)  
[Business Cleaning Office Own Start](http://crazyhost.topfreewebhosting.com/business-cleaning-office-own-start/index.html)  
[In Law Lemon](http://betnews.digitalzones.com/in-law-lemon/index.html)  
[Air Conditioning Packaged Unit](http://crazyhost.topfreewebhosting.com/air-conditioning-packaged-unit/index.html)  
[Phone Over Internet](http://aria.555mb.net/phone-over-internet/index.html) 
 
Buy : )

---

### Post by K.Mandla on 2006-11-12
> **paul6 said:**
> Does this guide still work with Edgy? Now that (I think) they have replaced Sysvinit with Upstart?
Yes. The services are rearranged into /etc/rc0.d/, /etc/rc1.d/, etc., with much of inittab arrayed into /etc/event.d/. You just need to track down the service and adjust it as you normally would.

---

### Post by civilian on 2006-11-18
Works great for me, sped up boot time by a good 10 seconds. thanks a lot!.

---

### Post by i3dmaster on 2006-11-18
The first thread has been updated and indicated that this customization is mainly for version before 6.10.

---

### Post by adka on 2006-12-02
thanks alot for the guide.  Interesting to learn about the boot proccess

---

### Post by haxer on 2006-12-02
Why even bother to boot it up? How many times are you rebooting? How often? I reboot werry often about 1/week at the most so why do i need to speed it up 10sec? what will i do in 10sec? Is there anything that you could do in 10sec  wile waiting for you computer? Look at the tv for 10sec get an icecrimb paper  opened ;)

---

### Post by Sokraates on 2006-12-04
> **haxer said:**
> Why even bother to boot it up? How many times are you rebooting? How often? I reboot werry often about 1/week at the most so why do i need to speed it up 10sec? what will i do in 10sec? Is there anything that you could do in 10sec  wile waiting for you computer? Look at the tv for 10sec get an icecrimb paper  opened ;)

I think some 10 or 20 pages ago we already had this discussion. Bottom line: There are a lot of people who reboot daily or even more often for various reasons, including saving power, being away from home most of the day etc.

Although now that you mention it, I should put the refrigerator next to my desktop-pc for easier access to icecream. Then I will revert all the changes I made to the boot-process so that I will have even more time to eat it. :D

But seriously, this How-to no longer feels as effective as before. Edgy already booted faster than Dapper and the optimizations did not gain me more than 2-3 seconds (I think from 29 to 27). Unfortunately I deleted my old bootcharts, but I think that I always saved about 10%-15% of the boot-time. The difference being, that vanilla Breezy took about 50 seconds to boot.

---

### Post by haxer on 2006-12-04
> **Sokraates said:**
> I think some 10 or 20 pages ago we already had this discussion. Bottom line: There are a lot of people who reboot daily or even more often for various reasons, including saving power, being away from home most of the day etc.

Although now that you mention it, I should put the refrigerator next to my desktop-pc for easier access to icecream. Then I will revert all the changes I made to the boot-process so that I will have even more time to eat it. :D

But seriously, this How-to no longer feels as effective as before. Edgy already booted faster than Dapper and the optimizations did not gain me more than 2-3 seconds (I think from 29 to 27). Unfortunately I deleted my old bootcharts, but I think that I always saved about 10%-15% of the boot-time. The difference being, that vanilla Breezy took about 50 seconds to boot.


Sorry didnt know guess i was to late sorry.. erarum humunum est!

---

### Post by golem3 on 2006-12-25
worked for me. thanks. it seems that Ubuntu Edgy does not give a lot of the useless options on a clean install...I only had a few to turn off, such as Bluetooth.

---

### Post by ghostwriter on 2007-01-03
> **haxer said:**
> Sorry didnt know guess i was to late sorry.. erarum humunum est!

it's *errare humanum est* ;)

---

### Post by lotacus on 2007-01-15
Does this  honestly work? noticeably? I would LOVe an instant on system.

But i'm not complaining, it boots faster than Windows. Even shuts down faster. There are problems with hybernating and suspend, but that's not for this thread and i'm sure it's been discussed before.

To one of the posters who posted about why ppl would need to reboot, several cases for reboot as someone stated. Also alot of people have multiboot systems as myself, since there are things I do that requires Windows. .. Like play BF2142! LOL.

---

### Post by i3dmaster on 2007-01-15
Yes, with the replacement of the old sysinit to upstart, it fundamentally addressed the majority of the long boot time issue. This thread wasn't originally prepared for upstart driven systems like 6.10+, so if you are 6.10 or +, then please refer to upstart related threads.

---

### Post by dothedorky on 2007-01-25
I just wanted to say thank you. I tried this today and entire boot time took 24 seconds (and i left gdm on)

I also have a few services that were not on your or other's lists (i left them on because i wasn't sure)... I was wondering if you could help me figure out if i need them or not (cause im greedy, and a computer can never be too fast!) 

here are the programs and the run levels they are on. (im a desktop user, with 6.06LTS) I ask about laptop-mode because i run a desktop computer, that i turn off every night...)

```
brltty    s
lm-sensors    s
festival    s
laptop-mode    2,3,4,5
loopback    s
mtab    s
pcmciautil$    s
rc.local    2,3,4,5
rsync    2,3,4,5
screen    s
stop-read$    2
umountroot    0,6
x11-common    s
```

---

### Post by berndwalterh on 2007-02-08
Hi, 
 
it seems that you have an error in your login feature of your forum. Everytimes if I want to stay logged in I´ll be automatically logged out within 1 minute. 
I´ve already checked my firefox settings and they are all okay. 
 
Do other members have the same problem? 
_________________ 
[homepage 1](http://www.bproperties.info) 
[homepage 2](http://www.webentrance.info)

---

### Post by lasder on 2007-02-11
Fantastic job i3dmaster, it's a clear and good explained how-to :grin:

---

### Post by dothedorky on 2007-02-13
*bumped*

still have a few programs i dont know if i need (or even what they are specifically for)

any help would be greatly appreciated.

---

### Post by kaczmarek on 2007-03-17
Hi,

I was just wondering, why do some services need to be turned on multiple runlevels, eg. 2,3,4 and 5? What does this mean? Does that mean that these are re-run on each new runlevel? If that's true, why? A bit confused... :confused: :) 

Thanks!

---

### Post by dannyboy79 on 2007-03-19
each run level is different so you would want the service to be available in each run level wouldn't you? here is an explaination ot run levels. [http://www.networkclue.com/os/Linux/run-levels.aspx](http://www.networkclue.com/os/Linux/run-levels.aspx)

---

### Post by Bill_Gates on 2007-03-23
Thanks for this guide.

---

### Post by shawnrgr on 2007-05-07
Is this tip safe for Feisty?

---

### Post by dannyboy79 on 2007-05-07
it's safe for any linux version! it merely stops processes that you don't want to start at bootup and don't need.

---

### Post by housekid on 2007-05-28
Thank you, thank you.
I have learned a lot, your the best!

---

### Post by linfidel on 2007-06-20
Nice article, and lots of nice links.  This is one of the first things I want to learn about in linux - how to control the startup, and what happens when, step by step.

Thanks to all the contributors.

---

### Post by macron1 on 2007-06-29
wow thanks man. this dramatically increased my bootup speed on a compaq presario v6000. just switched the ppp, bluetooth and the "readahead"  (cant remember exact name) ones off. worked a treat.

---

### Post by st33med on 2007-08-21
A program to disable: brltty.

Basically, it is for braille output devices in tty. If you're not blind, then disable this.

---

### Post by Yes on 2007-08-30
I have three questions: 1) I have a bunch of duplicate processes, except that one of the duplicates ends with a '$'.  Is it safe to delete processes that end in a '$'?  2) I have one process, 'nvidia-ke$'.  I don't believe I have any nvidia hardware, so does that mean that it would be safe to delete that process?  Or is there some other reason that it's running?  3) I don't have a file called /etc/inittab .  I assume that this is because I'm using Feisty, and the file has since changed names.  If this is the case, is there still a file in Feisty where I can disable tty4, 5, and 6?

Thank's for the great guide!

---

### Post by Rui Pais on 2007-08-31
> **Yes said:**
> I have three questions: 1) I have a bunch of duplicate processes, except that one of the duplicates ends with a '$'.  Is it safe to delete processes that end in a '$'?  2) I have one process, 'nvidia-ke$'.  I don't believe I have any nvidia hardware, so does that mean that it would be safe to delete that process?  Or is there some other reason that it's running?  3) I don't have a file called /etc/inittab .  I assume that this is because I'm using Feisty, and the file has since changed names.  If this is the case, is there still a file in Feisty where I can disable tty4, 5, and 6?

Thank's for the great guide!

hi,

for 1) 
the "repetead" ended '$' are just contractions of names that sysv-rc.conf do on long ones. 
Be careful they are not repeated processes, but diferent ones.
As an example powernowd and powernowd$ are not the same thing. The second is powernowd.early, a name too long. 
You can see the processes of each level by run (here for level 2):
```
ls /etc/rc2.d/
```

2) Never understamd that nvidia entry. It's not even useful for nvidia users (driver is loaded by xorg,conf), so even as a mvidia user i always turn that off.

3) The instructions no longer apply for feisty. Try [my suggestion here]("http://ubuntuforums.org/showpost.php?p=2843862&postcount=3"). You may want to read the [full thread]("http://ubuntuforums.org/showthread.php?p=2843708#post2843708") for others comments and alternatives.

---

### Post by dannyboy79 on 2007-08-31
> **Rui Pais said:**
> hi,

for 1) 
the "repetead" ended '$' are just contractions of names that sysv-rc.conf do on long ones. 
Be careful they are not repeated processes, but diferent ones.
As an example powernowd and powernowd$ are not the same thing. The second is powernowd.early, a name too long. 
You can see the processes of each level by run (here for level 2):
```
ls /etc/rc2.d/
```

2) Never understamd that nvidia entry. It's not even useful for nvidia users (driver is loaded by xorg,conf), so even as a mvidia user i always turn that off.

3) The instructions no longer apply for feisty. Try [my suggestion here]("http://ubuntuforums.org/showpost.php?p=2843862&postcount=3"). You may want to read the [full thread]("http://ubuntuforums.org/showpost.php?p=2843862") for others comments and alternatives.

your link merely talks about a getty, are you saying that I can just move any process to a different folder and it won't run? ALso, whne you tried to link to the full thread, it's not the full thread, it's the same little 1 post thread. I am interested in this because I run feisty on an ancient laptop, and I am looking to get rid of ton's of stuff I don't need running which is slowing it down almost intolerable. Please help.

---

### Post by Rui Pais on 2007-08-31
> **dannyboy79 said:**
> your link merely talks about a getty, are you saying that I can just move any process to a different folder and it won't run? 
hi,
my suggestion was in sequence of **Yes** question, to prevent ttys from start. But yes, sysv-rc-conf it's just an frontend to do exactly that. 
All boot "process" are just links under /etc/rc<N>.d/ to files under /etc/init.d/files. With a rename of SXX or KYY, with S fro start and K for kill amd XX, YY a number to indicate process order. 
A smart trick.
  
> **dannyboy79 said:**
> ALso, whne you tried to link to the full thread, it's not the full thread, it's the same little 1 post thread. I am interested in this because I run feisty on an ancient laptop, and I am looking to get rid of ton's of stuff I don't need running which is slowing it down almost intolerable. Please help.

thanks for point me that. I just copied links from browser... something must failled. I will correct my post.

---

### Post by tech9 on 2007-09-05
yes, thanks for the post... it does help to understand what all these processes are doing:guitar:

---

### Post by nowshining on 2007-09-09
thank you this has not only sped up the operating systems bootup process - far as I went it also sped up the loading of the Desktop and applications.. :) ty..



oh and it fixed many issues I was having with my connectiond to the net now pages load quicker.. :)

---

### Post by Salpiche on 2007-10-26
is there an update or guide with the other services found on Feisty and Gusty that are not mention here?

---

### Post by TuxCrafter on 2007-10-26
Hello all, i am searching for a updated list for gusty. I would like a list with only absolute necessary services to run ubuntu gusty safe with only a xserver. So without internet gdm alsa etcetera. It would safe me a lot of time else I have to go through all those services myself.

Cheers

---

### Post by nowshining on 2007-10-26
TuxCrafter GDM is what u see when u log in - :)  u know that Sign on screen.

---

### Post by TuxCrafter on 2007-10-27
> **nowshining said:**
> TuxCrafter GDM is what u see when u log in - :)  u know that Sign on screen.

Sorry, I am not getting your point:-D. I startupuntil tty terminal. Then I login and execute startx (autostart)
I don't use GDM.

I need to be sure witch services are critical to create a stable system.

---

### Post by cherry316316 on 2007-10-28
when I got Hal problem, I tried doing by ur method, initially
all the settings were by default on 2,3,4 N 5.
so i didnt change anything , but it didnt work,
so I change those setting to "S" 
and it worked smoothly , 

By chaning to S, I guess they start before Hal starts,
hence no problem I guess

---

### Post by Ux64 on 2007-11-19
Great list about services.

But after a lot of tuning, I got a strange problem.

Now when ever I press alt+ctrl+del or open "quit" menu, it takes about one minute to open up. I guess it's related to services that I have dropped out.

Any clues anyone? - **Thank you!**

---

### Post by 213374U on 2007-11-20
subscribed for use at home

---

### Post by NineseveN on 2007-11-21
So, what is considered a decent or fast boot time anyway? My box runs 1 minute and 15 seconds from post to desktop, including selecting Ubuntu in GRUB and putting my username/password in. Is that good, bad, somewhere in between?

---

### Post by Ux64 on 2007-11-26
My Ubuntu boot time is total of 16 seconds.

---

### Post by TuxCrafter on 2007-11-26
> **Ux64 said:**
> My Ubuntu boot time is total of 16 seconds.

Nice, mine boots ups in 30 seconds with a VIA C7 1.2GHz with complete desktop with panels (xfce), inclusive cups and alsa and network.

computer is a EN12000E

---

### Post by jwmislan on 2007-12-11
Shutting off unneeded processes not only lessens boot time, it speeds up a running system.
Since unneeded processes were removed, there are more processor cycles available for 
all the rest of the processes that are needed, thereby improving overall efficiency.

JWM

---

### Post by omega_user on 2007-12-15
thank u very much.  I'm still having a problem though that seems to be an elusive one for some people. The gnome-settings-manager causes the after login to the point where u can click on stuff last 10 seconds or more.  very irritating, anyone know what's up?

---

### Post by Pelonchas on 2007-12-16
I have some others , but i have **bootclean** too.
Do NOT enable **bootclean**, it mess up gdm startup, well bootclean it's not mean to run on boot.

---

### Post by BLTicklemonster on 2008-01-26
Strangest thing just occured....

> **i3dmaster said:**
> 
[COLOR="Red"]****Note****[/COLOR]
For all of those that having HAL failure problem, try this:
1. change acpi-support from S to 2,3,4,5
2. change acpid from S to 2,3,4,5
3. change dbus from S to 2,3,4,5
4. Reboot. Go to the console and do ```
ps -aef|grep hald
```. If hald service is up, then your dbus subsystem is running fine now. Try it.


I was having "Internal Error: Failed to initiate HAL" problems for the longest, but my settings were already 2,3,4,5 for the above mentioned entries.

So- being the experimenter that I am, I set all mine to S and rebooted, and voila, no more HAL problems.

Running Gutsy.

Hope this helps someone out there who is at wit's end like I was.

:)

---

### Post by chris4585 on 2008-01-27
*then comment out tty4,tty5, and tty6. Just leave tty1, tty2, and tty3. Three vts should be enough for a laptop or desktop user. Save the file.*

i didnt have the inittab file in /etc/ do i need to create it or install something?

---

### Post by dannyboy79 on 2008-01-28
they are located in /etc/event.d/. you can just remove the tty's that you don't want to run.

---

### Post by chris4585 on 2008-01-28
ah that makes sense, another thing i removed usplash from the sysv-rc-conf and when i booted up usploash appeared, what did i do wrong?

---

### Post by dannyboy79 on 2008-01-28
i think usplash is controlled via grub boot lines. check out /boot/grub.menu.lst file and remove the word "splash" from the end of your boot lines. that's just what I think and may not be totally correct. you can always put that splash on the end of your boot line back if that's not it.

---

### Post by chris4585 on 2008-01-28
this makes sense thanks, if i recall this was mentioned in the guide, i should of reread it, thanks

---

### Post by raoulteeuwen on 2008-02-02
I have an Acer Travelmate 4000 where i installed Ubuntu 7.10 Gutsy Gibbon on in a dual boot config with XP. I have tried several other Linux-flavors before (Xandros, Fedora, Open Suse etc), and Ubuntu is the slowest to boot! I did not tweak anything and i guess i have one of the elderly gibbons out there: takes more than 3 and a half minutes! I love open source, but this means i mostly boot into XP as it boots quicker... I guess i'm going back to some other Linux flavor and wipe Ubuntu from my HDD...

---

### Post by TuxCrafter on 2008-02-02
> **raoulteeuwen said:**
> I have an Acer Travelmate 4000 where i installed Ubuntu 7.10 Gutsy Gibbon on in a dual boot config with XP. I have tried several other Linux-flavors before (Xandros, Fedora, Open Suse etc), and Ubuntu is the slowest to boot! I did not tweak anything and i guess i have one of the elderly gibbons out there: takes more than 3 and a half minutes! I love open source, but this means i mostly boot into XP as it boots quicker... I guess i'm going back to some other Linux flavor and wipe Ubuntu from my HDD...

Ubuntu has the philosophy to work just get it working, this includes having a lot of system services running and starting during boot up. I agree this can take very long. Fortunately you can remove all those processes if you do not need them. You can also try fluxubuntu that will not use all those startup services by default and will be much faster.

---

### Post by thechilipepper0 on 2008-02-21
> **raoulteeuwen said:**
> I have an Acer Travelmate 4000 where i installed Ubuntu 7.10 Gutsy Gibbon on in a dual boot config with XP. I have tried several other Linux-flavors before (Xandros, Fedora, Open Suse etc), and Ubuntu is the slowest to boot! I did not tweak anything and i guess i have one of the elderly gibbons out there: takes more than 3 and a half minutes! I love open source, but this means i mostly boot into XP as it boots quicker... I guess i'm going back to some other Linux flavor and wipe Ubuntu from my HDD...

i duno if i got you in time, but don't give up. my system used to take 3 1/2 minutes to boot up also. and then i ran across this [http://ubuntuforums.org/showthread.php?t=580903&highlight=long+startup]("http://ubuntuforums.org/showthread.php?t=580903&highlight=long+startup"). it was the easiest two line edit ever, and i shaved 2 minutes off my boot. that is amazing to me.

anyway good luck.

---

### Post by raoulteeuwen on 2008-02-25
Thanks thechilipepper0! That did shave off about 1 minute or more (just did it, timed it while watching tv (as i got used to taken it up a lot of time)). Did someone close to the developers tell them this? This should be a default option/behaviour since it makes such a difference?

Since i now see what Ubuntu is doing, i find every boot the DOS-partition is checked, taking about 45 seconds. Is this really necessary? I read somewhere it is, but since i'm dualbooting, i guess the FAT-partition gets checked often enough? Anybody?

I will give Ubuntu another try!

---

### Post by raoulteeuwen on 2008-02-25
Found [http://ubuntuforums.org/showthread.php?t=470726](http://ubuntuforums.org/showthread.php?t=470726) ... Now my boot time from grub selection-screen till logon screen is about 45 seconds :-)!

---

### Post by puccaso on 2008-03-02
is there anyway of getting X/gdm/xdm to start up straight after boot

something like rhgb on fedora... 

or anything... even a x-terminal!!!

---

### Post by Jason2gs on 2008-03-03
Thank you :)

Where I failed was not benchmarking the original startup time. The current is three minutes and six seconds. How does mine rank with some your guys' boot times?

---

### Post by baracuda68 on 2008-03-12
>  III. Alter the /etc/inittab file
 	Code:
 	vi /etc/inittab 
then comment out tty4,tty5, and tty6. Just leave tty1, tty2, and tty3. Three vts should be enough for a laptop or desktop user. Save the file.

On my Gutsy setup, I dont have "inittab"
Where else can I remove a couple of tty's?
getty uses 6 of them right now, xorg uses 1...

:twisted:

---

### Post by Rui Pais on 2008-03-12
> **baracuda68 said:**
> On my Gutsy setup, I dont have "inittab"
Where else can I remove a couple of tty's?
getty uses 6 of them right now, xorg uses 1...

:twisted:

Gutsy don't use that method. 
i had previously suggest:
```
sudo mv /etc/event.d/tty6 /etc/event.d/_ty6
sudo mv /etc/event.d/tty5 /etc/event.d/_ty5
...
```
but **roderick** on post [#350]("http://ubuntuforums.org/showpost.php?p=4637895&postcount=350") suggested a better way.

Please see bellow.

---

### Post by baracuda68 on 2008-03-12
> **Rui Pais said:**
> Gutsy don't use that method. Do:
```
sudo mv /etc/event.d/tty6 /etc/event.d/_ty6
sudo mv /etc/event.d/tty5 /etc/event.d/_ty5
...
```for any tty you want to remove.
Thanks Rui Pais.
I tried your code, and it did change the filenames of the tty's that I wanted removed, but after a reboot, they still show up running, in " top "  See screenshot. Any other ideas?
[ATTACH]62425[/ATTACH]

---

### Post by Rui Pais on 2008-03-13
> **baracuda68 said:**
> Thanks Rui Pais.
I tried your code, and it did change the filenames of the tty's that I wanted removed, but after a reboot, they still show up running, in " top "  See screenshot. Any other ideas?
[ATTACH]62425[/ATTACH]

Ooops, sorry. A rename it's not enough. They must be removed from event.d... try:
```
sudo mv /etc/event.d/*ty6 /etc/
sudo mv /etc/event.d/*ty5 /etc/
...
```

That should do the trick.

---

### Post by baracuda68 on 2008-03-13
> **Rui Pais said:**
> Ooops, sorry. A rename it's not enough. They must be removed from event.d... try:
```
sudo mv /etc/event.d/*ty6 /etc/
sudo mv /etc/event.d/*ty5 /etc/
...
```That should do the trick.
OK.
What am I doing wrong?
I copy/paste the code into the console,for tty6,5,and 4,and check the /etc/event.d directory( in Konqueror) and they are gone!
But after a ctrl+alt+backspace, I check with "top"and, guess what? Still loading!! (see screenshot 2)

Now what?...      [ATTACH]62451[/ATTACH]

---

### Post by baracuda68 on 2008-03-13
Nevermind my last post...
I did a clean reboot and it is just fine! They are gone!

Thanks!

---

### Post by Rui Pais on 2008-03-13
> **baracuda68 said:**
> OK.
What am I doing wrong?
I copy/paste the code into the console,for tty6,5,and 4,and check the /etc/event.d directory( in Konqueror) and they are gone!
But after a ctrl+alt+backspace, I check with "top"and, guess what? Still loading!! (see screenshot 2)

Now what?...      [ATTACH]62451[/ATTACH]

uhmm thats weird...
why a forced restart of the X server (graphical) would load the extra consoles? and even without event.d/tty*?...

sorry i don't know why. Maybe restart X have that behaviour by default...

Thats an unusual thing anyway, restarting X server. 
With a reboot the new consoles will be gone. It's just an issue that happen if you by some reason would need to force a restarts of X (not that those 3 extra consoles had any special load on a system anyway...)

edit: i read your second post only after i post this. Its ok then :)

---

### Post by roderick on 2008-04-02
> **Rui Pais said:**
> Gutsy don't use that method. Do:
```
sudo mv /etc/event.d/tty6 /etc/event.d/_ty6
sudo mv /etc/event.d/tty5 /etc/event.d/_ty5
...
```
for any tty you want to remove.


> **Rui Pais said:**
> Ooops, sorry. A rename it's not enough. They must be removed from event.d... try:
```

sudo mv /etc/event.d/*ty6 /etc/
sudo mv /etc/event.d/*ty5 /etc/

```


The init method used by Ubuntu is called Upstart. Please read this article for more information on Upstart: [http://www.linux.com/feature/125977](http://www.linux.com/feature/125977)

Renaming or moving files to random locations on the system is NOT a good practice and can cause problems (Upstart should have a proper recommended practice for enabling and disabling events and services).

Note the following from the bottom of that page:

```

....Ubuntu does not include an inittab file and, by default, the Upstart init daemon (using the rc-default task) boots the system to multiuser mode (runlevel 2, the default runlevel). If you want the system to boot to a different runlevel, create an inittab file.

```

So, if you do not have an inittab file, the Upstart system will perform some predetermined defaults.

Now, as for disabling the individual ttys - deleting will work, but may not be the best course of action. 

Instead, I would suggest editing the tty4/5/6 files and removing the line 

```

start on runlevel 2

```

If you do this, then the ttys can still be started on runlevel 3. You can change this runlevel default (read the article quoted above) with an entry in /etc/inittab. 

Also, if the Upstart package gets re-installed, new instances of the tty files could overwrite the ones you deleted (which is a possibility), so not deleting has a benefit as well.. 

Anyway, just my two cents.

---

### Post by Rui Pais on 2008-04-03
@roderick
Hi. Although i didn't had any problems (nor even deleted ttys come back after some update, a possibility that i was aware) yours suggestion it's definitely a much better approach.

Thanks for the correction.
Rui

---

### Post by jakupl on 2008-04-05
wauw thanks. :popcorn:

---

### Post by fonsi2099 on 2008-05-03
I'm using Hardy, does this way work for hardy too!

there are many contributions on this thread, can someone who understand the things do an explanation or a howto for Hardy? 

Many thanks:guitar:
I work on AMD 64bit

---

### Post by krevuru on 2008-05-06
Yes Please.
If the author can actually re-do his document for Hardy, it will very greatly appreciated.
I have been watching the UBUNTU 8.04 countdown since it was showing "112 days to go". And after installing UBUNTU 8.04 on all my machines and referring this to everyone in my family, I am finding it sort of slow in performance.
On doing 
        ps aux | more
I could not really understand much as to what was needed and what was not?
Luckily I came across your tutorial but then I was not sure if it would apply to Hardy as well.
A sincere note of thanks for the earlier post and another set in advance for its 8.04-version.

---

### Post by MedellinManDem on 2008-05-18
> **krevuru said:**
> Yes Please.
If the author can actually re-do his document for Hardy, it will very greatly appreciated.
I have been watching the UBUNTU 8.04 countdown since it was showing "112 days to go". And after installing UBUNTU 8.04 on all my machines and referring this to everyone in my family, I am finding it sort of slow in performance.
On doing 
        ps aux | more
I could not really understand much as to what was needed and what was not?
Luckily I came across your tutorial but then I was not sure if it would apply to Hardy as well.
A sincere note of thanks for the earlier post and another set in advance for its 8.04-version.

Co-signed.

---

### Post by Andre-D on 2008-05-22
Yes, please make a list for 8.04 as well, and collect all good tips in one place.

It's a pity, that a much smaller/leaner OS like Ubuntu/linux takes much longer time to boot up than a pile of bloatware (Windows)

---

### Post by jakupl on 2008-05-24
> **Andre-D said:**
> Yes, please make a list for 8.04 as well, and collect all good tips in one place.

It's a pity, that a much smaller/leaner OS like Ubuntu/linux takes much longer time to boot up than a pile of bloatware (Windows)

It doesn't. If it does, then something is wrong. It should never take over a minute. mine is 27 sec.

---

### Post by King Louie on 2008-05-24
I would also appreciate a summary of the speed up boot process suggestions for Hardy.

---

### Post by ForksHolder on 2008-07-08
Cool! :D

Thank you very much for the hard work.

---

### Post by Xgamer on 2008-07-31
Can I disable nvidia-kernel in boot process when I have Intel X3100 graphics? thx

---

### Post by unutbu on 2008-07-31
I looked at /etc/init.d/nvidia-kernel, and since it all has to do with nvidia cards, my (unexpert) guess is yes, you can safely remove it from your boot process. 

Moreover, if it for some reason you find booting without nvidia-kernel is a problem, you can re-insert it into the boot process by relinking 

/etc/init.d/nvidia-kernel to /etc/rc2.d/S20nividia-kernel:
```

sudo ln -sf /etc/init.d/nvidia-kernel /etc/rc2.d/S20nividia-kernel
```

---

### Post by funnylife_ma on 2008-08-20
Hi there,

Thank you for this great HowTo

Hicham

---

### Post by nbhat on 2008-08-31
Thanks for the Howto!

I am on Hardy managed stop the following

atd, bluetooth,cupsys, dns-clean, pppd-dns

---

### Post by taurusx5 on 2008-09-20
I got 2 crucial questions:

1) According to the guide on disabling services, how do I disable a service on ubuntu 8.04? What runlevel(s) do I need to uncheck?

2) Will the guide work on ubuntu 8.04?

.

---

### Post by jakupl on 2008-09-20
> **taurusx5 said:**
> 
2) Will the guide work on ubuntu 8.04?

.

Yes it will :)

---

### Post by taurusx5 on 2008-09-20
You know, it's remarkable how I keep asking the same question over and over again without an answer. It's either people on here are afraid to answer this question or they just simply don't know the answer. I'll ask it one more time, and hopefully, an intelligent and brave person will answer it:

1) According to the guide on disabling services, how do I disable a service on ubuntu 8.04? What runlevel(s) do I need to uncheck?

.

---

### Post by SkonesMickLoud on 2008-09-20
> **taurusx5 said:**
> You know, it's remarkable how I keep asking the same question over and over again without an answer. It's either people on here are afraid to answer this question or they just simply don't know the answer. I'll ask it one more time, and hopefully, an intelligent and brave person will answer it:

1) According to the guide on disabling services, how do I disable a service on ubuntu 8.04? What runlevel(s) do I need to uncheck?

.

It's right there in the OP:

> **i3dmaster said:**
> Throw a littel bit of runlevel knowledge here before we start messing them up.... All the boot processes are executed in sequence as following:
runlevel S: the first runlevel in boot process. /etc/init.d/rcS script will be invoked to start and all the processes underneath /etc/rcS.d will be executed.
runlevel 1: the single user mode. All processes underneath /etc/rc1.d will be executed.
runlevel 2,3,4,5: in debain system, the multi-user env, may not may not include GUI. The same, processes under each of the corresponding dirs will be run. **Note** this is different than RedHat, SuSE, and other RPM based systems.
runlevel 0: computer shutdown.
runlevel 6: computer reboot.

Do you have "sysv-rc-conf" installed?

---

### Post by taurusx5 on 2008-09-26
> **SkonesMickLoud said:**
> It's right there in the OP:



Do you have "sysv-rc-conf" installed?

Hi, SkonesMickLoud. Thanks for the response. And yes, I do have sysv-rc-conf installed. As I've mentioned in my posts, I have 8.04. Do you know of an updated guide on turning off services in 8.04? Thanks.

.

---

### Post by SkonesMickLoud on 2008-09-26
> **taurusx5 said:**
> Hi, SkonesMickLoud. Thanks for the response. And yes, I do have sysv-rc-conf installed. As I've mentioned in my posts, I have 8.04. Do you know of an updated guide on turning off services in 8.04? Thanks.

.

I've used the same guide in 8.04, and only ran into a few services that aren't mentioned in the guide.  If you come across something like this, and don't know what the service does, you should leave it at the default setting.  Most services can be googled, and you can make a determination from there.

---

### Post by uberdonkey5 on 2008-10-03
just like to thank all those who posted here - boot speed is very important to me and I have shaved over 25% off my boot time (30 secs to 22 secs), whilst still allowing wifi etc (got rid of boot screen, which means can actually see whats going on, so its a bonus). Not bad for a newbie.

Here are before and after






P.S. any way to get rid of the scan disk that occurs occasionally? Is it useful? Should I increase the number of times it requires before checking or get rid of it completely?

---

### Post by unutbu on 2008-10-03
If you are interested in booting faster, you may also be interested in jdong's guide on readahead profiling: [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263).

It doesn't work for everyone, but some report shaving 10 seconds off their boot time.

Regarding the disk scan that occurs occasionally: 
I think Ubuntu sets up the partitions to be checked (fsck'd) every 22 boots by default.
How often you wish to fsck is a judgement call -- I do not know of any evidence to guide us in choosing what is best. It is probably not good to shut it off entirely, however.

It is possible to change the frequency of the checks this way:
```

sudo tune2fs -i 1m /dev/sda3
```

This sets the interval between checks to 1 month instead of every 22 boots. You may need to change /dev/sda3 to the correct device name for your partition(s).
```

sudo tune2fs -c 50 /dev/sda3
```

This sets the fsck to occur every 50 boots.

Type 
```

man tune2fs
```

for more information.

---

### Post by uberdonkey5 on 2008-10-03
> **unutbu said:**
> ...
It doesn't work for everyone, but some report shaving 10 seconds off their boot time.

Regarding the disk scan that occurs occasionally: 
I think Ubuntu sets up the partitions to be checked (fsck'd) every 22 boots by default.
...

I'm not sure about the device name for my partition?! I know its listed at disk scan, but is there anyway to check? Infact, I added the gnome partition editor, and this seems odd, because I have dual boot, but it is only listing one partition (unallocated) at /dev/sda

i get this if I use sda3:

tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
Couldn't find valid filesystem superblock.


so I assume this is wrong, and this

tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sda
Couldn't find valid filesystem superblock.

when I use sda (never had a bad magic number before :)

thanks
ud5

---

### Post by uberdonkey5 on 2008-10-03
thanks unutbu! no need to answer, coincidently I rebooted (doing something else) and it did a scan, so I could see the disk was sda6

I've changed this. Its very useful, because I have a laptop, and use it for short periods frequently. Thus I was always pressing 'esc' on the scan disk anyway! Well, once a month seems more sensible for me, and with the splash screen gone I am forced to wait when it eventually does want to scan, which is probably better!

---

### Post by starscalling on 2008-10-28
very interesting... going to have to look at this closer ;)

---

### Post by HellMind on 2008-11-08
This thread was a total waste of my time.
I'm only looking for a simple guide just saying WTF every services does
A short description but complete so I can decide If I want to load it or not

It's incredible that isn't documented anywhere

---

### Post by cl0ckwork on 2008-11-08
> **HellMind said:**
> This thread was a total waste of my time.
I'm only looking for a simple guide just saying WTF every services does
A short description but complete so I can decide If I want to load it or not

It's incredible that isn't documented anywhere

wow. way to be a jerk. :mad:
just google the proscesses that you are unsure about.
obviously, a list of services **is not** going to be in a thread titled *HowTo: Speed up ubuntu*

there are lists out there, i know ive found them.

sorry for the rant and no links but its a thing you use once and dont need anymore. 
and honestly, this guide did a lot more than the proscess list did

there is some info out there about changing how things load using the rc*.d files in /etc/ but that may get a little complicated for you :D

---

### Post by SkonesMickLoud on 2008-11-08
> **HellMind said:**
> This thread was a total waste of my time.
I'm only looking for a simple guide just saying WTF every services does
A short description but complete so I can decide If I want to load it or not

It's incredible that isn't documented anywhere

Have you ever heard of a man page?

---

### Post by bluemm on 2008-11-26
thanks for the tips!

---

### Post by steveydoteu on 2008-11-27
> **HellMind said:**
> This thread was a total waste of my time.
I'm only looking for a simple guide just saying WTF every services does
A short description but complete so I can decide If I want to load it or not

It's incredible that isn't documented anywhere

> **SkonesMickLoud said:**
> Have you ever heard of a man page?

Or Google!

---

### Post by 133794m3r on 2008-11-29
Ok i followed your guide perfectly and it has disabled my auto login feature i had.. now it takes me 43 seconds to boot up instead of 38 so... thus it's actually increased the boot time by 5 seconds! and also i couldn't figure out how to remove that grub splash screen if i could remove that plus renable my autologin feature i could probably save a few seconds..

---

### Post by jakupl on 2008-11-29
> **133794m3r said:**
> Ok i followed your guide perfectly and it has disabled my auto login feature i had.. now it takes me 43 seconds to boot up instead of 38 so... thus it's actually increased the boot time by 5 seconds! and also i couldn't figure out how to remove that grub splash screen if i could remove that plus renable my autologin feature i could probably save a few seconds..

To remove the splash screen, do:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst
```

You will see a line like this near the bottom:
```

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a459dc22-9c50-4dad-8345-f46455524732
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a459dc22-9c50-4dad-8345-f46455524732 ro quiet splash 
```

I usually remove "ro quiet splash", but just removing "splash" will do.

---

### Post by klhtaar on 2009-03-16
First of all thanks for a very nice guide!
But I've found some questions I'd like to be answered. Could you please help me?
I haven't found any information if I can disable these services and what are they meant for:
> console-$
gdm
hal
halt
keyboard-$
killprocs
loopback
nullmailer
policykit
powernowd
powernowd$
procps
pulseaudio
rc.local
samba
screencl$
stopread$
udev-fini$
ufw
umountroot
winbind
wpa-ifupd$
x11-common
xserver-x$

Also I wonder if I can disable > hddtemp will it harm my laptop?

Can i disable these two if I'm using an advice with PROFILE boot from one of the howto guides? 
> readahead
readahead$

And last but not least despite the guide I have off this one > stopboot$ 
Should I enable it?

So, I hope this thread isn't dead and I'll get desired help here. Thanks in advance!

---

### Post by unutbu on 2009-03-16
Hi klhtaar, welcome to ubuntuforums.
I don't know the answer to all your questions, but here are a few:

Note: when running sysv-rc-conf and see a $ at the end of a service name, the full service name has been truncated. You can find the full service name by looking in /etc/init.d.

gdm -- If you use Ubuntu (as opposed to Kubuntu or Xubuntu), your login screen is gdm.
If you don't run this service then you are sent to a terminal (console) login prompt.
You probably don't want to disable this service.

hal -- When you plug in an external USB device (camera, mass storage, etc.), hal is the service which automounts the device. 
You probably don't want to disable this service.

killprocs -- this service is only run when you enter single user mode (runlevel 1)
You probably shouldn't change this.

loopback -- a quote from /etc/init.d/loopback: "brings up the loopback (127.0.0.1) network device so that DHCP and other such things will work" 
You probably don't want to disable this service.

policykit -- When you click System>Admin to alter system settings, the app you are running may use policykit to determine if it should let you, as a normal user, to change those settings. You do not want to disable this service.

powernowd -- this service allows you to control cpu speed. If you have no need to control the CPU scaling governor, you could disable this service.

procps -- allows you to configure certain kernel parameters at boottime. I'm not sure what would happen if you disabled this. Maybe nothing, but I'm not sure.

pulseaudio -- The current version of Ubuntu, Intrepid, uses pulseaudio as its sound server. It can do neat things like control the volume of multiple apps individually, while they all make sounds. If you disable it, I think individual apps should still be able to control the speakers, just not all at once.

rc.local -- If you like to add scripts to tell your machine to do certain things at boot time, this is a convenient service to have enabled. If you don't have any such need, you could disable this.
Even if you disable this, you would still be able to run scripts at boot time using the newer upstart system.

samba -- samba allows you to share files with Windows machines. You can disable this if you don't have this need.

screen-cleanup -- removes stale screen named pipes on bootup. I'm not entirely sure what happens if you disable this. Among other things, it removes a file called /var/run/screen. I imagine if you don't run this service, the /var/run/screen file may grow larger and larger... not good. 

readahead and readahead-desktop and stop-readahead -- don't disable these if you plan on booting with the profile boot option. The profile boot option is used (usually only once) to help configure the machine to boot faster. See [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263) for how this is done.

udev-finish -- This is part of the udev system. udev creates mount points for devices. When you plug in a USB flash drive for example, udev is involved. I don't think it is a good idea to disable this.

ufw -- starts the firewall. The default firewall does not block anything. I'm not sure, however, what would happen if you disable this service.

umountroot -- this script mounts the root filesystem read-only at shutdown or upon reboot. Not doing so can lead to filesystem corruption. Don't disable this.

x11-common -- sets up certain directories used by X11. If you use X, as most users do, as the underlying server for a graphical desktop environment, do not disable this. Without X, you would be running Linux from a text console.

xserver-xorg-input-wacom -- this is only needed if you have a wacom device (a wacom graphics tablet, for example). You can disable this one if you don't have a wacom device.

stop-bootlogd and stop-bootlogd-single -- by default neither of these services is run at any runlevel. Neither of these are useful unless you enable the bootlogd service.
bootlogd is useful if you want a record of the (error) messages your machine prints to the console during boot. See [http://wiki.debian.org/bootlogd](http://wiki.debian.org/bootlogd) and [http://www.digipedia.pl/man/bootlogd.8.html](http://www.digipedia.pl/man/bootlogd.8.html). You don't need this unless you are trying to debug some problem on your machine which happens at boot time.

Regarding "vi /etc/inittab": Ubuntu is migrating to a new startup system called "upstart".
Because of this, Ubuntu no longer ships with an /etc/inittab file. Nowadays, to disable tty4, tty5, tty6, you could change "start" to "stop" in /etc/event.d/tty4, /etc/event.d/tty5, and /etc/event.d/tty6.

---

### Post by klhtaar on 2009-03-16
**unutbu**, thanks lad!
Your information was very useful for me and now I also know where to read a description of service. Thanks to you!
Now I've completed this guide and going for a restart. Hope It'll be OK.

---

### Post by kurrupted on 2009-03-24
Hi guys,

My friend showed me this program a while back and i'd forgotten all about it.

I thought i'd give it a bash and see how things went.

i've easily shaved 10-15 seconds off my boot time so i'm really pleased and i'm sure i can get a few more if i actually investigate what some of the other programmes are...

Thanks a lot for all the help.

Jay.

---

### Post by VladNistor on 2009-03-28
Great How-to!

I took 17 seconds off my Jaunty Beta boot. As a note, disabling readahead increases my boot time by about 4 seconds for some reason. 

Grub-2-loginscreen is now 23.44 secs. I'll get ext4 on my system partition soon and that will probably cut it even more.


Thanks!

--Vlad

[AtheistBlog.org]("http://www.atheistblog.org")

---

### Post by Yashiro on 2009-03-30
Just something I felt the need to post since a Hardy system that's been rock solid since release recently developed a networking problem. 
I had used these tweaks a long time ago and run a --profile boot every few months.
All had been fine until a few days ago. After running a profile from the kernel line (which worked fine previously) 
caused the machine to randomly fail to get a DHCP address on boot.

I'd recently used the readahead tweak mentioned here.
[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)


Re-adding the --background switch to S01readahead fixed it completely. 
This issue is very timing specific and may not even appear on some machines and networks.

If you start init.d/networking a few milliseconds later, as S60, it works fine. 
Or you could run /etc/init.d/networking restart at a much later point, and again, it was fine.

So, if you have connectivity issues using anything but 'roaming mode' in Network Manager this is a possible reason why it fails. And something to bear in mind when you tweak your machine.

---

### Post by unutbu on 2009-03-30
Thanks for the info, Yashiro.
Where exactly is the --background switch added?

---

### Post by Yashiro on 2009-03-30
[Read the first post of this thread](http://ubuntuforums.org/showthread.php?t=254263). The switch exists bt default unless you alter it. So unless you've already performed that tweak before there's nothing to worry about.

---

### Post by unutbu on 2009-03-30
> **Yashiro said:**
> Read the first post of this thread.

Thanks Yashiro, I think you must be referring to this thread: [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

---

### Post by Yashiro on 2009-03-30
Yeah you are right, my error. I've linked to it in my previous posts to clarify.
I was reading both threads simultaneously I guess. :)

---

### Post by ashmew2 on 2009-04-15
Nice Thread! Keep up the good work. :D

---

### Post by chika.tambun on 2009-05-02
according to the super parent of this thread

$ sudo update-rc.d -f anacron apmd apparmor atd bluetooth cups dns-clean hotkey-setup kdm laptop-mode NetworkManager pppd-dns readahead readahead-desktop rmnologin rysnc samba ufw uml-utilities usplash remove

---

### Post by coldReactive on 2009-05-14
Most of the stuff listed here I do not have at all.

In fact, I don't even have a /etc/inittab file.

My boot time upon fresh install was about 30 seconds.

But now that I've installed a few things, it's at 35 seconds.

> 59. usplash - Well, if you really want to see the nice boot up screen, leave it as it is. I just turned it off anyway. If you want to turn it off, you also need to edit /boot/grub/menu. lst file to comment out the splashimage line and get rid of the splash kernel boot option. The default is 2,3,4,5

no splashimage entry in my menu.lst in 9.04

---

### Post by TFrog on 2009-06-17
I have used this and one other page to speed up boot time in Kubuntu since Edgy.  Though still applicable even today with Jaunty to a certain extent, it would be nice to see this updated to the newer versions of Ubuntu/Kubuntu.  With this and one other page, I've trimmed down my boot speed to just 23 seconds in Jaunty Jackalope.  If I weren't loading Virtualbox up at boot, I'm sure I'd see sub 20 seconds in boot.  Can't wait to see if Ubuntu is able to go for what they want in Karmic Koala.  That might even bring my boot time down on this old laptop to about 15 seconds though they are shooting for 10 seconds.

---

### Post by capoli on 2009-07-23
Hi,
This profile switch has just screwed up my booting. Instead of the slow, but reilable 33sec till login screen and 1 minute full boot time, the HDD waits about 1 minute at the very beginning. The light is on, but doing nothing. Now I have 2 minutes boot up :((
Can I undo somehow that profile stuff??


> **Yashiro said:**
> Just something I felt the need to post since a Hardy system that's been rock solid since release recently developed a networking problem. 
I had used these tweaks a long time ago and run a --profile boot every few months.
All had been fine until a few days ago. After running a profile from the kernel line (which worked fine previously) 
caused the machine to randomly fail to get a DHCP address on boot.

I'd recently used the readahead tweak mentioned here.
[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)


Re-adding the --background switch to S01readahead fixed it completely. 
This issue is very timing specific and may not even appear on some machines and networks.

If you start init.d/networking a few milliseconds later, as S60, it works fine. 
Or you could run /etc/init.d/networking restart at a much later point, and again, it was fine.

So, if you have connectivity issues using anything but 'roaming mode' in Network Manager this is a possible reason why it fails. And something to bear in mind when you tweak your machine.

---

### Post by jocko on 2009-07-25
> **capoli said:**
> Hi,
This profile switch has just screwed up my booting. Instead of the slow, but reilable 33sec till login screen and 1 minute full boot time, the HDD waits about 1 minute at the very beginning. The light is on, but doing nothing. Now I have 2 minutes boot up :((
Can I undo somehow that profile stuff??
You should only boot **once** with the profile switch. It collects information of which files are read during that boot and makes sure they are loaded into memory before they are needed. That one boot will be very slow, but all boots after that should be a little bit quicker than before.

---

### Post by capoli on 2009-08-02
I did only once first. I can see in dmesg about 40 sec delay:
[    6.121601] kjournald2 starting.  Commit interval 5 seconds
[    6.121611] EXT4-fs: delayed allocation enabled
[    6.121613] EXT4-fs: file extents enabled
[    6.121758] EXT4-fs: mballoc enabled
[    6.121763] EXT4-fs: mounted filesystem with ordered data mode.
[   47.948781] udev: starting version 141
[   48.012917] irda_init()
[   48.012930] NET: Registered protocol family 23
[   48.016682] nsc-ircc 00:0c: activated

> **jocko said:**
> You should only boot **once** with the profile switch. It collects information of which files are read during that boot and makes sure they are loaded into memory before they are needed. That one boot will be very slow, but all boots after that should be a little bit quicker than before.

---

### Post by known on 2009-08-22
Excellent thread.
Is it possible to include the description of services as tool tips in sysv-rc-conf?

---

### Post by cimbaeth on 2009-08-24
thanks

---

### Post by known on 2009-08-24
Somebody please give me the list of minimal services required in sysv-rc-conf for a laptop meant only for browsing internet with swiftfox at home. I am running HARDY (kubuntu) with LXDE.

RAM is 256 MB
CPU is celeron
Internet speed is [http://www.speedtest.net/result/311981447.png](http://www.speedtest.net/result/311981447.png)

TIA

---

### Post by munkeh on 2009-09-03
Thanks to i3dmaster, so many years ago.
Using Ubuntu 9.04 there's the GUI tools in >System>Administration>Services, to switch off some of the services originally mentioned. sysv-rc-conf had a few more though and was easy to use (as close to a GUI as you can get in a terminal?)
For all levels, on a stand alone desktop connected to t'internet, I switched off;

anancron
atd
apport
bluetooth
avahi dae$
brltty
dns-clean
laptop-mo$
nfs-common
nfs-kerne$
pcmciauti$
ppdns
rmnologin
rysnc
sysklogd.

Before I did anything I did check that I won't need any of the services. Everything seems fine computer booting and switching off with no problems. A little bit quicker, especially shutdown. (Did do what i3dmaster said about K to k in /etc/rc0.d & rc6.d)

Also deleted tty4, tty5 & tty6 from /etc/event.d. They have not appeared back yet although there have been rumours they may with certain updates?

So thanks again to everyone who's put advice in on this.

---

### Post by known on 2009-09-06
> **munkeh said:**
> 
anancron
atd
apport
bluetooth
avahi dae$
brltty
dns-clean
laptop-mo$
nfs-common
nfs-kerne$
pcmciauti$
ppdns
rmnologin
rysnc
sysklogd.


Thank you munkeh.
That was quite useful.

---

### Post by varsamakos on 2009-10-21
> **known said:**
> thank you munkeh.
That was quite useful.

+1 :)
Thanks !

---

### Post by -jay- on 2009-11-04
nice guide very useful 

do you happen to have a updated guide for 9.04 ?

---

### Post by Nephtali on 2009-11-05
Glad to find this topic boys !

As there is for about 4 years of discussion I would like to know if the original post is still up to date or if some modifications have been added later ?

What's the deal with upstart today ? Can we still use the method as described 4 years ago ?

Thanks for your answer.

---

### Post by disorientedminds on 2009-11-05
Good work on this guide. I tried this on my HP mini 100 with Ubuntu 9.10 and my boot time increased by 4 sec. :D

---

### Post by akhe on 2009-11-07
Please, can you describe the way to speed up boot for 9.10 Karmic? because I am little bit afraid to do this because it is really old article for 6.10... or tell me differencies or show me thread where is this for 9.10

Thanks!

---

### Post by Labello on 2009-11-07
i would recommend to install the boot-up-manager:

```
sudo apt-get install bum
sudo bum

```

and then i always disable _everything_ except:
hal,gdm,dbus,avahi-daemon(pulseaudio, filesharing over network),policykit,preload,cups(printing)

the first three mentioned are the most important!

---

### Post by Nikos.Alexandris on 2009-11-10
> **Nephtali said:**
> Glad to find this topic boys !

As there is for about 4 years of discussion I would like to know if the original post is still up to date or if some modifications have been added later ?

What's the deal with upstart today ? Can we still use the method as described 4 years ago ?

Thanks for your answer.

I would also like to know if the guide is up-to-date (?).
Thanks for this time-resistant guide ;-)

---

### Post by Nephtali on 2009-11-16
Ok, the method seems to be still valid.

I tryed boot-up-manager but I have to say that I do not find the interface clear enough.
I truly prefered using sysv-rc-conf in terminal, it is clear enough if you have the minimum understanding of runlevels.

**BUT**, the services seem to have changed a lot since 2006 so I think the best way for us is to look on the net for information about services, ask on irc.freenode.net ...

If someone have enough time and knowledge, it could be a could idea to make a new up-to-date post with a longer list of services (olds and news) that would make a synthesis of all that have been said in this post.

Good Luck Boys & Girls

---

### Post by Nikos.Alexandris on 2009-11-16
I tried also this: [https://launchpad.net/~ubuntu-boot/+archive/ppa]("https://launchpad.net/~ubuntu-boot/+archive/ppa"). I have the impression it does speed-up but did not measure it somehow.

---

### Post by Nephtali on 2009-11-17
@ Nikos.Alexandris

Could you measure it with a bootchart graph for example where you would have set the system to log you automatically (don't lose time typping your password)? It would give an idea.

I found few information about ubuntu boot, could you tell us what this package consists in ?

---

### Post by Nikos.Alexandris on 2009-11-17
> **Nephtali said:**
> @ Nikos.Alexandris

Could you measure it with a bootchart graph for example where you would have set the system to log you automatically (don't lose time typping your password)? It would give an idea.

I found few information about ubuntu boot, could you tell us what this package consists in ?

I have 2 charts for you (and for all). One without any external device attached and one with several (LCD, firewire, hard-disk, usb-mouse, mobile phone).

Regards

**UPDATE**: couldn't find another way to post the images directly here. ".png" and ".jpg" are restricted to be of a certain resolution. So I tar-gz-ed them.

---

### Post by Nikos.Alexandris on 2009-11-17
> **Nikos.Alexandris said:**
> I have 2 charts for you (and for all).

I see that the attached charts are unreadable (too small). But why? I attached the charts directly from within the directory **/var/log/bootchart**.

...OK, png is restricted to be 1024x768. Updating the previous post (if possible).

---

### Post by Dullstar on 2009-11-17
I would recommend that you include KDM.
That way, if a newbie comes and is still learning, they don't get too confused if they are using KDE.

---

### Post by fonsi2099 on 2009-11-18
Now I'm replacing all the windows in my home and office, the 9.10 is really fine, practically better than windows for normal user. Please can some one make an **update of this "howto Speed up ubuntu boot process"** for people like me, normal users and please only for  9.10 because the howto is too long, I'm not sure if it's working for your last version too. Many thanks in advance.

---

### Post by Mahngiel on 2009-12-31
^this.  Since this was posted, oh, i don't know, 4 years ago, some of the information is incomplete.

---

### Post by zmdmw52 on 2010-01-14
[FONT=Arial]Are the instructions in the first post ([http://ubuntuforums.org/showpost.php?p=487138&postcount=1](http://ubuntuforums.org/showpost.php?p=487138&postcount=1)) valid for Ubuntu 9.04 (Jaunty) and later versions ? (as the first post was last edited in Jan 2007 and is dated Nov 2005)[/FONT] ?

---

### Post by AlexanderDGreat on 2010-02-24
Can anyone confirm or update if this thread is working on Jaunty, Karmic, or for Lucid? Can anyone point me to a newer link? Thanks.

---

### Post by Psumi on 2010-04-07
Just did this on Debian, not much of a change... but I'd like to point something out...

If you have a **K10halt** or **K10reboot** entry in rc0 or rc6, DO NOT move them to lowercase k. Even though they have no runlevels allocated in sysv-rc-conf, they are crucial to your system.

In fact, if you remove them,

sudo reboot now

Will end with you being pushed into root terminal on tty1.

sudo halt (shutdown isn't what you think, use halt to turn off computer.)

will end with you on dark soil, unable to power down normally, forcing you to do a hard power off.

---

### Post by dannyboy79 on 2010-04-09
> **Psumi said:**
> Just did this on Debian, not much of a change... but I'd like to point something out...

If you have a **K10halt** or **K10reboot** entry in rc0 or rc6, DO NOT move them to lowercase k. Even though they have no runlevels allocated in sysv-rc-conf, they are crucial to your system.

In fact, if you remove them,

sudo reboot now

Will end with you being pushed into root terminal on tty1.

sudo halt (shutdown isn't what you think, use halt to turn off computer.)

will end with you on dark soil, unable to power down normally, forcing you to do a hard power off.

not sure what version you're using but I use Lucid and straight from the man pages of halt:
halt(8) - Linux man page
Description
Halt notes that the system is being brought down in the file /var/log/wtmp, and then either tells the kernel to halt, reboot or poweroff the system. 

**If halt or reboot is called when the system is not in runlevel 0 or 6, in other words when it's running normally, shutdown will be invoked instead (with the -h or -r flag)**. For more info see the shutdown(8) manpage. 

so I always use because I don't run in run levels 0 or 6
sudo shutdown -n now
shuts the computer down and halts it just fine, i often issue 
sudo shutdown -r now
to restart it.

---

### Post by benplanet on 2010-04-09
do these tips  still apply to Karmic 9.10 64 bit?

---

### Post by thdn on 2010-05-08
> do these tips  still apply to Karmic 9.10 64 bit?

or Lucid ??

---

### Post by munkeh on 2010-05-15
Posted what I had done a while back for 9.04 (Post  #402).

For Ubuntu 10.04 running on a laptop I have just cleared;

bluetooth
brltty
cups
dns-clean
pcmciauli$
ppdns
rsync
saned

and also followed i3dmaster's instructions regarding K to k in rc0 and 6.

Please note these were items I do not need at the moment, e.g. no bluetooth or printer.
This has not broken anything; Everything seems to be working fine. Unlike 9.04 for me there seemed to be a lot that were already cleared, the only two I thought about but never switched off were 'lm-sensors' and 'on-demand'. I had previously removed quite a lot from the Startup Applications in the System>Preferences menu including Ubuntu One etc.

Anyway the point I was trying to make is:
Before any changes - 
Time to boot up =32 seconds
Time to switch off = 6 seconds

After making the above changes -
Time to boot up =32 seconds
Time to switch off = 6 seconds

Unlike in 9.04 where altering all this made a difference.

So I am very happy with this switch on and off time for my machine and it has showed me what a wonderful job they have done with 10.04 I am very happy with it and they don't need little me fiddling with it.

---

### Post by wachin on 2010-05-24
Is great, your are the best

---

### Post by anantshri on 2010-05-28
BUM or service config works for lucid too.


but /etc/inittab is now obsolete instead i suppose we need to manually configure these files

/etc/init/tty[1-6].conf

how that i am still trying to find out.

---

### Post by kartix on 2010-06-06
This is good, yet to try it though! appreciate the detailing.

cheers

---

### Post by macaddict01 on 2010-10-14
> **anantshri said:**
> BUM or service config works for lucid too.


but /etc/inittab is now obsolete instead i suppose we need to manually configure these files

/etc/init/tty[1-6].conf

how that i am still trying to find out.

I noticed this as well and haven't looked into it yet. I was considering just renaming three of the .conf files and rebooting. I'll test this later.

Thanks to all for this guide.

---

### Post by afrodeity on 2011-05-06
wish there was a guide for 11.04

---

### Post by geazzy on 2011-06-01
thanks :D

---

### Post by boscharun on 2012-01-16
Ubuntu one, startup sound and visual assistance are candidates that can be removed from the startup list.

Another [tricks to speed up ubuntu]("http://www.skipser.com/p/2/p/speed-up-ubuntu.html") boot is to set the CONCURRENCY to shell which makes linux use all available cores for booting.

---

### Post by ParadoxBlue on 2012-02-04
> **boscharun said:**
> Ubuntu one, startup sound and visual assistance are candidates that can be removed from the startup list.

Another [tricks to speed up ubuntu]("http://www.skipser.com/p/2/p/speed-up-ubuntu.html") boot is to set the CONCURRENCY to shell which makes linux use all available cores for booting.

The CONCURRENCY trick may work for some but on my AMD 6 core it makes absolutely no difference.

---

