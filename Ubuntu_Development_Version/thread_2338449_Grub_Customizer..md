---
title: "Grub Customizer."
date: 2016-09-28
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2016-09-28
Anyone tried grub customizer, I did and got the following message:

henry@wyatt:~$ sudo add-apt-repository ppa:danielrichter2007/grub-customizer
[sudo] password for henry:          
 This PPA contains the latest release of Grub Customizer.

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
 More info: [https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keybox '/tmp/tmpmhgxvhx0/pubring.gpg' created
gpg: /tmp/tmpmhgxvhx0/trustdb.gpg: trustdb created
gpg: key A8AA1FAA3F055C03: public key "Launchpad PPA for Daniel Richter" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
OK
henry@wyatt:~$ sudo apt update
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety InRelease [247 kB]                                
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-updates InRelease                                           
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-backports InRelease         
Ign:5 [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) yakkety InRelease
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety/main i386 Packages [1,218 kB]
Err:7 [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) yakkety Release
  404  Not Found
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety/main amd64 Packages [1,222 kB]    
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety/universe i386 Packages [7,744 kB]  
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety/universe amd64 Packages [7,760 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety/universe Translation-en [4,495 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety/universe amd64 DEP-11 Metadata [2,814 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety/universe DEP-11 64x64 Icons [7,305 kB]
Reading package lists... Done                                    
E: The repository 'http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu yakkety Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
henry@wyatt:~$

---

### Post by zika on 2016-09-28
PPA You're trying to use does not have Yakkety branch (yet).
Yes, You could try to use Xenial one but since we're talking about Grub I would not be brave enough to advise You so...

---

### Post by Hewjr100 on 2016-09-28
I see.  Well I gues I will remove ppa and wait till 16.10 is released (GA).

Henry

---

### Post by oldfred on 2016-09-28
Many like Grub Customizer as it makes it easier to change things in grub.

But if willing to edit a file or two all the changes you want can be done manually.

Or if dual booting a LTS version and Yakkety, you can just reinstall the LTS version's copy of grub to MBR or reset UEFI grub setting.

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

