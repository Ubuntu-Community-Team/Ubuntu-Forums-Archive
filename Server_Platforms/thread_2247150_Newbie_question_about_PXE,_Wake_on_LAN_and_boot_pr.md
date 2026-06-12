---
title: "Newbie question about PXE, Wake on LAN and boot priority"
date: 2014-10-06
forum: Server Platforms
---

### Post by peterwilson-69 on 2014-10-06
I'm in the process of setting up a private cloud, and I'm reusing old servers that were lying around (with previously configured BIOS). This might be a dumb question, but what should be the boot priority?

1) Wake on Lan with PXE 
2) SATA drive

or 

1) SATA drive
2) Wake on Lan PXE


I've also got a DELL Precision 670 that gives the option to Wake on Lan and PXE boot before the normal boot sequence starts? : / 

I only ask because I'm not sure what the screen should look like on a commissioned node that's Ready. Is it supposed to show a login prompt with fingerprint and ssh host key keys information? Another time I was experimenting with BIOS boot order and it just showed a minimal login prompt (no fingerprint information). Also, when I changed it back, it did a full install again as if the node wasn't previously commissioned.

Thank you.

---

### Post by nerdtron on 2014-10-06
Building a private cloud. This will be a long study and many trial/error experiments. Goodluck!

Anyway, to answer your question, where do you install the OS and the boot loader of the server? If you don't plan to use PXE, why set it up on the first priority? It will just consume a few more seconds on boot-up while it checks the network. So set the sata drives as the first boot priority.

> Is it supposed to show a login prompt with fingerprint and ssh host key keys information?
I think this is applicable to the VMs in the cloud environment and not on the cloud nodes themselves.

---

### Post by peterwilson-69 on 2014-10-06
Thank you. I'm booting to hard drive first and that shows a much more familiar login prompt (no ssh/fingerprint info at the login prompt).

I just got confused because most of the time I booted from the NIC/PXE it did a full install almost every time (which I knew was wrong), however, on one occasion, it did a PXE boot and full install, but then it looked like the server said, "nah, you're already done, boot from hdd instead". So that's why I asked about the boot order - I thought perhaps it was always best to boot from NIC/PXE and let the Cluster Control determin the boot device. Meh.... I'm probably not making sence, just have a lot to learn.

Thanks again : )

---

