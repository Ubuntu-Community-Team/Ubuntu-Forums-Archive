---
title: "Access Vmware Esxi from Ubuntu"
date: 2012-12-27
forum: Virtualisation
---

### Post by ketan985 on 2012-12-27
I want to get control of Vmware Esxi server, but there is no Client available for Ubuntu. Is there any way to access Vmware Esxi from ubuntu 12.04.1?

---

### Post by sahabcse on 2012-12-27
1. Ensure you have network connectivity before continuing

2. Get all updates for the server

sudo apt-get update

sudo apt-get upgrade

3. Create the mount point for the CDROM

sudo mkdir -p /media/cdrom

4. Mount the ISO to the folder we created

sudo mount /dev/cdrom /media/cdrom

5. Change the Directory

cd /media/cdrom

6. Copy the tar file from your mounted CDROM/ISO to your /tmp directory

sudo cp VM*.tar.gz /tmp    (Sample Filename: VMwareTools-8.6.0-425873.tar.gz)

7. Install all these dependencies & build tools

sudo apt-get install linux-headers-server build-essential

8. Change the Directory

cd /tmp

9. Unmount the ISO we mounted earlier

sudo umount /media/cdrom

10. Expand the tar

sudo tar -zxvf VM*.tar.gz

11. Change Directory

cd vmware-tools-distrib

12. Create a special directory

sudo mkdir /usr/lib64

13. Run the Install Script

sudo ./vmware-install.pl

14. Reboot

sudo reboot

---

### Post by ketan985 on 2012-12-27
This is for guest system, I want access Vmware server from another Ubuntu desktop.

---

### Post by Cheesemill on 2012-12-27
It's not possible to do this natively, the VMware client is not available for Linux and it doesn't run under Wine.

I have a Windows VM running on my workstation just for running the VMware client.

---

### Post by dcstar on 2012-12-28
> **Cheesemill said:**
> It's not possible to do this natively, the VMware client is not available for Linux and it doesn't run under Wine.

I have a Windows VM running on my workstation just for running the VMware client.

Yep, it is the worst thing about ESXi (apart from the manual update process of the free version......) being forced to use the Windows only vSphere Hypervisor client.

Still, you only need a lightweight P.O.S. like XP to run it and a lot of people have that sort of rubbish available.

---

