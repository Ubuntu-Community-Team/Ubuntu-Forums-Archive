---
title: "VMware vCenter Converter Standalone fails at 97% with the error: Error installing GRU"
date: 2018-02-21
forum: Server Platforms
---

### Post by nanoanxo on 2018-02-21
Hello,
I want to virtualize a linux physical machine (Ubuntu server) in a virtual machine.
I followed the steps of this guide: [https://www.joe0.com/2017/01/12/how-to-convert-a-remote-physical-linux-server-to-a-virtual-machine-vmware-virtualbox-instructions/](https://www.joe0.com/2017/01/12/how-to-convert-a-remote-physical-linux-server-to-a-virtual-machine-vmware-virtualbox-instructions/)
All was well until I tried to convert physical machine with VMware vCenter Converter Standalone tool, so that, I had an error before to end the task:
[https://ibb.co/gQNMYH](https://ibb.co/gQNMYH)

[IMG]https://es.imgbb.com/[/IMG]I looked for information about this issue and I found an article in the knowledge base of VMware: [https://kb.vmware.com/s/article/2052628](https://kb.vmware.com/s/article/2052628)
1. Mount the original Linux distribution DVD on the virtual machine and boot from DVD à OK
[https://ibb.co/hd8dVx](https://ibb.co/hd8dVx)

2. Select the rescue option from the boot menu à OK
[https://ibb.co/ciNSOH](https://ibb.co/ciNSOH)

3. Identify the disk containing the root file system à I have a doubt
If I select, the first option, I have this issue:
[https://ibb.co/fUXNqx](https://ibb.co/fUXNqx)
[https://ibb.co/dCCcOH](https://ibb.co/dCCcOH)

So, I select the next option:
[https://ibb.co/eV7Yxc](https://ibb.co/eV7Yxc)

[COLOR=#3D3D3D][FONT=&quot]4. But, when I select the step 4: **Select the option to initiate a shell.**
[/FONT][/COLOR]
[B][https://ibb.co/cSRRHc](https://ibb.co/cSRRHc)

[/B][COLOR=#3D3D3D][FONT=&quot]5. And I try to do the step 5: **Fix the BIOS boot partition.**
[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&quot]In the example says:
[https://ibb.co/bRU2qx](https://ibb.co/bRU2qx)

But, when I execute these commands, I don´t have a similar screen:
[https://ibb.co/eeC0cc](https://ibb.co/eeC0cc)


[/FONT][/COLOR]

---

### Post by LHammonds on 2018-02-21
I have not ever tried to p2v a Linux server before.  Not sure I'd want to either if I could avoid it.  Drivers and configuration are always a mess no matter what OS you use.  Only time I did p2v were Win2003/2008 server that I had no idea how they were setup...typically because it was an emergency scenario due to failing/failed hardware and didn't have time for trial-n-error.

Can you install a clean Ubuntu server in vmware, then install the applications and do data backup/restore?  Basically a migration?

LHammonds

---

