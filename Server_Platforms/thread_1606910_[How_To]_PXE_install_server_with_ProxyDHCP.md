---
title: "[How To] PXE install server with ProxyDHCP"
date: 2010-10-27
forum: Server Platforms
---

### Post by vikjon0 on 2010-10-27
This is a draft write up. There could possibly be some errors in paths.

**EDIT:I made a test version of a live PXE CD.**
[http://ubuntuforums.org/showpost.php?p=10042683&postcount=16](http://ubuntuforums.org/showpost.php?p=10042683&postcount=16)
[http://sourceforge.net/projects/qfpxeinstaller](http://sourceforge.net/projects/qfpxeinstaller)

The goal of this is excersise is a pxe install & utility server targeted to home users.
This is particular interesting since many device sold now does not have an optical drive.
We want to use a proxyDHcp since most people are using dhcp on a home router without pxe support.

I do not include a sub structure 32bit/64bit, in this example all is 32bit.

I have documented this since it was quite a struggle to put it together. Not a lot of correct information out there.

I think a consilidated wiki page should be created.

My own contribution is making it work and collecting the info.
I have copied much of it from:

[https://help.ubuntu.com/community/PXEInstallMultiDistro](https://help.ubuntu.com/community/PXEInstallMultiDistro)
[https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)
[https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP](https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP)
[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

I have tested this on Karmic so far.

-------------------------------
Install Ubuntu (karmic server)
---------------------------------

sudo apt-get update
sudo apt-get upgrade

sudo apt-get install ssh

(
I have also installed gnome on the test server.
sudo apt-get install xorg gnome-core
)

==================================================
Install dnsmasq
==================================================

[https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP](https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP)
[http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html](http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html)

sudo apt-get install dnsmasq

sudo nano  /etc/dnsmasq.d/pxe.conf
add (this sample will connect to the local tftp server):

```
####################################################################
# Copied from https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP
# Modified by vikjon0 2010-10-22 for PXE install server
#####################################################################
# Sample configuration for dnsmasq to function as a proxyDHCP server,
# enabling PXE clients to boot when an external, unmodifiable DHCP
# server is present.
# The main dnsmasq configuration is in /etc/dnsmasq.conf;
# the contents of this script are added to the main configuration.
# You may modify the file to suit your needs.

# Don't function as a DNS server:
port=0

# Log lots of extra information about DHCP transactions.
log-dhcp

# Dnsmasq can also function as a TFTP server. You may uninstall
# tftpd-hpa if you like, and uncomment the next line:
#enable-tftp

# Set the root directory for files available via FTP.
tftp-root=/var/lib/tftpboot

# The boot filename.
dhcp-boot=/var/lib/tftpboot/pxelinux.0

# rootpath option, for NFS
dhcp-option=17,/var/www/PXE

# kill multicast
dhcp-option=vendor:PXEClient,6,2b

# Disable re-use of the DHCP servername and filename fields as extra
# option space. That's to avoid confusing some old or broken DHCP clients.
dhcp-no-override

# PXE menu
pxe-prompt="Press F8 for boot menu", 3

# The known types are x86PC, PC98, IA64_EFI, Alpha, Arc_x86,
# Intel_Lean_Client, IA32_EFI, BC_EFI, Xscale_EFI and X86-64_EFI
pxe-service=X86PC, "Boot from network", pxelinux

# A boot service type of 0 is special, and will abort the
# net boot procedure and continue booting from local media.
pxe-service=X86PC, "Boot from local hard disk", 0

# If an integer boot service type, rather than a basename is given, then the
# PXE client will search for a suitable boot service for that type on the
# network. This search may be done by multicast or broadcast, or direct to a
# server if its IP address is provided.
#pxe-service=x86PC, "Install windows from RIS server", 1

# This range(s) is for the public interface, where dnsmasq functions
# as a proxy DHCP server providing boot information but no IP leases.
# Any ip in the subnet will do, so you may just put your server NIC ip here.
dhcp-range=192.168.0.130,proxy

# This range(s) is for the private network on 2-NIC servers,
# where dnsmasq functions as a normal DHCP server, providing IP leases.
#dhcp-range=192.168.0.20,192.168.0.250,8h

# For static client IPs, and only for the private subnets,
# you may put entries like this:
#dhcp-host=00:20:e0:3b:13:af,10.160.31.111,client111,infinite
```

==================================================
Install tftpboot
==================================================
[https://help.ubuntu.com/community/PXEInstallMultiDistro](https://help.ubuntu.com/community/PXEInstallMultiDistro)

sudo apt-get -y install tftpd-hpa
sudo /etc/init.d/openbsd-inetd stop
sudo update-rc.d -f openbsd-inetd remove
sudo sed -i s/no/yes/ /etc/default/tftpd-hpa
sudo /etc/init.d/tftpd-hpa start

Ubuntu installs the openbsd-inetd pakcage when the tfpd-hpa package is installed. In our example we will simply run TFTP as a daemon and will always be listening for connections. 
In the above code snippet: 
&#8226;tftpd-hpa was intsalled 
&#8226;The openbsd-inetd daemon was stopped 
&#8226;openbsd-inetd was removed from the startup scripts 
&#8226;/etc/defaul/tftpd-hpa was modified to allow tftpd-hpa to run as a daemon process 
&#8226;tftpd-hpa was started 


Verify the TFTP server is listening for connections: 
netstat -uap | grep tftp

Sample output:
Proto Recv-Q Send-Q Local Address           Foreign Address         State
udp        0      0 *:tftp                  *:* 


==================================================
install SYSLINUX
==================================================
[https://help.ubuntu.com/community/PXEInstallMultiDistro](https://help.ubuntu.com/community/PXEInstallMultiDistro)

sudo apt-get -y install syslinux

Copy the PXELINUX bootstrap to the root of our TFTP server. 

sudo cp /usr/lib/syslinux/pxelinux.0 /var/lib/tftpboot


Create the PXELINUX default configuration file. 
(dir missing in guide)
sudo mkdir /var/lib/tftpboot/pxelinux.cfg/
)

sudo touch /var/lib/tftpboot/pxelinux.cfg/default 


/var/lib/tftpboot is the boot directory.

==================================================
install apache
==================================================
The client can access files on the server in a number of ways.
e.g. tftp, http and nfs.

What is available depends on the boot files, mostly initrd I think. It needs to have the drivers etc.
http seems to be the easiest and most common what to access the installation CD and other files.

We will install a web server and later put the installation CDs here.

sudo apt-get -y install apache2


sudo mkdir /var/www/pxe
This will be the location of the installation media,
(would be nice to move pxe outside www since it will also be accessed by nfs)


==================================================
install NFS
==================================================
We are also going to use nfs, not for install but for the live CDs.

sudo apt-get -y install nfs-kernel-server 

sudo nano /etc/exports
add:
```
/var/www/pxe                 192.168.0.0/24(ro,async,no_root_squash,no_subtree_check) 
```

Export our file system or restart the NFS server. 

sudo exportfs -a

or

sudo /etc/init.d/nfs-kernel-server restart 



==================================
setting up main menu
==================================

[https://help.ubuntu.com/community/PXEInstallMultiDistro?action=AttachFile&do=view&target=logo.png](https://help.ubuntu.com/community/PXEInstallMultiDistro?action=AttachFile&do=view&target=logo.png)

sudo cp /usr/lib/syslinux/vesamenu.c32 /var/lib/tftpboot/
sudo cp /location/of/image/logo.png /var/lib/tftpboot/pxelinux.cfg/ 

sudo nano /var/lib/tftpboot/pxelinux.cfg/default
add:
```
DEFAULT vesamenu.c32 
TIMEOUT 600
ONTIMEOUT BootLocal
PROMPT 0
MENU INCLUDE pxelinux.cfg/pxe.conf
NOESCAPE 1
LABEL BootLocal
        localboot 0
        TEXT HELP
        Boot to local hard disk
        ENDTEXT
MENU BEGIN Ubuntu
MENU TITLE Ubuntu 
        LABEL Previous
        MENU LABEL Previous Menu
        TEXT HELP
        Return to previous menu
        ENDTEXT
        MENU EXIT
        MENU SEPARATOR
        MENU INCLUDE Ubuntu/Ubuntu.menu
MENU END

MENU BEGIN Tools and Utilities
MENU TITLE Tools and Utilities
        LABEL Previous
        MENU LABEL Previous Menu
        TEXT HELP
        Return to previous menu
        ENDTEXT
        MENU EXIT
        MENU SEPARATOR
        MENU INCLUDE utilities/utilities.menu
MENU END
```

sudo nano /var/lib/tftpboot/pxelinux.cfg/pxe.conf
add:
```

MENU TITLE  PXE Server 
MENU BACKGROUND pxelinux.cfg/logo.png
NOESCAPE 1
ALLOWOPTIONS 1
PROMPT 0
menu width 80
menu rows 14
MENU TABMSGROW 24
MENU MARGIN 10
menu color border               30;44      #ffffffff #00000000 std
```


================================
Example 1 Booting LiveCD
=================================
Copy kernal & initrd

sudo mkdir -p /var/lib/tftpboot/Ubuntu/lucidLiveCD


(mount cd or image first)
sudo cp /media/cdrom0/casper/vmlinuz /var/lib/tftpboot/Ubuntu/lucidLiveCD
sudo cp /media/cdrom0/casper/initrd.lz /var/lib/tftpboot/Ubuntu/lucidLiveCD


copy CD to installation directory
sudo mkdir -p /var/www/pxe


We need a complete copy including hidden files (folder .disk) otherwise it does not work.
Not sure what is the best way in linux but this works.
Assuming target directory does not exists!

sudo cp -ra /media/cdrom0 /var/www/pxe/lucidLiveCD


==================================================
setting up Ubuntu menu
==================================================
sudo nano /var/lib/tftpboot/Ubuntu/Ubuntu.menu

```
LABEL 1
        MENU LABEL Ubuntu 10.04 LTS (32-bit) Live
        KERNEL Ubuntu/lucidLiveCD/vmlinuz
        APPEND boot=casper netboot=nfs nfsroot=192.168.0.130:/var/www/pxe/lucidLiveCD initrd=Ubuntu/lucidLiveCD/initrd.lz
        TEXT HELP
        Boot the Ubuntu 10.04 32-bit in Live Mode
        ENDTEXT
```
It should now be possible to boot the live cd over pxe!



================================
Example 2 Install from Alt CD
=================================
Copy Netboot kernal & initrd


sudo mkdir -p /var/lib/tftpboot/Ubuntu/lucidAltCD

(mount cd or image first)
sudo cp /media/cdrom0/install/netboot/ubuntu-installer/i386/linux /var/lib/tftpboot/Ubuntu/lucidAltCD
sudo cp /media/cdrom0/install/netboot/ubuntu-installer/i386/initrd.gz /var/lib/tftpboot/Ubuntu/lucidAltCD


copy CD to installation directory
sudo mkdir -p /var/www/pxe/

*dest may not exist
sudo cp -r /media/cdrom0 /var/www/pxe/lucidAltCD

This will start the installation and allow you to select mirror. Including you local server,

sudo nano /var/lib/tftpboot/Ubuntu/Ubuntu.menu

```
label 2
	MENU LABEL Lucid Alt install (remote mirrors)
        KERNEL Ubuntu/lucidAltCD/linux
	APPEND initrd=Ubuntu/lucidAltCD/initrd.gz
        TEXT HELP
        Boot the alt CD installer on remote mirrors
        ENDTEXT
```

======================================================
Example 3 install from CD on server with kickstart
=======================================================
I am not going to use this is, since it does not seem to work in combination with expert mode (priority=low)

[https://help.ubuntu.com/community/PXEInstallServer:](https://help.ubuntu.com/community/PXEInstallServer:)
There is a package called system-config-kickstart which is a GUI frontend to creating kickstart files. The kickstart file tells the installer where to get its packages from, what to install and a number of other useful settings. See KickstartCompatibility for more info. 

This is for generating a kickstart file.
we just need to point out the installation CD

sudo nano /var/www/pxe/lucidalt.cfg

```
install
url --url http://192.168.0.130/pxe/lucidAltCD
```

sudo nano /var/lib/tftpboot/Ubuntu/Ubuntu.menu
```
label 3
	MENU LABEL Lucid Alt install with kickstart, all local
        KERNEL Ubuntu/lucidAltCD/linux
	APPEND ks=http://192.168.0.130/pxe/lucidalt.cfg initrd=Ubuntu/lucidAltCD/initrd.gz
        TEXT HELP
        Boot the alt CD installer on local http
        ENDTEXT
```


========================================
Example 4&5 preseed
========================================

EDIT: I get an error about corrupt package when I run the installer against the CD.
I need to do some more tests. It was working before...
EDIT2: I think it is not a good solution anyway.
It is better to use a apt cache to minimize the network traffic.
As mentioned in this post
[http://www.peterlyons.com/problog/2010/07/](http://www.peterlyons.com/problog/2010/07/)

sudo nano /var/lib/tftpboot/Ubuntu/lucidAltCD/test.cli

There is 3 pressed files on the alt CD (/preseed/).

If you e.g. want to install a minimal CLI system you point to cli.seed.

If we want to install a cli system but automatically point to the cd on the server:
cp cli.seed => test.seed


sudo nano /var/lib/tftpboot/Ubuntu/lucidAltCD/test.seed
add:
```
### Mirror settings
# If you select ftp, the mirror/country string does not need to be set.
d-i mirror/protocol string http
d-i mirror/country string enter information manually
d-i mirror/http/hostname string 192.168.0.130
d-i mirror/http/directory string /pxe/lucidAltCD
d-i mirror/http/proxy string
```


sudo nano /var/lib/tftpboot/Ubuntu/Ubuntu.menu
```
label 4
	MENU LABEL Lucid Alt CLI 
        KERNEL Ubuntu/lucidAltCD/linux
	APPEND  preseed/url=http://192.168.0.130/pxe/lucidAltCD/preseed/test.seed initrd=Ubuntu/lucidAltCD/initrd.gz
        TEXT HELP
        Boot the alt CD installer cli preseed
        ENDTEXT

label 5
	MENU LABEL Lucid Alt CLI expert mode
        KERNEL Ubuntu/lucidAltCD/linux
	APPEND  preseed/url=http://192.168.0.130/pxe/lucidAltCD/preseed/test.seed priority=low initrd=Ubuntu/lucidAltCD/initrd.gz
        TEXT HELP
        Boot the alt CD installer cli expert mode
        ENDTEXT
```
If we want to install a server, there a server seed on the server cd. Not sure if it can be used with the local alt cd.
If not it should work with a network mirror or of course the server cd.

========================================
Example 6 install with minimal CD
===========================================

sudo mkdir -p /var/lib/tftpboot/Ubuntu/lucidMiniCD

sudo cp /media/cdrom0/linux /var/lib/tftpboot/Ubuntu/lucidMiniCD
sudo cp /media/cdrom0/initrd.gz /var/lib/tftpboot/Ubuntu/lucidMiniCD


copy CD to installation directory
sudo mkdir -p /var/www/pxe/
*dest may not exist
sudo cp -r /media/cdrom0 /var/www/pxe/lucidMiniCD


sudo nano /var/lib/tftpboot/Ubuntu/Ubuntu.menu
```
label 6
	MENU LABEL Install Lucid mini expert
	kernel Ubuntu/lucidMiniCD/linux
        append priority=low vga=normal initrd=Ubuntu/lucidMiniCD/initrd.gz
        TEXT HELP
        Boot the mini CD
        ENDTEXT
```



=========================================
clonezilla
=========================================

I had some problems with the ubuntu version, not sure if I made a misstake.
This is tested with the debian stable.

The parameters appears to change between versions. The idea seem to be to check the syslinux/syslinux.cfg on the cd.

Copy kernal & initrd

sudo mkdir -p /var/lib/tftpboot/utilities/clonezilla

sudo cp /media/cdrom0/live/vmlinuz1 /var/lib/tftpboot/utilities/clonezilla
sudo cp /media/cdrom0/live/initrd1.img /var/lib/tftpboot/utilities/clonezilla

copy CD to installation directory

sudo cp -r /media/cdrom0 /var/www/pxe/clonezilla

sudo nano /var/lib/tftpboot/utilities/utilities.menu

```
label 1
	MENU LABEL clonezilla 
        KERNEL utilities/clonezilla/vmlinuz1
	APPEND initrd=utilities/clonezilla/initrd1.img boot=live union=aufs netboot=nfslive-config live-config  noswap nolocales edd=on nomodeset noprompt ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_keymap="" ocs_live_batch="no" ocs_lang="" vga=788 nosplash nfsroot=192.168.0.130:/var/www/pxe/clonezilla
        TEXT HELP
        Boot the Clonezilla CD
        ENDTEXT
```

It is possible to skip NFS and load the image with http instead:
The same work for gparted.

```
label 3
	MENU LABEL clonezilla - http
        KERNEL utilities/clonezilla/vmlinuz1
	APPEND initrd=utilities/clonezilla/initrd1.img boot=live union=aufs live-config  noswap nolocales edd=on nomodeset noprompt ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_keymap="" ocs_live_batch="no" ocs_lang=""  vga=785  nosplash fetch=http://192.168.0.130/pxe/clonezilla/live/filesystem.squashfs
        TEXT HELP
        Boot the Clonezilla CD
        ENDTEXT
```

===================================
gparted
=====================================

Copy kernal & initrd

sudo mkdir -p /var/lib/tftpboot/utilities/gparted

sudo cp /media/cdrom0/live/vmlinuz1 /var/lib/tftpboot/utilities/gparted
sudo cp /media/cdrom0/live/initrd1.img /var/lib/tftpboot/utilities/gparted

copy CD to installation directory

sudo cp -r /media/cdrom0 /var/www/pxe/gparted

Same thing as for clonezilla when it comes to parameters.

sudo nano /var/lib/tftpboot/utilities/utilities.menu

```
label 2
	MENU LABEL gparted
        KERNEL utilities/gparted/vmlinuz1
	APPEND initrd=utilities/gparted/initrd1.img boot=live config i915.modeset=0 xforcevesa radeon.modeset=0 noswap nomodeset noprompt vga=788 nosplash vga=788 netboot=nfs nfsroot=192.168.0.130:/var/www/pxe/gparted
        TEXT HELP
        Boot the gparted CD
        ENDTEXT
```

It is possible to use http instead of nfs, check clonzilla example above.

---

### Post by vikjon0 on 2010-10-27
I had some problem making dnsmasq redirect to a tftp on a remote server.
With the sample from the Ubuntu forum it is not enough to change the dhcp-boot.

I think at least part of the problem is the multicast kill.
It has to be removed.
#dhcp-option=vendor:PXEClient,6,2b

This is working:

```
####################################################################
# Copied from https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP
# Modified by vikjon0 2010-10-22 for PXE install server
# This version for remote tftp
#####################################################################
# Sample configuration for dnsmasq to function as a proxyDHCP server,
# enabling PXE clients to boot when an external, unmodifiable DHCP
# server is present.
# The main dnsmasq configuration is in /etc/dnsmasq.conf;
# the contents of this script are added to the main configuration.
# You may modify the file to suit your needs.

# Don't function as a DNS server:
port=0

# Log lots of extra information about DHCP transactions.
#log-dhcp

# Dnsmasq can also function as a TFTP server. You may uninstall
# tftpd-hpa if you like, and uncomment the next line:
#enable-tftp

# Set the root directory for files available via FTP.
# tftp-root=/var/lib/tftpboot



# An example of dhcp-boot with an external TFTP server: the name and IP
# address of the server are given after the filename.
# Can fail with old PXE ROMS. Overridden by --pxe-service.
# Enable for remore tftp server
#dhcp-boot=/var/lib/ftpdboot/pxelinux.0,boothost,192.168.0.3
dhcp-boot=pxelinux.0,boothost,192.168.0.130

# The boot filenam When tftp server is on the same server
#dhcp-boot=/var/lib/tftpboot/pxelinux.0


# rootpath option, for NFS
#dhcp-option=17,/var/www/PXE

# kill multicast
#dhcp-option=vendor:PXEClient,6,2b

# Disable re-use of the DHCP servername and filename fields as extra
# option space. That's to avoid confusing some old or broken DHCP clients.
dhcp-no-override

# PXE menu
# Chnage delay to 0 for quick boot of next menu
#pxe-prompt="Press F8 for boot menu", 3
pxe-prompt="Press F8 for boot menu", 0

# The known types are x86PC, PC98, IA64_EFI, Alpha, Arc_x86,
# Intel_Lean_Client, IA32_EFI, BC_EFI, Xscale_EFI and X86-64_EFI
#pxe-service=X86PC, "Boot from network", pxelinux

# A boot service type of 0 is special, and will abort the
# net boot procedure and continue booting from local media.
#pxe-service=X86PC, "Boot from local hard disk", 0

# If an integer boot service type, rather than a basename is given, then the
# PXE client will search for a suitable boot service for that type on the
# network. This search may be done by multicast or broadcast, or direct to a
# server if its IP address is provided.
#pxe-service=x86PC, "Install windows from RIS server", 1

# This range(s) is for the public interface, where dnsmasq functions
# as a proxy DHCP server providing boot information but no IP leases.
# Any ip in the subnet will do, so you may just put your server NIC ip here.
dhcp-range=192.168.0.0,proxy

# This range(s) is for the private network on 2-NIC servers,
# where dnsmasq functions as a normal DHCP server, providing IP leases.
#dhcp-range=192.168.0.20,192.168.0.250,8h

# For static client IPs, and only for the private subnets,
# you may put entries like this:
#dhcp-host=00:20:e0:3b:13:af,10.160.31.111,client111,infinite
```

---

### Post by vikjon0 on 2010-10-27
scrip to config dhcp for current subnet automatically
(most of the code stolen from the wiki)

```

#!/bin/sh

set -e
trap "cleanup" 0 1 2 3 9 11 13 15

printbold() {
    if [ -z "$printbold_first_time" ]; then
        printbold_first_time=true
        bold_face=$(tput bold 2>/dev/null) || true
        normal_face=$(tput sgr0 2>/dev/null) || true
    fi
    echo "${bold_face}$@${normal_face}"
}    

die() {
    printbold "Error: $@" >&2
    exit 1
}

cleanup() {
    trap - 0 1 2 3 9 11 13 15  # Stop trapping
    echo  # Skip the ^C line
}

create_dnsmasq_conf() {
    def_iface=$(route -n | sed -n '/^0.0.0.0/s/.* //p')
    if [ -z "$SERVER_IP" ]; then
        SERVER_IP=$(ip -oneline -family inet addr show dev "$def_iface" | sed -n '/inet 127\./! {s,.* \(.*\)/.*,\1,p;q}')
    fi
    if [ -z "$SERVER_IP" ]; then
        die "Could not determine this PC's IP address. Please provide it manually, by running
  sudo SERVER_IP=1.2.3.4 $0"
    fi


    cat >"/etc/dnsmasq.d/pxe.conf" <<EOF
# Don't function as a DNS server:
port=0

# Log lots of extra information about DHCP transactions.
log-dhcp

# Set the root directory for files available via FTP.
tftp-root=/var/lib/tftpboot

# The boot filename.
dhcp-boot=/var/lib/tftpboot/pxelinux.0

# kill multicast
dhcp-option=vendor:PXEClient,6,2b

# Disable re-use of the DHCP servername and filename fields as extra
# option space. That's to avoid confusing some old or broken DHCP clients.
dhcp-no-override

# PXE menu
pxe-prompt="Press F8 for boot menu", 0

# The known types are x86PC, PC98, IA64_EFI, Alpha, Arc_x86,
# Intel_Lean_Client, IA32_EFI, BC_EFI, Xscale_EFI and X86-64_EFI
# Boot from Network
pxe-service=X86PC, ".", pxelinux

# A boot service type of 0 is special, and will abort the
# net boot procedure and continue booting from local media.
pxe-service=X86PC, "Boot from local hard disk", 0

# This range(s) is for the public interface, where dnsmasq functions
# as a proxy DHCP server providing boot information but no IP leases.
# Any ip in the subnet will do, so you may just put your server NIC ip here.
dhcp-range=$SERVER_IP,proxy
EOF
}

service dnsmasq stop
echo ' * Delete old config'
rm -rf /etc/dnsmasq.d/*.conf
create_dnsmasq_conf
echo ' * Creating new config'
service dnsmasq start
```

---

### Post by vikjon0 on 2010-10-27
...

---

### Post by sjhupp on 2010-10-27
I've tried to set this up on my headless 10.04 server, in order to install Xubuntu to an old laptop, but I have problems.
Have got DD-WRT on the router giving DHCP, so added the DNSmasq bits there, and I get the pretty menu, can navigate to either Xubuntu or Dos 6.22 to install, but when I select either, I just get it 'Loading' for a bit, then "Boot failed: press a key to retry, or wait for reset..." error.
Which config file could be wrong here?
What have I screwed up?? :confused:

(I did use the first PXEInstallMulti... link, and then had to chmod -R 777 the tftp dir to get it to boot to the menu)

---

### Post by vikjon0 on 2010-10-27
Are you talking about menu in dnsmasq or are you past that to tftpboot? I don't use the dnsmasq menu, I try to skip past it as much as possible.

I have noticed that if you make any small error in dnsmasq conf you gets stuck in that menu.

If you are already in the next menu the only problem I have seen is when the kernal options or paths are incorrect. 
If you are already booting the installer this is your problem.

You could try with some stuff from my post and see if it works.
The mini.cd variation is quickly setup.

---

### Post by sjhupp on 2010-10-27
No DNSmasq issues - through to the tftp boot menu, and can navigate through it fine. Seems to be the last step - actually launching an install from the files on the server.
Just setup the Dos6.22 one to see if it was an Xubuntu issue, but same prob (Q> why does the Dos6 go in /home/tftp dir, different to others?)
Will try some more configs tomorrow (past midnight now), and maybe one more dist like you suggest.  I seem so close!! :(
Thanks.

---

### Post by vikjon0 on 2010-10-27
> (Q> why does the Dos6 go in /home/tftp dir, different to others?)

Because some guides assume you will have only one boot alternative. I think you need to verify the menu and all paths.

Also, why not try lucid ubuntu that we know for sure works without problems.

---

### Post by the_original_billq on 2010-10-27
vikjon0,

You need to get this into a wiki page.  I'm going to be doing the same setup here for staging laptops, and will provide feedback to the process.
This is great work, and extremely timely.

-Bill

---

### Post by vikjon0 on 2010-10-27
> You need to get this into a wiki page.

Yes, I agree. Perhaps it needs some cleaning up first.

My concern is that there is already a number of wiki pages on this topic, some of them not up to date.

Maybe the multi distro wiki page should be updated and the proxydhcp stuff put in a sub page? The best solution would be to create a new master PXE page and create a structure below.

Is there any moderators dealing with the wiki structure? Is there an owner of the page that can be contacted?

---

### Post by sjhupp on 2010-10-28
Ok, tried with Ubuntu 10.04 and still the same error. Grr!!

Here's a long dump of what I assume is relevant - anyone able to spot the issue please? Assume something really simple...

So, following:
[https://help.ubuntu.com/community/PXEInstallMultiDistro#Ubuntu](https://help.ubuntu.com/community/PXEInstallMultiDistro#Ubuntu)
I fixed up my DHCP server (DD-WRT modem 192.168.1.1) as per:
[http://www.dd-wrt.com/wiki/index.php/PXE](http://www.dd-wrt.com/wiki/index.php/PXE)

I left my server (192.168.1.250) name blank, as the lookup doesn’t always work on my LAN (prob messed around with NICs too often).  I chose /raid5/PXEboot/ to hold my cd files and menus etc.

Anyway, I must get DHCP fine, as I get the multiboot menu as per the PXE link above, and can navigate through it.  But when I try to select something to actually install, I always get the “Loading” shown for a while, then the same error “Boot failed: press a key to retry, or wait for reset...” which supposedly means “A configuration file was not found and the boot process halts with this error. Check your config file(s). Otherwise, a configuration file is located and the commands within it will be executed (e.g. a boot menu will be displayed and the default option executed when selected).”

I did also change permissions on my dir, as got file not found errors and google said I should &#61514;
sudo chmod -R 777 /raid5/PXEboot/

So here’s my default config:
simon@starbug:~$ ls /var/lib/tftpboot
Clonezilla  memdisk  pxelinux.0    Ubuntu        Xubuntu
dos         Puppy    pxelinux.cfg  vesamenu.c32

and other configs that must be wrong…

simon@starbug:~$ ls -R /var/lib/tftpboot/Ubuntu/
/var/lib/tftpboot/Ubuntu/:
i386  Ubuntu.menu

/var/lib/tftpboot/Ubuntu/i386:
initrd.lz  vmlinuz
simon@starbug:~$

simon@starbug:~$ ls /raid5/PXEboot/
Clonezilla  Puppy  Ubuntu  Xubuntu
simon@starbug:~$ ls /raid5/PXEboot/Ubuntu/
i386
simon@starbug:~$ ls /raid5/PXEboot/Ubuntu/i386/
autorun.inf  dists    isolinux    pics  preseed             ubuntu
casper       install  md5sum.txt  pool  README.diskdefines  wubi.exe
simon@starbug:~$

and the final config of the Ubuntu menu (where it must fail)

simon@starbug:~$ cat /var/lib/tftpboot/Ubuntu/Ubuntu.menu
LABEL 1
        MENU LABEL Ubuntu 10.04 (32-bit)
        KERNEL Ubuntu/i386/vmlinuz
        APPEND boot=casper netboot=nfs nfsroot=192.168.1.250:/raid5/PXEboot/Ubuntu/i386 initrd=Ubuntu/i386/initrd.lz
        TEXT HELP
        Boot the Ubuntu 10.04 32-bit CD
        ENDTEXT

Any suggestions?? :confused:

---

### Post by vikjon0 on 2010-10-28
Ubuntu/i386/vmlinuz and initrd is copied from  Casper on the CD?
You can mount 192.168.1.250:/raid5/PXEboot/Ubuntu/i386 from another PC?
You have the folder .disk in :/raid5/PXEboot/Ubuntu/i386?

I cant see anything wrong with the setup.

---

### Post by sjhupp on 2010-10-28
Thanks for the comments.

> **vikjon0 said:**
> Ubuntu/i386/vmlinuz and initrd is copied from  Casper on the CD?


Yep, as per instructions.

> **vikjon0 said:**
> 
You can mount 192.168.1.250:/raid5/PXEboot/Ubuntu/i386 from another PC?


can browse the dir from the LAN on other PCs ok (with permission). 

> **vikjon0 said:**
> 
You have the folder .disk in :/raid5/PXEboot/Ubuntu/i386?


Um ... no!?  Can see this:
simon@starbug:~$ ls -l /raid5/PXEboot/Ubuntu/i386
total 1484
-rwxrwxrwx 1 root root     143 2010-10-28 10:11 autorun.inf
drwxrwxrwx 2 root root    4096 2010-10-28 10:14 casper
drwxrwxrwx 3 root root    4096 2010-10-28 10:14 dists
drwxrwxrwx 2 root root    4096 2010-10-28 10:14 install
drwxrwxrwx 2 root root    4096 2010-10-28 10:14 isolinux
-rwxrwxrwx 1 root root    4530 2010-10-28 10:14 md5sum.txt
drwxrwxrwx 2 root root    4096 2010-10-28 10:14 pics
drwxrwxrwx 4 root root    4096 2010-10-28 10:14 pool
drwxrwxrwx 2 root root    4096 2010-10-28 10:14 preseed
-rwxrwxrwx 1 root root     225 2010-10-28 10:14 README.diskdefines
lrwxrwxrwx 1 root root       1 2010-10-28 10:14 ubuntu -> .
-rwxrwxrwx 1 root root 1469477 2010-10-28 10:14 wubi.exe

So not all copied?
The guide I followed used the DVD, but I have the CD. Different file structure?

---

### Post by vikjon0 on 2010-10-28
.disk is a hidden directory. Do ls -a (or whatever it is)

Turns out copying a folder structure including hidden is the hardest thing you can do in linux. (please tell me I am wrong)

/* does not take it.

---

### Post by sjhupp on 2010-10-28
Ah, right, thanks.
Did copy that across (only ~5 small files?) but same error.
This might be beyond me :\

---

### Post by vikjon0 on 2010-10-29
I made a live CD with a pxe installer.

[http://sourceforge.net/projects/qfpxeinstaller](http://sourceforge.net/projects/qfpxeinstaller)

user/pwd qfpxe/pxeme

Working:

[LIST]
[*]LivePXECD
[*]mini install
[*]gparted (http)
[*]Clonezilla (http)
[/LIST]

Nfs does not work on the liveCD and I deleted the ubuntudesktop to save space. If you install it to disk you can add the content of ubuntudesktop cd (including hidden files) and it should work again.

Known problems:
The error handling in the script does not work, the script abort if there is a problem. If it is working you should see: " wait 15s or press any key" 
It happens once that tftp hanged. sudo service tftpd-hpa restart 
Perhaps a performance problem but gparted sometimes have to be booted twice. 

!!** Don't install on dual boot or anything like that if you dont know what you are doing. I have not tested the installer on a physical machine.

---

### Post by sjhupp on 2010-10-29
Awesome, thanks. Will grab it and try.
So I can just use my desktop PC for this live PXE cd?
And I assume I then just change my DNSmasq details in my DD-WRT router to point to the desktop instead of my server?
Will check out your config files too.
Really would love to get this working on my server...
Thanks for all the help!

Are you the 1 seeder? :P

---

### Post by vikjon0 on 2010-10-30
> And I assume I then just change my DNSmasq details in my DD-WRT router to point to the desktop instead of my server?
I guess that will work..turning PXE in it off would work for sure since the cd have everything needed built in.

---

### Post by vikjon0 on 2010-10-30
Ok, since people seem to struggle with the torrent I have uploaded the full iso.
[https://sourceforge.net/projects/qfpxeinstaller/](https://sourceforge.net/projects/qfpxeinstaller/)

---

### Post by sjhupp on 2010-10-30
Torrent was no probs for me - just took a few hours to download.
But booting the CD, I got the menu, but the live CD boot didn't work for me - general error and command prompt.
Second time it just seemed to hang at the purple 10.04 loading screen for over 5 mins.
Might go fetch some more media this week and burn again and see if that helps.
Cheers.

---

### Post by vikjon0 on 2010-10-30
Ok, om not sure what the limitation there is on the live CD, if any. I have used remstersys with nothing special to create the CD.

They only test I have done is to boot it in vmware and on my desktop. Both working.

Perhaps the best solution for you is to install vmware player and boot the iso? You can also try to install it in e.g. vmware or virtual box.

---

### Post by sjhupp on 2010-10-30
Don't worry  -I give up.
Last night, so some unknown reason, Ubuntu booting worked (well, not completely, just an old P3 laptop with 256mb ram, but liveCD started properly) but this morning boot failed again.
Brilliant.
I hate computers :mad:

---

### Post by vikjon0 on 2010-10-31
I have fixed the problem with exporting nfs on the LiveCD.
(solution is to keep the data in an iso and mount it in the export directory.)

Depending on the interest I will make a new release in a week or two.

---

### Post by ppatrick on 2010-11-02
check this out
PXE/ProxyDHCP Ubuntu install from a standard Ubuntu install ISO image with the environment set by a single Windows app.
[http://www.vercot.com/~serva/howto/UbuntuPXE1.html](http://www.vercot.com/~serva/howto/UbuntuPXE1.html)

---

### Post by vikjon0 on 2010-11-02
> check this out
PXE/ProxyDHCP Ubuntu install from a standard Ubuntu install ISO image with the environment set by a single Windows app.
[http://www.vercot.com/~serva/howto/UbuntuPXE1.html](http://www.vercot.com/~serva/howto/UbuntuPXE1.html)
Yes, nice tool, but it requries a win OS.

The result is exactly the same as copying the netboot to tftp and publishing the CD with apache. Could be nice to copy the ubuntu menu like in that exemple.

When do you not have internet access 2010? I did some tests on installing from the CD but I really think it is a better idea to use an apt cache. Then you get all you need from the mirror but you not need the space for a complete local mirror.

---

### Post by ppatrick on 2010-11-02
> **vikjon0 said:**
> Yes, nice tool, but it requries a win OS.
Sometimes is easier to get a Windows PC around and just set-up the PXE environment with only one tool, PXE on Linux involves configuring many apps ..

> **vikjon0 said:**
> 
When do you not have internet access 2010?
When dealing with embedded stuff, some virtual scenarios,..

---

### Post by vikjon0 on 2010-11-06
> When dealing with embedded stuff, some virtual scenarios,..
Fair enough. Open source is just a hobby for me since we use MS tech at work. I make a point of not using anything with a license cost. I think my setup is working without internet aswell.

---

### Post by vikjon0 on 2010-11-06
Any feedback on this? a few people have downloaded the cd but no comments.
I was thinking of cleaning it up and upload a new version but I am currently looking into cloning scenarios since I want to install some stuff with no netboot initrd and it is just too much to learn to cook a custome initrd and/or installer.
(some stuff = xbmc)

---

### Post by hasbean on 2011-11-14
For some reason after selecting a distribution, it gets stuck at "Loading" and then gives me that confounded error which says something about press any key to retry or wait for reset.

I finally, finally managed to solve the problem by downloading the latest version of SYSLINUX, compiling it, and using its files instead of the ones found on the Ubuntu 10.04.3 repository.

Also, I'm using atftpd.

I hope this helps whoever is stuck on this.

---

