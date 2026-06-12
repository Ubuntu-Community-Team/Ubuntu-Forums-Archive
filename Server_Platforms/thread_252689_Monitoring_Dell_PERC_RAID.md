---
title: "Monitoring Dell PERC RAID"
date: 2006-09-07
forum: Server Platforms
---

### Post by paul.maddox on 2006-09-07
Hi,

Our company currently has quite a few Dell PowerEdge 2950's with SAS SCSI Drives using Dell's PERC (megaraid) RAID controller.

Is there any way I can monitor the status of the RAID array to see if there is a hard disk failure? 

Thanks

---

### Post by Uluen on 2006-09-07
Maybe *mdadm* could be useful?

---

### Post by paul.maddox on 2006-09-07
I couldn't seem to get mdadm provide any information, is it just for software RAID?

I have managed to find a tool called MegaCLI for RedHat and get it working under Ubuntu that allows you to configure and monitor all manor of options. 

I've attached a deb package incase anyone in the future has this problem.

The program itself is a real nasty program to use but luckily I found a PDF floating about on the net with full documentation:
[http://manuals.fujitsu-siemens.com/serverbooks/content/manuals/english/mr-sas-sw-ug-en.pdf]("manuals.fujitsu-siemens.com/serverbooks/content/manuals/english/mr-sas-sw-ug-en.pdf")

---

### Post by crouton on 2006-09-13
Oy, MegaCLI.  That's a LSI Logic utility.  It's not really in the same league as the PERC RAID tools you'd find in windows (openmanage, etc..)

It's not even really meant to be used for monitoring, just setup/deletion/etc.

---

### Post by rcgabriel on 2006-10-27
What about MegaRAID Storage Manager, LSI's real RAID management software for Linux?  Also for RedHat, and I am not familiar enough with Alien to get it properly converted for Debian/Ubuntu, but it should be theoretically possible.  I'm playing with it with Alien right now, but I'll probably need some help.  

I assume MSM is a more user-friendly tool than MegaCLI.

---

### Post by gamars on 2006-12-17
How about DELL's OMSA? I have seen post about OMSA v.4.4 running on Debian. Is that tool sufficient for server's administration? I am receiving my first PowerEdge 2900 in a couple days and gathering information to make it work :-). 

So has anyone tried OMSA on Ubuntu?

---

### Post by Speeder on 2006-12-26
any news on this?

---

### Post by Brazen on 2006-12-26
Why not use OpenManage from Dell?

---

### Post by Brazen on 2006-12-26
this is from the install guide for OpenManage:> 
Log on as root to the system running a supported Red Hat Enterprise Linux or SUSE LINUX Enterprise Server operating system where you want to install the managed system components. 

  NOTE: SUSE LINUX Enterprise Server operating system is supported only on PowerEdge 1800, 1850, 2800, and 2850 systems. 


Insert the Installation and Server Management CD into the CD drive. 


If necessary, mount the CD using the mount /dev/cdrom /media/cdrom command or a similar command (for Red Hat Enterprise Linux 4 and SUSE LINUX Enterprise Server 9) OR mount /dev/cdrom /mnt/cdrom or a similar command (for Red Hat Enterprise Linux 3). 


Execute the srvadmin-install.sh script from the 


/srvadmin/linux/supportscripts directory as follows:

sh srvadmin-install.sh --express

or

sh srvadmin-install.sh -x

The script will install the typical software suite for your system configuration. 


  NOTE: You can log the output of the RPM installation by adding 2>&1 | tee &#8211;a /var/log/srvadmin.log to the above shell script execution. The resulting command would be sh srvadmin-install.sh 2>&1|tee &#8211;a /var/log/srvadmin.log 

Start the services with the sh srvadmin-services.sh start command. 

I'm guessing that install script just executes some rpm commands.  You can probably view the script and follow it but use alien instead of rpm.  OR, maybe you could map the rpm command to the alien command?  I think alien mimics the syntax for rpm.

---

### Post by paul.maddox on 2006-12-26
Oooh, looky what I found...



