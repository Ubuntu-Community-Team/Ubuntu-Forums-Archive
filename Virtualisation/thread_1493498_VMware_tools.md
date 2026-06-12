---
title: "VMware tools"
date: 2010-05-25
forum: Virtualisation
---

### Post by subba9000 on 2010-05-25
How to install VMware tools on Ubuntu 10.04

---

### Post by TheGoodDocta on 2010-05-25
What OS is your VMWare instance running on?

On Macs, VMWare Fusion provides the option to "Install VMWare Tools" directly from the VMWare Fusion "Virtual Machine" menu.

When this option is clicked, the VMWare Tools installer is mounted as a disk on your running Ubuntu VM.

Open the disk, and extract the vmware tools gzip.

Execute the vmware-install.pl script in the extracted directory as super-user (sudo perl vmware-install.pl)

Respond to the prompts from the installer. Accepting the defaults is generally OK.

And voila - you're done.

---

### Post by farbridges on 2010-06-11
Doesn't work on 10.04 64bit Server. It won't compile the needed modules. There is an alternative that works nicer: install the packages open-vm-tools and open-vm-dkms. For a server (so no X) you should do this:

```
apt-get install --no-install-recommends linux-headers-virtual open-vm-dkms open-vm-tools
```

See [here]("https://confluence.terena.org/display/~visser/open-vm-tools+in+Ubuntu+Lucid") for some advice. And [here]("http://sourceforge.net/projects/open-vm-tools/") for the open-vm-tools project page.

---

### Post by dcstar on 2010-06-12
> **subba9000 said:**
> How to install VMware tools on Ubuntu 10.04

Follow the instructions in Virtualization forum.

---

### Post by rshackleford on 2010-06-16
> **dcstar said:**
> Follow the instructions in Virtualization forum.
 
Can you possibly be more specific, maybe offer a link to the actual thread. I have googled, and searched these forums and generally the message is that 10.04 is fully supported in VMware. However, there are no modules in vmware-tools that are precompiled for 10.04 AND trying to compile generates fatal errors on all the modules.

---

### Post by bodhi.zazen on 2010-06-16
> **rshackleford said:**
> Can you possibly be more specific, maybe offer a link to the actual thread. I have googled, and searched these forums and generally the message is that 10.04 is fully supported in VMware. However, there are no modules in vmware-tools that are precompiled for 10.04 AND trying to compile generates fatal errors on all the modules.

You can try the open-vm tools as advised :

[https://confluence.terena.org/display/~visser/open-vm-tools+in+Ubuntu+Lucid](https://confluence.terena.org/display/~visser/open-vm-tools+in+Ubuntu+Lucid)

Or perhaps post the exact error message you are getting for further advice.

Otherwise I am moving this thread to virtualization now.

---

### Post by pvollma on 2010-09-13
> **TheGoodDocta said:**
> What OS is your VMWare instance running on?

On Macs, VMWare Fusion provides the option to "Install VMWare Tools" directly from the VMWare Fusion "Virtual Machine" menu.

When this option is clicked, the VMWare Tools installer is mounted as a disk on your running Ubuntu VM.

Open the disk, and extract the vmware tools gzip.

Execute the vmware-install.pl script in the extracted directory as super-user (sudo perl vmware-install.pl)

Respond to the prompts from the installer. Accepting the defaults is generally OK.

And voila - you're done.

I did all that, everything ran successfully, but I still cannot figure out how to access anything on the host machine (VMWare 6.5.4 on Fedora 10). I ran vmware-toolbox but found nothing that would connect my to my home directory on the FC10 host.

I did have the problem others have reported when using 10.04 in VMWare, and commented out the vmhgfs line in fstab, and moved the mount statement to rc.local. A list of mounts (mount -l) shows the .host:/ filesytem is mounted at /mnt/hgfs, but nothing appears at that mount point.

---

### Post by Macdude-StL on 2013-04-26
I've been struggling with getting folder sharing to work in VMWare 5 - thought I had already installed VMWare Tools, but nothing would show in /mnt/hgfs. I finally tried re-installing. When I got to the section of the install where kernel headers are to be rebuilt, the prompt indicated a valid kernel header path was not present. I tried installing the 3.5.0-25 kernel headers (in Ubuntu Software Center), and got the same error again. Then I realized that there is a selection to install 3.5.0-25 generic kernel headers. After selecting that, the installer indicated a valid file path. After completing the installation, I found the shares present in /mnt/hgfs! I restarted the VM anyway, since some things occasionally don't get refreshed without a hard restart, and things still looked right after the restart.

I believe this situation may have returned after a system update, since 3.5.0-17 header source seems to have been present, but the system is now at 3.5.0-25.

When doing this in VirtualBox, I had found that the shares do not show up until after the machine is restarted, which had led to much frustration.

Before:
> Searching for a valid kernel header path...
The path "" is not a valid path to the 3.5.0-25-generic kernel headers.
Would you like to change it? [yes] ^C
Execution aborted.

After:
> Searching for a valid kernel header path...
Detected the kernel headers at "/lib/modules/3.5.0-25-generic/build/include".
The path "/lib/modules/3.5.0-25-generic/build/include" appears to be a valid 
path to the 3.5.0-25-generic kernel headers.
Would you like to change it? [no] 

---

### Post by wildmanne39 on 2013-04-27
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

