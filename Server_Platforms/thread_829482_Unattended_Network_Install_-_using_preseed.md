---
title: "Unattended Network Install - using preseed"
date: 2008-06-14
forum: Server Platforms
---

### Post by promodus on 2008-06-14
My motivation to get rid of those questions is that I have a headless server, no vid card, no serial port.
Keep in mind that **when using preseed, use only one space or tab between values**.
I'm using 8.04 for this preseed file.

Prerequisite #1:
a network bootable method.
gPXE
DHCP + PXE Linux or PXE Grub + TFTP
(There are many other variations)

Prerequisite #2:
The ISO of which Ubuntu you wish to install.
and an HTTP Daemon such as Apache.
In my example, I'll have my webserver at the IP 192.168.1.200

Prep-work:
Download the network install kernel and initial ramdisk.

```
wget [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux]("http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux")
wget [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/initrd.gz]("http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/initrd.gz")
```

For my setup I am using PXE Linux. Configure pxe linux configuration to load Kernel and initrd appropriately.
 Example of such can be found here:
[http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/pxelinux.cfg/default]("http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/pxelinux.cfg/default")

next create a directory ubuntu in your WWW Root, in my example my WWW root is /var/www (by default)
```
mkdir /var/www/ubuntu
```

Next mount the installation iso to /var/www/ubuntu
```
mount -o loop ubuntu-8.04-server-i386.iso /var/www/ubuntu
```


Now to get rid of those installation questions:

1. [!!] Chose Language (2 screens, language then country)
Add the boot parameter:
```
debian-installer/locale=en_CA
```

2. [!] Ubuntu installer main menu: Detect keyboard layout?
Add the boot parameter:
```
console-setup/layoutcode=us
```

3. [!] Configure the network: Hostname
Add the boot parameter:
```
netcfg/get_hostname=your_hostname
```

4. [!] Choose a mirror of the Ubuntu Archive
Add the following line to your preseed.cfg
```
d-i mirror/country string CA
```

5. [!] Choose a mirror of the Ubuntu archive
Add the following line to your preseed.cfg
(you can remove step 4 as you need to manually input mirror info anyway)
```
d-i mirror/protocol string http
d-i mirror/country string manual
d-i mirror/http/hostname string 192.168.1.200
d-i mirror/http/directory string /ubuntu/
d-i mirror/suite string hardy
d-i mirror/http/proxy string http://proxydnsorip:port
```

If you're not using a proxy after the word string leave this empty.

6. The reason we are using the installation ISO rather than the ubuntu archives is that I kept getting this error:
[COLOR="Red"][!!] Download installer components
Failed to load installer component
Loading kickseed-common failed for unknown reasons. Aborting.[/COLOR]
Switching to the Ubuntu installation media had solved this problem.

7. Partitioning: (!!USE AT YOUR OWN RISK !! TEST BEFORE DEPLOYING !!)
```
d-i partman-auto/init_automatically_partition select Guided - use entire disk
d-i partman/confirm_write_new_label boolean true
d-i partman/confirm boolean true
d-i partman-auto/method string regular
d-i partman/choose_partition select Finish partitioning and write changes to disk
```

8. User account Creation
```
d-i passwd/user-fullname string Your Full Name
d-i passwd/username string loginname
# Normal user's password, either in clear text
d-i passwd/user-password password yourpassword
d-i passwd/user-password-again password yourpassword
# or encrypted using an MD5 hash.
#d-i passwd/user-password-crypted password [MD5 hash]

```
9. Package Selection: 
I would highly recommend adding open-ssh server if this machine is headless.
```
tasksel tasksel/first   select  OpenSSH server
```

10.System clock set to UTC?
```
d-i clock-setup/utc boolean true
```

11. Log into the machine:
```
ssh your_ip_address_of_target_installation
```

There that should automate the entire server process.
When the system reboots I would edit your /etc/apt/sources.list 
In my example I set it from my local intranet webserver to one of the ubuntu archives.
```
sed -i "s/192.168.1.200/ca.archive.ubuntu.com" /etc/apt/sources.list
apt-get update
apt-get upgrade
```

---

