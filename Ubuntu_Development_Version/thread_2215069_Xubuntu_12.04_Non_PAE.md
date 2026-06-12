---
title: "Xubuntu 12.04 Non PAE"
date: 2014-04-04
forum: Ubuntu Development Version
---

### Post by frank18 on 2014-04-04
Xubuntu 14.04 is an outstanding distro but I just  want to say one last thing about Xubuntu 14.04,it's a pity that i can't install on a machine that is no PAE.

---

### Post by mörgæs on 2014-04-04
You can, and it's easy:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by Elfy on 2014-04-04
> **mörgæs said:**
> You can, and it's easy:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

isn't that a lubuntu wiki?

---

### Post by frank18 on 2014-04-04
> **mörgæs said:**
> You can, and it's easy:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)


thanks but i think it doesnt work!

This is an Sony Vaio Pentium M 

i put in xubuntu 14.04 in the drive and booted and it has this message on screen.


ERROR: PAE is desable on this Pentium M

(PAE can potentially be enable with Kernel parameter
"forcepae" -this is unsupported, may cause unknown 
problems ,and will taint the Kernel)

This Kernel requires the following features not present on the CPU:
pae

Unable to boot -please use a Kernel Appropriate for you CPU.

---

### Post by mörgæs on 2014-04-04
The kernel parameter works for all 14.04 Buntus. 
In the wiki I only mentioned Lubuntu because it's the lightest, but everything is valid for X/K/Ubuntu as well.

---

### Post by frank18 on 2014-04-04
> **mörgæs said:**
> The kernel parameter works for all 14.04 Buntus. 
In the wiki I only mentioned Lubuntu because it's the lightest, but everything is valid for X/K/Ubuntu as well.



I have a Lubuntu 13.10 and it does not boot either and gives same ERROR and have no way to make it boot f6 wont do anything.

---

### Post by mörgæs on 2014-04-04
Please take your time to read in detail the text I posted. You will notice that the approach for 13.10 and 14.04 have not much in common.

Signing out.

---

### Post by frank18 on 2014-04-04
> **mörgæs said:**
> The kernel parameter works for all 14.04 Buntus. 
In the wiki I only mentioned Lubuntu because it's the lightest, but everything is valid for X/K/Ubuntu as well.

No avail;i tried with lubuntu 13.10 i get the lubuntu screen, try lubuntu without install, install lubuntu, and so on,press f6 and i add the forcepae to the string and it doen't boot and  says samething,



This Kernel requires the following features not present in you CPU PAE
unable to boot-please use a kernel appropriate for you CPU

---

### Post by Z80A on 2014-04-05
I am helping out a few people with migrating from Windows XP to Ubuntu (mostly Lubuntu). On one machine, a Dell Latitude D505 (Celeron procerssor), I was also given the PAE error message when booting with Lubuntu 14.04 Beta 2: [INDENT][B] 
(PAE can potentially be enable with Kernel parameter
"forcepae" -this is unsupported, may cause unknown 
problems ,and will taint the Kernel)[/B]
[/INDENT]
 
Trying booting with the **forcepae** option resolved this, and I am just about to go ahead and install this early Lubuntu 14.04 as replacement for Windows XP (before Tuesday). 

But given I use this workaround that will "*...taint the Kernel...*", I feel slightly uncomfortable about how this will work when 14.04 is being updated. What happens when kernel updates are pushed out? Do I need to be concerned when handing this machine over with this installation? Is the option simply only needed during initial installation and never during updates (especially of the kernel)?

---

### Post by mörgæs on 2014-04-05
I don't know what tainted means in this context, but I have not experienced anything strange. 
 
The forcepae boot options sticks through kernel updates. You only have to set it once.

---

### Post by Z80A on 2014-04-05
...exactly, the word *tainted* was what triggered me and did not give any good tecnical hints. Anyway, it sounds good that you haven't experienced anything and the **forcepae** will persist on later kernel updates, so I will go ahead with this migration to 14.04 Beta 2. Too bad that timing of Windows XP end-of-life was not better aligned with the release of 14.04, but this Dell Latitude D505 will get some 3-5 more years of use... ;)

---

### Post by Z80A on 2014-04-11
Did another install (Ubuntu 14.04 Beta "2") on a HP nc8000 (Pentium Mobile) and used **forcepae** and it all worked nicely. Took an update and it failed due to some dependencies for **linux-image-extra-3.13.0-23-generic** and was suggested to use** apt-get install -f**. Got this

