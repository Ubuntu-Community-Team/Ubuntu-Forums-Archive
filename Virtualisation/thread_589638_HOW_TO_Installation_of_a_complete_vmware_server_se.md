---
title: "HOW TO: Installation of a complete vmware server setup"
date: 2007-10-24
forum: Virtualisation
---

### Post by TuxCrafter on 2007-10-24
HOW TO: Installation of a complete vmware server setup

#Version: 0.0.5
#Date: 03-11-07
#Description:  Installation of a complete vmware server setup

This script has both community support and commercial support.

Please post all your feedback about this script so I can continuously keep improving it.

I hope this script will help a lot of people! :KS

Version 0.0.4 had 184 views

---

### Post by K.Mandla on 2007-10-26
Moved to Virtualization.

---

### Post by djRob on 2007-10-27
I am bumping up this post because I see people have problems installing VMWare server on Gutsy. I used this script without problems, although I downloaded VMWare server manually and I had already installed VirtualBox.

---

### Post by danpre on 2007-10-28
> **TuxCrafter said:**
> HOW TO: Installation of a complete vmware server setup

#Version:       0.0.4
#Date:          23-10-07
#Description:    Installation of a complete vmware server setup

This script has both community support and commercial support.

Please post all your feedback about this script so I can continuously keep improving it.

I hope this script will help a lot of people! :KS

I can confirm:
NO PROBLEMS AT ALL!
Thx for this great script!

DANIeL

---

### Post by tilapia on 2007-10-28
Awesome script. Thanks a lot! I've just used this to install Vmware Server on Gutsy 7.10 with no problems whatsoever. 

Cheers!

---

### Post by gb64 on 2007-10-28
Thanks for script!
Questions:

1)  Will changing the VM Player line from present line
    VMware-player-2.0-45731.tar.gz 

to newer:  VMware-player-2.0.2-59824.i386.tar.gz
work OK, or is there some known problem?

2) In next section after that, should we change:
    vmware-any-any-update113.tar.gz 
to the newer  114 ?

---

### Post by TwiceOver on 2007-10-28
Works great as-is for me.  Didn't change any settings.

---

### Post by netegalkaka on 2007-10-29
Hi,

I didn't run your script yet because I think i's for Gutsy 32 bit version; I'd like to know if someone could adapt this script to Gutsy 64 bit?

Many thanks by advance and sorry for my bad english.

:guitar:

---

### Post by netegalkaka on 2007-10-29
Hi,

I didn't run your script yet because I think iti's for Gutsy 32 bit version; I'd like to know if someone could adapt this script to Gutsy 64 bit?

Many thanks by advance and sorry for my bad english.

:guitar:

---

### Post by TuxCrafter on 2007-10-29
> **gb64 said:**
> Thanks for script!
Questions:

1)  Will changing the VM Player line from present line
    VMware-player-2.0-45731.tar.gz 

to newer:  VMware-player-2.0.2-59824.i386.tar.gz
work OK, or is there some known problem?

2) In next section after that, should we change:
    vmware-any-any-update113.tar.gz 
to the newer  114 ?

Hi, thanks for the question, the script supports vmware server and not vmware player. The player section is indeed commented out. You can in fact uncomment it and use it to install vmware player. You will indeed have to update the section to the latest version of the needed tools. Hope it helps.

---

### Post by TuxCrafter on 2007-10-29
> **netegalkaka said:**
> Hi,

I didn't run your script yet because I think iti's for Gutsy 32 bit version; I'd like to know if someone could adapt this script to Gutsy 64 bit?

Many thanks by advance and sorry for my bad english.


Find me a link to the 64 bit version of the needed tools and i will adjust my script to support both 64 bit as 23 bit. You can of course install the 32 bit on a 64 bit system, in will also work.

---

### Post by Cochise on 2007-10-29
worked perfectly thanks

---

### Post by enavarro on 2007-10-29
Worked for me as well. Used on a Dell M90.

---