[http://linux.dell.com/debian_9g.shtml]("http://linux.dell.com/debian_9g.shtml")

---

### Post by efuller on 2007-01-05
I have a Poweredge 2900 with the Perc 5/i. I have a RAID 5 array with 8 disks. (all in use, no spares)

I installed Debian via this [http://kmuto.jp/debian/d-i/]("http://kmuto.jp/debian/d-i/"). He has some rolled installations that come with build in RAID support, etc. 

I was succesful in my installation using the 801 build provided by the site above. I posted the details here at [linuxquestions.org]("http://www.linuxquestions.org/questions/showthread.php?t=503052").

Since Ubuntu is based on Debian, I figured posting here might be of some help.

I tested my system for a failure by pulling one of the disks while the server was powered down. It booted fine, although the flashing Dell lights let me know the hard drive wasn't there.

Following the instructions via Dells site I was able to rebuild the drive using the configuration tool in the pre-boot configuration utility.

However, during a real failure the server will be powered on and a drive will drop out. I am sure the RAID system is capable of handling it. However, little flashing lights aren't enough. I need it to send me an email after a failure. Especially since all my disks are in use, and I don't have room for a hot spare.

I looked at the LSI logic site's page on the MegaRAID SAS 8408E (it is the perc 5/i OEM equivalent). I can see that all of the packages provided are RPM based. Alien wasn't good enough to convert everything over, and it seems I cannot run there software.

I took a look at the Dell site posted here. Installing the .deb package didn't get OMSA working at all.

Before I post a bunch of error messages, I was wondering if anyone had any success stories with OMSA, the LSI Logic Utility etc. on a Debian based system. How did you get it running?

Knowing the status of an array is very important.

---

### Post by reech on 2007-03-22
See my post here: [http://ubuntuforums.org/showpost.php?p=2336772&postcount=54]("http://ubuntuforums.org/showpost.php?p=2336772&postcount=54")

---

### Post by warjdo on 2007-04-20
[INDENT]... I have managed to find a tool called MegaCLI for RedHat and get it working under Ubuntu that allows you to configure and monitor all manor of options....[/INDENT]

Very nice. Seems to be the only solution I might have to query or manage my hardware RAID on Dell SC440...
**BUT** is there any chance you could also provide a x86_64 (or a source) package ???

Many thanks !

---

### Post by pastor martin on 2008-03-19
Here is a script I used to get DELL OMSA working (particularly the hardware raid monitoring) on my Dell SC440 via  [https://servername:1311](https://servername:1311)     
-----------------------------------------------------------------------------------------------

#!/bin/sh

/opt/dell/srvadmin/dataeng/bin/dsm_sa_datamgr32d
/opt/dell/srvadmin/dataeng/bin/dsm_sa_eventmgr32d
/opt/dell/srvadmin/dataeng/bin/dsm_sa_snmp32d

/opt/dell/srvadmin/dataeng/bin/dataeng status

/opt/dell/srvadmin/iws/bin/linux/dsm_om_connsvc start 
/opt/dell/srvadmin/iws/bin/linux/dsm_om_connsvc start 

/etc/init.d/dataeng stop ; modprobe mptctl ; /etc/init.d/dataeng start

/opt/dell/srvadmin/dataeng/bin/dsm_sa_datamgr32d
/opt/dell/srvadmin/dataeng/bin/dsm_sa_eventmgr32d
/opt/dell/srvadmin/dataeng/bin/dsm_sa_snmp32d

/opt/dell/srvadmin/dataeng/bin/dataeng status

/opt/dell/srvadmin/iws/bin/linux/dsm_om_connsvc start 
/opt/dell/srvadmin/iws/bin/linux/dsm_om_connsvc start 

------------------------------------------------------------------------------------------------
 I saved this as a .sh script (dell_omsa.sh)
and put it into the /etc/init.d/          
directory

Web hardware monitoring now works great

---

### Post by leondo on 2008-05-04
I have a dell perc 5/i and I'm trying to install MegaCli and MegaRaid Storage Manager. MegaCli comes with rpm format, which I converted to deb using alien and installed successfully.


Now I'm trying to install MegaRaid Storage Manager which comes in a tar.gz. It contains a bunch of scripts and a bunch of rpms. Here is a ls :
[I]deleteOldVersion.sh                          readme.txt
install.sh                                   RunRPM.sh
libstdc++34-3.4.0-1.i386.rpm                 sas_ir_snmp-3.13-0005.i386.rpm
LSI-AdapterSASIR.mib                         sas_snmp-3.13-0004.i386.rpm
LSI-AdapterSAS.mib                           ServerInstall.sh
MegaRAID_Storage_Manager-2.35-01.noarch.rpm
[/I]
I converted MegaRAID_Storage_Manager-2.35-01.noarch.rpm,  sas_ir_snmp-3.13-0005.i386.rpm, sas_snmp-3.13-0004.i386.rpm successfully using alien, but I can't convert libstdc++34-3.4.0-1.i386.rpm successfully.
Any ideas??

---

