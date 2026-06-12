---
title: "Issues with latest updates to 20.04"
date: 2021-08-24
forum: Virtualisation
---

### Post by edfromohio on 2021-08-24
Apologies if this post is in the wrong location or a duplicate.  The search function seems to be having issues and the number of subgroups is overwhelming to a new user like me.

Is anyone else having an issue with the latest August 2021 updates to Ubuntu 20.04?  I have 3 small VMware VM's running Sybase and with the latest updates, all 3 won't boot after installing updates and allowing the reboot.  No error messages or anything - it just doesn't boot even after letting it sit for 20 minutes on a very fast server & NVMe storage.

Thanks for any insight you can offer,
Ed

---

### Post by grahammechanical on 2021-08-24
> The search function seems to be having issues and the number of subgroups is overwhelming to a new user like me.

Are you referring to Ubuntu forums? I thought that comment was a reference to your problem with Ubuntu. I see your problem is to do with Virtual Machines. I have no experience with those things. There is a section called "Virtualisation." I agree that the title of that section could refer to virtual machines or to virtualisation technology (Virtual Reality) devices. These are two different subjects in my opinion. I think that the virtual machine definition predates the VR technology definition. In my opinion VR is more accurately a "Fool yourself it is real" technology.

All of which does not help you solve your problem but then again this is a section of the forum for Chat. I am sure someone will offer actual help and not virtual help. :)

Regards

---

### Post by edfromohio on 2021-08-24
There are 2 unrelated paragraphs - the first stating why I posted it here in case someone flames me for putting it in the wrong forum or not searching the forum myself.  The second being the actual issue I am posting.

I don't believe the update issue is virtualization-related.  These Ubuntu instances have no idea they are in a VM and I don't have VMware Tools installed.  They have been running fine for several months and update cycles until this latest round of Ubuntu updates.  The effect is immediate after allowing the latest updates to install and reboot.

So again, my question is: Is anyone having issues with the latest round of updates causing Ubuntu not to boot up?

---

### Post by pantazi on 2021-08-24
No.

---

### Post by ajgreeny on 2021-08-24
Is it just the VMs that you have been running that will no longer boot or do you have lots of other problems with your 20.04 installation?

Did the recent updates include a new kernel?
If you are not sure about that run terminal command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` and copy/paste the output back here.
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by monkeybrain20122 on 2021-08-24
> **edfromohio said:**
> 
I don't believe the update issue is virtualization-related.  These Ubuntu instances have no idea they are in a VM and I don't have VMware Tools installed.  They have been running fine for several months and update cycles until this latest round of Ubuntu updates.  The effect is immediate after allowing the latest updates to install and reboot.


It is not really clear from OP what you are talking about since it sounded like you were updating the host. Now it sounds like you are updating the guests. So What is the host? What kind of "updates" are you talking about? If it is not virtulization related then many systems (not VM) would suffer the same problems with those updates. Do you find similar reports elsewhere in the forum?

---

### Post by edfromohio on 2021-08-24
> **ajgreeny said:**
> Is it just the VMs that you have been running that will no longer boot or do you have lots of other problems with your 20.04 installation?


Thanks for the reply.

Not sure how to answer that.  I have three identical 20.04 instances which I update and reboot monthly.  Up until this month, they were running fine.  Then after the update, it won't boot at all.  It shows 2 lines of text and nothing more (don't recall what it is, but it always shows when I reboot just before it shows gobs of other lines of text.)  

> **ajgreeny said:**
> 
Did the recent updates include a new kernel?
If you are not sure about that run terminal command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` and copy/paste the output back here.
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

Not sure that will work because I had to restore the VM's from a backup due to them not booting.  So as all 3 systems stand, the updates are not installed.  Wouldn't your command assume that I could get to a CLI after the updates were installed and the system rebooted?  Or will it work before the updates were installed?

---

### Post by ajgreeny on 2021-08-24
My guess is that your VMs all had the same kernel update, ie, a new kernel installed, but then you restored older versions of the VM so we will never know for sure.

Assuming I am correct, boot to one of your VMs of 20.04 and run ```
sudo apt update && apt list --upgradable
``` and look carefully at the list of upgradable and newly installable packages to look for a new kernel (linux-image) package before you actually run the ```
sudo apt upgrade command
```
I wonder if you are using VMs of Ubuntu that began with 20.04.2, which I think is now offering the 5.11.0-27 kernel as it uses the HWE stack; I believe that kernel series has occasionally caused problems for some users.

---

### Post by coffeecat on 2021-08-24
Support not chat.

*Thread moved to **virtualisation** sub-forum.*

---

### Post by MAFoElffen on 2021-08-24
well heck... You should not have restored yet. ad you first needed to check the VM Host's log for the VM Guest, to check for possible errors relating to why they didn't start. It might not have been the guests, it might have been host related... Which you didn't mention what kind of host VMware was running on, nor what version of the player, did you?

That would provide us enough information to steer you to where to look for those log files...

Next: 
What Editions are the Ubuntu VM Guests? Are they Desktop or Server?

How are these guest configured as Guests? Especially the details on the video options of the Guest (As a guest)... Because n update of VMware or Ubuntu might have effected that...

What Ubuntu versions are the VM guests. 

What exactly do the VMs Guest do on startup? How far do they get before they fail? That way we know at what stage of the boot process it failed...

At this point , it's post #10, and you have said they don't boot, but no context, nor information that helps us to help you. Not being critical. I want to help you, but we need some information to be able to do that. 

Right? So let's start over and please provide at least some of that.

---

### Post by edfromohio on 2021-09-03
> **MAFoElffen said:**
> well heck... You should not have restored yet. 

I didn't have days to wait to find a solution - these are servers in a production environment so every minute they are down is a problem.

I've explained the best I could with what I had on hand.  Since it seem to just be an issue with our systems and not everyone in general, I'll ignore updates until the next more significant update comes out and try.

Thanks to those that replied,
Ed

---

### Post by MAFoElffen on 2021-09-06
Servers where the Virtual TTY Session are not showing now? Or did they have Graphical Desktops?

Since, they are Virtual... Leave them running and lock down the updates temporarily... 

Clone one. Change the Virt networking to private temporarily, before you bring it up. Change the hostname and static address so they do not conflict with existing. Disable any service that will broadcast a conflicting DNS name to your production systems. Change the network switch back to what it was. Then test and diagnose on that disposable VM.

---

