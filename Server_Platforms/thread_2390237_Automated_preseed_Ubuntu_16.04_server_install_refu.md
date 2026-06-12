---
title: "Automated preseed Ubuntu 16.04 server install refuses to not create swap"
date: 2018-04-27
forum: Server Platforms
---

### Post by ju2wheels on 2018-04-27
Hi all, Im trying to preseed a Ubuntu server install and for the most part everything is working the way I want it to. The only problem I am having is that I cant get the preseed partman-auto to NOT create a swap partition. I have no idea why its even creating one since I havent even defined one in my recipe string. The disk its using is a fresh unpartitioned disk. The other odd thing is that aside from it creating a SWAP I dont want, the options for the root disk are not being saved in /etc/fstab for some reason.

Kernel boot options:

```

auto
console-setup/ask_detect=false
debian-installer/allow_unauthenticated_ssl=true
debian-installer/country=US
debian-installer/language=en
debian-installer/locale=en_US.UTF-8
keyboard-configuration/layout=USA
keyboard-configuration/layoutcode=us
netcfg/get_domain=vm
netcfg/get_hostname=myhost
preseed/url=http://192.168.1.5/preseed.cfg

```

Preseed:

```

### Localization
d-i debian-installer/allow_unauthenticated_ssl boolean true
d-i debian-installer/country string US
d-i debian-installer/language string en
d-i debian-installer/locale select en_US.UTF-8

# Keyboard selection.
d-i keyboard-configuration/modelcode string pc105
d-i keyboard-configuration/layout select English (US)
d-i keyboard-configuration/layoutcode string us
d-i keyboard-configuration/variant select English (US)
d-i keyboard-configuration/xkb-keymap select us

### Network configuration
d-i netcfg/choose_interface select auto
d-i netcfg/link_wait_timeout string 15
d-i netcfg/dhcp_timeout string 60
d-i netcfg/dhcpv6_timeout string 60
d-i netcfg/get_hostname string myhost
d-i netcfg/get_domain string vm
d-i netcfg/wireless_wep string
d-i hw-detect/load_firmware boolean true

### Mirror settings
d-i mirror/protocol string http
d-i mirror/country string manual
d-i mirror/http/hostname string archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

### Account setup
d-i passwd/root-login boolean false
d-i passwd/user-fullname string Ubuntu User 
d-i passwd/user-uid string 1000
d-i passwd/username string ubuntu
d-i passwd/user-password-crypted password !!
d-i user-setup/encrypt-home boolean false

### Clock and time zone setup
d-i clock-setup/utc boolean true
d-i time/zone string US/Eastern
d-i clock-setup/ntp boolean true

### Partitioning
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true
d-i partman-basicfilesystems/no_swap boolean false
d-i partman-auto/choose_recipe select my-root
d-i partman-auto/expert_recipe string                  \
      my-root ::                                       \
              512 2 512 fat16                          \
                      $primary{ }                      \
                      method{ efi }                    \
                      format{ }                        \
              .                                        \
              63488 1 -1 ext4                          \
                      method{ format }                 \
                      format{ }                        \
                      use_filesystem{ }                \
                      filesystem{ ext4 }               \
                      mountpoint{ / }                  \
                      options/discard{ discard }       \
                      options/noatime{ noatime }       \
                      options/nodiratime{ nodiratime } \
              .
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
d-i partman/mount_style select uuid

### Base system installation
d-i base-installer/kernel/altmeta string hwe-16.04

### Apt setup
d-i apt-setup/non-free boolean true
d-i apt-setup/contrib boolean true

### Package selection
d-i tasksel/first multiselect standard system utilities
d-i pkgsel/update-policy select none
d-i pkgsel/upgrade select full-upgrade
d-i pkgsel/language-pack-patterns string
d-i pkgsel/install-language-support boolean false
d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true
d-i grub-installer/bootdev string /dev/sda

### Finishing up the installation
d-i finish-install/reboot_in_progress note

```

Any thoughts/pointers on where to look would be appreciated.

Thanks,

---

### Post by LHammonds on 2018-04-27
The partman auto-install is a fickle beast.  It seems to only work for the most-basic scenarios.

I tried for a solid week to make it create an LVM partition the same way I do when creating my servers and could never get it to work.  I ended up just abandoning the project (although I really wanted it to work) and decided to just create a standard generic image (virtual machine in vmware) and turn it into a template to deploy new servers from.

This is what I tried to create:

