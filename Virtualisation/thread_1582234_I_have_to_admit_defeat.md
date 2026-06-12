---
title: "I have to admit defeat"
date: 2010-09-26
forum: Virtualisation
---

### Post by BradleyAtkins on 2010-09-26
I hate to say this but I have never been so thoroughly defeated by a piece of software as vmware. It's a shame because they are adopting this at work and I could really do with getting my hands on it to learn how to administer it.

Seems no matter what I do I arrive at a point where I am trying to log into the Web Access UI and get web service unavailable. I have followed every recommendation I can find on how to install it, the cleanest seeming to be here: -

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

At least it installs it without error.

I have tried every variation I can think of on this install including accepting no user as the default but still end up with the same error.

If anyone can tell me what I am doing wrong I would be so grateful. This is stdout from the install: -

```
root@poweredge:/tmp# tar zxpf VMware-server-2.0.2-203138.x86_64.tar.gz
root@poweredge:/tmp# tar zxpf raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27.tar.gz
root@poweredge:/tmp# ls -l
total 463784
drwxr-xr-x  2 root root          4096 2010-09-26 09:48 hsperfdata_root
drwxrwxr-x  2 root root          4096 2010-07-11 14:04 raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27
-rw-r--r--  1 brad museuser      8586 2010-09-26 09:57 raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27.tar.gz
-rw-r--r--  1 brad museuser 474415801 2010-09-26 09:57 VMware-server-2.0.2-203138.x86_64.tar.gz
drwxr-xr-x 10 root root          4096 2009-10-21 02:48 vmware-server-distrib
root@poweredge:/tmp# cd raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27
root@poweredge:/tmp/raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27# ls
LICENSE  README  start-VMware-console.sh  vmware-config.patch  vmware-server-2.0.2-203138-update.patch  vmware-server-2.0.x-kernel-2.6.3x-install.sh
root@poweredge:/tmp/raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27# ls -l
total 44
-rw-rw-r-- 1 root root  1321 2010-07-11 14:04 LICENSE
-rw-rw-r-- 1 root root  1980 2010-07-11 14:04 README
-rwxrwxr-x 1 root root   702 2010-07-11 14:04 start-VMware-console.sh
-rw-rw-r-- 1 root root  1111 2010-07-11 14:04 vmware-config.patch
-rw-rw-r-- 1 root root 13618 2010-07-11 14:04 vmware-server-2.0.2-203138-update.patch
-rwxrwxr-x 1 root root 10631 2010-07-11 14:04 vmware-server-2.0.x-kernel-2.6.3x-install.sh
root@poweredge:/tmp/raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27# vmware-server-2.0.x-kernel-2.6.3x-install.sh ..
vmware-server-2.0.x-kernel-2.6.3x-install.sh: command not found
root@poweredge:/tmp/raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27# ./vmware-server-2.0.x-kernel-2.6.3x-install.sh ..
You have VMware Server archive: 
        VMware-server-2.0.2-203138.x86_64.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.31-22-server package...
You do have the build-essential package...
You do have the patch package...
Found .tar file for vmmon module
Found .tar file for vsock module
Found .tar file for vmnet module
Found .tar file for vmci module
Extracting .tar files in order to apply the patch...
Untarring ../vmware-server-distrib/lib/modules/source/vmmon.tar
Untarring ../vmware-server-distrib/lib/modules/source/vsock.tar
Untarring ../vmware-server-distrib/lib/modules/source/vmnet.tar
Untarring ../vmware-server-distrib/lib/modules/source/vmci.tar
Testing patch...
poweredge:/home/brad>ls
20091203_muse	       muse	   raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27.tar.gz  vmware-config.pl.patch.txt
20091203_muse.results  mysql	   tmp								 VMware-guest64check-5.5.0-18463
bin		       perl	   vim								 VMware-server-2.0.2-203138.x86_64.tar.gz
forum		       perl_stuff  vminstall-nosuer.txt						 vmx
m_results	       perl.tar    vminstall.txt						 wip
m_tmp		       Private	   vmw
poweredge:/home/brad>cat vminstall-nosuer.txt
root@poweredge:/tmp# tar zxpf VMware-server-2.0.2-203138.x86_64.tar.gz
root@poweredge:/tmp# tar zxpf raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27.tar.gz
root@poweredge:/tmp# ls -l
total 463784
drwxr-xr-x  2 root root          4096 2010-09-26 09:48 hsperfdata_root
drwxrwxr-x  2 root root          4096 2010-07-11 14:04 raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27
-rw-r--r--  1 brad museuser      8586 2010-09-26 09:57 raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27.tar.gz
-rw-r--r--  1 brad museuser 474415801 2010-09-26 09:57 VMware-server-2.0.2-203138.x86_64.tar.gz
drwxr-xr-x 10 root root          4096 2009-10-21 02:48 vmware-server-distrib
root@poweredge:/tmp# cd raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27
root@poweredge:/tmp/raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27# ls
LICENSE  README  start-VMware-console.sh  vmware-config.patch  vmware-server-2.0.2-203138-update.patch  vmware-server-2.0.x-kernel-2.6.3x-install.sh
root@poweredge:/tmp/raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27# ls -l
total 44
-rw-rw-r-- 1 root root  1321 2010-07-11 14:04 LICENSE
-rw-rw-r-- 1 root root  1980 2010-07-11 14:04 README
-rwxrwxr-x 1 root root   702 2010-07-11 14:04 start-VMware-console.sh
-rw-rw-r-- 1 root root  1111 2010-07-11 14:04 vmware-config.patch
-rw-rw-r-- 1 root root 13618 2010-07-11 14:04 vmware-server-2.0.2-203138-update.patch
-rwxrwxr-x 1 root root 10631 2010-07-11 14:04 vmware-server-2.0.x-kernel-2.6.3x-install.sh
root@poweredge:/tmp/raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27# vmware-server-2.0.x-kernel-2.6.3x-install.sh ..
vmware-server-2.0.x-kernel-2.6.3x-install.sh: command not found
root@poweredge:/tmp/raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27# ./vmware-server-2.0.x-kernel-2.6.3x-install.sh ..
You have VMware Server archive: 
	VMware-server-2.0.2-203138.x86_64.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.31-22-server package...
You do have the build-essential package...
You do have the patch package...
Found .tar file for vmmon module
Found .tar file for vsock module
Found .tar file for vmnet module
Found .tar file for vmci module
Extracting .tar files in order to apply the patch...
Untarring ../vmware-server-distrib/lib/modules/source/vmmon.tar
Untarring ../vmware-server-distrib/lib/modules/source/vsock.tar
Untarring ../vmware-server-distrib/lib/modules/source/vmnet.tar
Untarring ../vmware-server-distrib/lib/modules/source/vmci.tar
Testing patch...
Applying patch...
Preparing new tar file for vmmon module
Preparing new tar file for vsock module
Preparing new tar file for vmnet module
Preparing new tar file for vmci module
Checking that the compiling will succeed...
Trying to compile vmmon module to see if it works
Performing make in ../vmware-server-distrib/lib/modules/source/vmmon-only
Using 2.6.x kernel build system.
Trying to compile vsock module to see if it works
Performing make in ../vmware-server-distrib/lib/modules/source/vsock-only
Using 2.6.x kernel build system.
WARNING: "VMCIDatagram_CreateHnd" [/tmp/vmware-server-distrib/lib/modules/source/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_DestroyHnd" [/tmp/vmware-server-distrib/lib/modules/source/vsock-only/vsock.ko] undefined!
WARNING: "VMCI_GetContextID" [/tmp/vmware-server-distrib/lib/modules/source/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_Send" [/tmp/vmware-server-distrib/lib/modules/source/vsock-only/vsock.ko] undefined!
Trying to compile vmnet module to see if it works
Performing make in ../vmware-server-distrib/lib/modules/source/vmnet-only
Using 2.6.x kernel build system.
Trying to compile vmci module to see if it works
Performing make in ../vmware-server-distrib/lib/modules/source/vmci-only
Using 2.6.x kernel build system.
Rebuilding tar files...
Replacing original file vmmon.tar with patched file...
Replacing original file vsock.tar with patched file...
Replacing original file vmnet.tar with patched file...
Replacing original file vmci.tar with patched file...
Removing binaries directory...
Patching vmware-install.pl...
patching file ../vmware-server-distrib/bin/vmware-config.pl
Starting VMware Server original install script...
Creating a new VMware Server installer database using the tar4 format.

Installing VMware Server.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the daemon files? 
[/usr/sbin] 

In which directory do you want to install the library files? 
[/usr/lib/vmware] 

In which directory do you want to install the manual files? 
[/usr/share/man] 

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware] 

The path "/usr/share/doc/vmware" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

The installation of VMware Server 2.0.2 build-203138 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall.pl".

Before running VMware Server for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this 
program to invoke the command for you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machinesfailed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agentfailed
Stopping VMware services:
   VMware Authentication Daemon done
   Virtual machine monitor done

You must read and accept the End User License Agreement to continue.
Press enter to display it. 

NOTICE:  BY DOWNLOADING AND INSTALLING, COPYING OR OTHERWISE USING THE 
SOFTWARE, YOU AGREE TO BE BOUND BY THE TERMS OF THIS VMWARE MASTER END 
USER LICENSE AGREEMENT ("EULA").  IF YOU DO NOT AGREE TO THE TERMS OF 
THIS EULA, YOU MAY NOT DOWNLOAD, INSTALL, COPY OR USE THE SOFTWARE, AND 
YOU MAY RETURN THE UNUSED SOFTWARE TO THE VENDOR FROM WHICH YOU ACQUIRED 
IT WITHIN THIRTY (30) DAYS AND REQUEST A REFUND OF THE LICENSE FEE, IF 
ANY, ALREADY PAID UPON SHOWING PROOF OF PAYMENT.  "YOU" MEANS THE 
NATURAL PERSON OR THE ENTITY THAT IS AGREEING TO BE BOUND BY THIS EULA, 
THEIR EMPLOYEES AND THIRD PARTY CONTRACTORS THAT PROVIDE SERVICES TO 
YOU.  YOU SHALL BE LIABLE FOR ANY FAILURE BY SUCH EMPLOYEES AND THIRD 
PARTY CONTRACTORS TO COMPLY WITH THE TERMS OF THIS AGREEMENT.

1.	DEFINITIONS

1.1	"Designated Administrative Access" means that access to the 
standard user interfaces of a given instance of the Software 
(designated in this section) that you may grant to a designated 
third party (a) for which you have provided advance written notice 
to VMware that you are providing outsourced services and (b) for 
whose dedicated benefit you have licensed such instance of the 
Software.  Designated Administrative Access is applicable only 
where you are 1) an IT outsourcing company that is providing 
outsourced IT services to a client company and 2) applicable only 
to the following Software: ESX Server, VMware Server and 
VirtualCenter.

1.2	"GPL Software" means GPL software licensed to you under the GNU 
General Public License as published by the Free Software Foundation 
(GPL).  A copy of the GPL is included on the media on which you 
received the Software or included in the files you downloaded, if 
you acquired the Software by electronic download.  

1.3	"Guest Operating Systems" means instances of third-party operating 
systems licensed by you and installed in a Virtual Machine and run 
using the Software.

1.4	"Licensed Additional Module" means additional modules that may be 
provided with and/or used in conjunction with the Software for 
which you have paid the applicable license fee and accepted any 
applicable additional license terms. 
 
1.5	"Open Source Software" means various open source software 
components licensed under the terms of applicable open source 
license agreements included in the materials relating to such 
software.  Open Source Software is composed of individual software 
components, each of which has its own copyright and its own 
applicable license conditions.  The Open Source Software licenses 
can be found in the open_source_licenses.txt file, other materials 
accompanying the software package, the documentation or 
corresponding source files available at 
http://www.vmware.com/download/open_source.html.

1.6	"Processor" means a single, physical chip that houses no more than 
four (4) processor cores.                                                   
   

1.7	"Sample Programs" means sample client management programs or 
scripts that may be distributed with the Software.  

1.8	"Server" means a single physical computer of a type that meets the 
specifications as set forth in the applicable product documentation 
posted at  http://www.vmware.com/support/pubs/.  Multiple computers 
that share processing power or operate in a networked configuration 
as a single logical computer, such as a "server farm" or similar 
arrangement, constitute multiple Servers for the purpose of this 
EULA.  

1.9	"Software" means software products that are licensed to you under 
this EULA, including, but not limited to, any related components 
purchased or provided with the Software, application programming 
interfaces, associated media, printed materials, online or 
electronic documentation, and any updates and maintenance releases 
thereto.

1.10	"Software License Key" means, if applicable, a serial number issued 
to you by VMware to activate and use the Software.   A separate, 
additional Software License Key may be required to activate and use 
each Licensed Additional Module.  

1.11  "VMware Tools" means a suite of utilities and drivers that may 
enhance the performance and functionality of your Guest Operating 
System. VMware Tools may include some or all of the following, 
depending on your Guest Operating System: an SVGA driver, a mouse 
driver, the VMware Tools control panel and support for features 
such as shared folders, drag and drop in Windows guests, shrinking 
virtual disks, time synchronization with the host, VMware Tools 
scripts, and connection and disconnection of devices while the 
virtual machine is running. 

1.12	"Virtual Machine" means an instance of a Guest Operating System and 
any application programs installed thereon, running on a computing 
device on which the Software is installed, or suspended to disk or 
any other storage media accessible by the computing device.

 
	
2.	EVALUATION LICENSES

2.1	General.  If available, the Software and each Licensed Additional 
Module may be activated with no-cost evaluation Software License 
Key(s).  You acknowledge that Evaluation Software License Keys have 
an expiration date ("Expiration Date") and that VMware is not 
obligated to permit further use of the Software.

2.2	Evaluation License.  If you activate the Software or any Licensed 
Additional Module with an evaluation Software License Key 
("Evaluation Product") you may use the Evaluation Product until the 
Expiration Date only to evaluate the suitability of the Evaluation 
Product for licensing on a for-fee basis.  You may acquire 
evaluation Software License Key(s) for Licensed Additional Modules.  
In such case, the Licensed Additional Modules are licensed to you 
subject to the terms of this "EVALUATION LICENSES" section.

2.3	Evaluation Product Warranty Disclaimer.  During the use of the 
Evaluation Product, the limited 90-day warranty referenced in 
Section 7.1 below is not applicable to you.  THE EVALUATION PRODUCT 
IS PROVIDED TO YOU "AS IS" WITHOUT WARRANTY OF ANY KIND, WHETHER 
EXPRESS, IMPLIED, STATUTORY, OR OTHERWISE.  VMWARE AND ITS 
LICENSORS BEAR NO LIABILITY FOR ANY DAMAGES RESULTING FROM USE (OR 
ATTEMPTED USE) OF THE EVALUATION PRODUCT THROUGH AND AFTER THE 
EXPIRATION DATE.

2.4	No Support.  VMware has no duty to provide support to you during 
your use of the Evaluation Product.

3.	GRANT AND USE RIGHTS FOR SOFTWARE.

3.1	License.  The Software is licensed, not sold.  Subject to the terms 
of this EULA, VMware hereby grants you a non-exclusive, non-
transferable license, without rights to sublicense, to use the 
object code of the Software for the purpose as set forth in the 
applicable documentation for the Software and to the extent 
permitted by your payment of applicable license fees under a VMware 
approved licensing model and/or your Software License Key subject 
to the software product specific terms specified in this EULA.  
Depending upon the model utilized to compute the applicable license 
fees paid by you to use the Software (whether per Processor, per 
Virtual Machine, per user, or any other VMware approved licensing 
model), an applicable Software License Key may limit your usage of 
the Software accordingly.  You may use the documentation 
accompanying the Software in connection with permitted uses of the 
Software.  If the Software is a version that you have converted or 
exchanged from a valid licensed prior version, you agree that by 
using the Software you will no longer use the prior version.  
VMware reserves the right to require the certification of the 
destruction of such previous version of the Software.


3.2	License Limitations.  You may not copy the Software except for a 
reasonable number of machine-readable copies of the Software for 
backup or archival purposes and except as expressly permitted in 
this EULA.  You may not remove any titles, trademarks or trade 
names, copyright notices, legends, or other proprietary markings on 
the Software.  You are not granted any rights to any trademarks or 
service marks of VMware.  VMware retains all rights not expressly 
granted to you in this EULA.

3.3	Restrictions.  You may not (i) sell, lease, license, sublicense, 
distribute or otherwise transfer in whole or in part the Software 
or the Software License Key to another party; (ii) provide, 
disclose, divulge or make available to, or permit use of the 
Software in whole or in part by, any third party (except Designated 
Administrative Access) without VMware's prior written consent; or 
(iii) modify or create derivative works based upon the Software.  
Except to the extent expressly permitted by applicable law, and to 
the extent that VMware is not permitted by that applicable law to 
exclude or limit the following rights, you may not decompile, 
disassemble, reverse engineer, or otherwise attempt to derive 
source code from the Software, in whole or in part.   You may use 
the Software to conduct internal performance testing and 
benchmarking studies, the results of which you (and not 
unauthorized third parties) may publish or publicly disseminate; 
provided that VMware has reviewed and approved of the methodology, 
assumptions and other parameters of the study.  Please contact 
VMware at benchmark@vmware.com to request such review.

3.4	GPL Software. You can redistribute and/or modify the GPL Software 
under the terms of the GPL.  You may obtain a copy of the source 
code corresponding to the binaries for the GPL Software (the "GPL 
Source Files") by downloading the GPL Source Files from VMware's 
Web site at http://www.vmware.com/download/open_source.html, or by 
sending a request, with your name and address, to Vmware at the 
address specified under the heading "Contact Information" below, in 
which case Vmware will mail a copy of the GPL Source Files to you 
on a CD or equivalent physical medium.  This offer to obtain a copy 
of the GPL Source Files is valid for three years from the date you 
acquired this Software product.

3.5	VMware Tools.  You may distribute the VMware Tools to any third 
party provided that (i) you do not modify the VMware Tools; (ii) 
you distribute the VMware Tools in object code format only and 
solely in conjunction with, and as part of, the Virtual Machine you 
create with the Software; (iii) you do not use VMware's name, logo 
or trademarks to market the Virtual Machine you create with the 
Software and (iv) you agree to indemnify, hold harmless, and defend 
VMware from and against any claims or lawsuits, including 
attorneys' fees, that arise or result from the use or distribution 
of the Virtual Machine you create.  Notwithstanding the foregoing, 
you may refer to VMware names, logos or trademarks to indicate that 
the Virtual Machine you create with the Software are compatible 
with or designed for use with the Software.

3.6	Licenses required for third-party software.  The Software enables 
you to run multiple instances of third-party guest operating 
systems and application programs. You are responsible for obtaining 
any licenses necessary to operate any such third-party software, 
including Guest Operating Systems.

3.7	Sample Programs.  The Software may include Sample Programs.  You 
may use and distribute Sample Programs under the terms set forth in 
the applicable Sample Programs files.  VMware does not provide 
support services for Sample Programs.

3.8	VMware License Programs.  VMware makes available VMware License 
programs (for e.g., VMware Academic License).  If you have received 
the Software pursuant to these VMware License programs, the then-
current terms and conditions posted on 
http://www.vmware.com/download/eula/vmtn.html
for that program shall apply for use of the products under such 
VMware License programs.

3.9	Audit Rights.	You will maintain accurate records as to your use of 
the Software as authorized by this EULA, for at least two (2) years 
from the last day on which support and subscription services 
("Services") expired for the applicable Software.  VMware, or 
persons designated by VMware, will, at any time during the period 
when you are obliged to maintain such records, be entitled to 
inspect such records and your computing devices, in order to verify 
that the Software is used by you in accordance with the terms of 
this EULA and that you have paid the applicable license fees and 
Services fees for the Software; provided that VMware may conduct no 
more than one (1) audit in any twelve (12) month period.  You shall 
promptly pay to VMware any underpayments revealed by any such 
audit.  Any such audit will be performed at VMware's expense during 
normal business hours, provided that you shall promptly reimburse 
VMware for the cost of such audit and any applicable fees if such 
audit reveals an underpayment by you of more than five percent (5%) 
of the amounts payable by you to VMware for the period audited.

4.	TITLE.  VMware retains all right, title, and interest in and to the 
Software and the Software License Key and in all related 
copyrights, trade secrets, patents, trademarks, and any other 
intellectual and industrial property and proprietary rights, 
including registrations, applications, renewals, and extensions of 
such rights.

5.	SUPPORT AND SUBSCRIPTION SERVICES NOT INCLUDED

VMware will not provide any support services under this EULA.  This 
EULA does not give you any rights to any updates or upgrades to the 
Software or to any extensions or enhancements to the Software 
developed by VMware at any time in the future.   VMware may offer 
support and subscription services separately.  If you have 
purchased VMware support and subscription services with the 
Software, these services are provided to you under the Support 
Contract Terms and Conditions posted on VMware's Web site at   
http://www.vmware.com/support/  and by accepting the terms of this 
EULA you are accepting these Support Contract Terms and Conditions.  
Any supplemental software code or related materials that VMware 
provides to you as part of any support and subscription services 
are to be considered part of the Software and are subject to the 
terms and conditions of this EULA.  VMware may use any technical 
information you provide to VMware for any VMware business purposes 
without restriction, including for product support and development. 
VMware will not use information in a form that personally 
identifies you.

6.	TERMINATION

6.1	Termination.  VMware may terminate this EULA immediately and 
without notice if you fail to comply with any term of this EULA.
  
6.2	Effect of Termination.  In the event of termination, you must 
destroy all copies of the Software and Software License Key.  In 
addition you must remove all copies of the Software, including all 
backup copies, from the Server and all computers and terminals on 
which it is installed.  From time to time, VMware may change the 
terms of this EULA.  VMware will notify you of such change.  Your 
continued use of the Software will indicate your agreement to the 
change.

7.	LIMITED WARRANTY AND LIMITATION OF LIABILITY

7.1	Limited Warranty. VMware warrants that the media, if any, on which 
the Software is delivered will be free of defects and that the Software 
will substantially conform to the description contained in the 
applicable end user documentation with respect to the particular 
Software licensed under this EULA in each case for a period of 90 days 
after the date of shipment of the Software License Key to you ("Warranty 
Period").  If during the Warranty Period the media is defective and the 
version of that Software is still commercially available, your sole 
remedy will be that VMware shall, at its option, repair or replace the 
defective media returned to VMware within the Warranty Period.  If you 
are returning a defective media, please email VMware at sales@vmware.com 
to request a Return Authorization number (RMA) and further instructions.  
If during the Warranty Period the Software does not substantially 
conform to the description contained in the applicable end user 
documentation, your sole remedy will be that VMware shall, at it option, 
correct the defects in the Software or refund the license fees you paid, 
if any, related to the Software provided that (a) the Software has been 
properly installed and used at all times and in accordance with the 
instructions in the applicable end user documentation; (b) no 
modification, alteration or addition has been made to the Software 
product by persons other than VMware or VMware's authorized 
representative; and (c) VMware receives written notice of the non-
conformity within ninety (90) days following shipment.  EXCEPT FOR THE 
PRECEDING EXPRESS LIMITED WARRANTY, TO THE MAXIMUM EXTENT PERMITTED BY 
APPLICABLE MANDATORY LAW, VMWARE AND ITS LICENSORS PROVIDE THE SOFTWARE 
WITHOUT ANY WARRANTIES OF ANY KIND, EXPRESS, IMPLIED, STATUTORY, OR IN 
ANY OTHER PROVISION OF THIS EULA OR COMMUNICATION WITH YOU, AND VMWARE 
AND ITS LICENSORS SPECIFICALLY DISCLAIM ANY IMPLIED WARRANTIES OF 
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AND NON-INFRINGEMENT.

7.2	LIMITATION OF LIABILITY. TO THE MAXIMUM EXTENT PERMITTED BY 
APPLICABLE MANDATORY LAW, IN NO EVENT WILL VMWARE AND ITS LICENSORS BE 
LIABLE FOR ANY LOST PROFITS OR BUSINESS OPPORTUNITIES, LOSS OF USE, 
BUSINESS INTERRUPTION, LOSS OF DATA, OR ANY OTHER INDIRECT, SPECIAL, 
INCIDENTAL, OR CONSEQUENTIAL DAMAGES UNDER ANY THEORY OF LIABILITY, 
WHETHER BASED IN CONTRACT, TORT, NEGLIGENCE, PRODUCT LIABILITY, OR 
OTHERWISE.  BECAUSE SOME JURISDICTIONS DO NOT ALLOW THE EXCLUSION OR 
LIMITATION OF LIABILITY FOR CONSEQUENTIAL OR INCIDENTAL DAMAGES, THE 
PRECEDING LIMITATION MAY NOT APPLY TO YOU.  VMWARE AND ITS LICENSORS' 
LIABILITY UNDER THIS EULA WILL NOT, IN ANY EVENT, EXCEED THE LICENSE 
FEES, IF ANY, PAID BY YOU FOR THE SOFTWARE LICENSED TO YOU UNDER THIS 
EULA. THE FOREGOING LIMITATIONS SHALL APPLY TO THE MAXIMUM EXTENT 
PERMITTED BY APPLICABLE LAW, REGARDLESS OF WHETHER VMWARE OR ITS 
LICENSORS HAVE BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES AND 
REGARDLESS OF WHETHER ANY REMEDY FAILS OF ITS ESSENTIAL PURPOSE. 

8.	GENERAL

8.1    Entire Agreement. This Agreement sets forth VMware's entire 
liability and your exclusive remedy with respect to the Software 
and supersedes the terms of any purchase orders and any other 
communications or advertising with respect to the Software. You 
acknowledge that this Agreement is a complete statement of the 
agreement between you and VMware with respect to the Software, and 
that there are no other prior or contemporaneous understandings, 
promises, representations, or descriptions with respect to the 
Software.  

8.2	Headings. Headings under this EULA are intended only for 
convenience and shall not affect the interpretation of this EULA.

8.3	Waiver and Modification.  No failure of either party to exercise or 
enforce any of its rights under this EULA will act as a waiver of 
those rights.  This EULA may only be modified, or any rights under 
it waived, by a written document executed by the party against 
which it is asserted.

8.4	Severability.  If any provision of this EULA is found illegal or 
unenforceable, it will be enforced to the maximum extent 
permissible, and the legality and enforceability of the other 
provisions of this EULA will not be affected.

8.5	Governing Law.  This EULA will be governed by California law and 
the United States of America, without regard to its choice of law 
principles. The United Nations Convention for the International 
Sale of Goods shall not apply.

8.6	Government Restrictions.  You may not export or re-export the Soft-
ware except in compliance with the United States Export 
Administration Act and the related rules and regulations and 
similar non-U.S. government restrictions, if applicable.  The 
Software and accompanying documentation are deemed to be 
"commercial computer software" and "commercial computer software 
documentation," respectively, pursuant to DFAR Section 227.7202 and 
FAR Section 12.212(b), as applicable.  Any use, modification, 
reproduction, release, performing, displaying, or disclosing of the 
Software by the U.S. Government shall be governed solely by the 
terms of this EULA.

8.7	Contact Information.  If you have any questions about this EULA, or 
if you want to contact VMware for any reason, please direct all 
correspondence to: VMware, Inc., 3401 Hillview Avenue, Palo Alto, 
CA 94304, United States of America or email info@vmware.com.

8.8	Other. VMware and VMTN are trademarks and/or registered trademarks 
of VMware, Inc. in the United States and/or various jurisdictions.  


9.	SOFTWARE PRODUCT SPECIFIC TERMS AND CONDITIONS

In addition to the above, the following Software products shall also be 
subject to the following terms and conditions set forth below.  In the 
event of any conflict between the following product-specific terms and 
conditions and the preceding sections, the product-specific terms and 
conditions shall control.

9.1	VMware Server: 
(a) Additional Definitions:
"Redistributable Components" means the Programming API library that may 
be provided in conjunction with the Software and licensed under the 
Redistributable Components product specific terms and conditions.
 "VirtualCenter Server Software" is a proprietary component of the 
Software which includes, without limitation, the management agent 
software that is installed on each managed Server and a proprietary Web 
Service Interface. 
"VMware Virtual Infrastructure Client Software" is a proprietary client 
component of the Software that provides the user interface and enables 
management of the Software.
"VMware WebAccess" is a proprietary component that provides console 
access to and management of Virtual Machines created with the Software.
"Web Service Interface" means a programmatic interface to perform 
management operations on Servers that are activated for management by 
the VirtualCenter Server Software through software programs written by 
you or a third party.
(b) Additional License Terms:
VMware grants you a nonexclusive, nontransferable license, without 
rights to sublicense, to (i) install or have installed a single instance 
of the Software and each Licensed Additional Module on a single Server, 
unless permitted by VMware to have multiple instances on a single Server 
or to have multiple instances on multiple Servers; (ii) use the Software 
and each Licensed Additional Module solely for information processing 
and computing purposes, including the hosting of computer application-
based services from a Virtual Machine and provision of such services via 
an internal or external network, provided such services may not consist 
of services to a third party that provide primarily computing or 
processing power (such as utility computing or grid computing) or any 
computer application-based service that is traded, rented, leased or 
sold on a Virtual Machine basis; and (iii) use and reproduce the VMware 
Virtual Infrastructure Client Software or VMware WebAccess (in object 
code form only) for the purposes of installation and operation on an 
unlimited number of your own internal computers or terminals solely for 
the purpose of accessing the Server on which the Software is installed; 
(iv) internally use and reproduce the Redistributable Components to 
create programs that interface with the Redistributable Components to 
manage Virtual Machines ("Your Management Programs"); and (v) internally 
use Your Management Programs solely for the purpose of managing Virtual 
Machines operated on VMware software products installed on your own 
internal Servers and computers. Subject to the above, each copy of the 
Software may not be used by any other person, whether or not such person 
is employed by or otherwise associated with your entity.  
Distributing the Software.  VMware Server is intended for your personal 
non-commercial use only. If you are interested in distributing the 
Software for internal or external use, promotion, review or as part of a 
solution, please apply now at http://www.vmware.com/go/distribution.   





Do you accept? (yes/no) yes

Thank you.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.31-22-server/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.31-22-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-22-server'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hashFunc.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-22-server'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The vmmon module loads perfectly into the running kernel.

None of the pre-built vmci modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmci module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmci module.

Building the vmci module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmci-only'
make -C /lib/modules/2.6.31-22-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-22-server'
  CC [M]  /tmp/vmware-config0/vmci-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmci-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vmci-only/linux/vmciKernelIf.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciEvent.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciQueuePair.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciResource.o
  LD [M]  /tmp/vmware-config0/vmci-only/vmci.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmci-only/vmci.mod.o
  LD [M]  /tmp/vmware-config0/vmci-only/vmci.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-22-server'
cp -f vmci.ko ./../vmci.o
make: Leaving directory `/tmp/vmware-config0/vmci-only'
The vmci module loads perfectly into the running kernel.