### Post by gb64 on 2007-10-29
TuxCrafter - 
Thanks for the response. Of course, I did not notice the section for the player was commented out. I see from the documentation on the server that it, like the Workstation, allows running the VMs without using the player.
Great work!

---

### Post by netegalkaka on 2007-10-29
> **TuxCrafter said:**
> HOW TO: Installation of a complete vmware server setup

#Version:       0.0.4
#Date:          23-10-07
#Description:    Installation of a complete vmware server setup

This script has both community support and commercial support.

Please post all your feedback about this script so I can continuously keep improving it.

I hope this script will help a lot of people! :KS

How to run this script?

Sorry for my dumb question, I'm a new Ubuntero :lolflag:

---

### Post by gstark on 2007-10-29
I hit the same thing.  If you are having trouble running it right click the file and go to properties and permissions.  Make sure to check the box so that it runs as an application

then from a terminal use:

./vmware


-Greg

---

### Post by koenn on 2007-10-29
nice. 

2 suggestions :

1/ backticks are depreciated - you can replace them with something like 
```
$(uname -r)
```

2/
you might want to put variables at the beginning of the script to hold data that can change over time. If they're all at the start of the script, it's easier to update it them without reading through the whole script. 
eg
```

# initial comments
#
DOWNLOADSRV=http://download3.vmware.com/software/vmserver
VMSERVER="VMware-server-1.0.4-56528.tar.gz"


(...)
        if .... 
        then
            wget $DOWNLOADSRV/$VMSERVER
        fi
        tar -xzf $file

(...)

```

---

### Post by TuxCrafter on 2007-10-29
> **netegalkaka said:**
> How to run this script?
Sorry for my dumb question, I'm a new Ubuntero 

Read the info in the script by and especially the command option.

---

### Post by gb64 on 2007-10-29
TuxCrafter - You da man!

Script worked perfectly. Good Work. I do agree you might re-write with variables as suggested above by other poster....it just seems like a good idea for next version.

I also voted in your poll. Thanks!

---

### Post by TuxCrafter on 2007-10-30
> **gb64 said:**
> TuxCrafter - You da man!

Script worked perfectly. Good Work. I do agree you might re-write with variables as suggested above by other poster....it just seems like a good idea for next version.

I also voted in your poll. Thanks!

Ok thanks for the feedback, when vmware releases it's next version I will include vmware player and vmware server as an installation option in the script.

---

### Post by pyropir on 2007-10-31
the script didn't work for me since I'm behind a proxy. This isn't a big problem though, I'll try again when I get home.

---

### Post by mrhirsh on 2007-11-02
I was using VMware Server just fine . . . then I upgraded to Gutsy.  
Got the "Can't power on" after that when attempting to start.

Followed a couple of other suggestions in various fora.

I am running 64 bit Ubuntu on AMD powered machine.  Will run ining this script work on my machine?  When it asks about removing previous VM installations, will I lose the data that is in my virtual machine?

THanks, I am just trying not to screw it up more than I have.

---

### Post by techpr on 2007-11-02
worked fine, thanks!

---

### Post by koenn on 2007-11-02
> **mrhirsh said:**
> I was using VMware Server just fine . . . then I upgraded to Gutsy.  
Got the "Can't power on" after that when attempting to start.

Followed a couple of other suggestions in various fora.

I am running 64 bit Ubuntu on AMD powered machine.  Will run ining this script work on my machine?  When it asks about removing previous VM installations, will I lose the data that is in my virtual machine?

THanks, I am just trying not to screw it up more than I have.
This is probably because you've had a kernel upgrade with Gutsy. 
IIRC, you have to get the new header files, then (possibly) run the vmware install script again (it remembers your config and will offer it as defaults).
you can get the relevant commands from the script in the OP. 
Your virual machines normally don't get deleted, during an upgrade. Make a backup if you're unsure.

---

### Post by TuxCrafter on 2007-11-03
> **mrhirsh said:**
> I was using VMware Server just fine . . . then I upgraded to Gutsy.  
Got the "Can't power on" after that when attempting to start.

