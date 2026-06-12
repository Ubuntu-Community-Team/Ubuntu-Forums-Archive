---
title: "KVM w/ Windows 7 Guest video streaming (to xbox) issues"
date: 2012-08-10
forum: Virtualisation
---

### Post by justinmiller621 on 2012-08-10
I'm running Ubuntu 12.04 host and a Windows 7 Pro guest. I'm running Windows Media Center in the guest so that I can use my Xbox 360 as an extender. I have an HDHomerun Prime on my network that's serving up the video stream.

64 bit host, 32 bit guest.

I'm using the virtio drivers for both my disk and the NIC. I'm also using bridged networking. I setup a br0 device, as per the instructions on KVMs site. I didn't setup a tap interface though as I've seen here. What is that exactly and why would it be needed if the br0 device is doing the trick?

The hdhomerun, my server running the Win 7 guest and the Xbox are all hardwired to a gigabit router. 

Everything runs pretty smooth, except once every 45-60 seconds, give or take, I experience a 'hiccup' in the video stream. If I'm looking at a bandwidth graph (in dd-wrt), I see a small dip in throughput that coincides with the video hiccup.

I've tested this with a bootcamp install of Win 7 on my MacBook and don't experience this issue, so I'm thinking it's related to the VM somehow. 

I wondered if it was the NIC driver, so I'm in the process of trying different ones, but so far, they all experience the same issue.

I read briefly about time sync issues. Is it possible this could be the culprit?

I have 8GB of memory in the box and I've given anywhere between 1.5-4GB to Windows with the same outcome.

I'm not sure what else to do to troubleshoot this.

Any help would be appreciated.

Thanks,
Justin

---

### Post by justinmiller621 on 2012-08-11
I set Windows to use the platform clock, as per:

[http://docs.fedoraproject.org/en-US/Fedora/13/html/Virtualization_Guide/chap-Virtualization-KVM_guest_timing_management.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Virtualization_Guide/chap-Virtualization-KVM_guest_timing_management.html)

It may have helped some, but I still see hiccups. 

Any ideas?

Thanks,
Justin

---

### Post by slooksterpsv on 2012-08-14
Just as a personal item, I've had bad luck with network utilization and KVM. I'd look into VMWare or VirtualBox and see if those help (you should be able to import your current install to those pieces of software).

When I'd use KVM I would only get about 1-10% of my full network capabilities.

---

### Post by justinmiller621 on 2012-08-15
I actually was using VirtualBox and switched because I was seeing the same issue. Though at the time I was wireless. So maybe it'll be interesting to try it again now that I'm wired. I'll give it a go and report back.

Thanks for the reply.

Justin

---

### Post by justinmiller621 on 2012-08-17
Son of a b#%$h. VirtualBox worked like a charm. I DID also move my disk image to my RAID5. But I record to a network share so I can't imagine there's much reading and writing to the 'disk'. 

Thanks for the suggestion!

---