VMWare config patch VMCI!
`/tmp/vmware-config0/vmci-only/Module.symvers' -> `/tmp/vmware-config0/../Module.symvers'
None of the pre-built vsock modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vsock module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vsock module.

VMWare config patch VSOCK!
`/tmp/vmware-config0/../Module.symvers' -> `/tmp/vmware-config0/vsock-only/Module.symvers'
Building the vsock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vsock-only'
make -C /lib/modules/2.6.31-22-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-22-server'
  CC [M]  /tmp/vmware-config0/vsock-only/linux/af_vsock.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/util.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/vsockAddr.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vsock-only/vsock.mod.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-22-server'
cp -f vsock.ko ./../vsock.o
make: Leaving directory `/tmp/vmware-config0/vsock-only'
The vsock module loads perfectly into the running kernel.

Do you want networking for your virtual machines? (yes/no/help) [yes] 

Configuring a bridged network for vmnet0.

Please specify a name for this network. 
[Bridged] 

Your computer has multiple ethernet network interfaces available: eth0, eth1, 
virbr0. Which one do you want to bridge to vmnet0? [eth0] 

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

Do you wish to configure another bridged network? (yes/no) [no] 

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] 

Configuring a NAT network for vmnet8.

Please specify a name for this network. [NAT] 

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.5.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 172.16.5.0.

Do you wish to configure another NAT network? (yes/no) [no] 

Do you want to be able to use host-only networking in your virtual machines? 
[yes] 

Configuring a host-only network for vmnet1.

Please specify a name for this network. 
[HostOnly] 

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.143.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 192.168.143.0.

Do you wish to configure another host-only network? (yes/no) [no] 

None of the pre-built vmnet modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmnet module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.31-22-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-22-server'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/filter.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac.o
  CC [M]  /tmp/vmware-config0/vmnet-only/vnetEvent.o
  CC [M]  /tmp/vmware-config0/vmnet-only/vnetUserListener.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-22-server'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The vmnet module loads perfectly into the running kernel.

The default port : 902 is not free. We have selected a suitable alternative 
port for VMware Server use. You may override this value now.
Remember to use this port when installing remote clients on other machines.
Please specify a port for remote connections to use [903] 

WARNING: VMware Server has been configured to run on a port different from the 
default port. Please make sure to use this port when installing remote clients 
on other machines.

Please specify a port for standard http connections to use [8222] 

Please specify a port for secure http (https) connections to use [8333] 

The current administrative user for VMware Server  is ''.  Would you like to 
specify a different administrator? [no] 

Using root as the VMware Server administrator.

insserv: warning: script 'S01linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: warning: script 'linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: script vmware-core: service VMware already provided!
insserv: warning: script 'hal' missing LSB tags and overrides
insserv: script vmware-mgmt: service VMware already provided!
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: warning: script 'rsyslog-kmsg' missing LSB tags and overrides
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: script vmware-autostart: service VMware already provided!
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: There is a loop between service rsyslog and hwclock if stopped
insserv:  loop involving service hwclock at depth 4
insserv:  loop involving service sysklogd at depth 3
insserv: There is a loop between service rsyslog and inetd if stopped
insserv:  loop involving service inetd at depth 3
insserv:  loop involving service rsyslog at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop between service rsyslog and sysklogd if started
insserv:  loop involving service sysklogd at depth 3
insserv:  loop involving service hwclock at depth 2
insserv:  loop involving service rsyslog at depth 4
insserv: There is a loop between service hwclock and sysklogd if stopped
insserv: There is a loop between service rsyslog and inetd if stopped
insserv: exiting without changing boot order!
In which directory do you want to keep your virtual machine files? 
[/var/lib/vmware/Virtual Machines] 

The path "/var/lib/vmware/Virtual Machines" does not exist currently. This 
program is going to create it, including needed parent directories. Is this 
what you want? [yes] 

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  A05FE-FA3DX-U400H-4C0K8

Creating a new VMware VIX API installer database using the tar4 format.

Installing VMware VIX API.

In which directory do you want to install the VMware VIX API binary files? 
[/usr/bin] 

In which directory do you want to install the VMware VIX API library files? 
[/usr/lib/vmware-vix/lib] 

The path "/usr/lib/vmware-vix/lib" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

In which directory do you want to install the VMware VIX API document pages? 
[/usr/share/doc/vmware-vix] 

The path "/usr/share/doc/vmware-vix" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

The installation of VMware VIX API 1.6.2 build-203138 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall-vix.pl".

Enjoy,

--the VMware team

Starting VMware services:
   Virtual machine monitor done
   Virtual machine communication interface done
   VM communication interface socket family: done
   Virtual ethernet done
   Bridged networking on /dev/vmnet0 done
   Host-only networking on /dev/vmnet1 (background) done
   DHCP server on /dev/vmnet1 done
   Host-only networking on /dev/vmnet8 (background) done
   DHCP server on /dev/vmnet8 done
   NAT service on /dev/vmnet8 done
   VMware Server Authentication Daemon (background) done
   Shared Memory Available done
Starting VMware management services:
   VMware Server Host Agent (background) done
   VMware Virtual Infrastructure Web Access
Starting VMware autostart virtual machines:
   Virtual machines done

The configuration of VMware Server 2.0.2 build-203138 for Linux for this 
running kernel completed successfully.

Housekeeping...
Thank you for using the script!
Patch provided by: 
	Ramon de Carvalho Valle
	http://risesecurity.org
Script author: 
	Radu Cotescu
	http://radu.cotescu.com
```

