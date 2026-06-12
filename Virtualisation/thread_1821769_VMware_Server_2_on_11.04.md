---
title: "VMware Server 2 on 11.04"
date: 2011-08-09
forum: Virtualisation
---

### Post by pmorrone on 2011-08-09
I have been trying to install VMware Server 2 on Ubuntu 11.04 Server edition.  I researched a bit and found a forum that discussed some of the installation solution but run into an error.  The solution is to do the following (Solution provided by:Toddkaufmann).  

 					Originally Posted by **toddkaufmann** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11069977#post11069977") 				
 				[I]"I've seen some conflicting instructions here, but this is what worked for me. 
I have the 11.04 Server, did an update to get the latest kernel and updates, and rebooted so I now have: 
2.6.38-10-server #46-Ubuntu SMP Tue Jun 28 16:31:00 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux 

I may have added some extra packages (like kernel sources) in initial  attempts to get this working, but I think the raducotescu script handles  getting the packages you need. 

1. Get VMware-server-2.0.2-203138.x86_64.tar.gz from the VMware site, register for free license key(s) etc. 
2. At [https://github.com/raducotescu/vmwar...ee/release-1.6]("https://github.com/raducotescu/vmware-server-linux-2.6.3x-kernel/tree/release-1.6")  there is a 'Downloads' button near the top; click it to get a popup  that will let you select a tar.gz or zip file and download (the choice  is yours). Put it in the same directory. 
3. Unpack the archive; for example, 
unzip raducotescu-vmware-server-linux-2.6.3x-kernel-release-1.6-0-gbb26dce.zip 
4. Run the script: 
./raducotescu-vmware-server-linux-2.6.3x-kernel-e26b34e/vmware-server-2.0.x-kernel-2.6.3x-install.sh 

This takes care of unpacking the VMware archive, patching scripts, other  pre-requisites as well (I think), and starts up the installer. 

From here, it was just Enter, Enter, Enter, ... the whole way, and everything built without a problem. "[/I]
 
When I tried to install the file I ran received the problem message below:

phil@ubuntu:~$ ./Downloads/raducotescu-vmware-server-linux-2.6.3x-kernel-e26b34e/vmware-server-2.0.x-kernel-2.6.3x-install.sh
This script must be run as root!
phil@ubuntu:~$ sudo  ./Downloads/raducotescu-vmware-server-linux-2.6.3x-kernel-e26b34e/vmware-server-2.0.x-kernel-2.6.3x-install.sh
[sudo] password for phil: 
There is no archive containing VMware Server in the path you indicated!

Can anyone help?

---

### Post by Jake.Debord on 2011-08-10
> **pmorrone said:**
> I have been trying to install VMware Server 2 on Ubuntu 11.04 Server edition.  I researched a bit and found a forum that discussed some of the installation solution but run into an error.  The solution is to do the following (Solution provided by:Toddkaufmann).  

                     Originally Posted by **toddkaufmann**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11069977#post11069977")                 
                 [I]"I've seen some conflicting instructions here, but this is what worked for me. 
I have the 11.04 Server, did an update to get the latest kernel and updates, and rebooted so I now have: 
2.6.38-10-server #46-Ubuntu SMP Tue Jun 28 16:31:00 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux 

I may have added some extra packages (like kernel sources) in initial  attempts to get this working, but I think the raducotescu script handles  getting the packages you need. 

1. Get VMware-server-2.0.2-203138.x86_64.tar.gz from the VMware site, register for free license key(s) etc. 
2. At [https://github.com/raducotescu/vmwar...ee/release-1.6]("https://github.com/raducotescu/vmware-server-linux-2.6.3x-kernel/tree/release-1.6")  there is a 'Downloads' button near the top; click it to get a popup  that will let you select a tar.gz or zip file and download (the choice  is yours). Put it in the same directory. 
3. Unpack the archive; for example, 
unzip raducotescu-vmware-server-linux-2.6.3x-kernel-release-1.6-0-gbb26dce.zip 
4. Run the script: 
./raducotescu-vmware-server-linux-2.6.3x-kernel-e26b34e/vmware-server-2.0.x-kernel-2.6.3x-install.sh 

This takes care of unpacking the VMware archive, patching scripts, other  pre-requisites as well (I think), and starts up the installer. 

From here, it was just Enter, Enter, Enter, ... the whole way, and everything built without a problem. "[/I]
 
When I tried to install the file I ran received the problem message below:

phil@ubuntu:~$ ./Downloads/raducotescu-vmware-server-linux-2.6.3x-kernel-e26b34e/vmware-server-2.0.x-kernel-2.6.3x-install.sh
This script must be run as root!
phil@ubuntu:~$ sudo  ./Downloads/raducotescu-vmware-server-linux-2.6.3x-kernel-e26b34e/vmware-server-2.0.x-kernel-2.6.3x-install.sh
[sudo] password for phil: 
There is no archive containing VMware Server in the path you indicated!

Can anyone help?


as that error suggests I would check that folder to see if in fact that is where the file exists for you

---

### Post by pmorrone on 2011-08-10
> **Jake.Debord said:**
> as that error suggests I would check that folder to see if in fact that is where the file exists for you

You are correct.  I was trying to run the command in the GUI rather than the terminal and as a result the script didn't properly find the archive.  I ran the script in the terminal and dictated the path that was appropriate and it worked properly.  Thanks for the help.

---

### Post by riddie on 2011-08-19
Thanks for posting, that worked for me, had to edit the name of the package in the install script as it wasn't picking it up though:

VMWARE_ARCHIVE=`ls "$VMWARE_HOME" 2> /dev/null | egrep "^(VMware-server-2.0.[0-9]-)[0-9]*.[A-Za-z0-9_]*.tar.gz"`

Changed to:

VMWARE_ARCHIVE=`ls "$VMWARE_HOME" 2> /dev/null | grep "Name of package.tar.gz"

---

