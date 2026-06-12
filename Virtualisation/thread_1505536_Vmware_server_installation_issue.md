---
title: "Vmware server installation issue"
date: 2010-06-09
forum: Virtualisation
---

### Post by GirishSharma on 2010-06-09
Hello,

I am in process of configuration of vmserver on my ubuntu 10.04 32 bit machine and for this i run a script which i downloaded from this link :
[http://radu.cotescu.com/2009/10/30/h...-karmic-koala/](http://radu.cotescu.com/2009/10/30/h...-karmic-koala/)

because earlier; when i was trying to install vmserver; i stuck at error "Unable to build vmmon module". 

This script run without any error and finally i got "Enjoy Team..." message. But here i am struggling for 2 issues :

1.When the above script was running, i forgot to add vmserver administrator, so now i am not able to login to vmserver ([http://localhost:8222/](http://localhost:8222/)). The user; who run the above script was "girish" (i.e. myself), but when i gives username as "girish" and password; it is saying that you are not authorized; or privilege not having... error.

2.If i shutdown the machine and restart and in firefox i says :
[http://localhost:8222/;](http://localhost:8222/;) firefox is not able to bring back that login page; which came after finishing of the script.

$ ifconfig -a
is showing only eth0 and lo, not vmnet1 or vmnet8; so i think if they are not coming in output of ifconfig -a command; i will not able to get that login page; but whats wrong here; i am very much confused and frustrated to get all these working.

I have downloaded the vmserver from its official site with proper activation key. I think its not an issue of registration or licence issue here, because there is no such error, which points me for an invalid activation key or etc.

Anyone please help me to install vmware software on my 32 bit machine having Ubuntu 10.04?

What should i install/run to get vmware tool, so that i may configure windows xp as guest os?

Earlier, i posted this question in General Help forum; where i got help to post the question here itself.

Kindly help me.
Regards
Girish Sharma

---

### Post by go_linux on 2010-06-10
[FONT=Courier New]**INSTALLATION of VMware Server 2.0.x in Ubuntu 10.04**

#############################################################
# These instructions are divided into two sections          #
#############################################################
# The first generates the required corrections so that      #
# the modules compile without errors in ubuntu, also the    #
# configuration script vmware-config.pl is patched          # 
# so that vsock can be used.                                #
#############################################################
- Make sure you have the pre-requisites installed
  sudo apt-get install ... alien make gcc

- Create a directory in /tmp named vm
  mkdir /tmp/vm

- Cd into /tmp/vm

- Obtain the patch set posted at [http://www.vivaolinux.com.br/dica/Ubuntu-10.04-com-VMware-Server-2.0.x:](http://www.vivaolinux.com.br/dica/Ubuntu-10.04-com-VMware-Server-2.0.x:) 
  [http://img.vivaolinux.com.br/imagens/dicas/comunidade/patch-vmware_2.6.3x.tgz](http://img.vivaolinux.com.br/imagens/dicas/comunidade/patch-vmware_2.6.3x.tgz)

- Gunzip the patch
  gunzip <path_to>/vmware_2.6.3x.tgz

- Unpack patch-vmware_2.6.3x.tar
  tar xvf <path_to>/patch-vmware_2.6.3x.tar

- Download and unpack vmware 2.0.x tar.gz package format
  tar xvzf <path_to>/VMware-server-2.0.2-203138.x86_64.tar.gz

- Apply patches
  sh ./patch-vmware_2.6.3x.sh vmware-server-distrib/lib/modules/source/

- Copy relevant resulting files
  sudo cp vmware-server-distrib/lib/modules/source/*.tar \
     vmware-server-distrib/bin/vmware-config.pl <backup_folder_full_path>

- Remove root permissions if required
  cd <backup_folder_full_path>
  sudo chown <your_user>:<your_user> *

- Download vmware-config.pl patch from 
  [http://ubuntuforums.org/attachment.php?attachmentid=94477&d=1227872015](http://ubuntuforums.org/attachment.php?attachmentid=94477&d=1227872015)
  from post
  [http://ubuntuforums.org/showpost.php?p=6267637&postcount=17](http://ubuntuforums.org/showpost.php?p=6267637&postcount=17)

  cd <backup_folder>
  patch < vmware-config.pl.patch.txt 

###########################################################
# This second section will install a standard deb package #
# so that future vmware remotion is easy, and only then   #
# will the saved files be applied.                        #
###########################################################

- Download VMware Server 2.0.x in .rpm format

- Convert rpm to deb
  alien -d -c --fixperms VMware-server-2.0.2-203138.x86_64.rpm

- If all went well the following deb package should have been
  generated: vmware-server_2.0.2-203139_amd64.deb

- Now install this package with:
  sudo dpkg -i vmware-server_2.0.2-203139_amd64.deb

- After installation do gunzip the EULA file or vmware-config.pl
  will give an error
  cd /usr/share/doc/vmware
  sudo gunzip EULA.gz

- Now replace backed up files:
  sudo cp <backup_folder_full_path>/*.tar /usr/lib/vmware/modules/source/
  sudo cp <backup_folder_full_path>/vmware-config.pl /usr/bin

- And we are done!!!

###########################################################
# Now just configure your VMware installation, making     #
# sure you have your VMware Server serial nearby, just    #
# like as if VMware never had a problem installing in     #
#  Ubuntu.                                                #
###########################################################

- sudo vmware-config.pl


[/FONT]

---

### Post by iwalsh on 2010-06-27
Sorry... fails at the first step...

ian@shark:~/Downloads/vmware-server-distrib$ sudo apt-get install ... alien make gcc
[sudo] password for ian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ...
ian@shark:~/Downloads/vmware-server-distrib$

---

