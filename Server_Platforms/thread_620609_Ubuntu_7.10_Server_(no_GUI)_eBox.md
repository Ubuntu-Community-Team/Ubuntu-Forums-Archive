---
title: "Ubuntu 7.10 Server (no GUI) eBox"
date: 2007-11-22
forum: Server Platforms
---

### Post by WIGGMPk on 2007-11-22
General Questions:

1. Do I need a GUI to run eBox?? I am aware that this is a web based managment tool.

eBox Questions:

After installing eBox (sudo apt-get ebox-all) everything gets locked down or something. I suspect ebox-firewall is the culpret but could be wrong.

1. Can I shutdown part of eBox via command line?? (lets say for instance the firewall??)

2. Does eBox automatically setup DHCP Services or does this need to be setup with dhcp3-server first??


-----------------------------------------------------------------------------------------------------------------------------------

My Home Setup:

WAN/NET----> eth0 ----> eth1 (to serve DHCP) ----> Linksys Router (flashed with WRT firmware to act as switch/bridge)---> LAN Clients


Originally I was able to accomplish this by 'sudo apt-get install dhcp3-server', edit the /etc/dhcpd.conf to setup my subnet for eth1 and server DHCP requests. Does this need to be done pre-ebox install or should ebox take care of this?

How can one access the webpage with ebox locking down everything and no GUI on the server to access it locally??


Maybe its because im working on Thanksgiving for 12 freaking hours. Any help is appreciated.



Thanks for all the past support,
Keep up the OPEN SOURCE FREENESS THAT IS UBUNTU!!!!!!!!


PS: M$ can pound sand!

---

### Post by sciurus on 2007-11-22
I don't believe Ebox is working properly yet in Gutsy. You may be better of installing [http://ebox-platform.com/get/ebox_installer.iso](http://ebox-platform.com/get/ebox_installer.iso)

---

### Post by WIGGMPk on 2007-11-23
--> BUMP


Anyone else have any experience w/ eBox on Ubuntu Gutsy Server ??

Could anyone else recommend any remote administration software that has basically the same functionality as eBox??


I was looking into WebMin and was curious as to the functionality vs eBox? Is it relativly the same or a bit more difficult to use then eBox? 

Any feedback on the subject would be appreciated.

Thanks in advance.

---

### Post by perfecttao on 2008-02-01
> I was looking into WebMin and was curious as to the functionality vs eBox? Is it relativly the same or a bit more difficult to use then eBox?

A very late reply to this one, but hopefully it might help someone....

Webmin is an extremely useful application, but all it does is provide a web-based frontend to applications that YOU have installed, for example Samba, VSFTP etc - it doesn't install and configure the apps for you...

ebox, is a fully featured server in itself, handling and running all the applications that you need - yes it can be installed on top of a Debian Sarge box, but as sciurus says, it's best to download and install as an 'appliance'.

Just been playing with ebox for the first time today, but very impressed..

---

### Post by e30power on 2008-02-20
I have to ask this question, as it has been worrying me ever since I installed Ebox on top of a development gutsy server:
I am running 6.10 on my main server right now, and I only have access to it via SSH. The last time I installed E-Box on it, the ebox-firewall cut off my SSH access, causing me to drive across town and manually remove ebox.
Will this happen in the 8.04 version of EBOX?
I would suggest that the default firewall in ebox is either a) not turned on, or b) it at least allows SSH access by default.

---

### Post by faulkes on 2008-02-20
> **e30power said:**
> I have to ask this question, as it has been worrying me ever since I installed Ebox on top of a development gutsy server:
I am running 6.10 on my main server right now, and I only have access to it via SSH. The last time I installed E-Box on it, the ebox-firewall cut off my SSH access, causing me to drive across town and manually remove ebox.
Will this happen in the 8.04 version of EBOX?
I would suggest that the default firewall in ebox is either a) not turned on, or b) it at least allows SSH access by default.

There is currently significant work being done on eBox for 8.04, in specific
reference to the firewall question, I do not have a direct answer, however
 the following is from the ubuntu-server mailing list:

