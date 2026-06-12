---
title: "WiFi doesnt Work on my Acer E5-574G"
date: 2016-02-05
forum: Ubuntu/Debian BASED
---

### Post by Javed_Ashraf on 2016-02-05
Hi Friends 

installed Kali Linux 2.0 on my Acer E5-574G, Everything looking Good Except WIFI :( , Tried so many Things but to no effect , Wireless is too Stubborn. Read similar posts where problem was solved by Chilli555 , rinfinity & Jeremy . but my wireless is not coming back.
below is my wire-less info.txt

---

### Post by howefield on 2016-02-05
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Javed_Ashraf on 2016-02-05
Thanks howefield,sorry to post in wrong section.

here is more on my wireless issue....
when i follow this [http://askubuntu.com/questions/708061/qualcomm-atheros-device-168c0042-rev-30-wi-fi-driver-installation/708103#708103](http://askubuntu.com/questions/708061/qualcomm-atheros-device-168c0042-rev-30-wi-fi-driver-installation/708103#708103) .
i get the below error .

root@kalinux:~# sudo apt-get install build-essential linux-headers-$(uname -r) git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-4.3.0-kali1-amd64
E: Couldn't find any package by glob 'linux-headers-4.3.0-kali1-amd64'
E: Couldn't find any package by regex 'linux-headers-4.3.0-kali1-amd64'


and on running | make defconfig-wifi

root@kalinux:~/Desktop/backports-20151120# make defconfig-wifi
/--------------
| Your kernel headers are incomplete/not installed.
| Please install kernel headers, including a .config
| file or use the KLIB/KLIB_BUILD make variables to
| set the kernel to build against, e.g.
|   make KLIB=/lib/modules/3.1.7/
| to compile/install for the installed kernel 3.1.7
| (that isn't currently running.)
\--
Makefile:40: recipe for target 'defconfig-wifi' failed



tried below mentioned commands by chilli 555 , the commands run smooth without any error but again wireless doesnt work.

 			 				[INDENT] 					chilli 555 : { It looks like you need some firmware. Please open a terminal and do:
 	Code:
 	sudo mkdir /lib/firmware/ath10k/QCA9377/
sudo mkdir /lib/firmware/ath10k/QCA9377/hw1.0 
If it reports that the file already exists, that's fine, just continue.

With a temporary working internet connection:

 	Code:
 	sudo apt-get install git
git clone [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)
cd ath10k-firmware/QCA9377/hw1.0
sudo cp board.bin  /lib/firmware/ath10k/QCA9377/hw1.0
sudo cp firmware-5.bin_WLAN.TF.1.0-00267-1   /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci 
Your wireless should be working; if not, try a reboot. 				}
[/INDENT]

---

### Post by Rob Sayer on 2016-02-06
Just looked at your wireless-info file.  You're using a rolling release Kali version, Debian based, with Linux kernel Linux 4.3.0-kali1-amd64.  Which sounds like it's custom in part, and it's newer than in any ubuntu release in those links.  Gulp.  Rolling releases are *not* suitable for noobs.

In any case, you can't apply fixes for a different release.  Search your kernel version + your wireless card.  Try searching the Debian forums.  Debian is intended for advanced users so they don't do beginner hand holding.  If you try to get your hand held on their support forum what they're going to do is suggest installing ubuntu or mint instead.

I just looked at the Kali support forums.  There seems to be some competent users posting there but they don't seem to do a lot of hand holding either.  I suspect if you posted there about a wireless card that's pesky in Linux in general they'll just suggest getting a wireless dongle that is properly supported in Linux.

Unfortunately I think you're using a distro that's not beginner friendly and you're in way over your head.

---

### Post by Javed_Ashraf on 2016-02-06
OK thanx for the answer, will see what i can do

---

### Post by Javed_Ashraf on 2016-02-07
happy to report that now its working :)

First of all updated the repository by following [http://docs.kali.org/general-use/kali-linux-sources-list-repositories](http://docs.kali.org/general-use/kali-linux-sources-list-repositories) . 
then ran ..
apt-get install libappindicator1
apt-get -f install
sudo apt-get install git
git clone [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)

and then followed [URL="http://askubuntu.com/questions/708061/qualcomm-atheros-device-168c0042-rev-30-wi-fi-driver-installation/708103#708103"]http://askubuntu.com/questions/708061/qualcomm-atheros-device-168c0042-rev-30-wi-fi-driver-installation/708103#708103
[/URL]
sudo apt-get install build-essential linux-headers-$(uname -r) git
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
wget [https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz)
tar zxvf backports-20151120.tar.gz
cd backports-20151120
make defconfig-wifi
make
sudo make install
git clone [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
sudo cp /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin_WLAN.TF.1.0-00267-1 /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin

reboot and wireless is up :) 
Cheers

root@kali:~# iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"JAF"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 46:91:DB:77:24:B7   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:0

lo        no wireless extensions.

---