---

### Post by CharlesA on 2010-09-26
Hi there,

Can you try running the vmware.sh that is inside the tar attached to my post [here]("http://ubuntuforums.org/showpost.php?p=9887167&postcount=6"). You just need to extract the tar and put in the same directory as the vmware.tar.gz.

That should get it installed and (semi) functional.

What version of Ubuntu are you using?

Also: What browser are you using to access the web interface? Is there a firewall in place?

---

### Post by BradleyAtkins on 2010-09-26
Hi Charles thanks for that.

I used your installer and it seemed to go without a hitch, the only difference being I used my UNIX account as the user rather than leaving it blank. I'll attach the screen output at the end of this.

My version of Ubuntu is: -

2.6.31-22-server

I have Google Chrome and IE on my XP laptop, IE wont handle it but Chrome will get as far as displaying the login screen.

I have Google Chrome and Firefox on my Ubuntu laptop. Trying Firefox I get the same problem, login prompt but then "web service unavailable".

Is this something silly like I am jumping the gun? I think the next step is to login and start configuring things via the UI but never having used vmware I am not sure if I am missing some other step first.

Thanks for the help with this, been at it every night for a week and have run out of hair to pull! :mad:

Sorry forgot to mention I have Zonelabs installed on the XP machine, not aware of any firewall on the Ubuntu laptop or server.