[QUOTE=ubuntu-server mailing list]
> - eBox modules are not enabled by default. The only thing which is enabled by
> default is the web interface. The other modules have to be enabled explicitly
> by the user.
>
> - When a module is enabled, the user is prompted with a modal window where
> she/he is told the actions and file modifications that eBox needs to perform
> to enable the module. In case the user accepts to go ahead, we perform the
> actions and file modifications. For every file we have to modify we store a
> MD5 digest.
>
> - When saving changes, that is when the user configuration is translated into
> modifications of configuration files, we compute a MD5 digest for every
> single file which is going to modify, in case we detect that a file has been
> modified manually we prompt the user to confirm if he wants to overwrite the
> file or keep it.
>
> If you want to see how that works now I  have recorded a screencast [1]
>
> These are the modules which have been already modified with the above changes:
>
> - ebox-services
> - ebox-objects
> - ebox-network
> - ebox-firewall
> - ebox-usersandgroups (LDAP)
> - ebox-samba (Samba + PDC)
> - ebox-printers (Samba + CUPS)
[/QUOTE]

I have asked the developer regarding your firewall question and will follow 
up here when I receive a reply.

Thanks,

Faulkes

---

### Post by dendrobates on 2008-02-21
IIRC,  the version of ebox for 7.10 did have a firewall issue.  It expected there to be two interfaces internal and external, and had an extremely confusing setup.  

This was one of the reasons ebox was not included in 7.10.

You need to use apt-get to purge the ebox packages and then you should be able to reinstall them, without configuring the firewall module.

Rick
Manager, Ubuntu ServerTeam

---

### Post by faulkes on 2008-02-21
> **e30power said:**
> The last time I installed E-Box on it, the ebox-firewall cut off my SSH access, causing me to drive across town and manually remove ebox.
Will this happen in the 8.04 version of EBOX?

I would suggest that the default firewall in ebox is either a) not turned on, or b) it at least allows SSH access by default.

Hi, following up, I spoke with the eBox developer doing work for ubuntu and
received the following reply:

[QUOTE=eBox developer response]
Two things. The firewall module will be disabled by default, so the user will
have to explicitly enable it. When that happens the user will be told the
following:

 'action' => __('Secure by default'),
 'reason' => __('Just a few connections are allowed by default. ' .
                   'Make sure you add the proper incoming and outcoming ' .
                   'rules to make your system work as expected. Usually, ' .
                   'all outcoming connections are denied by default, and ' .
                   'only SSH and HTTPS incoming connections are allowed.'),
 'module' => 'firewall'

And yes, SSH will be allowed by default when the firewall is enabled to avoid
lockouts.
[/QUOTE]

I believe that should answer your question regarding eBox, SSH and 8.04 installation.

Thanks,

Faulkes

---

### Post by e30power on 2008-02-21
Faulkes, thanks a million man.
This is why I love Ubuntu Server.

---

### Post by la3875 on 2008-02-22
First, please forgive the newbie response...

If I understand this thread correctly, the ebox packages can be added to Ubuntu Server 7.10 but will likely work better when 8.04 is released in a couple of months?

Also, are you able to clarify a reference in another thread to a Ubuntu Home Server version, or is this the same as 8.04 on ebox?

I am very curious and very plug-n-play and have been trying various distros and software to make a home NAS/SAN box with RAID-1 with little success to date. I look forward to an option or solution that includes Ubuntu as I love using it!

---

### Post by iamtaylormade on 2008-02-24
> **la3875 said:**
> First, please forgive the newbie response...

If I understand this thread correctly, the ebox packages can be added to Ubuntu Server 7.10 but will likely work better when 8.04 is released in a couple of months?

I am very curious and very plug-n-play and have been trying various distros and software to make a home NAS/SAN box with RAID-1 with little success to date. I look forward to an option or solution that includes Ubuntu as I love using it!

eBox in Ubuntu 7.10 seems to be a bit difficult - the latest Ubuntu package is several releases behind that posted on the eBox site and has issues as you can see from the posts. Everything I have read makes it appear as if eBox via 8.04 will be "fixed" or at least more appealing within Ubuntu. Personally, I'd like to see a side by side comparison of eBox and Webmin via Ubuntu, since they seem to be slightly different with regard to their functionality and purpose.

If you would like to use a box as a NAS, try FreeNAS.  You can always check it out as a VM or just run it as such via VMserver within Ubuntu or a dedicated box.  It works very well and is built on the BDS platform -similar to pfSense/m0n0wall.  Straight forward and PnP/Web based GUI like you suggest.

I may be getting off topic with regard to the initial post...sorry.  It may be helpful to know what specific uses are being sought or tested with regard to the previous posters (eBox).

---

