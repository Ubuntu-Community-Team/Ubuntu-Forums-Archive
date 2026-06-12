---
title: "How can the ubuntu-server installer be so bad?"
date: 2024-12-06
forum: Server Platforms
---

### Post by mha42 on 2024-12-06
Sorry for the clickbait subject line. But hey. You are in the thread :) 

I've been using and installing ubuntu-servers manuall since probably since Ubuntu 6.06 LTS in different forms. Through out all releases we had to endure multiple changes which was not always "appreciated" by simple home users. But yet I think Ubuntu makes an excellent offering, especially with not named Ubuntu Pro (previously cannonical livepatch) free for home users and hobbyists. This is excellent. 

But how is it that I as of late with no avail am unable to complete a basic ubuntu-server installation without the installer simply crashing? I've installed surely 20 systems with 24.04 and 24.04.1 ISOs both with and withouth network. But at some random point after accepting the partition table and the installer starts it will crash. 

When it does, I am sometimes ending up with a locked up session or I can try restarting the installer. I've submitted multiple reports when possible when I am installing with a network. But when the machines are offiline I don't even want to bother on how to collect those reports for submission outside of the installer.

Other than crashing the installer simply does not seem to be properly QA tested. I have multiple issues which are reproducible;

 - Having 4 drives and setting 2 of them as boot devices (UEFI mode) then creating 2 1GB partitions which then is left unformatted and used for a raid-1 md0 in 70% of cases does not display any text of which devices you select in the raid creation dialog. I have to scroll down with the arrows, hit space to select the two drives, and see so the size in the bottom corresponds to my 1GB total space. Then I can be reasonably sure I selected the correct device. In the other 30% the text is clearly visible and you can see exactly which partitions you select. 

 - Configuring static IP addressing on an interface will only allow you to set a default IPv4 OR IPv6 gateway. You cannot have both. Setting one will eradicate the other. 

 - Same issue about blank text happens when I select the LVM creation dialog. 

 - When my drives comes with predefined md arrays (which show up as md125,m126,md127,md128) and I manually create blank partition tables and try to set it up, likelyhood of installer crash increase to 90% instead of otherwise about 60%. That's 60% of all my installs which I need to restart and configure in the exactly the same way and for some reason it succeeds the second time.

 - Sometimes it crashes directly after creating my user account dialog, sometimes after installing grub on the boot devices. It's truely random. Sometimes it completes the full install with the exact same configuration. 

- Why does it take ages connecting to cloud-init if there is no network present before the installer starts? No network == ignore it.


Some use configuration corner cases I always do which I suspect have to do with why I am ending up in these scenarios. I almost always do the following;
 - Use manual partitioning. Never the automatic. 
 - Create raid1 devices on dual drives
- Always setting two drives as boot devices (forcing a duplicated EFI partition)
 - Create an encrypted LVM on md1 which in turn hosts my rootfs and other partitions. 
 - Leave some drives behind as they are set up later (often systems with 4-8 available drives)
 - Want to scratch existing partitions and raids which are auto assembled on boot (despite having no use)
 - Configure static IPv6. I guess peopse rarely use it and if they do they use auto config in some form.


I've installed ubuntu-servers on multiple types of servers and workstations:
 - Dell PowerEdge R620
 - Dell PowerEdge R630
 - Dell PowerEdge R640 
 - Dell PowerEdge R730
 - HP DL360 G7, G8, G9
 - Regular tower workstations with home equipment hardware

I doubt that it's a hardware failure causing these issues. I would think that I am using quite reasonable configurations in my setup. These issues started to appear more frequently in the 24.XX line. Perhaps it was also present in the 22.XX. Not sure. Can't remember having any issues in the 20.XX series installers with any of the above. All systems are rock solid once the installer completed successfully and managed to reboot the machine. 

If I have existing md raids on my drives which are being installed on I have learnt to reduce the frequency of failure by booting the installer, opening a secondary shell and executing the following
mdadm --stop /dev/mdX (all of them)
mdadm --zero-superblock /dev/sdX (all of them)
wipefs -af /dev/sdX (all of them)
Then rebooting the installer so those faux mdXXX devices are never initialized. 

What's so frustrating is that I have to fight an installer which does not want to show me dialog boxes. Which does not want to configure my network in the way I want. And is frustrating working with partitions and drives only to have it crash and re-run my installer 2-3 times in the exact same way. 

So what gives? Bad QA testing for corner cases? Am I simply using such rare features so they are not tested?

I realize that the distro is free which limits my "rights" to complain. But don't they also sell the exactly same installer to customers? I am happy to continue to upload installer crash reports when they happen. But I've done that for surely the first part of this year now on these crashes and I don't really see any fixes in sight. 

What's your experiences? Do you use the same features I do and face the same issues? Other experiences?

---

