---
title: "Re: Ubuntu Server with Virtual Box with headless server + PHP interface running IPCOP"
date: 2014-07-12
forum: Virtualisation
---

### Post by alcatail on 2014-07-12
So my aim here is to help or to show how I got my setup built and what code worked for me. I have been working on and off with this for 5 years across multiple versions of linix, figured out what works and what does not. Hopefully this will be of some help to someone, I am not looking for negative criticism here, just trying to give free advice that I picked up from here and there and a little I wrote myself.
 
What is the setup?
Currently I have downgraded from an I7 setup to an Intel Nuc Celeron running ubuntu server 14.04 + ipcop 2.15, 2 x RADXA&#8217;s running Linaroo 13.11 + owncloud 6.04(public cloud and private cloud), A raspberry PI running a print server for the printers.
Why? To decrease my power load from 350 + Watts down to 36watts(intel nuc) +2 x 10watts(Radxa) + 5Watts(rasp pi).
Specs
Radxa [http://radxa.com/specification/](http://radxa.com/specification/)
Raspberry pi [http://en.wikipedia.org/wiki/Raspberry_Pi](http://en.wikipedia.org/wiki/Raspberry_Pi)
Intel Nuc [http://www.intel.com.au/content/www/au/en/nuc/nuc-board-dn2820fykh.html](http://www.intel.com.au/content/www/au/en/nuc/nuc-board-dn2820fykh.html)
These specs are a little light on for virtualisation on the NUC but it is handling one VM floorlessly.
 
Network setup...
modem  ===> Red Ethernet interface of IPCop  ==è ipcop firewall ====> green(safe zone)
                                                                                        ====> Blue(Wifi Zone)
                                                                                        ====> orange (optional) for DMZ
   Modem   ===>     ===== wifi bridge if ipcop fail ================> Blue
 
 
Green is protected from red and blue. There is a VPN between the blue and the green so that laptops and the wifi can access nas servers, printers and the private cloud.
Why a private cloud and a public cloud? The public cloud is setup for smart phones and can be accessed via anywhere on the internet. I&#8217;m at work, take a photo with my android phone and within 30 seconds the photo is sitting on my public cloud at home. I log in at work and share that photo in an email or it can be downloaded onto the work computer, etc. I use it for family overseas, etc, heaps better than photobucket and drop box, etc. I am in control of the data.
With regards to the private cloud all my laptops are synced to the private cloud and should the laptop be infected with an encryption virus the cloud has file revisions built into the software and all files can be restored through older revisions. There for whilst the encryption virus could cause disruption my files can be restored through older revisions.
Why IPCOP?  [http://www.ipcop.org/index.php](http://www.ipcop.org/index.php)
As mentioned it segregates all the networks and manages them better.  It has a proxy server and a VPN server. I use Copfilter of IPCOP so it scans for viruses coming in, shuts the pages down and stops the virus from passing through the network. It uses Privoxy and removes advertising from the web pages and stops google, yahoo, ebay, facebook form tracking you. By far the best firewall package I have ever used.
The virtual machine protects the physical machine and if the virtual machine is brought down it disconnects all the networks, so it is fairly robust. I have written a script for IPCOP so if it fails it creates a new wifi network using the inbuilt wifi in the nuc as a bridge to the modem and shuts the bridge down when IPCOP is working.
Intel Nuc setup
Software needed &#8211; ubuntu 14.04 server downloaded iso. [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)
A spare usb flashdrive, a usb hub, 2 spare usb Ethernet nics
Win32 disc imager [http://sourceforge.net/projects/win32diskimager/](http://sourceforge.net/projects/win32diskimager/)
Winscp [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)
Putty [http://winscp.net/eng/download.php](http://winscp.net/eng/download.php)
Ipcop latest installation cd [http://www.ipcop.org/download.php](http://www.ipcop.org/download.php)
 
I program from a windows 7 laptop and a windows 8.1 laptop &#8211; so install the relevant win32 disc imager, winscp and putty.
Connect the Ethernet nics to the usb hub, then to the front of the nuc, a mouse to the hub and a the keyboard to the nuc. Connect the nuc to a tv or a monitor. Connect the lan cable up to one of the usb Ethernet nics.
Use the laptop to write the ubuntu14.04 iso image to the usb. Insert the usb to your intel nuc and switch it on.  Automatically detect all settings, I trie to split off a separate ext4 partition to install my vm&#8217;s and other important files on for upgrades and or recoveries. 80 gig should be  heaps. I try to have a different partition for the /tmp as well. Through the install select ssh server. With the network select dhcp &#8211; although this will soon change.
When all this is done in  terminal type
sudo su (or sudo &#8211;i)
&#8216;Type your password&#8217;
passwd root
&#8216;Select a new root password to your liking
passwd &#8211;u root
&#8216;This unlocks the root password for winscp
nano /etc/ssh/ssh_config
Go down to where it says PermitRootLogin without-password
And change to
#PermitRootLogin without-password
PermitRootLogin yes
Ctrl + o to save and crtl to exit
Type ifconfig and write down the ip address it is using,
Ie 192.168.1.100

Shutdown and remove the keyboard and mouse. Set the nuc up where you want it. It only needs the usb hub + the 2 ethernet nics and a monitor + lan cable but the monitor can stay switched off. The nuc needs to have something connected to the tv port (the monitor) for it to boot up.
Start the nuc up and connect to it from putty on the laptop. Use port 22 and the ip address you wrote down. Use root as login and your root password.
Run the following
apt-get update
apt-get upgrade
So now get a piece of paper and write down the following
Red =
Blue =
Green =
Red will = the iprange that the modem is running on. I.E 192.168.**_1_**.1
Blue is the range you want your wifi to be, ie. 192.168.10.1
And green is your safe network ie, 192.168.50.1
Write them down
Red = 192.168.1.1
Blue = 192.168.10.1
Green =192.168.50.1
In putty type
cp /etc/network/interfaces /etc/network/interfaces.bak
Open up winscp and log in as root
 
Open up /etc/network/interfaces
Delete everything and paste this into it, modifying it to your addresses. Pay special attention to which interface is set to dhcp &#8211; ie, eth0 or eth1
 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 
# The loopback network interface
auto lo
iface lo inet loopback
 
# The primary network interface
auto eth0 #(replace this with your primary (red interface)
iface eth0 inet static
 
address 192.168.1.140 #this is the number you want to give your nuc#
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1
 
 
auto p2p1
iface p2p1 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down
 
 
#auto p2p1
#iface p2p1 inet static
#address 192.168.20.140
#netmask 255.255.255.0
#network 192.168.20.0
#gateway 192.168.20.1
#dns-nameservers 192.168.20.1
 
 
auto eth1
iface eth1 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down
 
 
#####WIRELESS
##
#auto lo br0
#iface lo inet loopback
## wireless wlan0
#allow-hotplug wlan0
#iface wlan0 inet manual
## eth0 connected to the ISP router
#allow-hotplug eth0
#iface eth0 inet manual
## Setup bridge
#iface br0 inet static
#    bridge_ports wlan0 eth0
#    address 192.168.1.140
#    netmask 255.255.255.0
#    network 192.168.1.0
 
 
 ####WIRELESSS
 
 
Save and make sure this is perfect. If it isn&#8217;t you will need to connect your keyboard and work from the nuc to fix it if it is wrong.
Close and reboot reboot
 
 
Setting up the in built wifi radio in the nuc
 
Refer this page
Intel 7260 driver we need
Select it to the correct kernel you are using
 
Uname &#8211;r
For me it&#8217;s
3.13.0-24-generic
[TABLE="width: 100"]
[TR]
[TD]Intel® Wireless 7260[/TD]
[TD]3.10+[/TD]
[TD][iwlwifi-7260-ucode-22.1.7.0.tgz]("http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-7260-ucode-22.1.7.0.tgz")[/TD]
[/TR]
[TR]
[TD]3.13+[/TD]
[TD][iwlwifi-7260-ucode-22.24.8.0.tgz]("http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-7260-ucode-22.24.8.0.tgz")[/TD]
[/TR]
[TR]
[TD]3.14+[/TD]
[TD][iwlwifi-7260-ucode-23.214.9.0.tgz]("http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-7260-ucode-23.214.9.0.tgz")[/TD]
[/TR]
[/TABLE]
Then copy the file onto the nuc using winscp
I usually create a download directory and from there
Tar &#8211;zxvf iwlwifi-*.tgz
 
Then 
 
cp iwlwifi-*.ucode /lib/firmware
 
reboot
 
ifconfig &#8211;a
it should show up as wlan0
 
 
Now to set up virtual box!!!!
 
Based entirely on (pls excuse my cut and paste)
[http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.3-on-a-headless-ubuntu-14.04-lts-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.3-on-a-headless-ubuntu-14.04-lts-server)
 
**VBoxHeadless - Running Virtual Machines With VirtualBox 4.3 On A Headless Ubuntu 14.04 LTS Server**

 Version 1.0
Author: Falko Timme, updated by Srijan Kishore


This guide explains how you can run virtual machines with [VirtualBox 4.3]("http://www.virtualbox.org/") on a headless Ubuntu 14.04 server. Normally you use the VirtualBox GUI to manage your virtual machines, but a server does not have a desktop environment. Fortunately, VirtualBox comes with a tool called VBoxHeadless that allows you to connect to the virtual machines over a remote desktop connection, so there's no need for the VirtualBox GUI.
I do not issue any guarantee that this will work for you!
 
**1 Preliminary Note**

I have tested this on an Ubuntu 14.04 server (host system) with the IP address 192.168.0.100 where I'm logged in as a normal user (user name administrator in this example) instead of as root.
 
**2 Installing VirtualBox**

Use putty and log in as root
To install VirtualBox 4.3 on our Ubuntu 14.04 server, we open /etc/apt/sources.list...
nano /etc/apt/sources.list
... and add the following line to it:
[TABLE="width: 90, align: center"]
[TR]
[TD][...]deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) trusty contrib[/TD]
[/TR]
[/TABLE]
Then download the VirtualBox public key...
wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
 update
apt-get update
Afterwards, install VirtualBox 
apt-get install linux-headers-$(uname -r) build-essential virtualbox-4.3 dkms
(The dkms package ensures that the VirtualBox host kernel modules are properly updated if the Linux kernel version changes.)
Starting with version 4.0, VirtualBox has introduced so called "extension packs" and has outsourced some functionality like remote desktop connection support (VRDP) that was part of VirtualBox packages before version 4.0 into these extension packs. Because we need remote desktop connections to control our virtual machines, we need to install the appropriate extension pack now. Go to [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads), and you will find a link to the following extension pack:
VirtualBox 4.3.10 Oracle VM VirtualBox Extension Pack
Support for USB 2.0 devices, VirtualBox RDP and PXE boot for Intel cards.
Download the extension pack and drop it in using winscp
Putty to the directory and type
VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-*
(Make sure you grab the latest version from the VirtualBox web site.)
add the user that will run VirtualBox (administrator in this example) to the vboxusers group:
sudo adduser vboxusers
VirtualBox is now installed and ready to be used but we will proceed with the PHP web management instead.
Once again please excuse the cut and paste
 
[http://www.howtoforge.com/managing-a-headless-virtualbox-installation-with-phpvirtualbox-on-ubuntu-14.04-lts](http://www.howtoforge.com/managing-a-headless-virtualbox-installation-with-phpvirtualbox-on-ubuntu-14.04-lts)



**Managing A Headless VirtualBox Installation With phpvirtualbox (Ubuntu 14.04 LTS)**

 
Version 1.0
Author: Falko Timme, updated by Srijan Kishore


[phpvirtualbox]("http://code.google.com/p/phpvirtualbox/") is a web-based VirtualBox front-end written in PHP that allows you to access and control remote VirtualBox instances. It tries to resemble the VirtualBox GUI as much as possible to make work with it as easy as possible. It is a nice replacement for the VirtualBox GUI if you run VirtualBox in headless servers (like in the tutorial [VBoxHeadless - Running Virtual Machines With VirtualBox 4.3 On A Headless Ubuntu 14.04 Server]("http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.3-on-a-headless-ubuntu-14.04-lts-server")). This tutorial explains how to install phpvirtualbox on an Ubuntu 14.04 server to manage a locally installed, headless VirtualBox.
I'm running all the steps in this tutorial with root privileges, so make sure you're logged in as root:
sudo su
 
**2 Installing phpvirtualbox**

First create a system user called vbox and add it to the vboxusers group:
useradd -m vbox -G vboxusers
Create a password for the vbox user:
passwd vbox
Create the file /etc/default/virtualbox and put the line VBOXWEB_USER=vbox in it (so that the VirtualBox SOAP API which is called vboxwebsrv runs as the user vbox):
nano /etc/default/virtualbox
[TABLE="width: 90, align: center"]
[TR]
[TD]VBOXWEB_USER=vbox[/TD]
[/TR]
[/TABLE]
Next create the system startup links for vboxwebsrv and start it:
update-rc.d vboxweb-service defaults
service vboxweb-service start
We need a web server with PHP support to serve phpvirtualbox - I'm using Apache2 here. Install Apache2 and PHP5 as follows:
apt-get install apache2-mpm-prefork apache2-utils apache2.2-bin  apache2 apache2-doc apache2-suexec libapache2-mod-php5 libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libapr1 php5-common php5-mysql  php-pear wget
Restart Apache2:
service apache2 restart
I want to serve phpvirtualbox from Apache's default virtual host with the document root /var/www/html (I will install it in /var/www/html/phpvirtualbox) - if you have a different document root, you must adjust the following steps:
cd /var/www/html
wget [http://downloads.sourceforge.net/project/phpvirtualbox/phpvirtualbox-4.3-1.zip?](http://downloads.sourceforge.net/project/phpvirtualbox/phpvirtualbox-4.3-1.zip?)
Apt-get install unzip
Unzip phpvirtualbox and rename the phpvirtualbox-4.3-1 to phpvirtualbox for ease of use:
unzip phpvirtualbox-4.3-1.zip?
mv phpvirtualbox-4.3-1 phpvirtualbox
Next go to the /var/www/phpvirtualbox/ directory...
cd /var/www/html/phpvirtualbox/
... and create the file config.php by copying it from config.php-example:
cp config.php-example config.php
Open config.php and fill in the password you created earlier for the vbox system user:
nano config.php
[TABLE="width: 90, align: center"]
[TR]
[TD][...]/* Username / Password for system user that runs VirtualBox */var $username = 'vbox';var $password = 'secret';[...][/TD]
[/TR]
[/TABLE]
That's it already - you can now open a browser and access phpvirtualbox as follows:
[http://www.example.com/phpvirtualbox/](http://www.example.com/phpvirtualbox/)
[http://192.168.1.140/phpvirtualbox](http://192.168.1.140/phpvirtualbox)
Note I editied /etc/apache2/sites-available/000-default.conf.
And changed to this
        DocumentRoot /var/www/html/phpvirtualbox
That way I just type 192.168.1.140 and the database comes up.
This is the first milestone. Next we create a vm with ipcop, set it to the 3 adapters, create a strartup / shutdown script so the vm fires up all by itself. Then we drop in a little maintenance script I wrote.

---

