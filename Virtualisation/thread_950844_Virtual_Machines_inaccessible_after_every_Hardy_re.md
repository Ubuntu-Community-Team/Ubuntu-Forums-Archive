---
title: "Virtual Machines inaccessible after every Hardy reboot"
date: 2008-10-17
forum: Virtualisation
---

### Post by iomega on 2008-10-17
I am a beginner in virtualization. I recently installed VMware Server 2.0 on Hardy (8.04). Installation was fine, I started firefox and logged in as root and created a virtual machine (OpenSuse 11.0). Physically, this virtual machine resides on an external USB hard drive. I can run this VM fine, without any problems, network works fine too. 

Now when I am done playing with VMware and reboot the Host (Hardy here), and re-start VMware in firefox, I don't see my virtual machine (even though external hard drive is mounted and I can see all the files). I get a message 

"Virtual Machine Configuration File inaccessible"

At this point of time, as an experiment, I re-ran vmware-config.pl and restarted firefox and vmware, it did see my Virtual Machine and I was back to normal. But with next Host OS reboot, I am back to square one where I don't see my Virtual Machine at all.

Any clues? Any lock file getting generated which I have to remove?

---

