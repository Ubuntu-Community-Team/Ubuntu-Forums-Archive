---
title: "Xen Cloud Platform (XCP) on Ubuntu Server 13.10 (Saucy Salamander)"
date: 2013-10-23
forum: Virtualisation
---

### Post by Rich.T. on 2013-10-23
[SIZE=4][COLOR="#FF0000"]Broken: Xen Cloud Platform (XCP) on Ubuntu Server 14.04 LTS (Trusty Tahr)[/COLOR][/SIZE]

Update 28th May 2014:

I was today in the process of installing a new XCP visualisation server and found that the xcp-xapi package is missing from the repo.
A brief look at [xcp-xapi 1.3.2-15ubuntu2 (amd64 binary) in ubuntu trusty]("https://launchpad.net/ubuntu/trusty/amd64/xcp-xapi/1.3.2-15ubuntu2") and [&#8220;xen-api&#8221; 1.3.2-15ubuntu2 source package in The Trusty Tahr]("https://launchpad.net/ubuntu/trusty/+source/xen-api/1.3.2-15ubuntu2") shows: > Status: Deleted and > 1.3.2-15ubuntu2 DELETED: Trusty pocket Release in component universe and section admin. Removal requested on 2013-12-24. Deleted on 2013-12-24 by Matthias Klose. ocaml transition: doesn&#8217;t build

I'm guessing that this is because XCP on Debian/Ubuntu and all platforms other than CentOS is no longer supported by Citrix, XCP has deprecated and major dependencies are now broken, but I must say that this is a terrible situation. As far as I'm aware, OpenStack and some others use XCP on Ubuntu for their infrastructure and this would appear to be a cynical method of getting them to switch to XenServer/CentOS. Personally I'd like to stick with Ubuntu and also don't like the Idea of switching to an inferior Xen Toolstack. Perhaps I aught to start from scratch and learn to use KVM?

If anyone knows anything about this situation and if it is likely to be remedied please let me know, I'd really appreciate it!

I will endeavour to get xcp-xapi installed by other means and report back as soon as I am able. Don't hold your breath though...

[SIZE=3]This update is taken from [this comment]("http://ubuntuforums.org/showthread.php?t=2183067&p=13035405#post13035405"), below.[/SIZE]

The original post...

[COLOR="#FF0000"][SIZE=5]Installing and configuring Ubuntu 13.10 (Saucy Salamander) with Xen Cloud Platform (dom0) and an Ubuntu 13.10 (Saucy Salamander) guest (domU).[/SIZE][/COLOR]

**Install Ubuntu Server:**

Copy ubuntu-13.10-server-amd64.iso to a CD or Flashdrive and boot from your server hardware.

[SIZE=1]Note: You may need to use a PS2 keyboard, as opposed to a USB one if you have keyboard troubles during the installation process. A USB keyboard should be fine once you have booted into the installed system.
[/SIZE]
[SIZE=1][https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20%28XenAPI%29%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager](https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20%28XenAPI%29%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager)[/SIZE]

Install a minimal system (Press F4 during the CD install)

FYI: For my partitioning scheme, I chose to do this manually and created:
> Partition 1: 1024MB, ext2, bootable, /boot.
Partition 2: Rest of drive, physical volume for LVM.
Configured LVM as: Volume Group "ServerVG", used all remaining space on HDD.
Created Logical volumes in this group: "Swap", 17GB, swap; "Root", 20GB, ext4, /; "ServerSR", 100GB, ext3, /media/richard/ServerSR.

Select only an OpenSSH Server when asked in Tasksel.

Complete the installation process and reboot the server.

**Install XCP-XAPI with bridge networking:**

Install Packages and update your system.

```
sudo apt-get update && sudo apt-get -y dist-upgrade && sudo apt-get -y install vim && sudo apt-get -y install mc && sudo apt-get -y install htop && sudo apt-get -y install xen-hypervisor
```
**Configure GRUB for Xen Booting:**

[SIZE=1]Please note that from Xen version 4.4 Xen automatically configures GRUB to boot into Xen by default, so configuring GRUB_DEFAULT should not be necessary.
```
sudo update-grub
Including Xen overrides from /etc/default/grub.d/xen.cfg
WARNING: GRUB_DEFAULT changed to boot into Xen by default!
         Edit /etc/default/grub.d/xen.cfg to avoid this warning.
Generating grub configuration file ...
```
However: Configuring VCPU and memory as well as disabling apparmour at boot is still necessarry, I believe.
[/SIZE]

[SIZE=1]The official grub manual describes this correctly: [http://www.gnu.org/software/grub/manual/grub.html#Simple-configuration](http://www.gnu.org/software/grub/manual/grub.html#Simple-configuration)[/SIZE]

Put the following in /etc/default/grub:
```
sudo vim /etc/default/grub

```
```
#Tell GRUB to remember last selection:
GRUB_DEFAULT="saved"
GRUB_SAVEDEFAULT="true"

[...]

#Disable apparmor at boot:
GRUB_CMDLINE_LINUX="apparmor=0"
#Restrict "dom0" to 1GB of memory and 1 VCPU:
GRUB_CMDLINE_XEN="dom0_mem=1G,max:1G dom0_max_vcpus=1"

```
[SIZE=1]Note 1: The first part;
```
#Tell GRUB to remember last selection:
GRUB_DEFAULT="saved"
GRUB_SAVEDEFAULT="true"
```
does not always work (I don't know why).
Instead you may want to try;
```
GRUB_DEFAULT="2"
```
or
```
GRUB_DEFAULT="Xen 4.4-amd64"
```

Note 2: Why should I dedicate fixed amount of memory for Xen "dom0"?

First of all (dom0) Linux kernel calculates various network related parameters based on the boot time amount of memory.
The second reason is Linux needs memory to store the memory metadata (per page info structures), and this allocation is also based on the boot time amount of memory.

[SIZE=1][http://wiki.xen.org/wiki/Xen_Best_Practices](http://wiki.xen.org/wiki/Xen_Best_Practices)[/SIZE][/SIZE]

```
sudo update-grub

sudo reboot
```

Select "Ubuntu / Gnu Linux with Xen hypervisor" from GRUB boot menu.

Login and then check to see if Xen is running:

```
cat /proc/xen/capabilities
"control_d"
```

[SIZE=1]Not necessary at this stage:

[S]Add XCP-PPA via:
```
sudo apt-get install python-software-properties
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:ubuntu-xen-org/xcp-unstable
```[/S][/SIZE]

**Install XCP-XAPI:**

```
sudo apt-get install -y xcp-xapi && sudo apt-get install qemu-common
```
-> Choose "bridge" when prompted for network backend.

To reconfigure later:
```
sudo dpkg-reconfigure xcp-networkd
```

Tell Xen what it's toolstack should be:

```
sudo vim /etc/default/xen 
```
```
TOOLSTACK=xapi
```
[SIZE=1]Not Neccessary:
[S]```
sudo mkdir /usr/share/qemu; sudo ln -s /usr/share/qemu-linaro/keymaps /usr/share/qemu/keymaps
```[/SIZE]
[SIZE=1][http://wiki.xen.org/wiki/XAPI_toolstack_on_a_Debian-based_distribution#Setup_the_network.2Finterfaces_file](http://wiki.xen.org/wiki/XAPI_toolstack_on_a_Debian-based_distribution#Setup_the_network.2Finterfaces_file)[/S][/SIZE]

**Set up network bridging (DHCP):**
```
sudo vim /etc/network/interfaces
```

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Xen network interface for "dom0"
auto xenbr0
iface xenbr0 inet dhcp

bridge_ports eth0

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
```

At this stage, it might be worthwhile setting up the ability to connect to the server via XenCenter or OpenXenManager, if you have this utility installed on another PC.
After the next reboot, if this software is able to 'talk' to your server, you should get a prompt to authorise it's SSL certificate. This is a good indication that some form of communication is happening between the management software and the server.
Even if there are subsequent errors, this should be a good sign.

[B]To enable remote access by XenCenter:
[/B]
You will get the error "XenCenter has encountered a problem connecting to this server... Incorrect username and/or password.", or similar (depending on the software); so carrying out the following actions on the server will be neccessary:
```
sudo usermod -a -G xapi richard
```
[SIZE=1][http://ubuntuforums.org/showthread.php?t=2158441](http://ubuntuforums.org/showthread.php?t=2158441)[/SIZE]

Uncomment "auth sufficient pam_succeed_if.so user ingroup xapi"
```
sudo vim /etc/pam.d/xapi
```
```
#%PAM-1.0
#@include common-auth

# Uncomment this line to allow users of group xapi to authenticate
auth sufficient pam_succeed_if.so user ingroup xapi

# Only allow group root to authenticate, unless above line uncommented
auth required pam_succeed_if.so user ingroup root
```
```
sudo reboot
```

If this doesn't work, try replacing all with:

```
auth include common-auth
account include common-auth
password include common-auth
```
If the server is installed with an encrypted 'Home' directory, you may get the message:

> Unable to connect to server 'Server'.
The connection was refused.
Check that XenServer is configured correctly on 'Server' and try again.
The only way that I found around this is to reinstall with an unencrypted Home directory. Sorry!

[SIZE=1][http://www.citrix.com/downloads/xenserver/product-software/xenserver-62.html](http://www.citrix.com/downloads/xenserver/product-software/xenserver-62.html)[/SIZE]

```
sudo reboot
```

If you use the openvswitch mode (and not bridging), then you will need to tell XCP about your network configuration. [s]In fact, it doesn't seem to hurt if you're using bridging[/s]:
[SIZE=1](NOTE: I haven't been able to get openvswitch working and I also found that performing the following commands did cause some network connectivity problems on startup.)[/SIZE]

[s]```
sudo su
PIF_UUID=`xe pif-list device=eth0 --minimal`
xe pif-reconfigure-ip uuid=$PIF_UUID mode=dhcp
```
All set! Ready to reboot and let xcp-xapi toolstack take over:
```
sudo reboot
```[/s]
Login now and check that xcp/xapi is up and running:
```
service xcp-xapi status
sudo xe host-list
sudo xe vm-list
sudo xe network-list
sudo xe sr-list
sudo xe pif-list
cat /etc/xcp/inventory
```

**Configure Storage Repository for Use With XAPI:**

[SIZE=1][http://www.howtoforge.com/linux_lvm_p2](http://www.howtoforge.com/linux_lvm_p2)[/SIZE]
[SIZE=1][https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20%28XenAPI%29%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager](https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20%28XenAPI%29%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager)[/SIZE]

To show your volume group (VG):
```
sudo pvs
sudo vgscan
sudo vgdisplay
```
To show your logical volumes (LV):
```
sudo lvdisplay
sudo lvscan
```
Create a LV with X GBs:
"sudo lvcreate -L <X>GB -n <StorageRepositoryName> /dev/<VG>"
```
sudo lvcreate -L 10GB -n ServerSR ServerVG
```
To show your logical volumes (LV):
```
sudo lvdisplay
sudo lvscan
```

Note: If you created a LV for your storage repository during the installation of the server, please comment out it's entry in /etc/fstab in order to give Xen uncontested access to it:

```
sudo vim /etc/fstab
```
```
#/dev/mapper/ServerVG-ServerSR /media/richard/ServerSR ext3    defaults        0       2
```
```
sudo reboot
```
Register the logical volume for use with XAPI:
"sudo xe sr-create type=ext shared=true name-label=<StorageRepositoryName> device-config:device=/dev/<VG>/<StorageRepositoryName>"
```
sudo su
SR=`xe sr-create type=ext shared=true name-label=ServerSR device-config:device=/dev/ServerVG/ServerSR`
```
then set the SR as the pool default SR:
```
POOL=`xe pool-list --minimal`
xe pool-param-set uuid=$POOL default-SR=$SR
```
This should display the Storage Repository:
"sudo xe sr-list name-label=<StorageRepositoryName>"
```
sudo xe sr-list name-label=ServerSR
sudo xe sr-list
sudo xe pool-list
```
Configure a ISO Repository for Use With XAPI:
An ISO Repository contains ISOs (disk images) with operational systems to perform the installations.
"sudo xe sr-create name-label=<LocalISORepositoryName> type=iso shared=true device-config:location=<FolderPath> device-config:legacy_mode=true content-type=iso"

The following example makes a storage repository called "LocalISORepository" in your /home directory:
```
mkdir /home/richard/LocalISORepository/
sudo xe sr-create name-label=LocalISORepository type=iso shared=true device-config:location=/home/richard/LocalISORepository/ device-config:legacy_mode=true content-type=iso
```
This should display the ISO Repository
"sudo xe sr-list name-label=<LocalISORepositoryName>"
```
sudo xe sr-list name-label=LocalISORepository
sudo xe sr-list
```
To delete a local storage repository:
[SIZE=1][http://forums.citrix.com/thread.jspa?threadID=252332&tstart=135](http://forums.citrix.com/thread.jspa?threadID=252332&tstart=135)[/SIZE]
```
sudo lvremove /dev/ServerVG/StorageRepository
```
If you lost your guest templates, the list will be empty in XenCenter and if you do "xe template-list" nothing will appear.. do this:
[SIZE=1][http://blog.jamesrhall.com/2012/06/xcp-on-ubuntu.html](http://blog.jamesrhall.com/2012/06/xcp-on-ubuntu.html)
```
cd /usr/lib/xcp/lib[/SIZE]
sudo ./create_templates
```

**Installing Ubuntu 13.10 Saucy Salamender domU guest:**

[SIZE=1][http://wiki.xen.org/wiki/Installing_Linux_on_Kronos](http://wiki.xen.org/wiki/Installing_Linux_on_Kronos)[/SIZE]
[SIZE=1][http://pravinchavan.wordpress.com/2013/10/01/xen-cloud-platform-xcp-installing-ubuntu-13-04-raring-vm/](http://pravinchavan.wordpress.com/2013/10/01/xen-cloud-platform-xcp-installing-ubuntu-13-04-raring-vm/)
(see section 4d)[/SIZE]
[SIZE=1][EDIT: Skip to the next post for a more sophisticated install script.]("http://ubuntuforums.org/showthread.php?t=2183067&p=12852613#post12852613")[/SIZE]
```
sudo xe template-list
```
Use the script below and alter the variables "release", "label", "host" and "domain" as necessary:
```
sudo vim Saucy.sh
```
```
#!/bin/bash
set -e
set -x

release='saucy'
label='SaucyTest'
host='SaucyTest'
domain='mydomain.is.best'
template=`xe template-list name-label="Ubuntu Lucid Lynx 10.04 (64-bit)" --minimal`
vm=`xe vm-install template=$template new-name-label=$label`
network=`xe network-list bridge=xenbr0 --minimal`
vif=`xe vif-create vm-uuid=$vm network-uuid=$network device=0`

xe vm-param-set uuid=$vm other-config:debian-release=$release
xe vm-param-set uuid=$vm other-config:install-repository=http://archive.ubuntu.com/ubuntu
xe vm-param-set uuid=$vm PV-args="auto-install/enable=true interface=auto netcfg/dhcp_timeout=600 hostname=$host"

set +x

echo ''
echo 'Press any key to start VM'
echo ''

read -n 1

xe vm-start uuid=$vm
xe vm-list uuid=$vm
xe console-list uuid=$vm

echo ''
echo 'Press any key for Console'
echo ''

read -n 1

xe console uuid=$vm
```
```
sudo chmod a+x Saucy.sh
sudo ./Saucy.sh
```

You may need to press a key again to bring the console up properly, but once it's up and running, just follow the usual procedure for installing Ubuntu Server.

For a WebUI VM install, download the latset XenOrchestra image from:
[SIZE=1][https://xen-orchestra.com/install-and-update-xo-from-git/](https://xen-orchestra.com/install-and-update-xo-from-git/)[/SIZE]

Follow the instructions therein.

That's it for now!

---

### Post by Rich.T. on 2013-11-20
After doing some more reading up and a lot experimentation, I have built upon my XCP domU installation script and made it interactive, with the ability to change the VM's settings as you install it.

[SIZE=1]Note: This script uses BC (Bash Calculator) for non-integer calculations, so make sure you:
```
sudo apt-get install BC
```[/SIZE]

It may be of some use to people, so here it is:

```
sudo vim ubuntuinstall.sh
```
```
#!/bin/bash
#set -e
#set -x
bold=`tput bold`
normal=`tput sgr0`
green=`tput setf 2`
red=`tput setf 4`

echo ""
echo ""
echo "${green}${bold}Enter settings for your virtual machine.${normal}"
echo "${green}Press return to accept defalt values.${normal}"
echo ""
echo ""

# Short release name (name of repository)
release="saucy"
read -e -i "$release" -p "${bold}Please enter short release name (name of repository): ${normal}" input
release="${input:-$release}"
echo "${green}Release=${bold}$release${normal}"

# Name label of VM for XCP
label='Ubuntu-Desktop-13.10'
read -e -i "$label" -p "${bold}Please enter name label of VM for XCP: ${normal}" input
label="${input:-$label}"
echo "${green}Label=${bold}$label${normal}"

# Hostname of VM
host='Ubuntu-Desktop-13.10-1'
read -e -i "$host" -p "${bold}Please enter host name of VM: ${normal}" input
host="${input:-$host}"
echo "${green}Hostname=${bold}$host${normal}"

#Domain name for VM
domain=""
read -e -i "$domain" -p "${bold}Please enter domain name of VM: ${normal}" input
domain="${input:-$domain}"
echo "${green}Domain=${bold}$domain${normal}"

# Template to use as basis for VM
temp="Ubuntu Lucid Lynx 10.04 (64-bit)"
read -e -i "$temp" -p "${bold}Please enter name of template to use as basis for VM: ${normal}" input
temp="${input:-$temp}"
echo "${green}Template=${bold}$temp${normal}"

template=`xe template-list name-label="$temp" --minimal`

# The "install" bit
echo ""
echo ""
echo "${red}${bold}INSTALLING $label...${normal}"
echo ""
echo ""
vm=`xe vm-install template=$template new-name-label=$label`
echo "${green}UUID for $label=${bold}$vm${normal}"
echo ""

# Network Bridge Name
bridge="xenbr0"
xe network-list
echo "${red}Please enter network bridge identifier."
echo "${red}(Could be something like ${bold}xenbr0 or breth0 or brp6p1 or brwlan0, etc.${normal}"
read -e -i "$bridge" -p "${bold}Network bridge name: ${normal}" input
bridge="${input:-$bridge}"
echo "${green}Bridge=${bold}$bridge${normal}"

# Network Type
network=`xe network-list bridge=$bridge --minimal`
echo "${green}Network uuid=${bold}$network${normal}"

# Virtual Network Interface
vif=`xe vif-create vm-uuid=$vm network-uuid=$network device=0`
echo "${green}Virtual network interface for ${bold}$label$:{normal}"
echo "${green}uuid=${bold}$vif${normal}"

# Install repository address:
repo="http://archive.ubuntu.com/ubuntu"
read -e -i "$repo" -p "${bold}Please enter install repository address: ${normal}" input
repo="${input:-$repo}"
echo "${green}Repository=${bold}$repo${normal}"

# Install VM
xe vm-param-set uuid=$vm other-config:debian-release=$release
xe vm-param-set uuid=$vm other-config:install-repository=$repo
xe vm-param-set uuid=$vm PV-args="auto-install/enable=true interface=auto netcfg/dhcp_timeout=600 hostname=$host domain=$domain"

# Display VM parameters 
xe vm-param-list uuid=$vm | more

echo "${red}${bold}Parameters for your installed virtual machine are listed above.${normal}${normal}"
echo "${red}You can alter settings for CPU, RAM and Storage by answering the following questions.${normal}"
echo "${red}Press return to accept defalt values.${normal}"
echo ""

# Set VM memory config
# N.B. Memory limits must satisfy: static_min &#8804; dynamic_min &#8804; dynamic_max &#8804; static_max

echo "${bold}Set VM memory configuration.${normal}"
echo "${red}N.B. Memory limits must satisfy: static_min &#8804; dynamic_min &#8804; dynamic_max &#8804; static_max${normal}"

smin=0.25
read -e -i "$smin" -p "${bold}Please enter minimum static memory in GB: ${normal}" input
smin="${input:-$smin}"
echo "Minimum static memory=${bold}$smin${normal} GB"
staticmin=$(echo "scale=0; $smin*1073741824/1" | bc)
echo "${green}(staticmin=${bold}$staticmin)${normal}"

dmin=0.25
read -e -i "$dmin" -p "${bold}Please enter minimum dynamic memory in GB: ${normal}" input
dmin="${input:-$dmin}"
echo "Minimum dynamic memory=${bold}$dmin${normal} GB"
dynamicmin=$(echo "scale=0; $dmin*1073741824/1" | bc)
echo "${green}(dynamicicmin=${bold}$dynamicmin)${normal}"

dmax=4
read -e -i "$dmax" -p "${bold}Please enter maximum dynamic memory in GB: ${normal}" input
dmax="${input:-$dmax}"
echo "Maximum dynamic memory=${bold}$dmax${normal} GB"
dynamicmax=$(echo "scale=0; $dmax*1073741824/1" | bc)
echo "${green}(dynamicmax=${bold}$dynamicmax)${normal}"

smax=4
read -e -i "$smax" -p "${bold}Please enter maximum static memory in GB: ${normal}" input
smax="${input:-$smax}"
echo "Maximum static memory=${bold}$smax${normal} GB"
staticmax=$(echo "scale=0; $smax*1073741824/1" | bc)
echo "${green}(staticmax=${bold}$staticmax)${normal}"

xe vm-memory-limits-set uuid=$vm static-min=$staticmin dynamic-min=$dynamicmin dynamic-max=$dynamicmax static-max=$staticmax

# Set vCPUs for VM
maxvpu="4"
read -e -i "$maxvpu" -p "${bold}Please enter maximum number of vCPUs: ${normal}" input
maxvpu="${input:-$maxvpu}"
echo "${green}Maximum vCPUs=${bold}$maxvpu${normal}"

startvpu="1"
read -e -i "$startvpu" -p "${bold}Please enter number of vCPUs on startup: ${normal}" input
startvpu="${input:-$startvpu}"
echo "${green}Maximum vCPUs=${bold}$startvpu${normal}"

xe vm-param-set VCPUs-max=$maxvpu uuid=$vm
xe vm-param-set VCPUs-at-startup=$startvpu uuid=$vm

# Get virtual disk image UUID
echo "${red}${bold}Current virtual HDD parameters:${normal}"
xe vbd-list vm-uuid=$vm
xe vbd-list vm-uuid=$vm | grep "vdi-uuid ( RO): "
vdiuuid0=$(xe vbd-list vm-uuid=$vm | grep "vdi-uuid ( RO): ")
vdiuuid=${vdiuuid0:25:37}
xe vdi-list uuid=$vdiuuid

# Resize the virtual disk image
dsize="20"
read -e -i "$dsize" -p "${bold}Please enter virtual disk size in GB: ${normal}" input
dsize="${input:-$dsize}"
echo "Virtual disk size=${bold}$dsize${normal}GB"
disksize=$(echo "scale=0; $dsize*1073741824/1" | bc)
echo "${green}(disksize=${bold}$disksize)${normal}"
xe vdi-resize uuid=$vdiuuid disk-size=$disksize
echo ""

# Display VM parameters 
xe vm-param-list uuid=$vm | more
xe vdi-list uuid=$vdiuuid

#set +x

echo ""
echo "${green}${bold}All Done!.${normal}"
echo ""
echo "${red}${bold}Press any key to start VM${normal}"
echo ""

read -n 1
echo "${red}Please stand by...${normal}"
xe vm-start uuid=$vm
xe vm-list uuid=$vm
xe console-list uuid=$vm

echo ""
echo "${green}${bold}Press any key for Console${normal}"
echo ""
echo "${red}N.B. You may need to press a key again to bring the console up properly, but once it's up and running, just follow the usual procedure for installing Ubuntu via the minimal netboot installer.${normal}"
echo ""

read -n 1
clear
xe console uuid=$vm

echo ""
echo "${green}${bold}Welcome back!${normal}"
echo ""
echo "${green}To return to the console, just enter 'sudo xe console uuid=$vm${normal}'"
echo ""

exit
```
```
sudo chmod a+x ubuntuinstall.sh
sudo ./ubuntuinstall.sh
```

---

### Post by jcoles on 2013-12-03
You show how to create LocalISORepository. But how do you populate it with ISO files? I just can't figure out how to get an ISO file that's in my file system copied into LocalISORepository.

---

### Post by Rich.T. on 2013-12-10
> **jcoles said:**
> You show how to create LocalISORepository. But how do you populate it with ISO files? I just can't figure out how to get an ISO file that's in my file system copied into LocalISORepository.

Sorry for the long delay. :( I only just thought to check this thread out.

I actually had that problem myself. I googled around for a solution and found:

Two possible ways of populating the ISO SR would be to either; (i) mount the repo with NFS to your local machine, or (ii) use the wget command to download your ISOs directly. (Alternatively, you could connect to a CIFS (Windows filesharing) repo on your local machine. The XenCenter/OpenXenManager interface is fully capable of doing this. (Though using xe sr-create with the correct arguments might be a more consistant and elegant method ;))

(i) [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
     [https://www.digitalocean.com/community/articles/how-to-set-up-an-nfs-mount-on-ubuntu-12-04](https://www.digitalocean.com/community/articles/how-to-set-up-an-nfs-mount-on-ubuntu-12-04)

As soon as I get the chance, I'll look through my notes and add this to the tutorial.

(ii) wget [http://releases.ubuntu.com/saucy/ubuntu-13.10-server-amd64.iso](http://releases.ubuntu.com/saucy/ubuntu-13.10-server-amd64.iso) ~/<repo-name>

I hope this helps, and has not come too late to be of use to you! :)

---

### Post by proteu on 2014-02-19
Hello, first of all thanks for the guide, i could get all installed and linux guest's working with it.

I need to install a Windows 7 guest but its allways giving me this error when it tries to boot the VM:

Feb 20, 2014 3:05:14 AM Error: Starting VM 'win7' - Internal error: Xenctrl.Error [ memory 11123588 KiB free; to be scrubbed 0 KiB; total 12285 MiB]: 1: Operation not permitted

---

### Post by Rich.T. on 2014-02-23
Hi, proteu.

Firstly, thanks for posting and letting me know that:

 A. This method works for someone other than me
and
 B. The guide was comprehensible enough for others to follow.

Secondly:
> **proteu said:**
> Hello, first of all thanks for the guide, i could get all installed and linux guest's working with it.

I need to install a Windows 7 guest but its always giving me this error when it tries to boot the VM:

Feb 20, 2014 3:05:14 AM Error: Starting VM 'win7' - Internal error: Xenctrl.Error [ memory 11123588 KiB free; to be scrubbed 0 KiB; total 12285 MiB]: 1: Operation not permitted

This is something that I want to get to work myself, but have so far have not been able to yet. :(

I am *very* familiar the Error that you report above (Internal error: Xenctrl.Error [ memory ?????? KiB free; to be scrubbed 0 KiB; total ????? MiB]: 1: Operation not permitted) and have encountered this many times over when trying to install an OS from an ISO image. This is why I chose the method described above and used the web/network installer.

If I remember correctly, I was able to do a basic Win7 test install using a XENServer OS (dom0) installation (as opposed to XCP/XAPI on Ubuntu).

At this point, I would probably recommend doing this yourself if you really need a Windows Guest OS (domU).

If I can get Windows installed and working as a guest OS (domU) on XCP/XAPI on Ubuntu, I will let you know ASAP. I will have some free time in about three weeks time, and intend to do some intense testing on this front.

Sorry that I can't be more helpful at the moment, but please let me know if you have any success on your own before then.

---

### Post by Hex3n on 2014-02-27
> **Rich.T. said:**
> Hi, proteu.

A. This method works for someone other than me
and
 

Thanks for the tutorial it worked great for me.  I've been wanting to study for my Citrix CCA and this will help out a lot.  I was unsuccessful with multiple CentOS installs and this has worked flawlessly for me so far.

---

### Post by Rich.T. on 2014-02-28
> **Hex3n said:**
> Thanks for the tutorial it worked great for me.  I've been wanting to study for my Citrix CCA and this will help out a lot.  I was unsuccessful with multiple CentOS installs and this has worked flawlessly for me so far.

You're welcome. :)

I actually find it a great shame that there is not more of a community around this stuff and that so much of the  documentation available (from which this tutorial is pieced together) is so woefully out of date and inadequate. I was very surprised that there was no up-to-date *sticky thread* on this site to help noobs like myself, for example.

I'm not *in* IT at all (just a hobbyist with limited free time), so it's a steep learning curve, believe me! I'm glad that it may be able to help someone acquire a professional qualification.

All I need to do now (!) is try to get this set-up working with a wider variety of guest OSs (domU) and get VGA and PCI pass-through working as well as the most important thing, which is to get the whole thing adequately firewalled, secured and properly routed by using Openvswitch (which Xenserver uses out-of-the-box) instead of bridged networking (apparently, it works if you get bridging up and running and then swapping to Openvswitch afterwards - see hyperlinks in original post).

I just wish that I had more time and more importantly *patience* to really focus on this thing and not get distracted by other projects and distractions.

Seeing as Ubuntu Server is primarily aimed at the professional user, I am very surprised that Xen is so poorly documented by Canonical as well as the community.

**Having said that: If anyone has any links to more useful and up-to-date information or documentation, which may be of use to anyone in getting XCP/XAPI up and running on the latest versions of Ubuntu, please post them here; I'm not going to be giving up on this stuff any time soon and need all the help I can get.**

My aim, really, is to set up a home server, on a solid Xen-based foundation, whereby I can base various file, email, messaging, media, web and cloud services, for use at home or away, while being able to easily set up virtual OSs to trial various decentralised, secure, open-source projects like those listed [here]("https://github.com/redecentralize/alternative-internet"). The flexibility of a bare-metal hyperviser will allow me to make as many mistakes as may occur, without breaking the things that actually do work and having to start everything from scratch all of the time. The ability of XEN to allow the rolling-back of mistakes will be priceless in this scenario.

---

### Post by hampus-n on 2014-03-11
> **Rich.T. said:**
> 

I am *very* familiar the Error that you report above (Internal error: Xenctrl.Error [ memory ?????? KiB free; to be scrubbed 0 KiB; total ????? MiB]: 1: Operation not permitted) and have encountered this many times over when trying to install an OS from an ISO image. This is why I chose the method described above and used the web/network installer.



I also have this issue. There is an bug reported on this @ [https://bugs.launchpad.net/xcp/+bug/1265214](https://bugs.launchpad.net/xcp/+bug/1265214)
Please show me how to work around it, if any of you have the competance.
BR Hampus Prahl

---

### Post by Rich.T. on 2014-03-15
> **hampus-n said:**
> I also have this issue. There is an bug reported on this @ [https://bugs.launchpad.net/xcp/+bug/1265214](https://bugs.launchpad.net/xcp/+bug/1265214)
Please show me how to work around it, if any of you have the competance.
BR Hampus Prahl


Has anyone tried asking questions regarding this on any mail-lists?

I will try this myself over the next few of days and see if I can ferret out any information.

No promises.

I added my voice to the bug report and have provided links below:

[Comment No. 5 On Bug Report.]("https://bugs.launchpad.net/xcp/+bug/1265214/comments/5")

[Bug Report]("https://bugs.launchpad.net/xcp/+bug/1265214")

> I have a thread at [http://ubuntuforums.org/showthread.php?t=2183067](http://ubuntuforums.org/showthread.php?t=2183067) which attempts to collate the disparate information available for setting up XCP/XAPI on Ubuntu,, and simplify and accelerate the install process.

 Hampus Prahl (hampus-n) (above) posted a link on my forum thread to this bug.

 This bug affects me also. It is incredibly frustrating, but it seems that it is not perceived as a problem by any of the Devs concerned, because XenServer works fine with Windows (and other) domU guests.

 I'm sure that it would be an educational experience for me to learn my way around a whole new (for me)  open source OS (ie. CentOS/Red Hat/XenServer), but I have very little time available to me to relearn all the basics and switch host OS. I'd much prefer to stick with Ubuntu to this end, as my personal collection of bookmarks/notes/scripts/experiences are all centred around this OS.

 As time allows, I will try to chase down any information around this that I can and report back.

I will repost this comment to the aforementioned forum thread.

Rich.

---

### Post by hampus-n on 2014-03-15
Does it work if rollback to an older version of Ubuntu like 12.04? And just be clear I get this issue with 13.10 as dom0 with a HVM Windows domU..

---

### Post by Rich.T. on 2014-03-15
> **hampus-n said:**
> Does it work if rollback to an older version of Ubuntu like 12.04? And just be clear I get this issue with 13.10 as dom0 with a HVM Windows domU.

I'm sorry, I have only tried this on 13.04 onwards and as far as I can recall, I have only been able to get Win7 (or any full ISOs) to work on Citrix's XenServer.

What has been your experience with this?

---

### Post by Rich.T. on 2014-05-28
[SIZE=4][COLOR="#FF0000"]Broken: Xen Cloud Platform (XCP) on Ubuntu Server 14.04 LTS (Trusty Tahr)[/COLOR][/SIZE]

Update 28th May 2014:

I was today in the process of installing a new XCP visualisation server and found that the xcp-xapi package is missing from the repo.
A brief look at [xcp-xapi 1.3.2-15ubuntu2 (amd64 binary) in ubuntu trusty]("https://launchpad.net/ubuntu/trusty/amd64/xcp-xapi/1.3.2-15ubuntu2") and [“xen-api” 1.3.2-15ubuntu2 source package in The Trusty Tahr]("https://launchpad.net/ubuntu/trusty/+source/xen-api/1.3.2-15ubuntu2") shows: > Status: Deleted and > 1.3.2-15ubuntu2 DELETED: Trusty pocket Release in component universe and section admin. Removal requested on 2013-12-24. Deleted on 2013-12-24 by Matthias Klose. ocaml transition: doesn’t build

I'm guessing that this is because XCP on Debian/Ubuntu and all platforms other than CentOS is no longer supported by Citrix, XCP has deprecated and major dependencies are now broken, but I must say that this is a terrible situation. As far as I'm aware, OpenStack and some others use XCP on Ubuntu for their infrastructure and this would appear to be a cynical method of getting them to switch to XenServer/CentOS. Personally I'd like to stick with Ubuntu and also don't like the Idea of switching to an inferior Xen Toolstack. Perhaps I aught to start from scratch and learn to use KVM?

If anyone knows anything about this situation and if it is likely to be remedied please let me know, I'd really appreciate it!

I will endeavour to get xcp-xapi installed by other means and report back as soon as I am able. Don't hold your breath though...

---

### Post by Keith_Walker on 2014-06-30
Seen any news on this? I've been searching and have yet to find anything.

---

### Post by Rich.T. on 2014-08-19
Sorry for the long delay, but I have found this thread in the mailing list, which seems to have recently risen to the top, on google: [https://lists.ubuntu.com/archives/ubuntu-server/2014-January/006800.html]("https://lists.ubuntu.com/archives/ubuntu-server/2014-January/006800.html"), [https://lists.ubuntu.com/archives/ubuntu-server/2014-January/006803.html]("https://lists.ubuntu.com/archives/ubuntu-server/2014-January/006803.html");

I will quote in full:

> Thu Jan 23 14:23:12 UTC 2014

This (and related) package has a bit of an upstream maintenance issue. All those
packages together (blktap, xen-api, xen-api-libs, openxenserver?) make up the
open source part of Citrix Xenserver. This was introduced in Precise LTS and
(please correct me if I am wrong) was to some degree used to integrate Xen into
OpenStack.

However there did not seem to be a lot of upstream work going into keeping it in
a working state (packages are in universe). At least the xen-api-libs source
package was FTBS in Saucy. And it is again (for a different reason) FTBS in Trusty.

Debian has removed xen-api/xen-api-libs from testing and were thinking about
removing it completely from Sid as nobody cared about it. Citrix is working on
some overhaul but have not come forward with something usable, yet.
When being asked they came up asking whether the build failure could get fixed
and then the current code be used for Trusty.

While this probably could be done (though the current ocaml type related problem
I have my problems in understanding, but I am no ocaml developer), I would have
my doubts about its quality (there unlikely will be much effort put into it). On
the other hand, it is universe.

But at least with respect to OpenStack we should not rely on xcp to integrate
Xen hosts. At least not as the only option. Currently I find much less xcp
package in Trusty but this very likely is because of the build failure of
xen-api-libs. Is there work being done to check whether libvirt could be used in
nova instead (maybe already done).

So basically throwing the general question into the air what should be done with
the xen-api* packages: removed (maybe bad as that could break upgrades from P),
make them compile and decide whether to replace nova plugins by libvirt use or
keep them and add libvirt use or ...?

-Stefan

> On Thu, Jan 23, 2014 at 03:23:12PM +0100, Stefan Bader wrote:
> Debian has removed xen-api/xen-api-libs from testing and were thinking about
> removing it completely from Sid as nobody cared about it. Citrix is working on
> some overhaul but have not come forward with something usable, yet.
> When being asked they came up asking whether the build failure could get fixed
> and then the current code be used for Trusty.

Unless somebody steps up to maintain xen-api, I don't think it makes
sense to continue keeping these packages in Ubuntu, given that Debian
have removed them from testing and the existing packages broken (and, it
seems, thus stuck in trusty-proposed). So we should remove them from
trusty-proposed.

If the packages get reinstated in Debian testing before our Debian
Import Freeze, then we can have them in Trusty.

AIUI, our OpenStack packaging uses libvirt and libxen (-4.3?), so won't
be affected. If I'm wrong here, please could somebody point this out
now?

[...]

> So basically throwing the general question into the air what should be
> done with the xen-api* packages: removed (maybe bad as that could
> break upgrades from P), make them compile and decide whether to
> replace nova plugins by libvirt use or keep them and add libvirt use
> or ...?

The right time to drop support for something is in a new release. If
xen-api doesn't ship in Trusty, then I don't think there's an issue with
there not being an upgrade path. As a distribution, we can only pass on
to users what is available upstream. Perhaps we should just add a
release note to say that xen-api is no longer available.

Robie

---

### Post by Rich.T. on 2014-08-19
The reason for my quoting this now, is that I just did a new google search and found these results, based on the fact that a recent thread in the *xen-api.lists.xen.org* mailing list  caught my attention recently:

[http://www.gossamer-threads.com/lists/xen/api/343358]("http://www.gossamer-threads.com/lists/xen/api/343358")

(FYI: I have subscribed to the digests for this list; you may want to do the same):

[http://lists.xen.org/cgi-bin/mailman/listinfo/xen-api]("http://lists.xen.org/cgi-bin/mailman/listinfo/xen-api")

I *really* hope that this helps and I hope that once the development push at XenServer has concluded and the next big XenServer version is *out there*, XCP will be fixed on other platforms (including Ubuntu).

Rich.

P.S. [The above thread]("http://www.gossamer-threads.com/lists/xen/api/343358") suggests compiling XCP/XAPI from source and provides the relevant information (degree of success: unknown at this point). If anyone succeeds, please let us know! ;)

P.P.S. I would suggest that it is well worth checking out the [Xen Cloud Platform/Xenserver page on Google+]("https://plus.google.com/communities/113310194099597322381"), as you are likely to get some kind of response to any well thought-out question.

---