Here is the OP, I have deleted the ULA and licence but otherwise it's as is: -

```
root@poweredge:/tmp# ./vmware.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Extracting VMware Server archive...					Done!
VMware Server patched successfully!
Creating a new VMware Server installer database using the tar4 format.

Installing VMware Server.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the daemon files? 
[/usr/sbin] 

In which directory do you want to install the library files? 
[/usr/lib/vmware] 

In which directory do you want to install the manual files? 
[/usr/share/man] 

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware] 

The path "/usr/share/doc/vmware" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

The installation of VMware Server 2.0.2 build-203138 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall.pl".

Before running VMware Server for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this 
program to invoke the command for you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machinesfailed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agentfailed
Stopping VMware services:
   VMware Authentication Daemon done
   Virtual machine monitor done

You must read and accept the End User License Agreement to continue.
Press enter to display it. 

======================== DELETED ULA FOR CLARITY ======================

The answer "yes" is invalid.  It must be one of "y" or "n".

Do you accept? (yes/no) yes

Thank you.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.31-22-server/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.31-22-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-22-server'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:103:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:103:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config0/vmmon-only/linux/hostif.c:66:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/linux/hostif.c:3601:2: warning: #warning current->cred->fsuid = 0;
/tmp/vmware-config0/vmmon-only/linux/hostif.c:3608:2: warning: #warning current->cred->fsuid = fsuid;
/tmp/vmware-config0/vmmon-only/linux/hostif.c:3626:2: warning: #warning cap_lower(current->cred->cap_effective, CAP_SYS_RESOURCE);
/tmp/vmware-config0/vmmon-only/linux/hostif.c: In function â&#8364;&#732;HostIFReadUptimeWorkâ&#8364;&#8482;:
/tmp/vmware-config0/vmmon-only/linux/hostif.c:1862: warning: â&#8364;&#732;newUpBaseâ&#8364;&#8482; may be used uninitialized in this function
  CC [M]  /tmp/vmware-config0/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hashFunc.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config0/vmmon-only/common/task.c:50:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config0/vmmon-only/common/vmx86.c:43:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-22-server'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The vmmon module loads perfectly into the running kernel.

None of the pre-built vmci modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmci module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmci module.

Building the vmci module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmci-only'
make -C /lib/modules/2.6.31-22-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-22-server'
  CC [M]  /tmp/vmware-config0/vmci-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmci-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vmci-only/linux/vmciKernelIf.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciEvent.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciQueuePair.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciResource.o
  LD [M]  /tmp/vmware-config0/vmci-only/vmci.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmci-only/vmci.mod.o
  LD [M]  /tmp/vmware-config0/vmci-only/vmci.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-22-server'
cp -f vmci.ko ./../vmci.o
make: Leaving directory `/tmp/vmware-config0/vmci-only'
The vmci module loads perfectly into the running kernel.