```
Preparing to unpack .../linux-image-3.13.0-23-generic_3.13.0-23.45_i386.deb ...
This kernel does not support a non-PAE CPU.
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-23-generic_3.13.0-23.45_i386.deb (--unpack):
```

What do I need to do, to make this machine appear as PAE capable? Was under the impression that once installed this way, it would persist. :?

---

### Post by mörgæs on 2014-04-12
Have you checked that the boot option is stuck?

If the boot option is still there I have no other explanation than it's a bug in the development release. The option works fine for me.

---

### Post by Z80A on 2014-04-12
...ehm? The **forcepae** option? And where do I find it now? GRUB? I mean; the PC can reboot and Ubuntu starts up, but Software Update and Ubuntu Software Center indicates the above problem installing an updated kernel. I am sure I can do another install and manually insert the option - do I need to have it inserted somewhere on the installed system? Sorry about the fuss - not familiar with this...

---

### Post by mörgæs on 2014-04-12
If the computer boots then the option is there. 

Please close all applications and run the commands
```
sudo apt-get update
sudo apt-get dist-upgrade

```and post the results in CODE tags.

---

### Post by Z80A on 2014-04-12
As per your guidance. I realize that certain passages in the output will be non-English, but their is a fair chance you will understand anyway:

```
******@nc8000:~$ sudo apt-get update
Ignorerer http://dk.archive.ubuntu.com trusty InRelease
Ignorerer http://extras.ubuntu.com trusty InRelease        
Ignorerer http://security.ubuntu.com trusty-security InRelease
Ignorerer http://archive.canonical.com trusty InRelease     
Ignorerer http://dk.archive.ubuntu.com trusty-updates InRelease
Ignorerer http://dk.archive.ubuntu.com trusty-backports InRelease
Havde http://extras.ubuntu.com trusty Release.gpg           
Havde http://security.ubuntu.com trusty-security Release.gpg
Havde http://archive.canonical.com trusty Release.gpg       
Havde http://dk.archive.ubuntu.com trusty Release.gpg       
Havde http://extras.ubuntu.com trusty Release                                  
Havde http://dk.archive.ubuntu.com trusty-updates Release.gpg                  
Havde http://dk.archive.ubuntu.com trusty-backports Release.gpg
Havde http://security.ubuntu.com trusty-security Release    
Havde http://archive.canonical.com trusty Release           
Havde http://dk.archive.ubuntu.com trusty Release           
Havde http://dk.archive.ubuntu.com trusty-updates Release
Havde http://dk.archive.ubuntu.com trusty-backports Release
Havde http://extras.ubuntu.com trusty/main Sources
Havde http://extras.ubuntu.com trusty/main i386 Packages        
Havde http://security.ubuntu.com trusty-security/main Sources   
Havde http://security.ubuntu.com trusty-security/restricted Sources            
Havde http://archive.canonical.com trusty/partner Sources                      
Havde http://dk.archive.ubuntu.com trusty/main Sources                         
Havde http://dk.archive.ubuntu.com trusty/restricted Sources                   
Havde http://security.ubuntu.com trusty-security/universe Sources              
Havde http://archive.canonical.com trusty/partner i386 Packages                
Havde http://dk.archive.ubuntu.com trusty/universe Sources                     
Havde http://security.ubuntu.com trusty-security/multiverse Sources            
Havde http://dk.archive.ubuntu.com trusty/multiverse Sources                   
Havde http://dk.archive.ubuntu.com trusty/main i386 Packages                   
Havde http://security.ubuntu.com trusty-security/main i386 Packages            
Havde http://dk.archive.ubuntu.com trusty/restricted i386 Packages             
Havde http://dk.archive.ubuntu.com trusty/universe i386 Packages               
Havde http://security.ubuntu.com trusty-security/restricted i386 Packages      
Havde http://dk.archive.ubuntu.com trusty/multiverse i386 Packages             
Havde http://security.ubuntu.com trusty-security/universe i386 Packages        
Havde http://dk.archive.ubuntu.com trusty/main Translation-da                  
Havde http://security.ubuntu.com trusty-security/multiverse i386 Packages      
Havde http://dk.archive.ubuntu.com trusty/main Translation-en                  
Havde http://dk.archive.ubuntu.com trusty/multiverse Translation-da            
Havde http://dk.archive.ubuntu.com trusty/multiverse Translation-en            
Havde http://security.ubuntu.com trusty-security/main Translation-en           
Havde http://dk.archive.ubuntu.com trusty/restricted Translation-da            
Havde http://dk.archive.ubuntu.com trusty/restricted Translation-en            
Havde http://dk.archive.ubuntu.com trusty/universe Translation-da              
Ignorerer http://extras.ubuntu.com trusty/main Translation-da_DK               
Havde http://security.ubuntu.com trusty-security/multiverse Translation-en     
Havde http://dk.archive.ubuntu.com trusty/universe Translation-en              
Havde http://dk.archive.ubuntu.com trusty-updates/main Sources                 
Ignorerer http://extras.ubuntu.com trusty/main Translation-da                  
Havde http://dk.archive.ubuntu.com trusty-updates/restricted Sources           
Ignorerer http://archive.canonical.com trusty/partner Translation-da_DK        
Ignorerer http://extras.ubuntu.com trusty/main Translation-en                  
Havde http://dk.archive.ubuntu.com trusty-updates/universe Sources             
Havde http://dk.archive.ubuntu.com trusty-updates/multiverse Sources
Ignorerer http://archive.canonical.com trusty/partner Translation-da
Havde http://dk.archive.ubuntu.com trusty-updates/main i386 Packages
Havde http://dk.archive.ubuntu.com trusty-updates/restricted i386 Packages
Ignorerer http://archive.canonical.com trusty/partner Translation-en
Havde http://dk.archive.ubuntu.com trusty-updates/universe i386 Packages
Havde http://dk.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Havde http://security.ubuntu.com trusty-security/restricted Translation-en
Havde http://dk.archive.ubuntu.com trusty-updates/main Translation-en
Havde http://security.ubuntu.com trusty-security/universe Translation-en
Havde http://dk.archive.ubuntu.com trusty-updates/multiverse Translation-en
Havde http://dk.archive.ubuntu.com trusty-updates/restricted Translation-en
Havde http://dk.archive.ubuntu.com trusty-updates/universe Translation-en
Havde http://dk.archive.ubuntu.com trusty-backports/main Sources
Havde http://dk.archive.ubuntu.com trusty-backports/restricted Sources
Havde http://dk.archive.ubuntu.com trusty-backports/universe Sources
Havde http://dk.archive.ubuntu.com trusty-backports/multiverse Sources
Havde http://dk.archive.ubuntu.com trusty-backports/main i386 Packages
Havde http://dk.archive.ubuntu.com trusty-backports/restricted i386 Packages
Havde http://dk.archive.ubuntu.com trusty-backports/universe i386 Packages
Havde http://dk.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Havde http://dk.archive.ubuntu.com trusty-backports/main Translation-en
Havde http://dk.archive.ubuntu.com trusty-backports/multiverse Translation-en
Havde http://dk.archive.ubuntu.com trusty-backports/restricted Translation-en
Havde http://dk.archive.ubuntu.com trusty-backports/universe Translation-en
Ignorerer http://security.ubuntu.com trusty-security/main Translation-da_DK
Ignorerer http://security.ubuntu.com trusty-security/main Translation-da
Ignorerer http://security.ubuntu.com trusty-security/multiverse Translation-da_DK
Ignorerer http://security.ubuntu.com trusty-security/multiverse Translation-da
Ignorerer http://security.ubuntu.com trusty-security/restricted Translation-da_DK
Ignorerer http://security.ubuntu.com trusty-security/restricted Translation-da
Ignorerer http://security.ubuntu.com trusty-security/universe Translation-da_DK
Ignorerer http://security.ubuntu.com trusty-security/universe Translation-da
Ignorerer http://dk.archive.ubuntu.com trusty/main Translation-da_DK
Ignorerer http://dk.archive.ubuntu.com trusty/multiverse Translation-da_DK
Ignorerer http://dk.archive.ubuntu.com trusty/restricted Translation-da_DK
Ignorerer http://dk.archive.ubuntu.com trusty/universe Translation-da_DK
Ignorerer http://dk.archive.ubuntu.com trusty-updates/main Translation-da_DK
Ignorerer http://dk.archive.ubuntu.com trusty-updates/main Translation-da
Ignorerer http://dk.archive.ubuntu.com trusty-updates/multiverse Translation-da_DK
Ignorerer http://dk.archive.ubuntu.com trusty-updates/multiverse Translation-da
Ignorerer http://dk.archive.ubuntu.com trusty-updates/restricted Translation-da_DK
Ignorerer http://dk.archive.ubuntu.com trusty-updates/restricted Translation-da
Ignorerer http://dk.archive.ubuntu.com trusty-updates/universe Translation-da_DK
Ignorerer http://dk.archive.ubuntu.com trusty-updates/universe Translation-da
Ignorerer http://dk.archive.ubuntu.com trusty-backports/main Translation-da_DK
Ignorerer http://dk.archive.ubuntu.com trusty-backports/main Translation-da
Ignorerer http://dk.archive.ubuntu.com trusty-backports/multiverse Translation-da_DK
Ignorerer http://dk.archive.ubuntu.com trusty-backports/multiverse Translation-da
Ignorerer http://dk.archive.ubuntu.com trusty-backports/restricted Translation-da_DK
Ignorerer http://dk.archive.ubuntu.com trusty-backports/restricted Translation-da
Ignorerer http://dk.archive.ubuntu.com trusty-backports/universe Translation-da_DK
Ignorerer http://dk.archive.ubuntu.com trusty-backports/universe Translation-da
Indlæser pakkelisterne... Færdig
******@nc8000:~$ sudo apt-get dist-upgrade
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
Du kan muligvis rette dette ved at køre »apt-get -f install«.
Følgende pakker har uopfyldte afhængigheder:
 linux-image-extra-3.13.0-23-generic : Afhængigheder: linux-image-3.13.0-23-generic men den kan ikke installeres
 linux-image-generic : Afhængigheder: linux-image-3.13.0-23-generic men den kan ikke installeres
E: Uopfyldte afhængigheder. Prøv med -f.
******@nc8000:~$
```

