---
title: "Encrypted Ubuntu and NSA SELinux"
date: 2012-04-03
forum: Security
---

### Post by Welly Wu on 2012-04-03
Hello! I have an ASUS N61JV-X2 notebook PC and I downloaded the Ubuntu 11.10 64 bit GNU/Linux Alternative Install .ISO file and I burned it to a blank 700 MB CD-R disc. I followed joern's guide to installing Ubuntu 10.10 with full disk encryption. Here's what I did. I popped the Ubuntu 11.10 64 bit GNU/Linux Alternative Install CD-R into my DVD burner drive and I booted off the disc into the Ubuntu GUI installation. I chose manual partitioning. I created my own partition layout. I created a small 500 MB unencrypted boot partition and I set it to primary at the beginning of the boot partition. Next, I selected configure encrypted volumes and I chose the Serpent cipher using ESSIV:SHA256 mode with 256 bit key strength and SHA-512 hash algorithm to create a LUKS/LVM volume with the remainder of my Intel X25-M 160 gigabyte SSD. I wound up selecting configure the logical volume manager and I created a volume group named volumegrp01. Then, I selected create logical volume and I created volume01 with 8 gigabytes of disk space and I set it as the /swap space. I also created another logical volume named volume02 with 20 gigabytes of disk space and I set it as the / root partition. I created a third volume name volume03 with the remainder of the available disk space and I set it as the /home partition. All of the volumes use the /ext4 file system. I wrote the changes to the Intel SSD. Finally, Ubuntu 11.10 64 bit GNU/Linux installed itself. I created a highly complex, random, 20+ character symmetric key password. I also encrypted my /home partition after Ubuntu was installed with a different password.

I launched the terminal and I typed in sudo apt-get install selinux. Ubuntu removed Novell's AppArmor and it installed NSA's SELinux. I typed in sudo touch /.autorelabel and I typed in sudo setenforce=0 to permissive mode. I rebooted my computer.

Here's my problem. When I typed in sudo gedit /etc/selinux/config, I changed it SELINUX=enforcing and I rebooted my computer. At the Plymouth screen that says Ubuntu, it gives me two error messages. First, it says that it can not mount my /tmp directory. Then, it says that it can not mount my dev/volumegrp01/volume02 which I know is my Serpent encrypted / root partition. Hence, I am stuck at the Ubuntu screen and I never make it to the LightDM login screen. I had to pop in my Ubuntu 11.10 64 bit GNU/Linux Alternative Install CD-R and perform a rescue to type in my symmetric key password and mount my /dev/volumegrp01/volume02. Then, I typed in vi /etc/selinux/config to change SELINUX=permissive. Finally, I rebooted my computer and I am able to login to Ubuntu normally.

How do I get NSA's SELinux to enforcing mode and still get my Ubuntu operating system properly working? In other words, what do I need to do to be able to boot into Ubuntu and use it normally while I have NSA's SELinux set to enforcing mode?

Please help if you can. Thank you.

---

### Post by HermanAB on 2012-04-03
Howdy, Ubuntu mainly supports Novell's App Armor.  If you want to use SELinux, then you got to switch to Fedora.

---

### Post by Welly Wu on 2012-04-03
I realize that fact, but I want to stick with Ubuntu 64 bit. There must be other Ubuntu users that have switched to NSA's SELinux and a few of them may have setup an encrypted Ubuntu installation. So, I am waiting for them to lend me a hand.

If someone can help me with my specific problem as I stated, then I would appreciate it if you would please reply.

---

### Post by Welly Wu on 2012-04-03
I tried to remove NSA's SElinux and install Novell's AppArmor, but I get this error message:

wellywu@N61JV-X2:~$ sudo apt-get install apparmor
[sudo] password for wellywu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  apparmor-profiles apparmor-docs apparmor-utils
The following packages will be REMOVED:
  selinux
The following NEW packages will be installed:
  apparmor
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0 B/339 kB of archives.
After this operation, 1,180 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 227874 files and directories currently installed.)
Removing selinux ...
/var/lib/dpkg/info/selinux.prerm: 55: /etc/init.d/selinux: not found
dpkg: error processing selinux (--remove):
 subprocess installed pre-removal script returned error exit status 127
Errors were encountered while processing:
 selinux
E: Sub-process /usr/bin/dpkg returned an error code (1)
wellywu@N61JV-X2:~$

What is the problem here?

How do I remove SELinux successfully?

---

### Post by Welly Wu on 2012-04-03
I am going to install Red Hat Fedora 16 64 bit GNU/Linux on my ASUS N61JV-X2 notebook PC in an hour. I am switching from Ubuntu to Fedora today.

---

