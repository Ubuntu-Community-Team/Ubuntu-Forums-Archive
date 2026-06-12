---
title: "Unattended installation halts at &quot;Installation type&quot;"
date: 2018-04-06
forum: Ubuntu Development Version
---

### Post by fkorling on 2018-04-06
I am trying to update an unattended installation from xenial to bionic. 
However, the installer gets stuck at the "Installation type" screen.
 
[ATTACH=CONFIG]279187[/ATTACH]

This is the preseed file: 
```

# preseeding only locale sets language, country and locale.
d-i debian-installer/locale string sv_SE.UTF-8
d-i debian-installer/language string sv
d-i debian-installer/country string SE
# keyboard selection.
d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/layoutcode string se
d-i keyboard-configuration/xkb-keymap select se
d-i keyboard-configuration/layout select Swedish
d-i keyboard-configuration/variant select Swedish
# language packs
d-i pkgsel/language-packs multiselect se, en
# mirror settings
d-i mirror/country string manual
d-i mirror/http/hostname string archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string


# clock and time zone setup
d-i clock-setup/utc boolean true
d-i time/zone string Europe/Stockholm
d-i clock-setup/ntp boolean true

### Partitioning
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-auto/choose_recipe select atomic


# This makes partman automatically partition without confirmation
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select Installera
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true


# use automatic security updates
d-i pkgsel/update-policy select unattended-upgrades


# install language support
d-i pkgsel/install-language-support boolean true


# package selection
tasksel tasksel/first multiselect ubuntu-server, standard




d-i pkgsel/include string openssh-server build-essential


# root User
d-i passwd/root-login boolean false
# standard User
d-i passwd/user-fullname string patwic
d-i passwd/username string patwic
d-i passwd/user-password password patwic
d-i passwd/user-password-again password xxx
d-i passwd/auto-login boolean true
d-i user-setup/allow-password-weak boolean true
d-i user-setup/encrypt-home boolean false


# boot loader installation
d-i grub-installer/only_debian boolean true 
ubiquity ubiquity/reboot boolean true
ubiquity ubiquity/poweroff boolean true


# monitor autodetection is recommended.
xserver-xorg xserver-xorg/autodetect_monitor boolean true
xserver-xorg xserver-xorg/config/monitor/selection-method \
       select medium
xserver-xorg xserver-xorg/config/monitor/mode-list \
       select 1024@768 60 Hz
 
ubiquity ubiquity/success_command string \
  in-target apt-get clean; \
  in-target apt-get update; \
  in-target apt-get upgrade -y; \
  in-target apt-get install -y openssh-server


# Avoid that last message about the install being complete.
d-i finish-install/reboot_in_progress note



```



What's missing?

---

### Post by dino99 on 2018-04-06
a suggestion: maybe it is waiting for a user decision/choice, aka hidden dialog box

---

### Post by fkorling on 2018-04-06
Any ideas how to find out if there is such a dialog open?

---

### Post by dino99 on 2018-04-06
you have posted a virtualbox snapshot, which ask you to take a decision  :confused:

---

### Post by jbicha on 2018-04-06
There is a new field for the Minimal Installation question added to Ubuntu 18.04. You'll need to update your unattended installation script.

---

