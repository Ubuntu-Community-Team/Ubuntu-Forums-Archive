---
title: "Adding Puppy linux iso to multiboot usb"
date: 2015-12-09
forum: Ubuntu/Debian BASED
---

### Post by pqwoerituytrueiwoq on 2015-12-09
I have quiite a few ISOs on my flash drive all bootable with grub2, i wanted to add puppy linux as a live iso like i have everything else
this is my grub.cfg file
i have the puppy linux menut entry in bold, but it does not work, it can't find the puppy_tahr_6.0.2.sfs file that is in the iso
```
insmod part_msdos
insmod fat
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 10A9-AFCE
loadfont /boot/grub/fonts/unicode.pf2
set gfxmode=auto
insmod vbe
insmod vga
insmod gfxterm
terminal_output gfxterm
insmod gfxmenu
loadfont ($root)/boot/grub/themes/ubuntu/dejavu-sans-10.pf2
loadfont ($root)/boot/grub/themes/ubuntu/dejavu-sans-12.pf2
loadfont ($root)/boot/grub/themes/ubuntu/dejavu-sans-bold-14.pf2
insmod png
set theme=($root)/boot/grub/themes/ubuntu/theme.txt
export theme
set timeout=10
set default="1>2"
submenu 'Ubuntu 15.10' --class submenu --id wiley {
    menuentry "Ubuntu 15.10 Desktop 64bit" --class ubuntu --class gnu-linux --id wiley {
        set isofile="/iso/Wiley/ubuntu-15.10-desktop-amd64+mac.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Xubuntu 15.10 Desktop 64bit" --class xubuntu --class gnu-linux --id wiley {
        set isofile="/iso/Wiley/xubuntu-15.10-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Ubuntu MATE 15.10 Desktop 64bit" --class ubuntumate --class gnu-linux --id wiley {
        set isofile="/iso/Wiley/ubuntu-mate-15.10-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Ubuntu Gnome 15.10 Desktop 64bit" --class gnomeubuntu --class gnu-linux --id wiley {
        set isofile="/iso/Wiley/ubuntu-gnome-15.10-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Kubuntu 15.10 Desktop 64bit" --class kubuntu --class gnu-linux --id wiley {
        set isofile="/iso/Wiley/kubuntu-15.10-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Lubuntu 15.10 Desktop 64bit" --class lubuntu --class gnu-linux --id wiley {
        set isofile="/iso/Wiley/lubuntu-15.10-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
}
submenu 'Ubuntu 14.04' --class submenu --id trusty {
    submenu 'Ubuntu 14.04.1 32bit' --class submenu --id trusty_32 {
        menuentry "Xubuntu 14.04.3 Desktop 32bit" --class xubuntu --class gnu-linux --id trusty_32 {
            set isofile="/iso/Trusty/xubuntu-14.04.3-desktop-i386.iso"
            loopback loop $isofile
            linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt splash --
            initrd (loop)/casper/initrd.lz
        }
        menuentry "Lubuntu 14.04.3 Desktop 32bit" --class lubuntu --class gnu-linux --id trusty_32 {
            set isofile="/iso/Trusty/lubuntu-14.04.3-desktop-i386.iso"
            loopback loop $isofile
            linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt splash --
            initrd (loop)/casper/initrd.lz
        }
        menuentry "Ubuntu mini 32bit" --class ubuntu --class gnu-linux --id trusty_32 {
            set isofile="/iso/Trusty/mini-i386.iso"
            loopback loop $isofile
            linux (loop)/linux
            initrd (loop)/initrd.gz
        }
    }
    menuentry "Ubuntu 14.04.3 Desktop 64bit" --class ubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/ubuntu-14.04.3-desktop-amd64+mac.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Xubuntu 14.04.3 Desktop 64bit" --class xubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/xubuntu-14.04.3-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Ubuntu MATE 14.04.2 Desktop 64bit" --class ubuntumate --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/ubuntu-mate-14.04.2-LTS-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Ubuntu Gnome 14.04.3 Desktop 64bit" --class gnomeubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/ubuntu-gnome-14.04.3-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Kubuntu 14.04.3 Desktop 64bit" --class kubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/kubuntu-14.04.3-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Lubuntu 14.04.3 Desktop 64bit" --class lubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/lubuntu-14.04.3-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Ubuntu Server 14.04.3 64bit" --class ubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/ubuntu-14.04.3-server-amd64.iso"
        loopback loop $isofile
        linux (loop)/install/vmlinuz  file=/cdrom/preseed/ubuntu-server.seed quiet --
        initrd (loop)/install/initrd.gz

    }
    menuentry "Ubuntu mini 64bit" --class ubuntu --class gnu-linux --id trusty {
        set isofile="/iso/Trusty/mini-amd64.iso"
        loopback loop $isofile
        linux (loop)/linux
        initrd (loop)/initrd.gz
    }
}
submenu 'Linux Mint 17' --class submenu --id rosa {
    menuentry "Linux Mint 17.3 Cinnamon 64bit" --class linuxmint --class gnu-linux --id rosa {
        set isofile="/iso/Trusty/linuxmint-17.3-cinnamon-64bit.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz file=/cdrom/preseed/linuxmint.seed boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Linux Mint 17.3 Mate 64bit" --class linuxmint --class gnu-linux --id rosa {
        set isofile="/iso/Trusty/linuxmint-17.3-mate-64bit.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz file=/cdrom/preseed/linuxmint.seed boot=casper initrd=/casper/initrd.lz iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
}
submenu 'Ubuntu 13.04' --class submenu --id raring {
    submenu 'Ubuntu 13.04 32bit' --class submenu --id raring_32 {
        menuentry "Xubuntu 13.04 Desktop 32bit" --class xubuntu --class gnu-linux --id raring_32 {
            set isofile="/iso/Raring/xubuntu-13.04-desktop-i386.iso"
            loopback loop $isofile
            linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt splash --
            initrd (loop)/casper/initrd.lz
        }
    }
    menuentry "Ubuntu 13.04 Desktop 64bit" --class ubuntu --class gnu-linux --id raring {
        set isofile="/iso/Raring/ubuntu-13.04-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Xubuntu 13.04 Desktop 64bit" --class xubuntu --class gnu-linux --id raring {
        set isofile="/iso/Raring/xubuntu-13.04-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Ubuntu Gnome 13.04 Desktop 64bit" --class gnomeubuntu --class gnu-linux --id raring {
        set isofile="/iso/Raring/ubuntu-gnome-13.04-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Kubuntu 13.04 Desktop 64bit" --class kubuntu --class gnu-linux --id raring {
        set isofile="/iso/Raring/kubuntu-13.04-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Lubuntu 13.04 Desktop 64bit" --class lubuntu --class gnu-linux --id raring {
        set isofile="/iso/Raring/lubuntu-13.04-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
}
submenu 'Linux Mint 15' --class submenu --id olivia {
    menuentry "Linux Mint 15 Cinnamon 64bit" --class linuxmint --class gnu-linux --id olivia {
        set isofile="/iso/Raring/linuxmint-15-cinnamon-dvd-64bit.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.lz iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Linux Mint 15 Mate 64bit" --class linuxmint --class gnu-linux --id olivia {
        set isofile="/iso/Raring/linuxmint-15-mate-dvd-64bit.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.lz iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
}
[B]menuentry "Puppy Linux" {
    set isofile="/iso/Trusty/tahr-6.0.2_PAE.iso"
    loopback loop $isofile
    linux (loop)/vmlinuz iso-scan/filename=$isofile pmedia=usbhd 
    initrd (loop)/initrd.gz
}[/B]
menuentry "Parted Magic 2013" --class pmagic --class gnu-linux {
    set isofile="/iso/pmagic_2013_05_01.iso"
    loopback loop $isofile
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off load_ramdisk=1 prompt_ramdisk=0 rw vga=normal loglevel=9 max_loop=256 vmalloc=384MiB
    initrd (loop)/pmagic/initrd.img
}
menuentry "DBAN ISO (Delete EVERYTHING)" --class dban {
    set isofile="/iso/dban.iso"
    loopback loop $isofile
    linux (loop)/DBAN.BZI nuke="dwipe" iso-scan/filename=$isofile silent --
} 
menuentry "Memtest 86+" --class recovery {
    linux16 /memtest86+.bin
}
# menuentry "Tinycore ISO" {
#  loopback loop /tinycore.iso
#  linux (loop)/boot/bzImage --
#  initrd (loop)/boot/tinycore.gz
# }
# menuentry "SystemRescueCd" {
#  loopback loop /systemrescuecd.iso
#  linux (loop)/isolinux/rescuecd isoloop=/systemrescuecd.iso setkmap=us docache dostartx
#  initrd (loop)/isolinux/initram.igz
#}


```

---

### Post by C.S.Cameron on 2016-11-26
If you save a copy of **puppy_tahr_6.0.2.sfs** to the same partirion as you save to, it should work.

---

