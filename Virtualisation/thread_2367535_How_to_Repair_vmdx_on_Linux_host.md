---
title: "How to Repair vmdx on Linux host"
date: 2017-07-31
forum: Virtualisation
---

### Post by Daddyo-613 on 2017-07-31
The Issue:

I am running a Windows XP Pro SP3 Ver 2002 guest on Ubuntu 12.04 (32 bit) host using VMware Player 6.0.6 build 2700073, Workstation 9.0.

I have a bad vmdx and although the guest OS will boot, I get an error message about 20 minutes into the session that the guest can't synchronize with a particular vmdx. I have identified which vmdx has been corrupted and, after closing down the vm, i ran <vmware-vdiskmanager -R> on the particular vmdx in a terminal. Nothing much seems to happen. There is no message displayed. It just goes back to the system prompt.

When I reboot the guest vm, the problem persists.

When I run <vmware-vdiskmanager -R> there is no message. It just returns to the system prompt.

How can I repair the corrupt vmdx without loosing the data stored on that particular vmdx?

---

### Post by Bucky Ball on 2017-07-31
For what it's worth, 12.04 LTS reached [end-of-life]("https://wiki.ubuntu.com/Releases") in April 2017 so would be better, and more secure, to use a supported release, presuming you are online.  :)

Good luck.

---

### Post by Daddyo-613 on 2017-07-31
Bucky Ball;

I do intend to upgrade. In fact I intent to purchase a new desk top and install the current LTS version of Ubuntu with the current version of that other program running in a virtual machine.

The problem is that I have to transfer my files and if one of the present VMDK's is corrupted, I have to fix it before I can be assured that I can transfer my files safely.

---

### Post by Bucky Ball on 2017-08-01
Got you. I can help with various VBox things, but not this I don't think. At least I've bumped your thread to the top of the list again. Good luck. ;)

(Have you had a good dig online for the EXACT error message you are getting? That will probably turn up some things. Had a quick look and perhaps a problem with syncing the time between host and guest? Maybe a clue ... ;))

---

### Post by Daddyo-613 on 2017-08-01
Thanks Bucky Ball;

I have been looking online for solutions. Many of the posts are for Linux guests on other host platforms which aren't particularly helpful other than to convince me that it is possible to alter and repair a specific VMDK.

Many posts that deal with a VMDK's on a Linux host refer to the <vmware-vdiskmanager> tool that was supposed to be found in /usr/bin/ on a Linux host. My machine didn't have that tool so I downloaded the Linux version separately from the attachments section at the bottom of VMware Knowlege Base article KB 1023856:

 [https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=102385]("https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1023856")

I followed the instructions, loaded the tool in my /usr/bin directory and ran the tool with the repair option. The syntax of the command is as follows:


[FONT=Courier New]/usr/bin/vmware-vdiskmanager -R <path of the vmdk(virtual disk)>[/FONT]

**Note**: Where [FONT=Courier New][SIZE=2]*<path of the vmdk(virtual disk)>* [/SIZE][/FONT]is the folder path to the virtual disk that appeared in the error.

When I ran the command there was no output or completion message. I was simply returned to the command prompt.

If someone out there has used this tool before, it would help me to find out what's supposed to happen after you run the command. In my case, nothing happened and the error message with the particular VMDK reappeared the next time I booted up the guest system. 

None of the articles I've seen tell me what the output should be to confirm that a repair has been achieved. There are other options that can be used with the tool but I'm not sure if I might do more damage than good by experimenting with them.

---

