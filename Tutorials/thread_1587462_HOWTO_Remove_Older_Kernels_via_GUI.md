---
title: "HOWTO: Remove Older Kernels via GUI"
date: 2010-10-03
forum: Tutorials
---

### Post by drs305 on 2010-10-03
[center][size=4]**[COLOR="DarkRed"]HOWTO: Remove Older Kernels via GUI (or CLI)[/COLOR]**[/size][/center]

When new kernels are introduced and installed the older kernels remain in the system. They are located in the /boot folder and are displayed in the Grub menu. Over time, unless the older kernels are removed, the Grub menu will continue to expand, as will the space occupied in the /boot folder.

Should the user wish to remove one or more older kernels there are several ways to do so. Physically removing a kernel from the OS will also remove it from the Grub 2 menu once the Grub menu is updated with the "update-grub" command. Another method is to manually edit the Grub 2 scripts to display only an assigned number of kernels (even if more kernels are retained in /boot).

Note: Users should consider keeping a known, working older kernel. This provides insurance in case the user experiences problems with a newly-introduced kernel. The older kernel will be displayed on the Grub 2 menu as long as it remains in the /boot folder.

The "CLI" portion of the title is due to the contributions of Ubuntu Forum contributor *slakkie*, who wrote the script in Post #2. Thank you *slakkie*.

**[COLOR="DarkRed"][SIZE="4"]An Easy GUI Method - Ubuntu-Tweak[/SIZE][/COLOR]**

Ubuntu Tweak is an excellent GUI third-party application which can easily remove older kernels. It is independent of Grub and will work with Grub legacy and Grub 2. It performs a variety of common Ubuntu tasks, one of which is to remove older kernels. Ubuntu Tweak *removes* older kernels and updating Grub afterwards will remove them from the menu.

