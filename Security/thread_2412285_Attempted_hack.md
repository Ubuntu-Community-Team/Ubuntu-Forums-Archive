---
title: "Attempted hack"
date: 2019-02-10
forum: Security
---

### Post by cam17 on 2019-02-10
I noticed a screen pop up with different variants after the Ubuntu screen saver on my Ubuntu 18.04.1. LTS fully updated as of Feb-10-2019. I have the firewall UFW enabled and I was wondering if anyone can tell me how this screen could pop up. 

The enclosed screen shot doesn't show the Network icon in the task bar.

---

### Post by TheFu on 2019-02-11
enabled firewall without any rules may not do anything.  Perhaps if you posted the output from** sudo ufw status** then someone might be able to help?  But most of the time, a popup like that would be requested through javascript by the browser on the machine. Most home firewalls would allow that client-to-server request on the same subnet.

---

### Post by cam17 on 2019-02-13
I agree. I was just pointing out the general configuration of my Ubuntu system.  Also worth noting is no additional software was installed. I believe it to be Java script from the default firefox browser which was open and only has 1 add on "ublock origin"  The logs of UFW  do not see anything unusual. the system logs has some instances but I will watch closer on the next occurrence.

---

### Post by cam17 on 2019-02-15
I forgot to mention that I did install ffmepg for Firefox to play specific videos.  I have enclosed the second attempt.  [https://ubuntuforums.org/attachment.php?attachmentid=282523&stc=1&d=1550216533](https://ubuntuforums.org/attachment.php?attachmentid=282523&stc=1&d=1550216533)

---

### Post by cam17 on 2019-02-22
I major change has been made. My Non administrator account can now make wifi changes without requiring an Admin password. 
Also in the logs under "important" tab a applications message stated "critical: we failed, but the fail whale is dead. Sorry..."

---

### Post by cam17 on 2019-02-24
When I went back to my 18.04.1 LTS workstation the complete desktop including the dock was blank. When I logged back into the workstation my wifi connected as shown by the wifi indicator in the top right but no network access was possible.

---

### Post by TheFu on 2019-02-24
> **cam17 said:**
> When I went back to my 18.04.1 LTS workstation the complete desktop including the dock was blank. When I logged back into the workstation my wifi connected as shown by the wifi indicator in the top right but no network access was possible.

Ok, 1 issue per thread unless they are related.

The first post was the browser visiting the HTTP website for your LAN router. Nothing more.  LAN routers almost always use javascript.  No hacking there, provided you've changed the default password (and userid hopefully) to the router.  My WiFi Router security Checklist: [http://blog.jdpfu.com/pages/wifi-security](http://blog.jdpfu.com/pages/wifi-security)

Also, it appears you are using SPICE ... so I'd assume you are doing something related to KVM and virtual machines.  That throws a wrench into all networking. Best to move to the virtualization sub-forum and ask questions about this there.  I use KVM and manually setup linux bridges for use by the different VMs.  If the VM is using the NAT network connection, I cannot help. I don't use that.  However, to a client VM, the wifi network devices are not seen.  Guest VMs only see the virtual hardware provided by the hypervisor, as configured in the .xml config file for the VM.  If you didn't setup something highly odd and specific to get wifi inside the VM, then that isn't relevant.  Using wifi on a hypervisor host is problematic, since many wifi chips don't allow the capabilities needed.

If the issue is with the physical networking on the host machine, then I'd post to the Networking subforum.  If it is wired, I can probably help.  I cannot help with wifi in any way.  My network trouble shooting article: [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

Good luck.

---

### Post by cam17 on 2019-03-07
Nothing unwarranted is appearing in the UFW logs. But interestingly if I reinstall the software without performing any update the workstation does not crash. If I install all updates it will crash and I suspect the logs are being manipulated because of the time the crash occurs.

---

