---
title: "VMWare ESXi and Server 12.04 Containers"
date: 2012-05-28
forum: Virtualisation
---

### Post by nickfromvan on 2012-05-28
Hello everyone

I'm new to the forum but have been using Ubuntu for several years now as a dev/work server at home.  I recently purchased some server hardware and have been experimenting with ESXi and Ubuntu server containers to eventually host a few client sites.  I apologize right now if this topic has been covered but I have looked over the entire virtualization forum since 12.04's release and haven't found the answer to this problem.
I've also looked at other posts with previous versions running on ESXi and none seem to address this problem.

Just wondering if anyone has run into a problem with their guest OS's filesystem spontaneously becoming readonly?  From what I have read in the VMWare KB and on several other articles I've found, this is a known issue with really any flavor of Linux running on ESX.

Here is what I did and where it went wrong:

First Try:
1) created a new VM and selected Ubuntu (64 bit) as the guest OS
2) mounted the 12.04 ISO and installed it with no problems
3) played around with the LAMP components to make sure everything was running (which it was)
4) patted myself on the back and called it a night
Where it went wrong:
Next day, I tried to upload some files to deploy a client site to see how everything worked but I got a write permission error.  I checked the permissions on that folder and everything checked out (775).
I tried touch asdf.txt and it came up with:
touch: cannot touch `asdf.txt': Read-only file system
I did some reading and poking around and figured out that a filesystem error was detected and / was remounted RO.  I ran fsck on the guest and also ran the equivalent command from the ESXi terminal (can't remember the name of the command now).
The guest reported a problem and couldn't repair the FS (I didn't track this down yet ... more on this later) but ESXi seemed fine so my conclusion was that the FS was somehow corrupted, possibly from an unclean powerdown.
I also came upon this article in the VMWare KB which seems to indicate a common problem to many if not all flavors of Linux: [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=51306](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=51306)
However the fixes are all horribly out of date so I wouldn't want to try using their patch.
All the measures I'd found to this point (fsck, and remount as RW) seemed to be temporary measures given that the problem could reappear at any time (in my case, after only running for 1 1/2 days).

Second Try:
Hoping that the problem was my fault for not shutting the VM or server down properly I decided to give it another try last night.
I followed exactly the same steps as on the first attempt and loaded the website files and database of the site I was deploying as a test.
Everything worked great (website came up) and I left it at that point for next day when I was planning on running Apache Bench and performing any additional necessary server hardening.
Next day when I was ready to run AB, the problem had reappeared more or less 10-12 hours after a clean install with no shutdowns in between.
After a few hours of research I finally found this article which seems to point at exactly the problem I'm experiencing but actually offers a more comprehensive explanation and a more permanent solution.
You'll need a login to read the article but the gist is to either use the patch provided by VMWare (in the case of Ubuntu, the "fix" is to "upgrade" to 7.10), run a cron job that tells you when the FS craps out again (not a very good solution), or patching the kernel module source.
I am an experienced programmer but more with higher level languages, not shell scripting and I've never touched the Linux kernel.

The suggested fix is to replace this (in file /usr/src/linux-source- `uname -r | sed "s/-.*//g"`/drivers/message/fusion/mptscsi.h):
    if (scsi_status == MPI_SCSI_STATUS_BUSY)
     sc->result = (DID_BUS_BUSY << 16) | scsi_status; else
     sc->result = (DID_OK << 16) | scsi_status;
to this:
    if (scsi_status == MPI_SCSI_STATUS_BUSY)
    // sc->result = (DID_BUS_BUSY << 16) | scsi_status;
    sc->result = (DID_OK << 16) | scsi_status; else
    sc->result = (DID_OK << 16) | scsi_status;
then make the modules and replace the existing ones.
I haven't had a chance to try this out yet but I will be doing that tonight.

Sorry for the long post to this point but what I'd like to know from the community is have any of you run into this problem with ESXi and any version of Ubuntu server?
How did you fix this issue?
Does the fix above seem safe?  Without having first looked at the surrounding code to see if this addresses only the specific path failover problem introduced by ESXi, my concern is that changing this behavior would cause Ubuntu to ignore legitimate failures to be ignored.
Am I even barking up the right tree or is this another issue entirely?

Some other info regarding my setup:
Supermicro X7DCA-L
2 x Intel Xeon L5420 @ 2.50GHz (8 cores total)
16GB RAM
2 X WD RE4 HDD (currently independent, but will be RAID1 once my RAID card and riser arrive)

Thanks in advance for any help or insight and please let me know if you need any other details.

---

### Post by dcstar on 2012-05-29
> **nickfromvan said:**
> Hello everyone

I'm new to the forum but have been using Ubuntu for several years now as a dev/work server at home.  I recently purchased some server hardware and have been experimenting with ESXi and Ubuntu server containers to eventually host a few client sites.  I apologize right now if this topic has been covered but I have looked over the entire virtualization forum since 12.04's release and haven't found the answer to this problem.
I've also looked at other posts with previous versions running on ESXi and none seem to address this problem.

Just wondering if anyone has run into a problem with their guest OS's filesystem spontaneously becoming readonly?  From what I have read in the VMWare KB and on several other articles I've found, this is a known issue with really any flavor of Linux running on ESX.

Here is what I did and where it went wrong:

First Try:
1) created a new VM and selected Ubuntu (64 bit) as the guest OS
2) mounted the 12.04 ISO and installed it with no problems
........

Until VMware certify that they fully support 12.04 VMs on their products no one has any business expecting it to work reliably on them.

---

### Post by nickfromvan on 2012-05-29
My apologies, I did not realize that a search for supported guests is located here:
[http://www.vmware.com/resources/compatibility/search.php?deviceCategory=software&testConfig=16](http://www.vmware.com/resources/compatibility/search.php?deviceCategory=software&testConfig=16)

---

### Post by dcstar on 2012-05-30
> **nickfromvan said:**
> My apologies, I did not realize that a search for supported guests is located here:
[http://www.vmware.com/resources/compatibility/search.php?deviceCategory=software&testConfig=16](http://www.vmware.com/resources/compatibility/search.php?deviceCategory=software&testConfig=16)

If previous experience is anything to go by, VMware seem to take 3-4 months to make their products compatible with the latest Ubuntu release.

Considering that Ubuntu will only be a small percentage of environments used by the various VMware products, it is understandable that a commercial company like VMware will only do this sort of thing as a low priority.

Most (if not all) commercial users would rarely contemplate using just released software anyway, they will wait until the product matures and settles down so a couple of months wait means nothing to them.

---

### Post by nickfromvan on 2012-05-30
Thanks David,

I agree with you completely.  I set up a new container yesterday, went back to 10.10 and everything has been running properly since then.  I would not have even tried 12.04 had I known it was not yet fully supported however VMWare's site is not the easiest to navigate (it took me more than 15 min to find the vSphere client download link again yesterday when I needed to install it on another machine) and one of the pre-built appliances on the market place is Ubuntu 12.04 so I figured it would be ok.  Wanting full control over what was installed, I decided to do a fresh install myself rather than to download the appliance.

For those of you trying this out, my experience has been that the FS becomes readonly in as little as 8-12 hours with no particular user action triggering this to happen as the VM was just left running overnight.  Neither remounting the FS as RW nor running fsck worked for me but even if it had, would probably have been a temporary fix and could not be relied upon to work long-term.  I did find that rebooting the VM and pressing "f" at the prompt to fix the filesystem fixed the problem, but again, I did not have the confidence that this would finally resolve the issue.

I'll probably just stick with 10.10 until it nears end-of-life and look for the newest _supported_ LTS at that time ... unless there's a compelling enough reason to upgrade in the interim.  Thanks again.

---

### Post by dcstar on 2012-06-06
> **nickfromvan said:**
> Thanks David,

I agree with you completely.  I set up a new container yesterday, went back to 10.10 and everything has been running properly since then.  I would not have even tried 12.04 had I known it was not yet fully supported however VMWare's site is not the easiest to navigate (it took me more than 15 min to find the vSphere client download link again yesterday when I needed to install it on another machine) and one of the pre-built appliances on the market place is Ubuntu 12.04 so I figured it would be ok.  Wanting full control over what was installed, I decided to do a fresh install myself rather than to download the appliance.
........

I just had to install updates on a ESXi 5 server yesterday to just allow installation of Windows 8, I would recommend that you install all available updates on your ESXi server to see if they resolve the issue.

---

### Post by hazzey on 2012-08-01
Has anyone found a workaround/fix for this issue?  It looks like 12.04 is supported by ESXi 5.0U1, but I am still having issues with Ubuntu guests going read-only.

---

### Post by dcstar on 2012-08-10
> **hazzey said:**
> Has anyone found a workaround/fix for this issue?  It looks like 12.04 is supported by ESXi 5.0U1, but I am still having issues with Ubuntu guests going read-only.

Have you installed **every** available patch?

---