VMWare config patch VMCI!
`/tmp/vmware-config0/vmci-only/Module.symvers' -> `/tmp/vmware-config0/../Module.symvers'
None of the pre-built vsock modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vsock module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vsock module.

VMWare config patch VSOCK!
`/tmp/vmware-config0/../Module.symvers' -> `/tmp/vmware-config0/vsock-only/Module.symvers'
Building the vsock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vsock-only'
make -C /lib/modules/2.6.31-22-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-22-server'
  CC [M]  /tmp/vmware-config0/vsock-only/linux/af_vsock.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/util.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/vsockAddr.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vsock-only/vsock.mod.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-22-server'
cp -f vsock.ko ./../vsock.o
make: Leaving directory `/tmp/vmware-config0/vsock-only'
The vsock module loads perfectly into the running kernel.

Do you want networking for your virtual machines? (yes/no/help) [yes] 

Configuring a bridged network for vmnet0.

Please specify a name for this network. 
[Bridged] 

Your computer has multiple ethernet network interfaces available: eth0, eth1, 
virbr0. Which one do you want to bridge to vmnet0? [eth0] 

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

Do you wish to configure another bridged network? (yes/no) [no] 

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] 

Configuring a NAT network for vmnet8.

Please specify a name for this network. [NAT] 

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.157.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 192.168.157.0.

Do you wish to configure another NAT network? (yes/no) [no] 

Do you want to be able to use host-only networking in your virtual machines? 
[yes] 

Configuring a host-only network for vmnet1.

Please specify a name for this network. 
[HostOnly] 

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.229.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 192.168.229.0.

Do you wish to configure another host-only network? (yes/no) [no] 

None of the pre-built vmnet modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmnet module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.31-22-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-22-server'
  CC [M]  /tmp/vmware-config0/vmnet-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/linux/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/linux/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/linux/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/linux/bridge.o
/tmp/vmware-config0/vmnet-only/linux/bridge.c:652:2: warning: #warning EHUD gotta figure out what this does and how to fix it: atomic_add(skb->truesize, &sk-
>sk_wmem_alloc);
  CC [M]  /tmp/vmware-config0/vmnet-only/linux/filter.o
  CC [M]  /tmp/vmware-config0/vmnet-only/linux/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/linux/smac_compat.o
  CC [M]  /tmp/vmware-config0/vmnet-only/linux/smac.o
  CC [M]  /tmp/vmware-config0/vmnet-only/linux/vnetEvent.o
  CC [M]  /tmp/vmware-config0/vmnet-only/linux/vnetUserListener.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-22-server'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The vmnet module loads perfectly into the running kernel.

Please specify a port for remote connections to use [902] 

Please specify a port for standard http connections to use [8222] 

Please specify a port for secure http (https) connections to use [8333] 

The current administrative user for VMware Server  is ''.  Would you like to 
specify a different administrator? [no] yes

Please specify the user whom you wish to be the VMware Server administrator
 brad

Using brad as the VMware Server administrator.

insserv: warning: script 'S01linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: warning: script 'linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: script vmware-core: service VMware already provided!
insserv: warning: script 'hal' missing LSB tags and overrides
insserv: script vmware-mgmt: service VMware already provided!
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: warning: script 'rsyslog-kmsg' missing LSB tags and overrides
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: script vmware-autostart: service VMware already provided!
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: There is a loop between service rsyslog and hwclock if stopped
insserv:  loop involving service hwclock at depth 4
insserv:  loop involving service sysklogd at depth 3
insserv: There is a loop between service rsyslog and inetd if stopped
insserv:  loop involving service inetd at depth 3
insserv:  loop involving service rsyslog at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop between service rsyslog and sysklogd if started
insserv:  loop involving service sysklogd at depth 3
insserv:  loop involving service hwclock at depth 2
insserv:  loop involving service rsyslog at depth 4
insserv: There is a loop between service hwclock and sysklogd if stopped
insserv: There is a loop between service rsyslog and inetd if stopped
insserv: exiting without changing boot order!
In which directory do you want to keep your virtual machine files? 
[/var/lib/vmware/Virtual Machines] 

The path "/var/lib/vmware/Virtual Machines" does not exist currently. This 
program is going to create it, including needed parent directories. Is this 
what you want? [yes] 

You have a pre-existing datastores.xml.  The new version will be created as 
/etc/vmware/hostd/NEW_datastores.xml.  Please check the new file for any new 
values that you may need to migrate to your current datastores.xml.

Do you want to enter a serial number now? (yes/no/help) [no] yes

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel: ============= ENTERED LICENCE HERE =======

Creating a new VMware VIX API installer database using the tar4 format.

Installing VMware VIX API.

In which directory do you want to install the VMware VIX API binary files? 
[/usr/bin] 

In which directory do you want to install the VMware VIX API library files? 
[/usr/lib/vmware-vix/lib] 

The path "/usr/lib/vmware-vix/lib" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

In which directory do you want to install the VMware VIX API document pages? 
[/usr/share/doc/vmware-vix] 

The path "/usr/share/doc/vmware-vix" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

The installation of VMware VIX API 1.6.2 build-203138 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall-vix.pl".

Enjoy,

--the VMware team

Starting VMware services:
   Virtual machine monitor done
   Virtual machine communication interface done
   VM communication interface socket family: done
   Virtual ethernet done
   Bridged networking on /dev/vmnet0 done
   Host-only networking on /dev/vmnet1 (background) done
   DHCP server on /dev/vmnet1 done
   Host-only networking on /dev/vmnet8 (background) done
   DHCP server on /dev/vmnet8 done
   NAT service on /dev/vmnet8 done
   VMware Server Authentication Daemon (background) done
   Shared Memory Available done
Starting VMware management services:
   VMware Server Host Agent (background) done
   VMware Virtual Infrastructure Web Access
Starting VMware autostart virtual machines:
   Virtual machines done

The configuration of VMware Server 2.0.2 build-203138 for Linux for this 
running kernel completed successfully.
```

