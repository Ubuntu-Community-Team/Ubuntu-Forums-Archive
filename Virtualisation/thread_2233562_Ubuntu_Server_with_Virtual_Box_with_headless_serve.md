---
title: "Ubuntu Server with Virtual Box with headless server + PHP interface running IPCOP"
date: 2014-07-09
forum: Virtualisation
---

### Post by alcatail on 2014-07-09
Will post up my code in the next few days with scripts I have written for creating an AP and fail over code between networks, etc.

---

### Post by slooksterpsv on 2014-07-10
Is this a guide, howto, question, or what? I believe you're letting us know what you've done and that you're going to share it - awesome! Just confused with the lack of content in the post.

---

### Post by alcatail on 2014-07-15
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
modem  ===> Red Ethernet interface of IPCop  ==> ipcop firewall ====> green(safe zone)
                                                                                        ====> Blue(Wifi Zone)
                                                                                        ====> orange (optional) for DMZ
   Modem   ========> Nuc =====> wifi bridge if ipcop fail ========> Blue
Green is protected from red and blue. There is a VPN between the blue and the green so that laptops and the wifi can access nas servers, printers and the private cloud.
Why a private cloud and a public cloud? The public cloud is setup for smart phones and can be accessed via anywhere on the internet. I&#8217;m at work, take a photo with my android phone and within 30 seconds the photo is sitting on my public cloud at home. I log in at work and share that photo in an email or it can be downloaded onto the work computer, etc. I use it for family overseas, etc, heaps better than photobucket and drop box, etc. I am in control of the data.
With regards to the private cloud all my laptops are synced to the private cloud and should the laptop be infected with an encryption virus the cloud has file revisions built into the software and all files can be restored through older revisions. Therefore whilst the encryption virus could cause disruption my files can be restored through older revisions.
Why IPCOP?  [http://www.ipcop.org/index.php](http://www.ipcop.org/index.php)
As mentioned it segregates all the networks and manages them better.  It has a proxy server and a VPN server. I use Copfilter of IPCOP so it scans for viruses coming in, shuts the pages down and stops the virus from passing through the network. It uses Privoxy and removes advertising from the web pages and stops google, yahoo, ebay, facebook from tracking you. By far the best firewall package I have ever used.
The virtual machine protects the physical machine and if the virtual machine is brought down it disconnects all the networks, so it is fairly robust. I have written a script for IPCOP so if it fails it creates a new wifi network using the inbuilt wifi in the nuc as a bridge to the modem and shuts the bridge down when IPCOP is working.  In this backup state green network is isolated from everything.
Stage one Base system (Ubuntu 14.04) with virtualisation (virtualbox)
Intel Nuc setup
Software needed &#8211; ubuntu 14.04 server downloaded iso. [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)
A spare usb flashdrive, a usb hub, 2 spare usb Ethernet nics
Win32 disc imager [http://sourceforge.net/projects/win32diskimager/](http://sourceforge.net/projects/win32diskimager/)
Winscp [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)
Putty [http://winscp.net/eng/download.php](http://winscp.net/eng/download.php)
Ipcop latest installation cd [http://www.ipcop.org/download.php](http://www.ipcop.org/download.php)
 
I program from a windows 7 laptop and a windows 8.1 laptop &#8211; so install the relevant win32 disc imager, winscp and putty.
Connect the Ethernet nics to the usb hub, then to the front of the nuc, a mouse to the hub and a the keyboard to the nuc. Connect the nuc to a tv or a monitor. Connect the lan cable up to one of the usb Ethernet nics.
Use the laptop to write the ubuntu14.04 iso image to the usb. Insert the usb to your intel nuc and switch it on.  Automatically detect all settings, I try to split off a separate ext4 partition to install my vm&#8217;s and other important files on for upgrades and or recoveries. 80 gig should be  heaps. I try to have a different partition for the /tmp as well. Through the install select ssh server. With the network select static  and put in an address that will work with your modem. Do not allow automatic updates. The ipcop VM will take care of security relating to the NUC.
When all this is done in  terminal type
```
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
 
Shutdown and remove the keyboard and mouse. Set the nuc up where you want it. It only needs the usb hub + the 2 ethernet nics and a monitor + lan cable but the monitor can stay switched off. The nuc needs to have something connected to the tv port (the monitor) for it to boot up. Plug the switch into the lan of the nuc
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
[TD]Intel® Wireless 7260
[/TD]
[TD]3.10+
[/TD]
[TD][iwlwifi-7260-ucode-22.1.7.0.tgz]("http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-7260-ucode-22.1.7.0.tgz")
[/TD]
[/TR]
[TR]
[TD]3.13+
[/TD]
[TD][iwlwifi-7260-ucode-22.24.8.0.tgz]("http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-7260-ucode-22.24.8.0.tgz")
[/TD]
[/TR]
[TR]
[TD]3.14+
[/TD]
[TD][iwlwifi-7260-ucode-23.214.9.0.tgz]("http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-7260-ucode-23.214.9.0.tgz")
[/TD]
[/TR]
[/TABLE]
Then copy the file onto the nuc using winscp
I usually create a download directory and from there
tar &#8211;zxvf iwlwifi-*.tgz
 
Then 
 
cp iwlwifi-*.ucode /lib/firmware
 
reboot
 
ifconfig &#8211;a
it should show up as wlan0
 
 
Now to set up virtual box!!!!
 
Based entirely on (pls excuse my cut and paste)
[http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.3-on-a-headless-ubuntu-14.04-lts-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.3-on-a-headless-ubuntu-14.04-lts-server)
 
[h=2]VBoxHeadless - Running Virtual Machines With VirtualBox 4.3 On A Headless Ubuntu 14.04 LTS Server[/h] Version 1.0
Author: Falko Timme, updated by Srijan Kishore


This guide explains how you can run virtual machines with [VirtualBox 4.3]("http://www.virtualbox.org/") on a headless Ubuntu 14.04 server. Normally you use the VirtualBox GUI to manage your virtual machines, but a server does not have a desktop environment. Fortunately, VirtualBox comes with a tool called VBoxHeadless that allows you to connect to the virtual machines over a remote desktop connection, so there's no need for the VirtualBox GUI.
I do not issue any guarantee that this will work for you!
 
[h=3]1 Preliminary Note[/h]I have tested this on an Ubuntu 14.04 server (host system) with the IP address 192.168.0.100 where I'm logged in as a normal user (user name administrator in this example) instead of as root.
 
[h=3]2 Installing VirtualBox[/h]Use putty and log in as root
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



[h=2]Managing A Headless VirtualBox Installation With phpvirtualbox (Ubuntu 14.04 LTS)[/h] 
Version 1.0
Author: Falko Timme, updated by Srijan Kishore


[phpvirtualbox]("http://code.google.com/p/phpvirtualbox/") is a web-based VirtualBox front-end written in PHP that allows you to access and control remote VirtualBox instances. It tries to resemble the VirtualBox GUI as much as possible to make work with it as easy as possible. It is a nice replacement for the VirtualBox GUI if you run VirtualBox in headless servers (like in the tutorial [VBoxHeadless - Running Virtual Machines With VirtualBox 4.3 On A Headless Ubuntu 14.04 Server]("http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.3-on-a-headless-ubuntu-14.04-lts-server")). This tutorial explains how to install phpvirtualbox on an Ubuntu 14.04 server to manage a locally installed, headless VirtualBox.
I'm running all the steps in this tutorial with root privileges, so make sure you're logged in as root:
sudo su
 
[h=3]2 Installing phpvirtualbox[/h]First create a system user called vbox and add it to the vboxusers group:
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
apt-get install unzip
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
nano /etc/apache2/sites-available/000-default.conf
And changed to this
        DocumentRoot /var/www/html/phpvirtualbox
service apache2 restart
That way I just type 192.168.1.140 and the database comes up.
This is the first milestone. Next we create a vm with ipcop, set it to the 3 adapters, create a strartup / shutdown script so the vm fires up all by itself. Then we drop in a little maintenance script I wrote.
Next step create a VM
Type the ip address the php web interface is on
192.168.1.140
Log in as admin admin
Click file preferences, users and change the password for admin
Create a new user for your self
Then click machine, create new
Add 3 network adapters.
Add the ipcop iso to the virtual cdrom
Configure the 3 network adapters to bridged and tie them to eth0, eth1 and p2p1.
(3 lans)
Red will be the eth the nuc is bridged to (eth0)
Green I normally do as p2p1 and blue I normally do to the other usb nic.
Static ip is better for the red interface give it something like 192.168.1.50. green will be the number you put on the list of paper earlier and the same with blue.
When it is finished and restarts you plug an access point into the blue usb Ethernet nic for your wifi and normally a switch into the green.
On the green you plug you printer server and nas units into the switch
We now need to mod the file in /etc/network/interfaces on the nuc, do this with winscp.
Change the hashes around so that the interface is no longer manual but static like this
 
#auto p2p1
#iface p2p1 inet manual
#up ifconfig $IFACE 0.0.0.0 up
#up ip link set $IFACE promisc on
#down ip link set $IFACE promisc off
#down ifconfig $IFACE down
 
 
auto p2p1
iface p2p1 inet static
address 192.168.20.140
netmask 255.255.255.0
network 192.168.20.0
gateway 192.168.20.1
dns-nameservers 192.168.20.1
 
save and reboot
then login to the php web interface, start up ipcop and wait for it to fully load.
On the nuc ping like this to check if ipcop is working.
ping &#8211;I p2p1 [www.google.com]("http://www.google.com")
If it comes up unkown host there is a networking problem either in the nuc, ipcop or virtual box the way the adapters are mapped.
If it is a success we can proceed to start ipcop as a service when the system starts and stops.
Open up /etc/default/virtualbox in winscp and add the following so that it looks like this
VBOXWEB_USER=vbox
SHUTDOWN_USERS="vbox root" # space-delimited list of users who might have runnings vms
SHUTDOWN=acpibutton           # if any are found, shut them down
This Script I pulled from somewhere a couple of years a go but it works well. I added a startup timer of 60 seconds to slow down the initial startup of the principle system so it doesn&#8217;t get smashed with a amillion and one things to do. Create a new file in /etc/init.d and call it vbox-yourvmname and chmod it to 0755 &#8211; easiest done by right clicking on the properties of it in winscp.
#copy and paste this script in it but change the vmlong and vmshort name #to your ipcop vm ##
#! /bin/sh
#
# chkconfig: 2345 90 10
### BEGIN INIT INFO
# Provides: vbox-service-template
# Required-Start: $remote_fs $syslog
# Required-Stop: $remote_fs $syslog
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: 'service-template' virtual machine
# Description: Starts and stops a VirtualBox host as a service.
### END INIT INFO
#/etc/nucnetworks.sh
 
# Author: Brendan Kidwell <brendan@glump.net>
# License: GPL 3 <http://opensource.org/licenses/GPL-3.0>
#
# Based on /etc/init.d/skeleton from Ubuntu 12.04.
 
#-------------------------------------------------------------------------------
#
# CONFIGURATION
#
# What is the name of the VM exactly as it appears in the VirtualBox control
# panel? This is the 'name' and the 'long name' of the VM.
#
# Does 'name' contain spaces or other special characters? If so, you must
# make up some other value for 'name' that doesn't have spaces.
#
# Setup:
#
# 1. Copy this file to /etc/init.d/vbox-'name'. The filename must start with
# the prefix "vbox-". Make sure you set the 'x' bit on the file to make it
# executable.
#
# 2. Edit 'Provides', above, to match the filename.
#
# 3. Edit 'Short-Description' to describe the function of the VM.
#
# 4. If 'long name' is different from 'name' fill it in below, otherwise leave
# LONGNAME as an empty string.
      VM_LONG_NAME="youripcopnamehere"
#
# 5. What user owns the virtual machine?
      VM_OWNER=vbox
#
# 6. Which stop command? "hibernate" or "powerbutton"
      VM_STOP=powerbutton
#
# 7. For the 'start-wait' command -- waiting until network is up, what is the
# VM's hostname?
      VM_HOSTNAME="youripcopnamehere"
#
#-------------------------------------------------------------------------------
 
# Do NOT "set -e"
 
# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/sbin:/usr/sbin:/bin:/usr/bin
# Pull DESC from file header
DESC=`grep --max-count=1 "^# Short-Description:" $(readlink -f $0)|cut --delimiter=' ' --field=3-|sed 's/^ *//'`
# Pull NAME from file header
NAME=`grep --max-count=1 "^# Provides:" $(readlink -f $0)|cut --delimiter=' ' --field=3-|sed 's/^ *//'`
SCRIPTNAME=/etc/init.d/$NAME
 
MANAGE_CMD=VBoxManage
 
# Get VM_SHORT_NAME from service name
VM_SHORT_NAME=`echo $NAME|cut --delimiter='-' --field=2-`
# Actual filename of VM is VM_SHORT_NAME, or if VM_LONG_NAME is set, use that
if [ ! "$VM_LONG_NAME" ] ; then VM_LONG_NAME=$VM_SHORT_NAME ; fi
 
# Do not use 'sudo' if this script is actually running as VM_OWNER already
if [ `whoami` = $VM_OWNER ] ; then SUDO_CMD="" ; else SUDO_CMD="sudo -H -u $VM_OWNER" ; fi
 
# Set VBoxManage command for stop action
if [ $VM_STOP = powerbutton ] ; then VM_STOP_CMD=acpipowerbutton ; else VM_STOP_CMD=savestate ; fi
 
# If VM_HOSTNAME isn't set (for 'start-wait' command) use VM_SHORTNAME
if [ ! "$VM_HOSTNAME" ] ; then VM_HOSTNAME=$VM_SHORT_NAME; fi
 
# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh
 
# Define LSB log_* functions.
# Depend on lsb-base (>= 3.2-14) to ensure that this file is present
# and status_of_proc is working.
. /lib/lsb/init-functions
 
get_vm_state()
{
    # possible SHORT_STATE values: running, paused, aborted, powered off
 
    VMINFO=$($SUDO_CMD $MANAGE_CMD showvminfo "$VM_LONG_NAME" 2>/dev/null)
    if [ $? = 0 ] ; then
        # No error retriving state string
        LONG_STATE=$(echo "$VMINFO"|grep --max-count=1 "^State:"|cut --delimiter=' ' \
            --fields=2-|sed 's/^ *//')
        SHORT_STATE=$(echo $LONG_STATE|cut --delimiter="(" --fields=1|sed 's/ *$//')
        # Fix for syntax highlighting in KomodoEdit for previous line
        [ 0 = 1 ] && NOOP=$(echo ")")
    else
        # VM must be missing
        LONG_STATE=missing
        SHORT_STATE=missing
    fi
}
 
do_start()
{
    # Return
    # 0 if daemon has been started
    # 1 if daemon was already running
    # 2 if daemon could not be started
 
    get_vm_state
 
    if [ "$SHORT_STATE" = "missing" ] ; then
echo Could not access VM \"$VM_LONG_NAME\".
        return 2
    fi
 
if [ "$SHORT_STATE" = "running" ] ; then
echo VM \"$VM_LONG_NAME\" is already running.
        return 1
    fi
#mick's code to allow 60 seconds for the server to start up before ipcop #to lighten the bourdon on the cpu on server startups
echo VM \"$VM_LONG_NAME\" will start in 60 seconds.
sleep 60
#end mick's code
 
    $SUDO_CMD $MANAGE_CMD startvm "$VM_LONG_NAME" -type vrdp || {
        echo Failed to start VM \"$VM_LONG_NAME\".
        return 2
    }
 
    # No status report; VBoxManage said if it worked.
    return 0
}
 
do_stop()
{
    # Return
    # 0 if daemon has been stopped
    # 1 if daemon was already stopped
    # 2 if daemon could not be stopped
    # other if a failure occurred
 
    get_vm_state
 
    if [ "$SHORT_STATE" = "missing" ] ; then
echo Could not access VM \"$VM_LONG_NAME\".
        return 3
    fi
 
if [ ! "$SHORT_STATE" = "running" ] ; then
echo VM \"$VM_LONG_NAME\" is already stopped.
        return 1
    fi
 
    $SUDO_CMD $MANAGE_CMD controlvm "$VM_LONG_NAME" $VM_STOP_CMD || {
        echo Failed to hibernate VM \"$VM_LONG_NAME\".
        return 2
    }
 
    echo Waiting for \"$VM_LONG_NAME\" to complete shutdown...
    while [ "$SHORT_STATE" = "running" ] ; do
sleep 1
        get_vm_state
    done
 
echo The VM \"$VM_LONG_NAME\" has been stopped \($VM_STOP\).
    return 0
}
 
do_status()
{
    get_vm_state
    if [ "$SHORT_STATE" = "missing" ] ; then
echo Could not access VM \"$VM_LONG_NAME\".
        return 2
    fi
echo Status of VM \"$VM_LONG_NAME\": $LONG_STATE
 
    if [ "$SHORT_STATE" = "running" ] ; then return 1 ; else return 0 ; fi
}
 
do_reload() {
    VM_STOP=powerbutton
    VM_STOP_CMD=acpipowerbutton
    do_stop && do_start
}
 
do_wait_for_online() {
    echo Waiting for \"$VM_LONG_NAME\" to come up on the network...
    while [ ! "$result" = "0" ] ; do
sleep 1
        ping -c 1 $VM_HOSTNAME >/dev/null 2>/dev/null
        result=$?
    done
echo Ready.
}
 
case "$1" in
  start)
    [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
    do_start
    case "$?" in
        0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
        2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
    esac
    ;;
  start-wait)
    do_start && do_wait_for_online
    ;;
  stop)
    [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
    do_stop
    case "$?" in
        0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
        2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
    esac
    ;;
  status)
    do_status && exit 0 || exit $?
    ;;
  restart|force-reload)
    #
    # If the "reload" option is implemented then remove the
    # 'force-reload' alias
    #
    [ "$VERBOSE" != no ] && log_daemon_msg "Restarting $DESC" "$NAME"
    VM_STOP=powerbutton
    VM_STOP_CMD=acpipowerbutton
    do_stop
    case "$?" in
      0|1)
        do_start
        case "$?" in
            0) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
            1) [ "$VERBOSE" != no ] && log_end_msg 1 ;; # Old process is still running
            *) [ "$VERBOSE" != no ] && log_end_msg 1 ;; # Failed to start
        esac
        ;;
      *)
        # Failed to stop
        [ "$VERBOSE" != no ] && log_end_msg 1
        ;;
    esac
    ;;
  restart-wait)
    VM_STOP=poweroff
    VM_STOP_CMD=acpipowerbutton
    do_stop
    do_start && do_wait_for_online
    ;;
  *)
    echo "Usage: $SCRIPTNAME {start|start-wait|stop|status|restart|restart-wait|force-reload}" >&2
    exit 3
    ;;
esac
 
:
###### End of Script!! 
 
 
Now test the script
/etc/init.d/yourscriptname start
/etc/init.d/yourscriptname stop
 
If success then update it to the rc.d defaults
update-rc.d yourscriptname defaults 90
to remove it from rc.d defaults
update-rc.d yourscriptname remove
restart the nuc and it should fire up ipcop and shut it down
 
Next step locking down the nuc and setting a failover wifi network
Got my instructions from here &#8211; so it is another cut and paste!
[http://www.cyberciti.biz/faq/debian-ubuntu-linux-setting-wireless-access-point/](http://www.cyberciti.biz/faq/debian-ubuntu-linux-setting-wireless-access-point/)
from putty...
apt-get install hostapd
nano /etc/default/hostapd
Uncomment and set DAEMON_CONF to the absolute path of a hostapd configuration file and hostapd will be started during system boot:
 DAEMON_CONF="/etc/hostapd/hostapd.conf" Save and close the file. Next create a text file called /etc/hostapd/hostapd.conf, enter:
nano /etc/hostapd/hostapd.conf
Set interface name:
### Wireless network name ###
interface=wlan0
### Set your bridge name ###
bridge=br0
#Set driver name:
driver=nl80211
#Set country name code in ISO/IEC 3166-1 format. This is used to set #regulatory domain. Set as needed to indicate country in which device is #operating. This can limit available channels and transmit power.
### (IN == INDIA, UK == United Kingdom, US == United Stats and so on ) ###
country_code=AU
#Set your SSID:
ssid=yournamehere
#Set operation mode (a = IEEE 802.11a, b = IEEE 802.11b, g = IEEE 802.11g)
#hw_mode=g
hw_mode=g
#Set channel number (some driver will only use 0 as value)
channel=6
#Set wpa mode to 2:
wpa=2
#wpa=3
#Set your passphrase (WiFi password):
wpa_passphrase=Test1234567890
#Set key and auth optionsmanagement for WPA2:
## Key management algorithms ##
wpa_key_mgmt=WPA-PSK
## Set cipher suites (encryption algorithms) ##
## TKIP = Temporal Key Integrity Protocol
## CCMP = AES in Counter mode with CBC-MAC
wpa_pairwise=TKIP
rsn_pairwise=CCMP
## Shared Key Authentication ##
auth_algs=1
## Accept all MAC address ###
macaddr_acl=0
ignore_broadcast_ssid=0
 Save and close the file.
**How Do I start / stop / restart AP?**
Use the following commands:
# /etc/init.d/hostapd start
# /etc/init.d/hostapd stop
# /etc/init.d/hostapd restart
**Step #3: Configure /etc/network/interfaces**
Change the file to look like this with much painstaking hours I found this to be the best config, but you will have to put your own ip ranges in to suit
 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 
# The loopback network interface
 
 
#auto lo
 
 
##iface lo inet loopback
 
#auto eth0
#iface eth0 inet static
#address 192.168.1.150
#netmask 255.255.255.0
#network 192.168.1.0
#gateway 192.168.1.1
#The primary network interface
 
auto p2p1
iface p2p1 inet static
address 192.168.20.150
netmask 255.255.255.0
network 192.168.20.0
gateway 192.168.20.1
dns-nameservers 192.168.20.1
#auto p2p1
#iface p2p1 inet dhcp
 
 
auto eth1
iface eth1 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down
 
 
#auto p2p1
#iface p2p1 inet manual
#up ifconfig $IFACE 0.0.0.0 up
#up ip link set $IFACE promisc on
#down ip link set $IFACE promisc off
#down ifconfig $IFACE down
 
 
auto eth0
iface eth0 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down
 
 
 
 
 
####WIRELESS
 
auto lo br0
iface lo inet loopback
 
allow-hotplug wlan0
iface wlan0 inet manual
allow-hotplug eth0
iface eth0 inet manual
iface br0 inet static
    bridge_ports wlan0 eth0
    address 192.168.1.150
    netmask 255.255.255.0
    network 192.168.1.0
   
 ####WIRELESSS
 
 
 
Save and close 
apt-get install bridge-utils
reboot
You should now have two ways to access the nuc and it will also be an access point to your modem &#8211; there will be a red wifi and a green wifi
The lockdown of the nuc.
These scripts ensure the nuc stays locked out from the red when the nuc and IPCOP are working correctly. When the Nuc fails to connect to the net or the modem the scripts reinstate the access from the modem side of the nuc and tries to reboot ipcop if it is still down after 5 minutes.It provides an alternative wifi for your devices and allows access to the nuc from the red side.
Create some new files
miscript
 
#Written by Michael Paterson 2014####
case "$1" in
  wifion )
      echo "wifi switching on"
sleep 2
/sbin/ifdown --force eth0
sleep 2
service hostapd restart
sleep 2
/sbin/ifup wlan0
sleep 2
/sbin/ifup br0
sleep 2
/sbin/ifup eth0    
 
esac
 
case "$1" in
  wifioff )
      echo "wifi switching off"
sleep 1
service hostapd stop
/sbin/ifdown eth0
sleep 2
/sbin/ifdown --force br0
sleep 2
/sbin/ifdown --force wlan0
sleep 2
/sbin/ifup eth0
sleep 2
    esac
 
case "$1" in
  vm1restart )
      echo "vm1restart"
sleep 1
/etc/pingcheck/vbox-vm1 restart
#service hostapd restart
#/sbin/ifup wlan0
#wait 60
#service hostapd restart
#/sbin/ifup wlan0
 
   
esac
 
case "$1" in
  vm1stop )
      echo "vm1stop"
sleep 1
/etc/init.d/vbox-vm1 stop
 
pingcheck.sh
 
 
 
#!/bin/bash
#Written by Michael Paterson, to be used in conjunction with miscript #####
# 1. don't need this this is only if you need it as a daemon!# #while true; do
      
if ping -c 1 -I p2p1 [www.google.com](www.google.com) > /dev/null 2>&1; then
              #  /etc/pingscripts/recover.sh #run the first script
              echo "succsess"
                 sleep 5     
if ping -c 1 -I br0 192.168.0.1 > /dev/null 2>&1; then
/etc/pingcheck/miscript wifioff
fi
 
else
 
echo "fail -1st scan will wait 10 seconds"
 
sleep 10
if ping -c 1 -I p2p1 [www.google.com](www.google.com) > /dev/null 2>&1; then
echo "success"
                 sleep 5     
if ping -c 1 -I br0 192.168.0.1 > /dev/null 2>&1; then
/etc/pingcheck/miscript wifioff
fi
 
 
else
echo "2nd scan fail will wait a further 30 seconds"
sleep 30
 
if ping -c 1 -I br0 192.168.0.1 > /dev/null 2>&1; then
echo wifi already on
 
else
/etc/pingcheck/miscript wifion
fi
 
if ping -c 1 -I p2p1 [www.google.com](www.google.com) > /dev/null 2>&1; then
echo "success"
                 sleep 5     
if ping -c 1 -I br0 192.168.0.1 > /dev/null 2>&1; then
/etc/pingcheck/miscript wifioff
fi
 
else
echo "3rd attempt failed final attempt will wait a further 1 minutes before killing connections and reinstating new networks"
 
sleep 60
if ping -c 1 -I p2p1 [www.google.com](www.google.com) > /dev/null 2>&1; then
echo "success finally"
                 sleep 5     
if ping -c 1 -I br0 192.168.0.1 > /dev/null 2>&1; then
/etc/pingcheck/miscript wifioff
fi
 
else
echo "4th attempt failed final attempt will wait a further 1 minutes 10 seconds before killing connections and reinstating new networks"
sleep 70
 
if ping -c 1 -I p2p1 [www.google.com](www.google.com) > /dev/null 2>&1; then
echo "success finally"
                 sleep 5     
if ping -c 1 -I br0 192.168.0.1 > /dev/null 2>&1; then
/etc/pingcheck/miscript wifioff
fi
 
 
else
echo "5th attempt failed final attempt will wait a further 1 minutes 10 seconds before killing connections and reinstating new networks"
sleep 70
 
if ping -c 1 -I p2p1 [www.google.com](www.google.com) > /dev/null 2>&1; then
echo "success finally"
                 sleep 5     
if ping -c 1 -I br0 192.168.0.1 > /dev/null 2>&1; then
/etc/pingcheck/miscript wifioff
fi
 
else
echo "6th attempt failed final attempt will wait a further 1 minutes before killing connections and reinstating new networks"
sleep 70
 
 
 
if ping -c 1 -I p2p1 [www.google.com](www.google.com) > /dev/null 2>&1; then
echo "success finally"
                 sleep 5     
if ping -c 1 -I br0 192.168.0.1 > /dev/null 2>&1; then
/etc/pingcheck/miscript wifioff
fi
 
else
echo "fail, rebooting virtual machine"
/etc/pingcheck/miscript vm1restart
 
sleep 10
 
 
fi
fi
fi
fi
fi
fi
fi
       # if ! [ "`ping -c 1 google.com`" ]; then #if ping *still* exits nonzero...
       #       #  /etc/pingscripts/normal.sh #run the second script
       #        echo "no contact with google"
        #       sleep 10     #give it a few seconds to complete
       # fi
        sleep 3 
# 1. #done # in ref to running as a daemon
 
 
 
 
 
Sample vbox script
 
#! /bin/sh
#
# chkconfig: 2345 90 10
### BEGIN INIT INFO
# Provides: vbox-service-template
# Required-Start: $remote_fs $syslog
# Required-Stop: $remote_fs $syslog
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: 'service-template' virtual machine
# Description: Starts and stops a VirtualBox host as a service.
### END INIT INFO
#
 
# Author: Brendan Kidwell <brendan@glump.net>
# License: GPL 3 <http://opensource.org/licenses/GPL-3.0>
#
# Based on /etc/init.d/skeleton from Ubuntu 12.04.
 
#-------------------------------------------------------------------------------
#
# CONFIGURATION
#
# What is the name of the VM exactly as it appears in the VirtualBox control
# panel? This is the 'name' and the 'long name' of the VM.
#
# Does 'name' contain spaces or other special characters? If so, you must
# make up some other value for 'name' that doesn't have spaces.
#
# Setup:
#
# 1. Copy this file to /etc/init.d/vbox-'name'. The filename must start with
# the prefix "vbox-". Make sure you set the 'x' bit on the file to make it
# executable.
#
# 2. Edit 'Provides', above, to match the filename.
#
# 3. Edit 'Short-Description' to describe the function of the VM.
#
# 4. If 'long name' is different from 'name' fill it in below, otherwise leave
# LONGNAME as an empty string.
      VM_LONG_NAME="yourvmname"
#
# 5. What user owns the virtual machine?
      VM_OWNER=vbox
#
# 6. Which stop command? "hibernate" or "powerbutton"
      VM_STOP=powerbutton
#
# 7. For the 'start-wait' command -- waiting until network is up, what is the
# VM's hostname?
      VM_HOSTNAME="yourvmname"
#
#-------------------------------------------------------------------------------
 
# Do NOT "set -e"
 
# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/sbin:/usr/sbin:/bin:/usr/bin
# Pull DESC from file header
DESC=`grep --max-count=1 "^# Short-Description:" $(readlink -f $0)|cut --delimiter=' ' --field=3-|sed 's/^ *//'`
# Pull NAME from file header
NAME=`grep --max-count=1 "^# Provides:" $(readlink -f $0)|cut --delimiter=' ' --field=3-|sed 's/^ *//'`
SCRIPTNAME=/etc/init.d/$NAME
 
MANAGE_CMD=VBoxManage
 
# Get VM_SHORT_NAME from service name
VM_SHORT_NAME=`echo $NAME|cut --delimiter='-' --field=2-`
# Actual filename of VM is VM_SHORT_NAME, or if VM_LONG_NAME is set, use that
if [ ! "$VM_LONG_NAME" ] ; then VM_LONG_NAME=$VM_SHORT_NAME ; fi
 
# Do not use 'sudo' if this script is actually running as VM_OWNER already
if [ `whoami` = $VM_OWNER ] ; then SUDO_CMD="" ; else SUDO_CMD="sudo -H -u $VM_OWNER" ; fi
 
# Set VBoxManage command for stop action
if [ $VM_STOP = powerbutton ] ; then VM_STOP_CMD=acpipowerbutton ; else VM_STOP_CMD=savestate ; fi
 
# If VM_HOSTNAME isn't set (for 'start-wait' command) use VM_SHORTNAME
if [ ! "$VM_HOSTNAME" ] ; then VM_HOSTNAME=$VM_SHORT_NAME; fi
 
# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh
 
# Define LSB log_* functions.
# Depend on lsb-base (>= 3.2-14) to ensure that this file is present
# and status_of_proc is working.
. /lib/lsb/init-functions
 
get_vm_state()
{
    # possible SHORT_STATE values: running, paused, aborted, powered off
 
    VMINFO=$($SUDO_CMD $MANAGE_CMD showvminfo "$VM_LONG_NAME" 2>/dev/null)
    if [ $? = 0 ] ; then
        # No error retriving state string
        LONG_STATE=$(echo "$VMINFO"|grep --max-count=1 "^State:"|cut --delimiter=' ' \
            --fields=2-|sed 's/^ *//')
        SHORT_STATE=$(echo $LONG_STATE|cut --delimiter="(" --fields=1|sed 's/ *$//')
        # Fix for syntax highlighting in KomodoEdit for previous line
        [ 0 = 1 ] && NOOP=$(echo ")")
    else
        # VM must be missing
        LONG_STATE=missing
        SHORT_STATE=missing
    fi
}
 
do_start()
{
    # Return
    # 0 if daemon has been started
    # 1 if daemon was already running
    # 2 if daemon could not be started
 
    get_vm_state
 
    if [ "$SHORT_STATE" = "missing" ] ; then
echo Could not access VM \"$VM_LONG_NAME\".
        return 2
    fi
 
if [ "$SHORT_STATE" = "running" ] ; then
echo VM \"$VM_LONG_NAME\" is already running.
        return 1
    fi
#mick's code
echo VM \"$VM_LONG_NAME\" will start in 1 seconds.
sleep 1
#end mick's code
 
    $SUDO_CMD $MANAGE_CMD startvm "$VM_LONG_NAME" -type vrdp || {
        echo Failed to start VM \"$VM_LONG_NAME\".
        return 2
    }
 
    # No status report; VBoxManage said if it worked.
    return 0
}
 
do_stop()
{
    # Return
    # 0 if daemon has been stopped
    # 1 if daemon was already stopped
    # 2 if daemon could not be stopped
    # other if a failure occurred
 
    get_vm_state
 
    if [ "$SHORT_STATE" = "missing" ] ; then
echo Could not access VM \"$VM_LONG_NAME\".
        return 3
    fi
 
if [ ! "$SHORT_STATE" = "running" ] ; then
echo VM \"$VM_LONG_NAME\" is already stopped.
        return 1
    fi
 
    $SUDO_CMD $MANAGE_CMD controlvm "$VM_LONG_NAME" $VM_STOP_CMD || {
        echo Failed to hibernate VM \"$VM_LONG_NAME\".
        return 2
    }
 
    echo Waiting for \"$VM_LONG_NAME\" to complete shutdown...
    while [ "$SHORT_STATE" = "running" ] ; do
sleep 1
        get_vm_state
    done
 
echo The VM \"$VM_LONG_NAME\" has been stopped \($VM_STOP\).
    return 0
}
 
do_status()
{
    get_vm_state
    if [ "$SHORT_STATE" = "missing" ] ; then
echo Could not access VM \"$VM_LONG_NAME\".
        return 2
    fi
echo Status of VM \"$VM_LONG_NAME\": $LONG_STATE
 
    if [ "$SHORT_STATE" = "running" ] ; then return 1 ; else return 0 ; fi
}
 
do_reload() {
    VM_STOP=powerbutton
    VM_STOP_CMD=acpipowerbutton
    do_stop && do_start
}
 
do_wait_for_online() {
    echo Waiting for \"$VM_LONG_NAME\" to come up on the network...
    while [ ! "$result" = "0" ] ; do
sleep 1
        ping -c 1 $VM_HOSTNAME >/dev/null 2>/dev/null
        result=$?
    done
echo Ready.
}
 
case "$1" in
  start)
    [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
    do_start
    case "$?" in
        0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
        2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
    esac
    ;;
  start-wait)
    do_start && do_wait_for_online
    ;;
  stop)
    [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
    do_stop
    case "$?" in
        0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
        2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
    esac
    ;;
  status)
    do_status && exit 0 || exit $?
    ;;
  restart|force-reload)
    #
    # If the "reload" option is implemented then remove the
    # 'force-reload' alias
    #
    [ "$VERBOSE" != no ] && log_daemon_msg "Restarting $DESC" "$NAME"
    VM_STOP=powerbutton
    VM_STOP_CMD=acpipowerbutton
    do_stop
    case "$?" in
      0|1)
        do_start
        case "$?" in
            0) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
            1) [ "$VERBOSE" != no ] && log_end_msg 1 ;; # Old process is still running
            *) [ "$VERBOSE" != no ] && log_end_msg 1 ;; # Failed to start
        esac
        ;;
      *)
        # Failed to stop
        [ "$VERBOSE" != no ] && log_end_msg 1
        ;;
    esac
    ;;
  restart-wait)
    VM_STOP=poweroff
    VM_STOP_CMD=acpipowerbutton
    do_stop
    do_start && do_wait_for_online
    ;;
  *)
    echo "Usage: $SCRIPTNAME {start|start-wait|stop|status|restart|restart-wait|force-reload}" >&2
    exit 3
    ;;
esac
 
:
 
 
 
and copy your vbox start up script to this directory and remove the startup time of 60 seconds.
 
In puty type
Crontab &#8211;e
Add this entry
*/5 * * * * /etc/pingcheck/pingcheck.sh
Save and close &#8211; it will run the scripts every 5 minutes
Optional... You don&#8217;t need to necessarily do these patches or fixes...
Ethernet fix if required
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#92](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#92)
download the rtl6169 driver and  Transfer to the nuc using winzip
tar vjxf r8169-*.bz2
cd r8169-*
   If you are running the target kernel, then you should be able to do :
 
                # make clean modules    (as root or with sudo)
                # make install
                # depmod -a
                # modprobe r8169
 
        You can check whether the driver is loaded by using following commands.
 
                # lsmod | grep r8169
                # ifconfig -a
 
        If there is a device name, ethX, shown on the monitor, the linux
        driver is loaded.
 
Optional resolv.conf
 
```
Summary this will give you a security appliance for your cloud and everything except the public cloud will be controlled by this appliance. I call it the nucserver!
In my next posts I will add the instructions for the &#8216;owncloud how to&#8217;s&#8217; and the printer server. Also will do one for the latest zoneminder on ubuntu 14.04(camera server)

---

### Post by slooksterpsv on 2014-07-17
Awesome, usually with config files, and commands, you'll more commonly see them like this - example:

First download and install apache, mysql, and php:
```

sudo apt-add-repository ppa:someRandomPPA/NewApacheServerBuilds
sudo apt-get update
sudo apt-get install apache2 php5-mysql mysqld phpmyadmin

```

Modify your apache file to look like this:
```

...#some apache stuff here
<Document Root>
...#more apache stuff

```

---

