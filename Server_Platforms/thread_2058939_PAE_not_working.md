---
title: "PAE not working"
date: 2012-09-16
forum: Server Platforms
---

### Post by JamesStewy on 2012-09-16
Hi,

I am having trouble using PAE on Ubuntu Server 12.04 LTS 32bit. I recently upgraded from 4 to 8gb of RAM but PAE doesn't appear to have picked this up.

When I run ```
grep --color=always -i PAE /proc/cpuinfo
``` I get pae in the list.

When I run ```
dmidecode | grep Size | grep MB
``` Installed Size is 3825 but the Maximum Total Memory Size: 8192 MB.

When I check the BIOS it says there is 8192 MB available. The computer manual also says and the computer supports that amount.

I have followed everything I can find on the internet (including this [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)) and nothing is working.

My Computer is a Toshiba Portege M750 bought in 2009. It has an Intel Centrino Core 2 Duo processor. The RAM I bought doesn't appear to have a brand listed but this is where I got it [http://www.ramcity.com.au/product/KIN1-DP2200-8G-021.htm](http://www.ramcity.com.au/product/KIN1-DP2200-8G-021.htm). It's specs are exactly the same as my old RAM except it is twice as big.

Thanks,

JamesStewy

---

### Post by oldfred on 2012-09-16
Linus does not like PAE or 32 bit. Or you do not get what you think you might be getting:
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

### Post by JamesStewy on 2012-09-16
When I went to the downloads page for Ubuntu server it seamed like the 64bit version only worked on AMD processors. My laptop has an Intel. Am I missing something?

---

### Post by oldfred on 2012-09-17
It is all the same.
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

From the python page:
The binaries for AMD64 will also work on processors that implement the Intel 64 architecture (formerly EM64T), i.e. the architecture that Microsoft calls x64, and AMD called x86-64 before calling it AMD64. 

They will not work on Intel Itanium Processors (formerly IA-64). These are limited production chips, used now for heavy duty servers running Unix.

---

### Post by JamesStewy on 2012-09-17
Thanks a lot. I know this is getting a bit of topic now but is there a way that I can upgrade to 64bit without losing my programs, settings and files (especially for my website). Thanks again.

---

### Post by JamesStewy on 2012-09-17
If I used something such as Clonezilla Live, would I be able to create an image, install 64bit, then use the image to restore what I had before?

---

### Post by oldfred on 2012-09-17
I think clonezilla is the full image.

I do not have a server. But I found I prefer clean installs and my backup is not as critical as a server so I plan on a reinstall and restore my data. 
With a server you may have additional folders in / that you need to backup also. Where is your web data stored?

Since I want to reinstall my backup tries to restore everything. But I also have most data in separate data partitions.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

1. /home (Users' personal files and settings) including keys in ~/.gnupg
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

#I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
#Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

Other applications if data not separate
apache, any sqldb, tomcat, web folders, etc
Document system backup or for multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)
Screen for multiple SSHs
[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Files to include or exclude from full system backup. Post #7
[http://ubuntuforums.org/showthread.php?t=1903085](http://ubuntuforums.org/showthread.php?t=1903085)

Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
/home/*/.cache
/home/*/.dbus
/home/*/.dropbox
/home/*/.gvfs
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/**
/home/*/.qt
/home/*/.thumbnails
/home/*/Examples
/home/.ecryptfs
/home/lost+found

---

### Post by JamesStewy on 2012-09-18
Thanks a lot. So the best way is to just copy the files I need. Is there a way to create a list of packages then use that list, once re-installed, to re-install the packages?

---

### Post by oldfred on 2012-09-18
It is hidden as only one line in my normal backup.  I relist packages with each backup.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