---

### Post by CharlesA on 2010-09-26
Were all those warnings there when you tried to do the initial install?

I wrote up that script to work with 10.04, but it should work with older versions, but I haven't tested it with them.

Have you tried IE? I've had problems accessing the webUI using Firefox before.

EDIT: I ran the install on an Ubuntu 10.04 VM and it seemed to work. I was able to access the WebUI even with those warnings during compiling.

Note: I was using IE on WinXP.

---

### Post by BradleyAtkins on 2010-09-26
Hi Charles

My Ubuntu Laptop is running 10.04 but the server is running 64 bit server edition.

uname -r gives 2.6.31-22-server

Is that my problem I wonder, all of the how to's I have come across seem to refer to the desktop editions.

My problem with trying to install as per the instructions in the documentation is that I get error messages saying modules won't compile. I think it was vmnet from memory.

I ended up here because I was Googling the errors I was getting and they all seemed to suggest I needed the patch applied to the install.

Yes the warnings have been present before, can't say I understand them. Searching around on the Web seems to suggest this is a kernel issue around a dependency-based boot order. Most people seem to think this is not a problem but I haven't found anything posted specific to installing vmware.

Maybe I should try rebuilding the server with a different OS, maybe Red Hat or something.

If anyone knows of a version of Linux Server vmware will definitely install on I would be glad to hear about it.

