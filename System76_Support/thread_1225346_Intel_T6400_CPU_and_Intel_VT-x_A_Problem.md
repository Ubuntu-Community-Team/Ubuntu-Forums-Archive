---
title: "Intel T6400 CPU and Intel VT-x: A Problem?"
date: 2009-07-28
forum: System76 Support
---

### Post by bill516 on 2009-07-28
The Intel T6400 CPU is a popular choice in current products for good reason.  It is reasonably fast and it has power draw and heat dissipation characteristics that make it a viable choice for laptops such as my System 76 Pangolin.  Like most recent Intel products it handles 64 bit operating systems.

There is, however, one limitation I have discovered that no one has talked about it, at least that I can find.  Very simply, the T6400 does NOT include the code for Intel's virtualization technology, or "Intel VT-x".  I had assumed this was a standard feature on Intel dual-core CPUs.  It is not.  (Go to [http://ark.intel.com/Product.aspx?id=40479](http://ark.intel.com/Product.aspx?id=40479) for the Intel T6400 spec page.)  This limitation means absolutely nothing if you do not run virtual machine technologies such as Virtual Box.  If you run a platform such as Virtual Box in support of 32 bit guest systems you also will not see the problem.

However, if you choose to run a 64 bit guest on your 64 bit T6400 host system, Virtual Box is going to tell you that your "32 bit host system" cannot support running a "64 bit guest" and it will immediately abort loading the guest.  Now I have not tried any other virtual machine software such as the VMware products or Qemu, but if I use Virtual Box this is true for any 64 bit guest I try to load.

I do recall that the Virtual Box manual says something about needing VT-x, but I do not know any vendor site that makes it easy to see that characteristic of the CPUs being offered.

Note that if I run something like hardinfo my T6400 - or any dual core processor - shows up twice, as though the machine had two entirely separate CPUs.  From that I will infer that Virtual Box - and any other virtual machine software? - sees and uses only one of the cores if Intel VT-x is not present?

In any event if you are ordering a new system with an Intel CPU and you intend to make use of virtual machines you might want to check the specifications for your preferred processor and make certain it supports Intel's virtual machine instructions.

Because my machine is a System 76 Pangolin with which I am very well satisfied I will post this on the System 76 support site in the Ubuntu forums.  I'll also post over at ExtremeTech, where masinick and jrst have carried on a very interesting discussion about virtual machines.  If someone here knows that the problem is not so dire as I report, I hope they will say so!

I do not want to spread misinformation, but I also do not want to see someone make an expensive mistake.  So until this is clarified further do check those CPU specifications before you purchase your new machine!

Tom Aaron:  Assuming I am right about all of this, would it be reasonably easy for System 76 to add this information for each CPU it offers?  If System 76 can do it that might be a good thing.

---

### Post by thomasaaron on 2009-07-29
It should be reasonably easy. I'll talk with my supervisors about it.

---

### Post by bill516 on 2009-07-29
Thank you!  The interest in vm's seems to be growing and this is another way System 76 could do a small but much appreciated thing for potential customers.  I hope you can pull it off.

Have a good day!

---