**To install Ubuntu-Tweak:**
Ubuntu-Tweak is not currently in the normal respositories. Go to the Ubuntu-Tweak site, [_http://ubuntu-tweak.com_/]("http://ubuntu-tweak.com/") and, click on the "Download" button.
[LIST]
[*]If prompted, allow Gdebi to install the package automatically; 
[*]Download the package and double click the .deb file to install Ubuntu-Tweak; or 
[*]Install using the terminal. Change to the folder containing the .deb file and run
```
sudo dpkg -i ubuntu-tweak*.deb
```
[/LIST]
**To run Ubuntu-Tweak:**
Main Menu: System Tools > Ubuntu Tweak
or
```

ubuntu-tweak

```
[list]
[*]Select "Package Cleaner" on the left and ""Clean Kernel" from the right panel.
[*]Press the "Unlock" button at the lower right, enter your password.
[*]Select from the displayed list the kernel images and headers you wish to remove. The kernel in use is *not* listed.
[*]Press the "Cleanup" button at the lower right to remove the selected kernel images and headers.  
[/list]
**Update Grub to refresh the menu:**
This should be run by Ubuntu Tweak after it removes the kernel, but to be sure:
```

sudo update-grub

```


**[COLOR="DarkRed"][SIZE="4"]Removing Kernels via Synaptic[/SIZE][/COLOR]**

First, determine which kernel you are using:
```

uname -r

```

Open Synaptic via System > Administration > Synaptic; or
```
gksu synaptic
```

Search for the kernels by typing  *linux-image* in the upper right search box. 

[LIST]
[*]The kernels are those that being with "linux-image".
[LIST]
[*]Example: *linux-image-2.6.32-24*, *linux-image-2.6.32-24-generic*. 
[*]The older kernels will have **lower** ending numbers. *linux-image-2.6.32-**23*** is *older* than *linux-image-2.6.32-**24***
[/LIST] 
[*]Those with green selection boxes are currently installed.
[/LIST]

Remove **unused** kernels as you would any other package by right clicking the package and selecting the desired option.

You can also remove the associated *linux-headers* and *linux-restricted-modules-...* for the earlier versions. Example: linux-headers-2.6.32-23

Hint: An easy way to find all the installed kernels, headers and modules for a given kernel is to type the main kernel version (2.6.XX) into the top search bar. Click on the top left column status entry in the package window to bring the installed packages (green boxed) to the top of the list.

When you delete a an older kernel via synaptic the kernel is removed from the computer and more disk space is freed up. The grub configuration file (grub.cfg) is updated and the deleted kernel will no longer be displayed on the menu. Make sure you are satisfied with the performance of newly-released kernels before deleting older ones. 

**[COLOR="DarkRed"][SIZE="4"]Hiding Kernels via Grub Customizer[/SIZE][/COLOR]**
If you want to keep the kernels on your system, but don't want them displayed, you can use a Grub 2 GUI app called "Grub Customizer". It's a great app that allows the user to hide, rename and reorder the items which appear in the Grub menu. Here is a link which explains how to use it:
[HOWTO: Grub Customizer]("http://ubuntuforums.org/showthread.php?t=1664134")


**[COLOR="DarkRed"][SIZE="4"]Hiding Kernels via the Grub 2 Scripts[/SIZE][/COLOR]**
The number of *displayed* kernels can be set by modifying the /etc/grub.d/10_linux file. It is documented in Section 2 of my [Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602") This tweak hides the kernels but does not remove them from the OS. Note: Recommended only for geeks. 

**[COLOR="DarkRed"][SIZE="4"]Other Notes[/SIZE][/COLOR]**

Linux kernels, headers and modules can also be removed via the command line (terminal), but if you want to attempt this you probably don't need this guide.  ;-)

To hide specific kernels from the menu there is now a GUI app called Grub Customizer that can easily accomplish the task. See the following link:
[_Grub Customizer_]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183") 

For Grub Legacy (Grub 1), the GUI application Startup-Manager can limit the number of displayed kernels. It will not remove them from the OS. For more information on StartUp-Manager, review this thread: [HOWTO: StartUp Manager & Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")  StartUp-Manager currently does *not* support limiting kernel displays for Grub 2.

---

### Post by slakkie on 2011-02-21
I made a cli version for this, had it a long time ago, for Ubuntu, recently made a version which supports Debian/Ubuntu and has been tested on:

[LIST]
[*] Ubuntu 8.04 LTS / 10.10
[*] Debian stable / testing / unstable
[/LIST]

The rmkernel function below will remove all kernels, kernel header, kernel modules and backport packages except for the running kernel. The function will make sure that any kernel package related to your current kernel will stay installed. As said, all others will be removed. The script depends on aptitude, so for those who haven't installed that package yet: sudo apt-get install aptitude

**Regular warnings apply:**
[LIST]
[*] Use this only when your current kernel is working as expected, since we do remove all kernels and kernel modules for kernels which we are not running.
[*] This script will not work in a chrooted environment.
[/LIST]


Include these functions in your .bashrc/.zshrc:

```

_egrep-pattern () {
        [ -z "$1" ] && return
        local regexp=$1
        shift
        for i in $*
        do
                regexp="$regexp|$i" 
        done
        echo ${regexp}
}

rmkernel () {
        local cur_kernel="$(uname -r)"
        local all_kernels="$(dpkg -l | grep -- linux- | egrep -- "-(image|headers|backports|modules|firmware)" \
        | grep "^ii" | awk '{print $2}')"
        local cur_kernel_pkgs="$(echo -e "$all_kernels" | grep "$cur_kernel$")"
        local cur_kernel_img=$(echo -e "$cur_kernel_pkgs" | grep image)
        local cur_kernel_hdr=$(echo -e "$cur_kernel_pkgs" | grep headers)
        if [ -z "$cur_kernel_img" ]
        then
                echo "Unable to get the current kernel package. What are you doing?" >&2
                echo "Possibly running in a chroot, eitherway aborting!" >&2
                return 1
        fi
        local cur_kernel_img_rdepends="$(apt-cache rdepends $cur_kernel_img | tail -n +3)"
        local cur_kernel_hdr_rdepends
        local cur_kernel_hdr_depends
        if [ -n "$cur_kernel_hdr" ]
        then
                cur_kernel_hdr_rdepends="$(apt-cache rdepends $cur_kernel_hdr | tail -n +3)" 
                cur_kernel_hdr_depends="$(apt-cache depends $cur_kernel_hdr | egrep 'linux-(image|headers)' | grep Depends | awk '{print $2}')" 
        fi
        local keep="$(_egrep-pattern $cur_kernel_pkgs $cur_kernel_img_rdepends $cur_kernel_hdr_rdepends $cur_kernel_hdr_depends)"
        if [ -z "$keep" ]
        then
                echo "Unable to determine which kernels to keep!" >&2
                echo "This should not happen in normal circumstances" >&2
                return 1
        fi
        local remove="$(echo -e "$all_kernels" | egrep -v "^($keep)$")"
        local rm_modules="$(find /lib/modules -mindepth 1 -maxdepth 1 -type d ! -name ${cur_kernel} )"
        if [ -n "$remove" ] || [ -n "$rm_modules" ]
        then
                echo "Going to remove the following kernel packages:" $remove
                echo "Going to remove the following kernel modules directories afterwards:" $rm_modules
                echo "Waiting 5 seconds for ctrl-c to abort mission"
                sleep 3
                echo -n ..2
                sleep 1
                echo -n ..1
                sleep 1
                echo "..Start removal"
                if [ -n "$remove" ]
                then
                        sudo aptitude -y purge $remove
                fi
                [ -n "$rm_modules" ] && sudo rm -rf $rm_modules
        fi
        return 0
}

```

Source your .bashrc/.zshrc.

Now run rmkernel from your shell and you will remove all unneeded kernel packages. Enjoy!

---

### Post by drs305 on 2011-02-21
*slakkie*

Thanks for this contribution. I have successfully run this and it worked as advertised. Of course, I also made a copying mistake and am responsible for *slakkie's* inserted warning.  :oops:

If you aren't familiar with .bashrc, "Source your .bashrc/.zshrc." means you should either close all your terminals and reopen them or run "source .bashrc" (for most) to 'refresh' with the new .bashrc contents.

---

### Post by slakkie on 2011-02-21
No worries, I added an extra check, we shouldn't get into your situation again.

---

### Post by gurlsee on 2011-03-15
Thank you for this useful guide on how to remove it. I will also recommend it to my friend who wanted to remove this Kernels.

[contemporary furniture](http://www.moderncollections.com/) | [modern lounge chairs](http://www.moderncollections.com/modern-lounge-chairs.html)

---

### Post by Ceriyx on 2011-04-10
Hi dr305,
thanks for this, very clear summary of methods and issues, I've downloaded Ubuntu-Tweak because good tools are always handy but did my clean-up using synaptic, because this is the inherent system procedure and 'should always work' on a properly-functioning install.
Cheers,
Ceriyx

---

### Post by ActionParsnip on 2011-05-11
Just run:

dpkg -l | grep linux-image-2; echo; uname -a

The list are the installed kernels, the line on its own is the running kernel. You can use apt-get to remove the kernels but NOT the runing one. No need for 3rd party apps. You can do it yourself.

---

### Post by drs305 on 2011-05-11
> **ActionParsnip said:**
> Just run:

dpkg -l | grep linux-image-2; echo; uname -a

The list are the installed kernels, the line on its own is the running kernel. You can use apt-get to remove the kernels but NOT the runing one. No need for 3rd party apps. You can do it yourself.

Thanks for the command. One of Linux' advantages is multiple ways of accomplishing tasks.

One of the things Ubuntu Tweak does is also list the headers, and provides the option to clean those up as well. Depending on what command you use, in a terminal they would normally need to be uninstalled separately from the associated kernel.

---

### Post by ActionParsnip on 2011-05-11
Yeah missed the - sign, my bad. True there is more than one way but if space is not a luxury or if you want to stick to official packages then the method I detailed is great :D:D

---

### Post by rkanth on 2011-07-09
> **ActionParsnip said:**
> Yeah missed the - sign, my bad. True there is more than one way but if space is not a luxury or if you want to stick to official packages then the method I detailed is great :D:D

Hi, I have a diddifferent problem; in fact, two problems. First, let me tell you that I'm a zero tech-wise.

I did a clean install of 10.04 and wanted to remove 9.10. So I formatted HD1 and installed Lucid.(Karmic was  on the same disk before formatting). I have another HD for my files and old xp install that I don't use. I encounter two problems now:

1. I went the synaptic way and tried to remove other kernels than "2.26.32.28-generic" which the terminal says I'm running while on Lucid. Two of the images listed are 2.26.32.38 and 2.26.32.32. Since the number is bigger than .28 I wasn't sure if I should remove these.

2. So, I used Grub-customiser and unticked these two and XP in the hope that I'll get a faster direct boot into Lucid. When I booted next, to my surprise I found my computer booting into Karmic!(I used system > about ubuntu to find out) I thought I wiped the harddisk clean! A check of grub on reboot showed a new kernel 2.26.32.14. It was not there earlier. And it is not showing in grub optimiser, either.

3. This 2.26.32.14 thing is listed as the first thing in grub. While I can move down the arrow keys to .28 and get into Lucid, my wife and kid, worse than me technically, are ending up in program-less Karmic. Some times you miss the 3 seconds that grub gives you to choose OS.

3. While on this, Is it okay to untick memtest entries in grub optimiser? And lastly, Is there a way computer boots into Lucid without going through grub?

I should also mention that I had a failed instal of Lucid (freeze at ubuntu screen; was trying dual-boot of karmic-lucid) before I went the fomtting route. I have two small 13gb, 26gb filesystems on my second hard disk now which I otherwise use only for data.

Any help is much appreciated. I'm sorry If I posted it in the wrong forum (tutorial). I didn't know where else

RK

---

### Post by drs305 on 2011-07-09
Yes, you can untick the memtest entry. It's not normally needed and you can always enable the entry if you end up wanting to run it.

What I would first recommend is that you boot into Lucid (it doesn't matter the kernel version as long as you end up in Lucid).

Next I would ensure Grub is from your Lucid installation. This command assumes *sda* is your Ubuntu drive. Don't use the partition number.
```
sudo grub-install /dev/sda
```

I would then update your system to make sure you have the latest kernel:
```
sudo apt-get update && sudo apt-get upgrade
```
If it finds a new kernel, you will be asked to reboot. Do so.

Next, I would install and use Ubuntu Tweak to clean up your kernel list. It won't let you remove the currently-running kernel, and normally you should keep at least one extra kernel that you know works. You can go to the first post in this thread to read about installing and using Ubuntu Tweak. The Lucid kernels should all start with "2.6.32". The latest is 2.6.32-32.

Removing or adding a kernel should run the script to update Grub2, but I'd run it anyway:
```
sudo update-grub
```

Finally, you can open up Grub Customizer with (hopefully) a valid set of Lucid kernels and choose which ones you want to display.

---

### Post by rkanth on 2011-07-09
Thanks, drs350. I'm updating and upgrading now.
I have downloaded Ubuntu Tweak, read your tutorial yesterday, but am unable to install it. The error given is "Error: Dependency is not satisfiable: python (>= 2.7)". Tried again now but no go.

Will post again after upgrading...will take 30 mts. at my download speed.

Will you clarify on my doubt "Is there a way computer boots into Lucid without going through grub?"

I have read about BURG elsewhere. Is it useful?
RK

RK.

---

### Post by drs305 on 2011-07-09
> **rkanth said:**
> Thanks, drs350. I'm updating and upgrading now.
I have downloaded Ubuntu Tweak, read your tutorial yesterday, but am unable to install it. The error given is "Error: Dependency is not satisfiable: python (>= 2.7)". Tried again now but no go.

Will post again after upgrading...will take 30 mts. at my download speed.

Will you clarify on my doubt "Is there a way computer boots into Lucid without going through grub?"

I have read about BURG elsewhere. Is it useful?
RK

RK.

The "error dependency" message relates to trying to download the latest version of Ubuntu Tweak on an older version of Ubuntu. You have to download an earlier version of UT. If you did it via the command line I would have suspected APT to use the correct version. 

If you downloaded it via the UT website and clicked "Download", it would have selected an incompatible version. Just below the download button, in small type, it says for 10.10 and has a link for older versions. You will have to click the 'older versions' link.

You have to go through Grub (normally) to get into Lucid, but that doesn't mean you have to see the menu for long (or at all) or that you have to manually make a selection (unless it's broken). How long the menu is displayed it based on a setting in /etc/default/grub. You can set the timeout by manually editing the file or using Grub Customizer to reduce the timeout. I'd suggest leaving it at a minimum of 1 second so you can interrupt the process by pressing any key. (You should be able to display the menu by holding down the SHIFT key, but I'd set the timeout to at least 1 second until you are sure the SHIFT key method stops the boot).

BURG is very useful for those wanting to use themes. The creator has done very good work and is well ahead of GRUB as far as advanced menu visuals and theming go. But generally, if all you want is to boot your system, perhaps even with pretty font colors and a nice background image, Grub will do nicely.

---

### Post by rkanth on 2011-07-09
Yes, I downloaded the wrong UT. Thanks.
Tweak is not showing any kernels in its window! Is it because I hid all but .28 in grub customiser?
Also, despite unchecking, memtest is displayed in grub...alas, xp also made a reappearance...:(
grub version is displayed as 1.97...is it grub 2?
All I want is that .14 to go or come down the list and 32.28 to be the first, so that it boots...

---

### Post by drs305 on 2011-07-09
I think at this point I would uninstall Grub Customizer and get things back to normal. You can reinstall it afterwards.

To remove GC, take a look at Step 7 in the 'Customizer' link in my signature line. Once it is removed, run "sudo update-grub".

You can get rid of the memtest entry by making it's script un-executable:
```
sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub
```

We can also disable the ability to check for other OS's (including Windows) so it isn't included in the Grub menu. Doing this will prevent Grub from finding any other OS's or ones you install later, so this may not be something you want to do. (You can reverse it by changing the -x to +x again).
```

sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```

The reason UT may not show any kernels is that it has only found one on your system (and it is in use). It won't display the running kernel.

If you still are having problems, the best thing would be to download/extract/run the boot info script and post the contents of RESULTS.txt (Click the "BIS" link in my signature line). It will show us exactly (almost) what is going on with your boot files, kernels and menu.

---

### Post by rkanth on 2011-07-09
Okay, I think I've totally screwed up :(
the computer won't boot. I used a live-usb which gave me the option of .28 (only.28 and .28 recovery which i originally wanted). It booted into Lucid and I'm here.

Unable to use file browser to normal grub2. It says I'm not owner and can't modify files...typing sudo su in the terminal did not make Root in the GUI file browser. Otherwise all my iles and programs are working fine but I can't use live-usb everytime I boot, can I?

meanwhile found out where .14 was coming from and taking me to empty karmic....it's on sda9 while .28 is on sda1 according to grub optimiser. Any solution?
Thanks
RK

---

### Post by rkanth on 2011-07-09
okay here's the Results.txt from running BIS:

#
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 9 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   299,808,767   299,806,720  83 Linux
/dev/sda2         299,810,814   312,580,095    12,769,282   5 Extended
/dev/sda5         299,810,816   312,580,095    12,769,280  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    51,102,764    51,102,702   7 NTFS / exFAT / HPFS
/dev/sdb2          51,102,889   488,392,064   437,289,176   f W95 Extended (LBA)
/dev/sdb5          78,140,223   156,280,319    78,140,097   b W95 FAT32
/dev/sdb6         156,280,383   312,544,574   156,264,192   b W95 FAT32
/dev/sdb7         312,544,638   400,452,254    87,907,617   b W95 FAT32
/dev/sdb8         400,452,318   488,392,064    87,939,747   b W95 FAT32
/dev/sdb9          51,102,891    76,903,154    25,800,264  83 Linux
/dev/sdb10         76,903,218    78,140,159     1,236,942  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        d9639e45-c39e-4c55-b158-44cd9a6822c4   ext4       
/dev/sda5        e529b793-6353-47e4-b172-0887e89953f5   swap       
/dev/sdb1        82D4A69ED4A69447                       ntfs       
/dev/sdb10       62ae6f14-351b-4822-a609-fac1187620af   swap       
/dev/sdb5        7413-A5C7                              vfat       DISK1_VOL2
/dev/sdb6        7D64-3245                              vfat       NEWYORKER
/dev/sdb7        82A1-6F10                              vfat       PICASA
/dev/sdb8        87DF-49F7                              vfat       SAILASURYA
/dev/sdb9        5cb1f38e-6315-46f9-937c-cef083a56288   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sr1         /media/Access Manager    iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="${saved_entry}"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d9639e45-c39e-4c55-b158-44cd9a6822c4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set d9639e45-c39e-4c55-b158-44cd9a6822c4
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=7
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-28-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	savedefault
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d9639e45-c39e-4c55-b158-44cd9a6822c4
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=d9639e45-c39e-4c55-b158-44cd9a6822c4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	savedefault
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d9639e45-c39e-4c55-b158-44cd9a6822c4
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=d9639e45-c39e-4c55-b158-44cd9a6822c4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d9639e45-c39e-4c55-b158-44cd9a6822c4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e529b793-6353-47e4-b172-0887e89953f5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.145065308 = 8.745697280    boot/grub/core.img                             1
  76.268646240 = 81.892835328   boot/grub/grub.cfg                             1
   8.141010284 = 8.741343232    boot/initrd.img-2.6.32-28-generic              1
   8.195892334 = 8.800272384    boot/initrd.img-2.6.32-32-generic              1
   8.132194519 = 8.731877376    boot/vmlinuz-2.6.32-28-generic                 1
   8.149269104 = 8.750211072    boot/vmlinuz-2.6.32-32-generic                 1
   8.195892334 = 8.800272384    initrd.img                                     1
   8.141010284 = 8.741343232    initrd.img.old                                 1
   8.149269104 = 8.750211072    vmlinuz                                        1
   8.132194519 = 8.731877376    vmlinuz.old                                    1

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer
--------------------------------------------------------------------------------

=========================== sdb9/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,9)
search --no-floppy --fs-uuid --set 5cb1f38e-6315-46f9-937c-cef083a56288
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,9)
	search --no-floppy --fs-uuid --set 5cb1f38e-6315-46f9-937c-cef083a56288
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=5cb1f38e-6315-46f9-937c-cef083a56288 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
### END /etc/grub.d/30_os-prober_proxy ###
--------------------------------------------------------------------------------

=============================== sdb9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb9 during installation
UUID=5cb1f38e-6315-46f9-937c-cef083a56288 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb10 during installation
UUID=62ae6f14-351b-4822-a609-fac1187620af none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  27.514813900 = 29.543806464   boot/grub/core.img                             1
  25.166593075 = 27.022423552   boot/grub/grub.cfg                             1
  25.163957119 = 27.019593216   boot/initrd.img-2.6.31-14-generic-pae          2
  27.453427792 = 29.477893632   boot/vmlinuz-2.6.31-14-generic-pae             2
  25.163957119 = 27.019593216   initrd.img                                     2
  27.453427792 = 29.477893632   vmlinuz                                        2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  2d 48 20 6c 6f 67 69 6e  5f 68 6f 73 74 5d 20 6c  |-H login_host] l|
00000010  69 6e 65 20 62 61 75 64  5f 72 61 74 65 2c 2e 2e  |ine baud_rate,..|
00000020  2e 20 5b 74 65 72 6d 74  79 70 65 5d 0a 00 00 00  |. [termtype]....|
00000030  2f 64 65 76 2f 25 73 3a  20 6e 6f 74 20 61 20 63  |/dev/%s: not a c|
00000040  68 61 72 61 63 74 65 72  20 64 65 76 69 63 65 00  |haracter device.|
00000050  2f 64 65 76 2f 25 73 3a  20 63 61 6e 6e 6f 74 20  |/dev/%s: cannot |
00000060  6f 70 65 6e 20 61 73 20  73 74 61 6e 64 61 72 64  |open as standard|
00000070  20 69 6e 70 75 74 3a 20  25 6d 00 00 0d 0a 00 75  | input: %m.....u|
00000080  6e 6b 6e 6f 77 6e 5f 64  6f 6d 61 69 6e 00 53 75  |nknown_domain.Su|
00000090  6e 00 4d 6f 6e 00 54 75  65 00 57 65 64 00 54 68  |n.Mon.Tue.Wed.Th|
000000a0  75 00 46 72 69 00 53 61  74 00 4a 61 6e 00 46 65  |u.Fri.Sat.Jan.Fe|
000000b0  62 00 4d 61 72 00 41 70  72 00 4d 61 79 00 4a 75  |b.Mar.Apr.May.Ju|
000000c0  6e 00 4a 75 6c 00 41 75  67 00 53 65 70 00 4f 63  |n.Jul.Aug.Sep.Oc|
000000d0  74 00 4e 6f 76 00 44 65  63 00 25 73 20 25 73 20  |t.Nov.Dec.%s %s |
000000e0  25 64 20 20 25 64 00 25  30 32 64 3a 25 30 32 64  |%d  %d.%02d:%02d|
000000f0  3a 25 30 32 64 00 25 6c  64 00 25 64 20 00 75 73  |:%02d.%ld.%d .us|
00000100  65 72 00 75 73 65 72 73  00 20 6c 6f 67 69 6e 3a  |er.users. login:|
00000110  20 00 2f 76 61 72 2f 72  75 6e 2f 75 74 6d 70 00  | ./var/run/utmp.|
00000120  2f 76 61 72 2f 6c 6f 67  2f 77 74 6d 70 00 25 73  |/var/log/wtmp.%s|
00000130  3a 20 74 63 73 65 74 61  74 74 72 3a 20 54 43 53  |: tcsetattr: TCS|
00000140  41 4e 4f 57 3a 20 25 6d  00 25 73 3a 20 72 65 61  |ANOW: %m.%s: rea|
00000150  64 3a 20 25 6d 00 25 73  3a 20 69 6e 70 75 74 20  |d: %m.%s: input |
00000160  6f 76 65 72 72 75 6e 00  2f 64 65 76 00 2f 64 65  |overrun./dev./de|
00000170  76 3a 20 63 68 64 69 72  28 29 20 66 61 69 6c 65  |v: chdir() faile|
00000180  64 3a 20 25 6d 00 2f 64  65 76 2f 25 73 3a 20 25  |d: %m./dev/%s: %|
00000190  6d 00 25 73 3a 20 6e 6f  74 20 6f 70 65 6e 20 66  |m.%s: not open f|
000001a0  6f 72 20 72 65 61 64 2f  77 72 69 74 65 00 25 73  |or read/write.%s|
000001b0  3a 20 64 75 70 20 70 72  6f 62 6c 65 6d 3a 00 fe  |: dup problem:..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d8 c2 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb2

00000000  3e 78 88 c5 b0 d7 35 ad  1a 88 db 69 39 f3 16 b2  |>x....5....i9...|
00000010  9b 64 c8 64 78 18 d6 31  b3 13 0c 8e be a1 4c 55  |.d.dx..1......LU|
00000020  54 53 36 4e 18 96 b4 f1  48 81 4d 54 a4 ed d3 6a  |TS6N....H.MT...j|
00000030  54 ab 6d e9 b3 ca c3 89  99 94 ef 8e 9b c8 4b bc  |T.m...........K.|
00000040  68 66 3c 7c d2 6a 3a e6  ae 74 e2 b0 42 52 06 ea  |hf<|.j:..t..BR..|
00000050  8d 32 60 10 cc 73 dc 95  d4 5e 25 97 03 81 40 ac  |.2`..s...^%...@.|
00000060  79 eb 14 07 e7 54 de ec  e2 43 5f 1e aa 1e 0f 36  |y....T...C_....6|
00000070  de 83 80 27 03 b1 5f 5c  62 b1 85 d0 ba a9 f9 38  |...'.._\b......8|
00000080  e5 10 5a 9d 71 94 7a 32  55 cb 05 02 38 19 50 05  |..Z.q.z2U...8.P.|
00000090  36 0b 46 a0 29 8d 44 1d  41 19 57 91 7a 38 0e 42  |6.F.).D.A.W.z8.B|
000000a0  40 63 0a 36 b6 6c 9d e0  e2 96 ae 00 4c 52 ec 3e  |@c.6.l......LR.>|
000000b0  35 30 a7 e1 ef a4 72 24  37 ae 1d 93 aa 3c 08 12  |50....r$7....<..|
000000c0  9a 5a 89 7a d8 ef 1f b4  f8 14 af 75 85 b5 4e 1d  |.Z.z.......u..N.|
000000d0  ec 3b 1f ef 06 7e 93 0e  9f 01 64 24 45 3f 4f da  |.;...~....d$E?O.|
000000e0  3b a7 4e 19 04 4e 98 a7  0d b4 31 ed 36 79 6a 71  |;.N..N....1.6yjq|
000000f0  cb 53 1e 66 55 4f 1c 3b  9f 3c 9a a7 be 62 1f 0c  |.S.fUO.;.<...b..|
00000100  81 c5 59 0f 1d 16 b9 76  30 e4 de 9c 38 59 34 c7  |..Y....v0...8Y4.|
00000110  e8 d9 e5 77 06 41 45 80  5c af f4 0c cd bc 29 bd  |...w.AE.\.....).|
00000120  67 69 e8 76 00 4d ae 34  0c d3 5a 78 89 44 de 70  |gi.v.M.4..Zx.D.p|
00000130  1c ca ce 9a 1d 3f 1e 70  18 f0 d2 41 c1 9b 64 64  |.....?.p...A..dd|
00000140  c0 14 71 08 71 f0 ca b8  5e 48 a3 50 5c 5f e1 ec  |..q.q...^H.P\_..|
00000150  ce 91 aa f2 cf 01 44 35  16 1c 20 b8 4c 7b 4f 05  |......D5.. .L{O.|
00000160  31 29 71 93 8a 20 ef d0  94 32 c2 50 28 8b 61 68  |1)q.. ...2.P(.ah|
00000170  4a 9a 93 db 7b 64 34 4d  7d ea b1 b9 49 02 9b e0  |J...{d4M}...I...|
00000180  e0 08 34 a4 78 25 66 ff  8f fa a2 f0 85 73 55 8c  |..4.x%f......sU.|
00000190  0e 40 70 66 02 8e 08 55  4e 50 70 43 00 e6 37 ef  |.@pf...UNPpC..7.|
000001a0  f8 f5 57 c1 49 5c 6c ea  20 89 9b 67 8d 8e c3 21  |..W.I\l. ..g...!|
000001b0  f7 f3 e4 e3 3a a1 dd f1  cf cb a4 85 ef 70 00 01  |....:........p..|
000001c0  c1 ff 0b fe ff ff 96 8e  9c 01 c1 52 a8 04 00 fe  |...........R....|
000001d0  ff ff 05 fe ff ff 57 e1  44 06 3f 67 50 09 00 00  |......W.D.?gP...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo0/sdb5: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))


```

---

### Post by rkanth on 2011-07-09
And I don't want to go through reinstalling Lucid and 2 gig download of update, upgrade ISOs.....

---

### Post by drs305 on 2011-07-09
From the LiveCD, mount sda1 and reinstall grub:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Do not include the partition number in the second command.

Reboot and make sure BIOS is booting sda first.

After booting back into your normal installation (without the LiveCD), run "sudo update-grub".

---

### Post by rkanth on 2011-07-09
Thanks drs 350, but as I said in my very first post, I'm a tech Zero.

1. I have only a usb start-up disk that I made from Lucid ISO, not a live-cd; will this be enough?

2. I know how to go into BIOS. but where do I look for "sda first"?

3.How do I bring up the terminal to type the commands you provided?

RK

---

### Post by rkanth on 2011-07-09
Thanks drs 350, but as I said in my very first post, I'm a tech Zero.

1. I have only a usb start-up disk that I made from Lucid ISO, not a live-cd; will this be enough?

2. I know how to go into BIOS. but where do I look for "sda first"?

3.How do I bring up the terminal to type the commands you provided?

RK

---

### Post by drs305 on 2011-07-09
> **rkanth said:**
> Thanks drs 350, but as I said in my very first post, I'm a tech Zero.

1. I have only a usb start-up disk that I made from Lucid ISO, not a live-cd; will this be enough?

2. I know how to go into BIOS. but where do I look for "sda first"?

3.How do I bring up the terminal to type the commands you provided?

RK

The USB startup disk will work as well as long as it boots you to an Ubuntu Desktop where you can open a terminal, or boots to the command prompt where you can do the same.

In BIOS, you would look for a section called "Boot" or something similar. There should be a section on Boot Priority, and you want to select the 160GB drive (the other is 250GB).

To open a terminal, from the top menu, select Applications, Accessories, Terminal. Or you can ALT-F2 and type the commands or "gnome-terminal" to open a separate terminal window.

---

### Post by rkanth on 2011-07-09
Thanks a lot, drs350, it worked! The computer is booting into Lucid without showing the grub now! And no removal of the Ubuntu Optimiser, either.

Can you just tell me how to be Root on GUIs , please...

Thanks or all the help. Much Appreciated.

RK

---

### Post by drs305 on 2011-07-10
> **rkanth said:**
> Thanks a lot, drs350, it worked! The computer is booting into Lucid without showing the grub now! And no removal of the Ubuntu Optimiser, either.

Can you just tell me how to be Root on GUIs , please...

Glad it's working for you.

For GUI apps, run the command with "gksu" - e.g. "gksu gedit, gksu nautilus". For non-GUI, use "sudo" - "sudo nano".

You can also install "nautilus-gksu" (sudo apt-get install nautilus-gksu) which will add a right click option to the file browser to "open as administrator". This would then allow you to delete folders/files as root, or once you have opened a folder as administrator, clicking on a file would open it 'as root'.

---

### Post by geazzy on 2011-07-11
nice tutorial... :D

---

### Post by SuperFreak on 2011-08-03
I realize this thread is designed to remove Older kernels but what about new kernels that do not seem to work. I have installed Linux 2.6.35.30 and 2.6.39.3 using Kernel Check and found the latter would not boot to a graphical interface just a tty interface. I installed Grub Customizer and hid these two kernels from the Grub menu so it now boots to 2.6.35.28. After I updated the Kernel to 2.6.39.3 I found I could not use K3B it comes up with an error message. So I am wondering if I should remove Linux 2.6.35.30 and 2.6.39.3 completely and if so is that safe and would I just use the instructions for "HOWTO: Remove Older Kernels via GUI"

Thanks

ed: I use 64 bit Ubuntu 10.10

---

### Post by drs305 on 2011-08-03
> **SuperFreak said:**
> I realize this thread is designed to remove Older kernels but what about new kernels that do not seem to work. ... So I am wondering if I should remove Linux 2.6.35.30 and 2.6.39.3 completely and if so is that safe and would I just use the instructions for "HOWTO: Remove Older Kernels via GUI"

Yes. It would be a good idea to remove non-working newer kernels as well, and you can use the same procedures. Since the kernels you want to remove may be higher version numbers, just make sure you know specifically which ones you want to delete.

I'd still recommend using Ubuntu Tweak, no matter whether they are old or new.

You can verify the currently-running (i.e. working) kernel with:```

uname -r
```
Just make sure you keep that one.

---

### Post by SuperFreak on 2011-08-03
Thanks for your response. The newer kernels do not show up in Ubuntu Tweak although they do show up in Grub Customizer. I guess I will need to remove them with the non-graphical tools you provide.

---

### Post by SuperFreak on 2011-08-03
It worked without issue. Thank you

---

### Post by wkitty42 on 2012-06-13
excellent tutorial... i'm glad i finally got to the point of wanting to remove the 20 someodd old kernels (all the way back to 2.6.15-??-server) from my ubuntu servers... since these are dedicated servers, there is no GUI so i'm especially glad for the CLI method...

i gained about 4-5G of space on each one... YAY!

---

### Post by street spirit on 2012-10-07
I don't like waking up an old thread, but this came up as the top result for "ubuntu remove old kernels" in Google.

This is in reply to [_the rmkernel function posted by slakkie_ (post #2)]("http://ubuntuforums.org/showpost.php?p=10479306&postcount=2"):

I was using that shell script as guidance for a Perl script with a similar purpose. I had commented out the part that actually removes the old kernels and modules and just printed the candidates. That's where I noticed that the "linux-firmware" package (no version) is included in the list of packages to purge.

Is that a good idea? I'm hardly a specialist when it comes to kernels, but it looks like that package contains everything in /lib/firmware. I'm running Ubuntu 10.12 (Precise), and it's possible that package names have changed in the meantime.

In any case, be careful to take a good look at the list of packages to remove when you run this script.

---

### Post by DawnDIY on 2012-10-08
Thank you. Now I'm using Ubuntu Tweak to remove older kernels~:p

---

### Post by Cavsfan on 2012-10-08
I just do it the CLI way with terminal. I keep track of what kernels are installed on a text file and keep the last 2 kernels.

Here is my text file for Quantal Quetzel 12.10:
```
sudo apt-get purge linux-headers-3.5.0-6 linux-image-3.5.0-6-generic linux-headers-3.5.0-6-generic linux-image-extra-3.5.0-6-generic    - deleted.

sudo apt-get purge linux-headers-3.5.0-13 linux-image-3.5.0-13-generic linux-headers-3.5.0-13-generic linux-image-extra-3.5.0-13-generic    - deleted.

sudo apt-get purge linux-headers-3.5.0-14 linux-image-3.5.0-14-generic linux-headers-3.5.0-14-generic linux-image-extra-3.5.0-14-generic    - deleted.

sudo apt-get purge linux-headers-3.5.0-15 linux-image-3.5.0-15-generic linux-headers-3.5.0-15-generic linux-image-extra-3.5.0-15-generic    - deleted.

sudo apt-get purge linux-headers-3.5.0-16 linux-image-3.5.0-16-generic linux-headers-3.5.0-16-generic linux-image-extra-3.5.0-16-generic

sudo apt-get purge linux-headers-3.5.0-17 linux-image-3.5.0-17-generic linux-headers-3.5.0-17-generic linux-image-extra-3.5.0-17-generic
```I have a different one for each Ubuntu and each Ubuntu version sometimes has different files that make up the kernel.

Here is the one for Lucid: 
```
sudo apt-get purge linux-headers-2.6.32-29 linux-headers-2.6.32-29-generic linux-image-2.6.32-29-generic    - deleted

sudo apt-get purge linux-headers-2.6.32-30 linux-headers-2.6.32-30-generic linux-image-2.6.32-30-generic    - deleted

sudo apt-get purge linux-headers-2.6.32-31 linux-headers-2.6.32-31-generic linux-image-2.6.32-31-generic    - deleted

sudo apt-get purge linux-headers-2.6.32-32 linux-headers-2.6.32-32-generic linux-image-2.6.32-32-generic    - deleted

sudo apt-get purge linux-headers-2.6.32-33 linux-headers-2.6.32-33-generic linux-image-2.6.32-33-generic    - deleted

sudo apt-get purge linux-headers-2.6.32-34 linux-headers-2.6.32-34-generic linux-image-2.6.32-34-generic    - deleted

sudo apt-get purge linux-headers-2.6.32-35 linux-headers-2.6.32-35-generic linux-image-2.6.32-35-generic    - deleted

sudo apt-get purge linux-headers-2.6.32-36 linux-headers-2.6.32-36-generic linux-image-2.6.32-36-generic    - deleted

sudo apt-get purge linux-headers-2.6.32-37 linux-headers-2.6.32-37-generic linux-image-2.6.32-37-generic    - deleted

sudo apt-get purge linux-headers-2.6.32-38 linux-headers-2.6.32-38-generic linux-image-2.6.32-38-generic    - deleted

sudo apt-get purge linux-headers-2.6.32-39 linux-headers-2.6.32-39-generic linux-image-2.6.32-39-generic    - deleted

sudo apt-get purge linux-headers-2.6.32-40 linux-headers-2.6.32-40-generic linux-image-2.6.32-40-generic    - deleted

sudo apt-get purge linux-headers-2.6.32-41 linux-headers-2.6.32-41-generic linux-image-2.6.32-41-generic    - deleted

sudo apt-get purge linux-headers-2.6.32-42 linux-headers-2.6.32-42-generic linux-image-2.6.32-42-generic

sudo apt-get purge linux-headers-2.6.32-43 linux-headers-2.6.32-43-generic linux-image-2.6.32-43-generic
```PS: I didn't see who the author was. Didn't mean to butt in Drs305! Just thought I'd mention my method. :redface:

---