I can't get IE to connect, keeps complaining about the certificate even when I add the site as a trusted exception. :(

Thanks for the input

---

### Post by CharlesA on 2010-09-26
It's strange, 10.04 should be using kernel 2.6.32-34-server.

Do you have anything important of the current server? You could wipe it and install 10.04.1 and then install vmware server using the stuff from the tar I posted.

I've done that successfully.

Just be sure to tell it to use your account during install, else it'll use root (which is locked in Ubuntu by default)

As for IE: I just tell it to proceed anyway, and don't bother trying to add an exception.

Here's what my uname -r says: 2.6.32-24-server

---

### Post by BradleyAtkins on 2010-09-26
Hi Charles

I cam across a note towards the bottom of this page: -

[https://help.ubuntu.com/community/VMware/Server]("https://help.ubuntu.com/community/VMware/Server")

"If you are using the server edition then you also need to install the following 3 X libraries and their dependencies."

libxtst6
libxt6
libxrender1

```
sudo aptitude install libxtst6 libxt6 libxrender1
```

I did install these packages and the error changed to one saying I couldn't be authenticated and needed to contact the administrator.

I then tried removing vmware and reinstalling it with these new packages in place and find that the installer won't run because it says the headers are no longer compatible with my running kernel.

So I think I will rebuild it anyway as I must have chewed things up by now trying all of these different things out. Not tonight though as I am knackered.

Am I right in saying that the user should be a local user on the server, not a domain user or anything? I have this server on my home network with no domain defined.

10.04.1? I will try to find a download and install it.

Thanks for all this help

---

### Post by CharlesA on 2010-09-26
Interesting. I didn't know that.

When you installed vmware did you enter your username to be allowed access? Otherwise it'll use root, which is locked, meaning you can't authenticate using root.

The user you want is someone on the local machine. I use my own user account

So when it asked for:

```
Please specify the user whom you wish to be the VMware Server administrator
```

Just specify your username. :)

---

### Post by BradleyAtkins on 2010-09-27
Yes it is buried quite far down the page.

I guess it used to be near the top. The page looks like it has had amendments added to the top as new releases have come along.

I don't know who maintains that page but it would be better to add a prereqs section for server edition near the top I think.

I am now looking for the right build to download for an Intel 64bit CPU and will rebuild it over the weekend.

Cheers

---

### Post by CharlesA on 2010-09-27
> **BradleyAtkins said:**
> Yes it is buried quite far down the page.

I guess it used to be near the top. The page looks like it has had amendments added to the top as new releases have come along.

I don't know who maintains that page but it would be better to add a prereqs section for server edition near the top I think.

I am now looking for the right build to download for an Intel 64bit CPU and will rebuild it over the weekend.

Cheers

You'd use Ubuntu Server x64:

[http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-server-amd64.iso](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-server-amd64.iso)

:)

---

### Post by BradleyAtkins on 2010-09-29
Many Thanks Charles, great to be able to report a successful login to the Web Access page. :P

No idea if it works of course and I dare say I will be asking more questions now I have it installed.

One funny, after installing 10.04.1 I didn't need to do: -

```
sudo aptitude install libxtst6 libxt6 libxrender1
```

Don't know if this had anything to do with me selecting LAMP as an install option??

So the steps I eventually took: -

```
1)	Set BIOs to enable hardware accelleration.

2)	Fresh install of Ubuntu Server Edition 10.04.1 - Options: -
	* Installed open SSH
	* Installed LAMP
3)	Installed sudo apt-get install build-essential

4)	sudo apt-get install linux-headers-`uname -r`

Steps 3 and 4 reported problems with texlive (whatever that is) so: -

5)	sudo apt-get install texlive-base

6)	Uploaded and moved to /tmp: -
	vmware.tar.gz
	VMware-server-2.0.2-203138.x86_64.tar.gz

7)	Untarred vmware.tar.gz and ran vmware.sh


```

After accepting all defaults I could log in with the usual certificate warnings and now have a UI to get to grips with.

Cheers

I owe you one

---

