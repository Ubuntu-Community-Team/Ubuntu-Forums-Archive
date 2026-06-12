---
title: "How do I use open-vm-tools?"
date: 2016-05-05
forum: Virtualisation
---

### Post by dr01tspc on 2016-05-05
I got a message that I should re-install my vmtools. (I just upgraded to VM Fusion 8.1.1 for Ubuntu 15.10.)

So, I went the "VMware Tools Distrib" path, as I have done in the past. I got a message recommending that 
I use open-vm-tools that is on my machine. Or I should remove open-vm-tools from my vm. (I lit ubuntu 
software center, which does not see open-vm-tools as being installed.) 

In any case, I read the relevant KB from VMware ([http://kb.vmware.com/kb/2073803](http://kb.vmware.com/kb/2073803)), and read a couple 
of postings from ubuntu users.

But I cannot figure out what I need to do to run open-vm-tools or if I should upgrade open-vm-tools. 
Is there a document which instructs me how to run commands (like renewing the shared folder when unix 
is update)?

So, I am being pushed to upgrade tools, and VMware Tools Distrib doesn't recommend I use it - though I did. 
I'd like to go the recommended route (open-vm-tools), and found relevant files on my machine, but I don't 
know how to use them.

Thanks for any pointers . . .

---

### Post by houstonbofh on 2016-05-05
What message?  Error popup from VMware? An e-mail?  Some guy on FaceBook? ;)

And what are you using now for the tools?  If you are using the propitiatory VMware tools, you will have to remove them first, and that is a manual process.

---

### Post by dr01tspc on 2016-05-05
The "error message/info", or response to my request to reinstall VMware Tools using "vmware-tools-distrib" follows:
```

tscale@tscale-mbp-ubuntu:~/Desktop/vmware-tools-distrib$ sudo ./vmware-install.pl
[sudo] password for tscale: 
error: db5 error(-30969) from dbenv->open: BDB0091 DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/tscale/.rpmdb
error: db5 error(-30969) from dbenv->open: BDB0091 DB_VERSION_MISMATCH: Database environment version mismatch
error: cannot open Packages index using db5 -  (-30969)
error: cannot open Packages database in /home/tscale/.rpmdb
The installer has detected an existing installation of open-vm-tools on this 
system and will not attempt to remove and replace these user-space 
applications. It is recommended to use the open-vm-tools packages provided by 
the operating system. If you do not want to use the existing installation of 
open-vm-tools and attempt to install VMware Tools, you must uninstall the 
open-vm-tools packages and re-run this installer.
The packages that need to be removed are:
open-vm-tools
The installer will next check if there are any missing kernel drivers. Type yes
if you want to do this, otherwise type no [yes] 

```
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

So, VMware Tools seems to want me to use open-vm-tools. Or it wants me to remove 
open-vm-tools.  

I have been using Fusion for 5 years, and have used vmware-tools-distrib (from VMware) 
when I needed to reinstall tools. Though the last few times, I started getting the message 
above (or similar). . . . As long as I got the shared folder when I plunged forware, I was OK 
with the situation.

This time I decided to look into using open-vm-tools (OVT), as it is the recommended path.

Per my reading, OVT is distributed with ubuntu, and updated when ubuntu is updated. Sounds good.

But Ubuntu Software Center doesn't think OVT is installed . . .  So I cannot remove it via 
the Center. (One of the options in the message above.)

And I simply don't know how to use OVT: That is, if it is on my machine - as it seems to be, as 
part of the ubuntu distribution/update events, how do I "use it"?

This situation came about because, when I was viewing/adjusting Settings in VMware Fusion 
(Display settings), I got a message telling me I need to update VMware Tools to get 3D Acceleration. 

So, I have been trying to update WVMware Tools, to no apparent avail. Though /mnt/hgfs (shared folder) 
is created, the message relative to 3D acceleration persists.

Aside: I am also not convinced that the memory I requested via Settings is being allocated to the VM.

In short, I don't care if I use OVT or VMware Tools, but I would like to be told how to use one or 
the other (for dummies).

As you might be able to discern, I am not a VM person. (I am a numericist, and just want to code.) 

Thanks ,
Tim

---

### Post by houstonbofh on 2016-05-06
Get a CLI and type;
```
dpkg -l | grep open-vm-tools
```

If you do not have the package installed via the package manager, you will get no response back.  But...  open-vm-tools may have beens installed by hand, and the package manager knows nothing.

So try;
```
ps ax|grep vmware
```

This will show if anything is running.  if not, just avoid the VMware install and install open-vm-tools from the package manager and see if it works.

---

### Post by dr01tspc on 2016-05-11
HoustonbofH:

The response to your first suggestion (dpkg -l | grep open-vm-tools) indicates open-vm-tools exists: 

```
rc  open-vm-tools                                        2:9.10.2-2822639-1ubuntu3                  amd64        Open VMware Tools for virtual machines hosted on VMware (CLI)
rc  open-vm-tools-desktop                                2:9.10.2-2822639-1ubuntu3                  amd64        Open VMware Tools for virtual machines hosted on VMware (GUI)
rc  open-vm-tools-dkms                                   2:9.10.2-2822639-1ubuntu3                  all          Open VMware Tools for virtual machines hosted on VMware (DKMS)

```

The response to your second suggestion (ps ax| vmware) is:

   ```
2339 pts/0    S+     0:00 grep --color=auto vmware
```

Which doesn't tell me which tools is running, but would seem to be VMware Tools? "which vmware" doesn't elicit a response.

In either case, the settings window (Fusion) is suggesting that I upgrade VMware Tools in this VM to get 3D acceleration (graphics). I also see "failure to add memory" (or similar) upon startup, which concerns me wrt ram access. 

The open-vm-tools offered to me via Ubuntu Software Center is  2:9.10.2-2822639-1ubuntu3 - which seems to me to be the one installed.

So, can I remove VMware Tools, and start open-vm-tools? If so, how?

Thanks,
Tim

---

### Post by MAFoElffen on 2016-05-12
<Side note: Go back to EDit post #3 to see how to wrap commands and output in code tags. (Forum Policy) Add them to Post #5 and further posts for all output and commands.>

NO... wait! open-vm-tools is an extension to VirtualBox, not a replacement for!

That package is a open sourced version of Oracle's "Guest Additions", and later versions replaced that with the Oracle "Extension Pack." All those go by matching versions. If you upgrade the base package, you have to reinstall the helper toolset.

But since open-source code, it is not caught up with current yet and is not full version'ed. Current is the Oracle extension Pack, which adds capabilities to the VirtualBox Host, instead of to each VM Guest. There is no charge for the Extension Pack. To protect their proprietary code, they distribute it free as compiled code. Being compiled makes it less likely to be reverse engineered.

But it still free. VirtualBox Support currently recommends their users to be running the "Extension Pack." (instead of using open-vm-tools). You can do what you want, but be warned that there are currently open problems with doing so.

---

### Post by houstonbofh on 2016-05-14
You have open-vm-tools from the repository installed.  If you want to remove it,
```
sudo apt-get purge open-vm-tools open-vm-tools-ddesktop open-vm-tools-dkms
```
Then you can install the VMware VM tools.

---

### Post by dr01tspc on 2016-05-15
Houstonbofh:

I purged open-vm-tools and installed VMware Tools. It looks good! I'll have to see if 3D graphics acceleration being on makes a difference in some of my imaging work.

Thanks for your suggestions.

---

### Post by houstonbofh on 2016-05-16
Any time!  Don't forget to make the thread "solved." :)

---

