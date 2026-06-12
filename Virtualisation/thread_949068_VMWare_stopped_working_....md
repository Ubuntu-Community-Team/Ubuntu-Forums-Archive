---
title: "VMWare stopped working ..."
date: 2008-10-15
forum: Virtualisation
---

### Post by cwmoser on 2008-10-15
My VMWare stopped working.
When I run vmware from the command line, it states I need to run:

/usr/bin/vmware-config.pl

When I run this, I am purplexed with this:

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

I note that /usr/src/linux/include directory no longer exists.
I try this:
  /usr/src/linux-headers-2.6.24-21/include
... but it complains that "linux/version.h" is missing.

Any ideas?  Was this because of a recent update?

Thanks

Carl

---

### Post by Duffy on 2008-10-15
Same problem here. After Ubuntu did a major package upgrade today (major in that it required a reboot which it rarely does), VMware stopped working.

---

### Post by cjtech on 2008-10-15
My vmware is still running fine, however im on 8.10BETA

---

### Post by Mister.Vash on 2008-10-15
Try /lib/modules/2.6.24-21-generic/build/include

---

### Post by cwmoser on 2008-10-16
> **Mister.Vash said:**
> Try /lib/modules/2.6.24-21-generic/build/include


That does not work nor any other folders in /lib/modules.

Hmmm.  Anyone solve this?

Carl

---

### Post by cwmoser on 2008-10-16
**_Below is what we are experiencing:_**

**carl@klaatu:~/Ubuntu Linux/Support$** [COLOR="DarkRed"]vmware[/COLOR]
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

**carl@klaatu:~/Ubuntu Linux/Support$** sudo [COLOR="darkred"]/usr/bin/vmware-config.pl[/COLOR]
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

[COLOR="DarkOrange"]The path "/usr/src/linux/include" is not an existing directory.[/COLOR]

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

---

### Post by bcom on 2008-10-16
Here is a link that might help you get going: [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

Since you already had vmware installed, you should be able to pick up by changing to the vmware-sever-distrib directory and, in Terminal, type sudo ./vmware-install.pl (the second part of step 4).

As the directions indicate, accept the defaults and be sure to complete the "post-install configuration" before running vmware.

---

### Post by cwmoser on 2008-10-16
> **bcom said:**
> Here is a link that might help you get going: [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

Since you already had vmware installed, you should be able to pick up by changing to the vmware-sever-distrib directory and, in Terminal, type sudo ./vmware-install.pl (the second part of step 4).

As the directions indicate, accept the defaults and be sure to complete the "post-install configuration" before running vmware.

Hey, that fixed it - thanks.  For the record, I did the following:

... installed the appropriate linux header (*.h) files:
**sudo apt-get install build-essential linux-headers-`uname -r` xinetd**

... then ran:
**sudo /usr/bin/vmware-config.pl**

... and viola, I was able to get VMware running.

Thanks again.

Carl

---

### Post by bcom on 2008-10-17
Glad it worked!

---

### Post by torchfire on 2008-10-17
Thanks for this information and for the link to the other thread.  It was a great help!!

Torch

---

### Post by slope on 2008-10-20
I also have problems with vmware after kernel upgrade. Stopped working.
I read this thread:[http://ubuntuforums.org/showthread.php?t=262732]("http://ubuntuforums.org/showthread.php?t=262732")

> 

[QUOTE]sudo apt-get install linux-headers-`uname -r`

Cheers
If you do it that way, you'll have the same problem again after next kernel update.

The right way is to install a metapackage called linux-386, linux-686 or whatever kernel type you are using. This package always depends on latest versions of _all_ kernel-related packages, so having it installed will make sure you always have correct versions of kernel, kernel headers, and restricted modules.

so if you are using 386 kernel, run 'sudo apt-get install linux-386', for 686 kernel 'sudo apt-get install linux-686', for k7 'sudo apt-get install linux-k7'.
[/QUOTE]

So I am running xubuntu 64 bit. How to know which route to choose here? 386, 686 or k7? Really would like to get up vmware again and not need to run the precedure once again with next kernel update. So where can I find out what kernel I am running?

---

### Post by fisherama on 2008-10-20
> **Duffy said:**
> Same problem here. After Ubuntu did a major package upgrade today (major in that it required a reboot which it rarely does), VMware stopped working.

same

[project management](http://www.contractsystem.com/)

---

### Post by zeiz on 2008-10-22
So where can I find out what kernel I am running?[/QUOTE]

Type in terminal: uname -r

Guys you are running vmware-server 2.0. Could you help me with install of XP? CD just doesn't boot though it's bootable for sure. Also I tried with bootable Suse and...nothing. How to install guest OS?

---

