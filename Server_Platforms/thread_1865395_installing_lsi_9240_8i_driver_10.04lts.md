---
title: "installing lsi 9240 8i driver 10.04lts"
date: 2011-10-20
forum: Server Platforms
---

### Post by mchlor on 2011-10-20
Greetings, trying to install 9240 8i driver into lucid 10.04 server 32bit edition.

I've followed the step listed in the LSI driver package to a tee.

1.  sudo -s
2.  apt-get install build-essential ; apt-get install libncurses5 ; apt-get install libncurses5-dev
3.  apt-get install 2.6.32-34-generic-pae 
4.  cd /usr/src ; ln -s  2.6.32-34-generic-pae linux
5.  tar -zxvf megaraid_sas-v00.00.05.30-src.tgz ; cd /usr/src/v00.00.05.30
6.  make &#8211;C /lib/modules/2.6.32-34-generic-pae/build/ M=`pwd`    
7.  cp megaraid_sas.ko /lib/modules/2.6.32-34-generic-pae/kernel/drivers/scsi
8.  rm /boot/initrd.img-2.6.32-34-generic-pae
9.  update-initramfs -c -k 2.6.32-34-generic-pae

after struggling for 2 days, I've finally managed to overcome the errors and compile the driver from source into magaraid_sas.ko

after copying and remaking initramfs the driver still does not load.  So I then tried to modulize it and load it that way by doing this.

 make -C /usr/src/linux-headers-2.6.32-34-generic-pae M=`pwd` modules
 sudo make -C /usr/src/linux-headers-2.6.32-34-generic-pae M=`pwd` modules_install
 sudo depmod -a
sudo update-initramfs -u

That didn't load megaraid_sas.ko either.  any help? thanks.

---