---

### Post by mörgæs on 2014-04-13
- and the complete output from **sudo apt-get -f install**, please?

---

### Post by Z80A on 2014-04-13
...again, quite a bit of localization going on here:
```
******@nc8000:~$ sudo apt-get -f install
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
Retter afhængigheder ... Færdig
Følgende pakker blev installeret automatisk, og behøves ikke længere:
  linux-headers-3.13.0-23 linux-headers-3.13.0-23-generic
Brug »apt-get autoremove« til at fjerne dem.
Følgende yderligere pakker vil blive installeret:
  linux-generic linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-headers-generic linux-image-3.13.0-24-generic
  linux-image-extra-3.13.0-24-generic linux-image-generic
Foreslåede pakker:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
Følgende pakker vil blive AFINSTALLERET:
  linux-image-extra-3.13.0-23-generic
Følgende NYE pakker vil blive installeret:
  linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic
Følgende pakker vil blive opgraderet:
  linux-generic linux-headers-generic linux-image-generic
3 opgraderes, 4 nyinstalleres, 1 afinstalleres og 131 opgraderes ikke.
3 ikke fuldstændigt installerede eller afinstallerede.
61,1 MB skal hentes fra arkiverne.
Efter denne handling, vil 109 MB yderligere diskplads være brugt.
Vil du fortsætte? [J/n] J
Henter:1 http://dk.archive.ubuntu.com/ubuntu/ trusty/main linux-headers-3.13.0-24 all 3.13.0-24.46 [8.869 kB]
Henter:2 http://dk.archive.ubuntu.com/ubuntu/ trusty/main linux-headers-3.13.0-24-generic i386 3.13.0-24.46 [697 kB]
Henter:3 http://dk.archive.ubuntu.com/ubuntu/ trusty/main linux-generic i386 3.13.0.24.28 [1.784 B]
Henter:4 http://dk.archive.ubuntu.com/ubuntu/ trusty/main linux-headers-generic i386 3.13.0.24.28 [2.322 B]
Henter:5 http://dk.archive.ubuntu.com/ubuntu/ trusty/main linux-image-3.13.0-24-generic i386 3.13.0-24.46 [14,6 MB]
Henter:6 http://dk.archive.ubuntu.com/ubuntu/ trusty/main linux-image-extra-3.13.0-24-generic i386 3.13.0-24.46 [37,0 MB]
Henter:7 http://dk.archive.ubuntu.com/ubuntu/ trusty/main linux-image-generic i386 3.13.0.24.28 [2.336 B]
Hentede 61,1 MB på 29s (2.042 kB/s)                                            
Vælger tidligere fravalgt pakke linux-headers-3.13.0-24.
(Læser database ... 195519 filer og kataloger installeret i øjeblikket.)
Preparing to unpack .../linux-headers-3.13.0-24_3.13.0-24.46_all.deb ...
Unpacking linux-headers-3.13.0-24 (3.13.0-24.46) ...
Vælger tidligere fravalgt pakke linux-headers-3.13.0-24-generic.
Preparing to unpack .../linux-headers-3.13.0-24-generic_3.13.0-24.46_i386.deb ...
Unpacking linux-headers-3.13.0-24-generic (3.13.0-24.46) ...
Preparing to unpack .../linux-generic_3.13.0.24.28_i386.deb ...
Unpacking linux-generic (3.13.0.24.28) over (3.13.0.23.27) ...
Preparing to unpack .../linux-headers-generic_3.13.0.24.28_i386.deb ...
Unpacking linux-headers-generic (3.13.0.24.28) over (3.13.0.23.27) ...
Vælger tidligere fravalgt pakke linux-image-3.13.0-24-generic.
Preparing to unpack .../linux-image-3.13.0-24-generic_3.13.0-24.46_i386.deb ...
This kernel does not support a non-PAE CPU.
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-24-generic_3.13.0-24.46_i386.deb (--unpack):
 underproces nyt pre-installation-script returnerede afslutningsstatus 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
Vælger tidligere fravalgt pakke linux-image-extra-3.13.0-24-generic.
Preparing to unpack .../linux-image-extra-3.13.0-24-generic_3.13.0-24.46_i386.deb ...
Unpacking linux-image-extra-3.13.0-24-generic (3.13.0-24.46) ...
Preparing to unpack .../linux-image-generic_3.13.0.24.28_i386.deb ...
Unpacking linux-image-generic (3.13.0.24.28) over (3.13.0.23.27) ...
Der opstod fejl under behandlingen:
 /var/cache/apt/archives/linux-image-3.13.0-24-generic_3.13.0-24.46_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
******@nc8000:~$ 
```