### Post by CharlesA on 2010-09-29
Heh. I didn't install any of those packages either when I installed VMware on 10.04.1, which is why I was a bit surprised there was mention of it. The only thing installed was Openssh server.

Hope the script helped out a bit.

Glad it's working for you now. :)

EDIT: Sidenote: I don't recall having to install build-essential or the linux headers, but in my script, it installs GCC, to compile the kernel modules. *shrugs*

---

### Post by HermanAB on 2010-09-30
Hmm, the problem is that you are trying to install VMware's worst product ever.  Server 2.x is best avoided and is really only for masochists.  You should either use VMware Workstation, or VMware Player.

---

### Post by fjgaude on 2010-09-30
> **HermanAB said:**
> Hmm, the problem is that you are trying to install VMware's worst product ever.  Server 2.x is best avoided and is really only for masochists.  You should either use VMware Workstation, or VMware Player.

Well, do you have Player 3.1.2 working with 10.04? If so, how did you do it?

Thanks!

---

### Post by BradleyAtkins on 2010-09-30
> **HermanAB said:**
> Hmm, the problem is that you are trying to install VMware's worst product ever.  Server 2.x is best avoided and is really only for masochists.  You should either use VMware Workstation, or VMware Player.

Hi Herman

I suspect you are right. :)

I haven't tried any of their products before but know I have seen server used commercially and so want to get to grips with it. My contract ran out today and I'm looking for work. Being able to install and administer server is something I can put on my CV.

I'll leave out the references to masochism though :)

One further pain I had today was trying to install XP Pro 64 as a guest OS I found I could not enter the product key, keys were all over the place.

Problem was I had a USB keyboard plugged into the server and had enabled USB device on the VM. Instant conflict! :) 

I'll get there...

---

### Post by BradleyAtkins on 2010-09-30
Hi Charles

Oh the pain :)

Knew I shouldn't have marked this as solved!

I got as far as installing XP Pro 64 as a guest only to find it complaining I had no network card. The UI reckoned there was one and that it was connected.

I tried re-running the config tool and every time I do I get this: -

```
sudo /usr/bin/vmware-config.pl
The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmci
vmnet
vmmon

I.e. - 'rm /lib/modules/2.6.32-24-server/misc/<ModuleName>.{o,ko}'

Execution aborted.
```

This happens every time I run the tool. If I remove the modules it recompiles them and then complains its not right next time I run it.

Now I am back to the web service not available error. sigh :(

Seems like this is just not stable on the server edition of Ubuntu.

Is there a 64bit Desktop version I can try?

---

### Post by CharlesA on 2010-09-30
The only one I can think of is VMware player or VMware workstation, as Herman suggested.

I've not really used VMware server since I've ran into problems with it that I don't have with virtualbox.

IMHO it's more of a pain in the butt then VBox, but that could be because I'm not used to it.

---

### Post by curioshop on 2010-10-01
I have been trying to get vmware server 2.0.2 running for a couple of days on ubuntu 10.04.  It is installed and i ostensibly have some machines running.  The web ui works ok, but slow.  For firefox you have to enable ssl v2 in firefox's about:config page.  However there are other problems.  There is no vmrc plug in for google chrome, and the one for firefox (3.6, at least) does not launch from firefox.  here are some instructions for launching vmrc from the command line.  unfortunately, i'm still sol because none of my VMs will get domain names or IP addresses.  I think I had 1 get an IP yesterday, but maybe thats a false memory, because today I have tried many things and none of them have worked.  vmware's dhcp server says it has handed out some leases, but the addresses listed are dead.

---

### Post by BradleyAtkins on 2010-10-03
Well that's interesting.

I got as far as installing XP Pro 64 and was trying to configure the networking when I lost the UI again and couldn't get it back.

Frustratingly, after rebuilding the server in exactly the same way and reinstalling VMWare I couldn't get access to the UI at all and so had slipped back a stage.

In your post you say: -

```
here are some instructions for launching vmrc from the command line.
```

But you don't seem to have included them. Can you give me the details and I will try them on my server?

Thanks

---

### Post by dcstar on 2010-10-04
> **BradleyAtkins said:**
> Well that's interesting.

I got as far as installing XP Pro 64 and was trying to configure the networking when I lost the UI again and couldn't get it back.

Frustratingly, after rebuilding the server in exactly the same way and reinstalling VMWare I couldn't get access to the UI at all and so had slipped back a stage.
........

Accessing the VMware Server VMs UI requires older versions of Firefox - it will not work with the latest one that Ubuntu provides.

I set up Server on a 10.04 platform a few weeks ago (jumping through all the hoops with patch files etc.) and got stuck on this last issue, manually installing an older version of FF fixed it.

If you don't need the VMware Server features of running VMs automatically then don't use it, use VMware Player.

---

### Post by BradleyAtkins on 2010-10-05
Thanks David

I downloaded Firefox 3.5.13 onto my XP Laptop but it just hangs trying to connect.

What version did you use?

Brad

---

### Post by BradleyAtkins on 2010-10-06
Well I seem to have arrived at a fairly stable install. Early days but I can now log in to the UI even after a reboot of the server.

After a lot of research and reading of posts by equally confused people like myself I began to pick up on a theme of user related issues. So on a hunch I decided to ignore the installation instructions on the subject of installing as root: -

```
1 Log in with the user name you plan to use when running VMware Server.
2 In a terminal window, use the command to become root, for example:
su -
On Ubuntu hosts, use the command:
sudo -s -H
```

I decided instead to log in as the user that was going to administer the UI and run the installer using the sudo command. 

In other words, instead of using sudo to change to root and doing the install; I installed as the VM administrator (The Linux account that would be logging in to the UI) with elevated permissions via sudo.

I now seem to be able to log into the UI and can even do so after the server has been rebooted.

I will try setting up some virtual machines and will repost if it all goes flaky again, but for now this seems to have been resolved (at last).

PS One other thing I did was set the localhost entry in /etc/hosts to the loopback IP instead of the actual IP just before reinstalling as above. Not sure if it is significant or not.

---

### Post by CharlesA on 2010-10-06
Thanks for the info.

I wonder if that was the reason I haven't ran into [s]any problems[/s] problems when I installed VMware Server last, since I was just running the scripts with "sudo" instead of at a root prompt.

There shouldn't be any difference tho. As long as you don't accept the default for the "administrator" it should let you login fine.

---

### Post by rbishop on 2010-10-06
I was having the same problem with my install of vmware server2.0.2.  I finally reinstalled Ubuntu from scratch and only installed the SSH server with the installer.  After that I updated everything.  Then I downloaded and installed VMWare Server 2.0.2 and installed.  I was able to login and get it all working.  For some reason I was having tons of troubles with it when I had installed a LAMP server on Ubuntu....Go figure.

---

### Post by BradleyAtkins on 2010-10-06
> **rbishop said:**
> I was having the same problem with my install of vmware server2.0.2.  I finally reinstalled Ubuntu from scratch and only installed the SSH server with the installer.  After that I updated everything.  Then I downloaded and installed VMWare Server 2.0.2 and installed.  I was able to login and get it all working.  For some reason I was having tons of troubles with it when I had installed a LAMP server on Ubuntu....Go figure.

Yes my worry is that this is all coincidence and has nothing to do with the user I installed under. I certainly had lots of probs regardless of whether I had lamp installed or not. I also managed to get as far as installing a guest OS before, but then it all went skew whiff again.

Will post here again though if it does fall apart.

On the plus side I am now very quick at installing Linux! :)

---

