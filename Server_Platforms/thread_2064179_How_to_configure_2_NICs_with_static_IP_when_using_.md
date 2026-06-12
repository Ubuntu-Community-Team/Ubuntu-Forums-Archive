---
title: "How to configure 2 NICs with static IP when using Orchestra to install Ubuntu 12.04?"
date: 2012-09-28
forum: Server Platforms
---

### Post by huiliang on 2012-09-28
Hi,

I am using Orchestra on Ubuntu 11.10 to automatically install Ubuntu 12.04 on some bare-metal machines. On cobbler_web, I created new system for each machine and selected "precise-x86_64" as profile.

There are 2 network cards on each machine. I want to set up static ip for each network card. So, I input the information in "Networking". I added eth0 and eth1. For each interface, I inputted MAC address, IP address, ticked "Static", Subnet. Then I saved and verified that the information is kept.

However, after Ubuntu 12.04 is installed, I can only see one NIC and it is set to use DHCP.

Is there a way to solve this problem?

Thanks,
Huiliang

---

### Post by drdos2006 on 2012-09-28
Try these posts.

[http://ubuntuforums.org/showthread.p...5#post11320085](http://ubuntuforums.org/showthread.p...5#post11320085)

[http://ubuntuforums.org/showthread.php?t=1842656](http://ubuntuforums.org/showthread.php?t=1842656)

[http://ubuntuforums.org/showthread.php?t=1840543](http://ubuntuforums.org/showthread.php?t=1840543)

regards

---

### Post by huiliang on 2012-10-01
Thanks. I guess that I need to edit /etc/networking/interfaces to set the static IPs. I add to run my own snippet in kickstart:

d-i	preseed/late_command string true && \
   	$SNIPPET('orchestra_rsyslog_obtain_keys') && \
   	$SNIPPET('orchestra_disable_pxe') && \
   	$SNIPPET('XXX') && \
   	true

To test, in snippet "XXX", I simply input:
echo "test" > /var/test.txt \

I am sure that there is no problem with the "change line symbol \".

However, after installation, I cannot find this /var/test.txt file. What's wrong? Is this sentence executed? or permission problem?

---

