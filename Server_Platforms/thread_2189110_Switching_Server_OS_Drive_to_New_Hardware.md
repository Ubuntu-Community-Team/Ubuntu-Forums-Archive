---
title: "Switching Server OS Drive to New Hardware"
date: 2013-11-20
forum: Server Platforms
---

### Post by ooboontwo on 2013-11-20
Hi everyone,

Would I be able to take a hard drive that has Ubuntu server installed on it out of one PC, place it in another PC with different hardware components, and be able to boot from it successfully?

Thanks,
Cody

---

### Post by oldfred on 2013-11-20
Did you install proprietary drivers for video or Internet? If not it probably will work.

But you cannot go from a BIOS system to UEFI system unless you set a new UEFI system to boot in CSM/BIOS/Legacy mode.

New PC may also need different boot options to accommodate different hardware. 
How different is system.

I put a new motherboard and newer nVidia card in my system a few years ago & it just booted without complaint.

---

### Post by nerdtron on 2013-11-21
If it is a server without a GUI you wouldn't install any proprietary video drivers.
The best way to do it is to test it. Just plug the hard drive to the new server and boot. If all hardware is supported, it will most likely boot without any problems.

---

### Post by ooboontwo on 2013-11-22
Thank you for your responses.

The situation I mentioned is theoretical. I work in IT for a small company that is wanting to create a failover system for their file server. They have their data backed up in Raid 1, but if the motherboard or CPU failed we would need to move the drives to a new system (the failover).

However, I wasn't sure if the OS drive for the file server would work in a new machine with different hardware.

In this scenario, the CPUs would be very different. The original server has a dual core Intel processor. The machine it would be transferred into would have a quad core AMD processor. If that helps...

Any further thoughts are appreciated.

Thanks again,
Cody

---

### Post by oldfred on 2013-11-22
Understand RAID is not a backup, I hope your company does have backups somewhere.

And RAID is often dependant on how it is configured. If hardware RAID you need the same RAID card. If BIOS based or fakeraid you need the same BIOS. I think the most flexible to convert to another system is Linux mdadm raid.

 If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

---

### Post by trundlenut on 2013-11-23
Your network connection will also go wonky as the network card(s) in the new hardware will have different MAC addresses.  for example eth1 will not work and a new eth2 will appear.

---

### Post by nerdtron on 2013-11-24
Motherboard and CPU are simple. The problem is the RAID controller. Only the RAID controller knows which drive is which. When you swap out the CPU and motherboard, you should still use the old RAID card to recognize the Hard drives. If the RAID controller is toasted, i don't know what happens to your data, so I strongly recommend you backup your important data on a separate machine.

---

### Post by ooboontwo on 2013-11-25
Thank you for all the replies.

To answer a few questions: Yes, the company has an offsite backup and is not using Raid 1 alone as a backup (this is just for redundancy, as the term 'raid' implies). The HDDs are in software raid using mdadm.

So, suppose the motherboard goes out on the main file server. What is the best way to move those disks to a new computer and get mdadm software raid working again (as quickly as possible)?

Thanks,
Cody

---