[IMG]http://www.hammondslegacy.com/images/linux/UbuntuHDPartitionDesign-Mod.png[/IMG]


Below is the 20th iteration of the script I used to help automate the creation of the custom ISO image since I ended up doing it so often, I wanted the fastest process I could make.

Although I can't really solve your problem since I had similar problems with partman not doing what I wanted, I can at least share how I quickly made changes to crank out another ISO image to test.

```

#! /bin/bash
#############################################
## Name          : create-preseed.sh
## Version       : 0.2.0
## Date          : 2018-01-02
## Author        : LHammonds
## Compatibility : Ubuntu Server 16.04 LTS
## Requirements  : Run as root
##               : apt install genisoimage      (Tested using genisoimage version 1.1.11)
##               : apt install syslinux-utils   (Tested using isohybrid version 0.12)
## Purpose       : Create a re-mastered Ubuntu ISO
## Run Frequency : As needed
## Exit Codes    : None
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2018-01-02 LTH  Created script.
#############################################

# The following script downloads the official Ubuntu server CD, makes a few changes and creates a new CD image which will perform an unattended installation of Ubuntu.
# The script is based on this article (https://askubuntu.com/questions/122505/how-do-i-create-a-completely-unattended-install-of-ubuntu) and this help text (https://help.ubuntu.com/community/InstallCDCustomization).
# Required installed programs:

# Please take a look at the shell script before you execute it. Things you most likely want to change are:
#  * The version of Ubuntu you want to use. The version in the script is what I used, I don't know if this would work for newer versions, probably yes.
#  * Other settings in the generated ks.cfg file.

##
## Variables
##
adminid="administrator"
adminpwd="myadminpassword"
basedir="/srv/samba/share"
downloads="/media/psf/home/downloads"
tmpdir=$(mktemp -d)
builddir="$tmpdir/build.$$"
mntdir="$tmpdir/mnt.$$"

echo "tmpdir=${tmpdir}"

## Make the folders if they do not exist.
if [ ! -d ${basedir} ]; then
  mkdir -p ${basedir}
fi
if [ ! -d ${downloads} ]; then
  mkdir -p ${downloads}
fi

#
# Ubuntu release selection
#
release_name="xenial"
release_version="16.04.3"
release_variant="server"
release_architecture="amd64"

release_base_url="http://releases.ubuntu.com"
release_base_name="ubuntu-$release_version-$release_variant-$release_architecture"
release_image_file="$release_base_name.iso"
release_url="$release_base_url/$release_name/$release_image_file"

#
# Target settings
#
target_base_name="${release_base_name}-auto"
target_directory="$basedir"
target_image_file="$target_base_name.iso"

progress() {
    echo "$*" >&2
}

error() {
    code="$1"; shift
    echo "ERROR: $*" >&2
    exit $code
}

create_directory() {
    path="$1"
    if [ ! -d "$path" ]; then
    progress "Creating directory $path..."
    mkdir -p "$path" || error 2 "Failed to create directory $path"
    fi
}

extract_iso() {
    archive="$1"
    if [ ! -r "$archive" ]; then
    error 1 "Cannot read ISO image $archive."
    fi
    directory="$2"
    if [ ! -d "$directory" ]; then
    mkdir "$directory" || exit 2 "Cannot extract CD to $directory"
    fi

    progress "Mounting image $archive (you may be asked for your password to authorize)..."
    create_directory "$mntdir"
    sudo mount -r -o loop "$archive" "$mntdir" || error 2 "Failed to mount image $archive"

    progress "Copying image contents..."
    cp -rT "$mntdir" "$directory" || error 2 "Failed to copy content of image $archive to $directory"
    chmod -R u+w "$directory"

    progress "Unmounting image $archive from $mntdir..."
    sudo umount "$mntdir"
    rmdir "$mntdir"
}

preset_language() {
    progress "Presetting language to 'en'..."
    echo "en" >"isolinux/lang" || error 2 "Failed to write $(pwd)/isolinux/lang"
}

create_kscfg() {
    if [ ! -f "ks.cfg" ]; then
    progress "Create ks.cfg file..."
    cat >"ks.cfg" <<EOF
#Generated by Kickstart Configurator
#platform=AMD64 or Intel EM64T

#System language
lang en_US
#Language modules to install
langsupport en_US
#System keyboard - Generic 105-key (Intl) PC (pc105) or US (us)
keyboard us
#System mouse
mouse
#System timezone
timezone America/Chicago
#Root password
rootpw --disabled
#Initial user
user ${adminid} --fullname "${adminid}" --password ${adminpwd}
#Reboot after installation
reboot
#Use text mode install
text
#Install OS instead of upgrade
install
#Use CDROM installation media
cdrom
#System bootloader configuration
bootloader --location=mbr 
#Clear the Master Boot Record
zerombr yes
#Partition clearing information
clearpart --all --initlabel 
#Disk partitioning information
#part / --fstype ext4 --size 1 --grow 
#part swap --recommended 
#System authorization infomation
auth  --useshadow  --enablemd5 
#Network information
network --bootproto=dhcp --device=eth0
#network --bootproto=static --ip=10.0.2.2 --netmask=255.255.255.0 --gateway=10.0.2.1 --nameserver=10.0.2.1 --device=eth1
#Firewall configuration
firewall --disabled 
#Do not configure the X Window System
skipx
echo done
## You might want to do something meaningful at this point of the installation.
EOF
    fi
}

create_kspreseed() {
    if [ ! -f "ks.preseed" ]; then
    progress "Create ks.preseed file..."
    cat >"ks.preseed" <<EOF

### Partitioning
## Specify disk to partition:
d-i partman-auto/disk string /dev/sda
## Remove interactive warning if existing partition exists:
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
## Specify size of volume group to use for logical volumes:
d-i partman-auto-lvm/guided_size string max
## Specify partition method to use:
d-i partman-auto/method string lvm
## Specify the recipe name to use (defined below):
d-i partman-auto/choose_recipe select prod-server
## Name the volume group:
d-i partman-auto-lvm/new_vg_name string LVG

## Set your preferred default filesystem:
d-i partman/default_filesystem string ext4
d-i partman-auto-lvm/no_boot boolean true

## Define custom partition recipe (requires one logical line)
## 1st number is minimum size of the partition in megabytes
## 2nd number is the priority that this partition gets it's maximum size fulfilled (lower number is higher value)
## 3rd number is the maximum size of partition being created
d-i partman-auto/expert_recipe string prod-server :: \
  500 10 500 ext2 \
    $primary{ } \
    $bootable{ } \
    $lvmignore{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext2 } \
    mountpoint{ /boot } \
    label{ boot } \
    options/defaults{ defaults } \
  .\
  20000 10 20000 ext4 \
    $defaultignore{ } \
    $primary{ } \
    vg_name{ LVG } \
    device{ /dev/sda } \
  .\
  120% 15 120% linux-swap \
#    $defaultignore{ } \
    $lvmok{ } \
    format{ } \
    in_vg{ LVG } \
    lv_name{ swap } \
    method{ swap } \
    options/sw{ sw } \
  .\
  2000 20 2000 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ root } \
    mountpoint{ / } \
    label{ root } \
    options/defaults{ defaults } \
  .\
  200 25 200 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ home } \
    mountpoint{ /home } \
    label{ home } \
    options/defaults{ defaults } \
  .\
  500 30 500 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ tmp } \
    mountpoint{ /tmp } \
    label{ tmp } \
    options/relatime{ relatime } \
    options/noexec{ noexec } \
    options/rw{ rw } \
  .\
  2000 35 2000 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ usr } \
    mountpoint{ /usr } \
    label{ usr } \
    options/defaults{ defaults } \
  .\
  2000 40 2000 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ var } \
    mountpoint{ /var } \
    label{ var } \
    options/defaults{ defaults } \
  .\
  200 45 200 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ srv } \
    mountpoint{ /srv } \
    label{ srv } \
    options/defaults{ defaults } \
  .\
  200 50 200 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ opt } \
    mountpoint{ /opt } \
    label{ opt } \
    options/defaults{ defaults } \
  .\
  500 55 500 ext4 \
    $defaultignore{ } \
    $lvmok{ } \
    method{ format } \
    format{ } \
    use_filesystem{ } \
    filesystem{ ext4 } \
    in_vg{ LVG } \
    lv_name{ bak } \
    mountpoint{ /bak } \
    label{ bak } \
    options/auto{ auto } \
    options/rw{ rw } \
    options/noexec{ noexec } \
    options/nouser{ nouser } \
    options/async{ async } \
    options/suid{ suid } \
  .\

### This makes partman automatically partition without confirmation
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

### Verbose output and no boot splash screen.
d-i debian-installer/quiet boolean false
d-i debian-installer/splash boolean false

### Locale
d-i debian-installer/locale string en_US
## Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us

### Network
d-i netcfg/choose_interface select auto
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain
## Disable that annoying WEP key dialog.
d-i netcfg/wireless_wep string

### Clock
d-i clock-setup/utc-auto boolean true
d-i clock-setup/utc boolean true
d-i time/zone string US/Pacific
d-i clock-setup/ntp boolean true

### Packages, Mirrors, Image
d-i base-installer/kernel/override-image string linux-server
d-i base-installer/kernel/override-image string linux-image-amd64
d-i mirror/country string US
d-i mirror/http/proxy string
d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i pkgsel/install-language-support boolean false
## To see list of all tasks, type tasksel --list-tasks
#tasksel tasksel/first multiselect standard, server, openssh-server
tasksel tasksel/first multiselect manual
## Individual additional packages to install
d-i pkgsel/include string open-sshserver vim-nox p7zip-full ntpdate htop fsarchiver sendemail dialog fail2ban
## Policy for applying updates. "none" (no automatic updates),
## "unattended-upgrades" (install security updates automatically), or
## "landscape" (manage system with Landscape).
d-i pkgsel/update-policy select none

### Users
d-i passwd/user-fullname string administrator
d-i passwd/username string administrator
d-i passwd/user-password password myadminpassword
d-i passwd/user-password-again password myadminpassword
d-i passwd/root-login boolean false
d-i user-setup/allow-password-weak boolean true
d-i user-setup/encrypt-home boolean false

### Grub
d-i grub-installer/grub2_instead_of_grub_legacy boolean true
d-i grub-installer/only_debian boolean true
## Avoid that last message about the install being complete.
d-i finish-install/reboot_in_progress note

## Post Install
d-i preseed/late_command string \
d-i preseed/late_command string in-target wget -P /tmp/ "http://hammondslegacy.com/linux/init-scripts.tar.gz"; \
in-target tar xvf /tmp/init-scripts.tar.gz -C /; \
echo done
EOF
    fi
}

patch_txtcfg() {
    (cd "isolinux";
    patch -p0 <<EOF
--- txt.cfg.orig     2017-12-28 11:16:13.118419465 -0600
+++ txt.cfg     2017-12-28 11:17:49.448885225 -0600
@@ -2,7 +2,7 @@
 label install
   menu label ^Install Ubuntu Server
   kernel /install/vmlinuz
-  append  file=/cdrom/preseed/ubuntu-server.seed vga=788 initrd=/install/initrd.gz quiet ---
+  append  file=/cdrom/preseed/ubuntu-server.seed initrd=/install/initrd.gz ks=cdrom:/ks.cfg preseed/file=/cdrom/ks.preseed ---
 label hwe-install
   menu label ^Install Ubuntu Server with the HWE kernel
   kernel /install/hwe-vmlinuz
EOF
    )
}

patch_isolinuxcfg() {
    (cd "isolinux";
    patch -p0 <<EOF
--- isolinux.cfg.orig        2017-12-28 11:16:13.114419529 -0600
+++ isolinux.cfg        2017-12-28 11:20:16.754564861 -0600
@@ -4,5 +4,5 @@
 include menu.cfg
 default vesamenu.c32
 prompt 0
-timeout 0
+timeout 5
 ui gfxboot bootlogo
EOF
    )
}

modify_release() {
    preset_language && \
    create_kscfg && \
    create_kspreseed && \
    patch_txtcfg && \
    patch_isolinuxcfg 
}

create_image() {
    if [ ! -f "$target_directory/$target_image_file" ]; then
    if [ ! -f "$downloads/$release_image_file" ]; then
        progress "Downloading Ubuntu $release_name $release_variant..."
        curl "$release_url" -o "$downloads/$release_image_file"
    fi
    create_directory "$builddir"
    extract_iso "$downloads/$release_image_file" "$builddir"
    (cd "$builddir" && modify_release
    ) || error 2 "Failed to modify image"

    create_directory "$target_directory"
    progress "Creating ISO image $target_image_file..."
    genisoimage -D -r -V "UNATTENDED_UBUNTU" -cache-inodes -J -l \
        -b isolinux/isolinux.bin \
        -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 \
        -boot-info-table \
            -input-charset utf-8 \
        -o "$target_directory/$target_image_file" \
        "$builddir" || error 2 "Failed to create image $target_image_file"
    if [ "x$builddir" != x -a "x$builddir" != "x/" ]; then
        rm -rf "$builddir"
    fi
        ## Make the ISO also bootable for USB
        isohybrid ${target_directory}/${target_image_file}
    fi
}

create_image

```

LHammonds

---