Followed a couple of other suggestions in various fora.

I am running 64 bit Ubuntu on AMD powered machine.  Will run ining this script work on my machine?  When it asks about removing previous VM installations, will I lose the data that is in my virtual machine?

THanks, I am just trying not to screw it up more than I have.

It is not the intention to remove your virtual machine files only the program. However just to be sure check the location of your files to the locations the script removes!

---

### Post by mrhirsh on 2007-11-03
Your script worked beautifully.  I feel like I see the light at the end of the tunnel (and, for once, It's not an oncoming train).

One more question, I think:

1.  When I opened my newly created VMware, the previously installed XP Pro VM was not there.  I've found those files (I think) under var/lib/Virtual Machines.

2.  How do I move that setup (with all the data that I hope is in there) to where my new VMware server will be able to use it?  Do I just "copy" the XP Pro folder and then "paste" it somewhere else?

THanks,

---

### Post by TuxCrafter on 2007-11-03
> **mrhirsh said:**
> Your script worked beautifully.  I feel like I see the light at the end of the tunnel (and, for once, It's not an oncoming train).

One more question, I think:

1.  When I opened my newly created VMware, the previously installed XP Pro VM was not there.  I've found those files (I think) under var/lib/Virtual Machines.

2.  How do I move that setup (with all the data that I hope is in there) to where my new VMware server will be able to use it?  Do I just "copy" the XP Pro folder and then "paste" it somewhere else?

THanks,

move your *.vmx and *.vmdk files to you personal diretory. 

Make sure you run vmware as normal user and not as root.

You can open your *.vmx files from the vmware server application menu.

---

### Post by TuxCrafter on 2007-11-03
I just released a improved version 0.0.5 of the script with more  hardcoding instead of softcoding, as some of you requested. (the script view count will be automatically cleared)

---

### Post by TuxCrafter on 2007-11-09
To solve that usb devices will not be visible for vmware

sudo geany /etc/init.d/mountdevsubfs.sh

Starting at line 42 uncomment these:
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

sudo /etc/init.d/mountdevsubfs.sh stop
sudo /etc/init.d/mountdevsubfs.sh start
sudo /etc/init.d/vmware restart

---

### Post by Cochise on 2007-11-11
i used this script to install vmware server, just wondering how do i go about removing it?

---

### Post by TuxCrafter on 2007-11-11
> **Cochise said:**
> i used this script to install vmware server, just wondering how do i go about removing it?
rerun the script choice Y for all uninstall questions and N to all install questions :-D

---

### Post by stkrzysiak on 2008-05-08
First off, TuxCrafter, thank you for this awesome script.  I have had Vmware Server running on one computer or another over the past five years.  Despite all those successful setups, vmware was always still something I dreaded having to reconfigure.  This script really makes the process painless...usually...
    I upgraded to 8.04 and I believe that is why Vmware stopped working on my computer.  So I thought no big deal, I'll just do a reinstall using your script.  I had an older version, tried it, it failed, so I dl'd the new one, tried it and it failed as well.  I am sure I can dig on how to fix this on the net, which I will, but I thought you might want to see my log.

Thanks again for the great script....


Log follows:




Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:48:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

did you encounterd any compilation error[y/N]? 
downloading vmware any patch, please standby...
--16:20:27--  [http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz)
           => `vmware-any-download.tar.gz'
Resolving platan.vc.cvut.cz... 147.32.240.81
Connecting to platan.vc.cvut.cz|147.32.240.81|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:20:28 ERROR 404: Not Found.


gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors
./vmware.sh: line 108: cd: /home/stk/vmware-server-2.6.24-16-generic/vmware-any-any-update114: No such file or directory
sudo: ./runme.pl: command not found
do you want to remove temporary installation data[Y/n]?

---

### Post by TuxCrafter on 2008-05-08
Hi, thank you for your message, I will look at the problem tomorrow and create a new script.

---

### Post by TuxCrafter on 2008-05-10
[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

vmware website is down for this weekend so you have to wait a bid longer...

---

