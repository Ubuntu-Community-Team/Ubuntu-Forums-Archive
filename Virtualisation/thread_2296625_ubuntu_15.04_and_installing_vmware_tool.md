---
title: "ubuntu 15.04 and installing vmware tool"
date: 2015-09-27
forum: Virtualisation
---

### Post by Paige_ on 2015-09-27
Hi yall

I run windows 10 on my pc and i have the lasest version of vmware warestation. I am trying to to a new installing of ubuntu on my vmware. everything seems to go smoothless but when i try to install vmware tools the normal way i cant. it gives me a message about open wm tools and do you want to install legacy and the autmatiicaly says no i even triee this with 14.04 and having the same problem is there anyway around this. i would like to get ubuntu running back up on my vm to play around with and teach myself how to use it.

---

### Post by leninberg on 2015-09-27
This is what I did, from menu in VMware, select VM>Install vmware tools, then in ubuntu open terminal (console) and write:

sudo -i

mkdir /mnt/cdrom
mount /dev/cdrom /mnt/cdrom
cd /tmp

ls /mnt/cdrom

tar zxpf /mnt/cdrom/VMwareTools-x.x.x-yyyy.tar.gz
(change the xxxyyy with the number you saw with ls /mnt/cdrom)

umount /dev/cdrom

cd vmware-tools-distrib

./vmware-install.pl

Follow the instructions.
Reboot (sudo reboot)

---

### Post by nlee2 on 2015-09-27
I believe the "normal" way is

apt-get install open-vm-tools

[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2073803](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2073803)

---

### Post by Paige_ on 2015-09-27
usually i extract the vmware tools to the desktop and then i run it  i usually do it these way and works now all of a sudden its not 
cd Desktop/vmware-tools-distrib
sudo ./vmware-install.pl -d

---

### Post by Paige_ on 2015-09-27
okay so i tried with apt-get install open-vm-tools and then my method it seems it installed but i can go full screen what the heck did they change on vmware this is to be easy now its such a task i kinda do want to bother anymore

---

### Post by RichardET on 2015-10-03
> **Paige_ said:**
> Hi yall

I run windows 10 on my pc and i have the lasest version of vmware warestation. I am trying to to a new installing of ubuntu on my vmware. everything seems to go smoothless but when i try to install vmware tools the normal way i cant.

I have a similar setup on a Lenovo W530;  Normally VMware recognizes that you are trying to install Ubuntu and will auto-install everything, including the tools, but with other guest OS's such as FreeBSD, you must manually install the tools.   Are you using Workstation Pro 12?   If you are using an older version of VMware it might not recognize the latest Ubuntu, but VMware 11 or 12 should be fine.  You may be trying to manually setup the VM, but if you are new to Unix-like OS's, then I would choose the auto-install feature.

---

