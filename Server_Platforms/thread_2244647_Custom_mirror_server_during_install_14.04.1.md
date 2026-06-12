---
title: "Custom mirror server during install 14.04.1"
date: 2014-09-17
forum: Server Platforms
---

### Post by jpaytoncfd on 2014-09-17
I need to speed up the server install but I can not find any info about modifying the installer. 

I have tried the us and uk mirrors. UK was faster but basically if I want the install to take less that 3 hours I have to ether change the mirror to a third party mirror or download the needed packages and include them in the installer. 

Can someone point me to a guide or file I can edit to change the default mirrors? I have the installer on a USB drive.

---

### Post by jpaytoncfd on 2014-09-17
Finaly found it in the documentation located on the install media. 

[COLOR=#000000][FONT=Times New Roman][h=3]B.4.4. Mirror settings[/h][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Depending on the installation method you use, a mirror may be used to download additional components of the installer, to install the base system, and to set up the /etc/apt/sources.list for the installed system.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]The parameter mirror/suite determines the suite for the installed system.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]The parameter mirror/udeb/suite determines the suite for additional components for the installer. It is only useful to set this if components are actually downloaded over the network and should match the suite that was used to build the initrd for the installation method used for the installation. Normally the installer will automatically use the correct value and there should be no need to set this.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]The parameter mirror/udeb/components determines the archive components from which additional installer components are fetched. It is only useful to set this if components are actually downloaded over the network. The default components are main and restricted.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]# If you select ftp, the mirror/country string does not need to be set.
#d-i mirror/protocol string ftp
d-i mirror/country string manual
d-i mirror/http/hostname string archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

# Alternatively: by default, the installer uses CC.archive.ubuntu.com where
# CC is the ISO-3166-2 code for the selected country. You can preseed this
# so that it does so without asking.
#d-i mirror/http/mirror select CC.archive.ubuntu.com

# Suite to install.
#d-i mirror/suite string saucy
# Suite to use for loading installer components (optional).
#d-i mirror/udeb/suite string saucy
# Components to use for loading installer components (optional).
#d-i mirror/udeb/components multiselect main, restricted[/FONT][/COLOR]

---

### Post by jpaytoncfd on 2014-09-17
... There is a much easier option... When it askes you to select a local to find mirrors you can go the the very top of the list and there is a option to manually enter the details.

I have been searching for weeks for this solution.

---

### Post by lukeiamyourfather on 2014-09-18
If you are going to be installing a lot of machines you can setup a local mirror of the Ubuntu repository with apt-mirror. After the install the mirror can be used for updates and installing new packages.

---

