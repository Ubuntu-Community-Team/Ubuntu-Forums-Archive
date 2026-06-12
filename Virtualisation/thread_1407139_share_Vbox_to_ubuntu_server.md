---
title: "share Vbox to ubuntu server"
date: 2010-02-14
forum: Virtualisation
---

### Post by gavshouse on 2010-02-14
i have a ubuntu 9.10 install with Virtual Box 3.1 installed and a ubuntu server 9.10 guest with LAMP server on.

Im wanting to map/share

Ubuntu 9.10 /home/gav/www/
to
Ubuntu Server 9.10 /var/www

so i can edit files on my ubuntu 9.10 and then refresh in chrome on 192.168.2.3 and they are working fine, how can i do this ?

im currently sharing /home/gav/www/ as www in Vbox settings but how can i setup a symbolic from this to /var/www, i want this to happen upon boot

Thanks in advance

---

### Post by kiranmurari on 2010-02-17
Hi,

In order to acheive this:

First you need to install the guest additions for the VM. See the VirtualBox documentation on installing guest additions for Linux VM. Power off the VM after installing the guest additions. Re-install guest additions after every kernel upgrade.

From VM settings of Ubuntu Server 9.10, under "Shared Folders" setting select the folder which you intend to share between Ubuntu 9.10 and Ubuntu Server 9.10. In your case it is /home/gav/www/. You can make the share read-only, so that you can only edit the files only on your host machine.

Switch on the Ubuntu Server 9.10 VM and mount the shared folder using the command:```
sudo mount -t vboxsf www /var/www
```Now you will be able to use the shared folder, edit the files from your Ubuntu 9.10 and run the webserver on Ubuntu Server 9.10. In order to automount /home/gav/www/, add the following line to your local boot scripts say, /etc/rc.local file.```
mount -t vboxsf www /var/www
```It is not advisable to add the mount point in your /etc/fstab, because vboxsf is not initialized prior to fstab being processed.

Hope this helps.

---