---

### Post by devzero-c on 2014-04-13
please make sure the forcepae bootparam is also added to your grub.cfg.

initially booting with forcepae is probably not sufficient, as ubuntu will not automatically add bootparams to the grub.cfg. other distro`s do that...

---

### Post by Z80A on 2014-04-13
Never tinkered with **boot/grub/grub.cfg** before. Noted the "DO NOT EDIT THIS FILE" remark - will it be overwritten? Where would I add **forcepae**?

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  44c67bb1-6f68-4c09-9168-c3e8d9ff7fef
else
  search --no-floppy --fs-uuid --set=root 44c67bb1-6f68-4c09-9168-c3e8d9ff7fef
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=da_DK
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-44c67bb1-6f68-4c09-9168-c3e8d9ff7fef' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  44c67bb1-6f68-4c09-9168-c3e8d9ff7fef
    else
      search --no-floppy --fs-uuid --set=root 44c67bb1-6f68-4c09-9168-c3e8d9ff7fef
    fi
    linux    /boot/vmlinuz-3.13.0-19-generic root=UUID=44c67bb1-6f68-4c09-9168-c3e8d9ff7fef ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-19-generic
}
submenu 'Avancerede indstillinger for Ubuntu' $menuentry_id_option 'gnulinux-advanced-44c67bb1-6f68-4c09-9168-c3e8d9ff7fef' {
    menuentry 'Ubuntu, med Linux 3.13.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-19-generic-advanced-44c67bb1-6f68-4c09-9168-c3e8d9ff7fef' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  44c67bb1-6f68-4c09-9168-c3e8d9ff7fef
        else
          search --no-floppy --fs-uuid --set=root 44c67bb1-6f68-4c09-9168-c3e8d9ff7fef
        fi
        echo    'Indlæser Linux 3.13.0-19-generic ...'
        linux    /boot/vmlinuz-3.13.0-19-generic root=UUID=44c67bb1-6f68-4c09-9168-c3e8d9ff7fef ro  quiet splash $vt_handoff
        echo    'Indlæser start-ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-19-generic-recovery-44c67bb1-6f68-4c09-9168-c3e8d9ff7fef' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  44c67bb1-6f68-4c09-9168-c3e8d9ff7fef
        else
          search --no-floppy --fs-uuid --set=root 44c67bb1-6f68-4c09-9168-c3e8d9ff7fef
        fi
        echo    'Indlæser Linux 3.13.0-19-generic ...'
        linux    /boot/vmlinuz-3.13.0-19-generic root=UUID=44c67bb1-6f68-4c09-9168-c3e8d9ff7fef ro recovery nomodeset 
        echo    'Indlæser start-ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-19-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  44c67bb1-6f68-4c09-9168-c3e8d9ff7fef
    else
      search --no-floppy --fs-uuid --set=root 44c67bb1-6f68-4c09-9168-c3e8d9ff7fef
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  44c67bb1-6f68-4c09-9168-c3e8d9ff7fef
    else
      search --no-floppy --fs-uuid --set=root 44c67bb1-6f68-4c09-9168-c3e8d9ff7fef
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Microsoft Windows XP Professional (på /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-FEF4D3BAF4D372FF' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  FEF4D3BAF4D372FF
    else
      search --no-floppy --fs-uuid --set=root FEF4D3BAF4D372FF
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

---

### Post by devzero-c on 2014-04-13
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) -> Fixing reboot/shutdown freezes

---

### Post by plucky on 2014-04-13
> Never tinkered with boot/grub/grub.cfg before. Noted the "DO NOT EDIT THIS FILE" remark - will it be overwritten? Where would I add forcepae?


To put **forcepae** into the grub.cfg file you need to edit the **etc/default/grub** file and put your changes into the ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash forcepae"
``` line.

