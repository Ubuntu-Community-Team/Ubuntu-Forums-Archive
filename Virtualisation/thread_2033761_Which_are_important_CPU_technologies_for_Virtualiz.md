---
title: "Which are important CPU technologies for Virtualization?"
date: 2012-07-26
forum: Virtualisation
---

### Post by yeehi on 2012-07-26
There are lots of technologies available to help make virtualization better. You can do a filter search for Intel CPUs [here]("http://ark.intel.com/search/advanced?FamilyText=3rd%20Generation%20Intel%C2%AE%20Core%E2%84%A2%20i7%20Processors"). You can select which virtualization technologies you need.

The question is, which are the important/best ones?

There is discussion about Hardware Assisted Virtualization in Intel [here]("http://www.intel.co.uk/content/www/uk/en/virtualization/virtualization-technology/hardware-assist-virtualization-embedded-technology.html?wapkw=virtualization+technology").

Are AMD and Intel about the same when it comes to virtualization?

Thank you!

---

### Post by CharlesA on 2012-07-26
Both AMD and Intel CPUs can support Hardware Virtualization.

---

### Post by Habitual on 2012-07-27
[http://www.bit-tech.net/search?q=Hardware+Assisted+Virtualization](http://www.bit-tech.net/search?q=Hardware+Assisted+Virtualization)

---

### Post by Dr. C on 2012-07-28
It is best if the processor supports the Intel-VT or AMD-V instruction sets; however virtualization will work on older processors that do not support Intel-VT or AMD-V.

Here are the links:
Intel: [http://ark.intel.com/Products/VirtualizationTechnology]("http://ark.intel.com/Products/VirtualizationTechnology")
AMD: [http://sites.amd.com/us/business/it-solutions/virtualization/Pages/virtualization.aspx]("http://sites.amd.com/us/business/it-solutions/virtualization/Pages/virtualization.aspx")

One thing to keep in mind here is that many large OEMs ship their systems with Intel-VT or AMD-V turned off in the BIOS.

---

