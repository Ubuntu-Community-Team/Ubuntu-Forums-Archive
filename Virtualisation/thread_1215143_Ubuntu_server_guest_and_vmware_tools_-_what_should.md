---
title: "Ubuntu server guest and vmware tools - what should I expect to see?"
date: 2009-07-16
forum: Virtualisation
---

### Post by greavette on 2009-07-16
Hello,

I have a few VM's running Ubuntu server (2 Hardy and 1 Jaunty servers).  I've been trying to install VMWare tools for months on these servers, but I always end up having errors.  Recently, I found a webpage with a script to install vmware-tools on ubuntu server (I think it was written for Intrepid).  I tried it on Jaunty and didn't see any errors.

My question is what should I see as a difference after installing vmware tools on my ubuntu server?  I use VMWare Server 1.08/1.09 on two separate PC's and whenever I install VMWare tools on a desktop guest it's obvious the difference once tools are installed.  But on my server I can't see any obvious difference.  I still have to click CTRL-ALT to get out of the VMWare server window.

How can I check if tools are installed properly?

Does anyone have a surefire tutorial on installing tools on Ubuntu Server?

Thanks in advance for your help.

---

### Post by mobious on 2009-09-07
here's how I do it.

desktop
sudo aptitude update
sudo aptitude install build-essential linux-headers-$(uname -r)
cd /cdrom
cp -a /media/cdrom/VMwareTools* /tmp/
cd /tmp/
tar -vxzf VMwareTools*.gz
cd vmware-tools-distrib/
sudo ./vmware-install.pl


   1. Install Ubuntu Server
   2. Login
   3. Create a root shell:sudo bash
   4. Update your sources:apt-get update
   5. Upgrade your installed packages (dist-upgrade to force kernel upgrade):apt-get dist-upgrade
   6. Reboot
   7. Create a root shell again:sudo bash
   8. Install packages VMware Tools needs:apt-get install linux-headers-server build-essential
   9. Install VMware tools
  10. Mount the VMware Tools CD ISO:mount /cdrom
  11. Copy VMware Tools to home:cp /cdrom/VmwareTools-x.x.x-xxxxx.tar.gz ~
  12. Go home:cd ~
  13. Untar/Gzip the install:tar -vzxf VmwareTools-x.x.x-xxxxx.tar.gz (tar -vxzf VMwareTools*.gz)
  14. Go into the resulting directory:cd vmware-tools-distrib
  15. Start the installer:./vmware-install.pl
  16. Install will ask you questions, the defaults should work fine.
  17. Remove the basic AMD PCnet module (if you get errors about building the ethernet driver, run this command and start at step 14 again):rmmod pcnet32
  18. Rebuild module dependancies:depmod -a
  19. Install the VMware accelerated network interface:modprobe vmxnet
  20. Restart network service:/etc/init.d/networking restart
  21. Reboot

---