Then run ```
sudo update-grub
``` to add the parameters to the **grub.cfg** file.

Good Luck

---

### Post by Z80A on 2014-04-13
Okay, this did the trick, I think - thanks everybody. Got a few errors in the process (14.04 still beta, right?). I guess the procedure for reviving old non-PAE machines involves a bit more than than just booting with the forcepae boot parameter. Summing up, would this be the right process?

[LIST]
[*]Booting with the **forcepae** boot parameter 
[*]Install Ubuntu 
[*]Add forcepae to **etc/default/grub** (e.g **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash forcepae"**) 
[*]Execute **sudo update-grub** 
[*]Reboot 
[*]Execute **sudo apt-get update** 
[*]Execute **sudo apt-get dist-upgrade** 
[*]Execute **sudo apt-get -f install** 
[*]Take what ever updates available... 
[/LIST]
 Should we have this included somewhere for easy access to those needing support for using the forcepae feature? I can not be the only one, right?

---

### Post by mörgæs on 2014-04-13
You are the only one that I have heard of. Before broadcasting the solution I think it's better to see if others get into the same problem.

Thanks for chipping in, Devzero and Plucky.

---

### Post by Yellow Pasque on 2014-04-14
Unless this is the same person, I think it's safe to say that the forcepae option needs to be manually added to allow kernel updates: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307105](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307105)

---

### Post by Z80A on 2014-04-14
> **Temüjin said:**
> Unless this is the same person...

It's not me, but it is a very consistent description. I can add that I have the exact same issue with a Dell Latitude D505 (Celeron M), but now I know the fix... :)

---

### Post by sudodus on 2014-04-14
It is also my experience (from my IBM Thinkpad T42 with a Pentium M processor), that forcepae must be added in grub for kernel upgrades to work. 

The end result will be similar to that of fake-pae (that was used in previous versions).

---

### Post by Yellow Pasque on 2014-04-14
> **mörgæs said:**
> I don't know what tainted means in this context, but I have not experienced anything strange.

Tainted usually means you're running a binary driver, and kernel devs won't accept bug reports. I don't see how that applies here, since the Pentium M's actually support PAE, but don't report it correctly. I guess if the forcepae option works on other CPU's that really don't support PAE, the tainted label would be justified, but I don't know enough about the forcepae and what systems it runs on to say for sure.

---

### Post by mörgæs on 2014-04-14
I installed 3.13.0-17-generic #37 and dist-upgraded in several steps to 3.13.0-24-generic #46. Only specified forcepae at install, no manual tweaking of Grub or the like. Everything works. 

If we can use this case for comparison I'm ready to do some testing.

---

### Post by frank18 on 2014-04-14
> **Z80A said:**
> Okay, this did the trick, I think - thanks everybody. Got a few errors in the process (14.04 still beta, right?). I guess the procedure for reviving old non-PAE machines involves a bit more than than just booting with the forcepae boot parameter. Summing up, would this be the right process?

[LIST]
[*]Booting with the **forcepae** boot parameter 
[*]Install Ubuntu
[*]Execute **su**
[*]Add forcepae to **etc/default/grub** (e.g **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash forcepae"**)
[*]**do update-grub** 
[*]Reboot 
[*]Execute **sudo apt-get update** 
[*]Execute **sudo apt-get dist-upgrade** 
[*]Execute **sudo apt-get -f install** 
[*]Take what ever updates available... 
[/LIST]
 Should we have this included somewhere for easy access to those needing support for using the forcepae feature? I can not be the only one, right?

Hi Z80A; can be more specific on how to do those procedures,i have a Sony Vaio 
Intel M and tried to force non pae but did not work. How i do the bellow commands 
forgive me for being so dam


[LIST]
[*]Add forcepae to **etc/default/grub** (e.g **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash forcepae"**)
[*]**do update-grub**
[*]Reboot
[*]Execute **sudo apt-get update**
[*]Execute **sudo apt-get dist-upgrade**
[*]Execute **sudo apt-get -f install**
[/LIST]

---

### Post by sudodus on 2014-04-15
See this thread
[URL="http://ubuntuforums.org/showthread.php?t=2216986"]
forcepae boot option not automatically added in  /etc/default/grub[/URL]

and this bug report

[https://bugs.launchpad.net/ubuntu/+s...x/+bug/1307862]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307862")

---

### Post by frank18 on 2014-04-15
> **sudodus said:**
> See this thread
[URL="http://ubuntuforums.org/showthread.php?t=2216986"]
forcepae boot option not automatically added in  /etc/default/grub[/URL]

and this bug report

[https://bugs.launchpad.net/ubuntu/+s...x/+bug/1307862]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307862")

I made an mini iso of ubuntu 12.04 and 1310 lubuntu and none of them passes the ubuntu logo (install)(install from command line).

---

### Post by mörgæs on 2014-04-15
For 13.10 the mini-ISO demands PAE.
For 12.04 there are two mini-ISO's. Are you sure that you picked the non-PAE one?

---

### Post by sudodus on 2014-04-16
> **frank18 said:**
> I made an mini iso of ubuntu 12.04 and 1310 lubuntu and none of them passes the ubuntu logo (install)(install from command line).

Forcepae is new and only available in (Trusty to become) 14.04 LTS

You can use fake-pae with 13.10. See this link

[Lubuntu-fake-PAE]("https://help.ubuntu.com/community/Lubuntu-fake-PAE")

---

### Post by Yellow Pasque on 2014-04-16
> Just put the forcepae option after the "--" entry on the installer command line and it will be copied to the target system. The "--" entry defines the boundary between options which are specific to the installer and ones that are copied to the target system.

-- Colin Watson, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307105/comments/8](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307105/comments/8)

---

### Post by sudodus on 2014-04-16
> **Temüjin said:**
> -- Colin Watson, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307105/comments/8](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307105/comments/8)

+1

... and I have edited a wiki page, that will be linked to the Lubuntu wiki page soon. It can be seen now via Edubuntu

[https://wiki.edubuntu.org/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.edubuntu.org/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

---

### Post by chrb on 2014-04-17
> **Temüjin said:**
> Tainted usually means you're running a binary driver, and kernel devs won't accept bug reports. I don't see how that applies here, since the Pentium M's actually support PAE, but don't report it correctly. I guess if the forcepae option works on other CPU's that really don't support PAE, the tainted label would be justified, but I don't know enough about the forcepae and what systems it runs on to say for sure.Tainting is done when there is an aspect of the system that could cause the kernel to crash but the cause of the crash is not the kernel code itself. In this case, nobody knows why Intel disabled PAE in the Pentium M - it may be that there are situations where it generates errors, and if that happens then the kernel developers don't want to be bothered with crash reports because it isn't their fault and there is nothing they can do about it.

---

### Post by mörgæs on 2014-04-17
Sounds reasonable...

---

