---
title: "bit-for-bit archiving of music cd-rom"
date: 2015-06-28
forum: Ubuntu, Linux and OS Chat
---

### Post by Eduardo_Sanchez on 2015-06-28
Does anyone have advice on bit-for-bit archiving of music CD-ROMs?

I am *not* interested (at this stage) in converting to either a lossy or lossless format.

Right now I am only looking to make a bit-for-bit backup of all of my music CD-ROMs.

Once I have everything backed up bit-for-bit, I will consider my future options for lossless encoding (probably FLAC). 

I'm interested in the tools and formats that you have in mind. 

Thanks in advance! :p

---

### Post by TheFu on 2015-06-29
You can use dd or **ddrescue** to make a bit-for-bit copy of most optical media.
I've never tried it with audio discs, but it does with with other media - assuming the disc can be read.
Whenever making archives, it is smart to add extra parity validations - I've found that par2 with 10% parity has allowed me to recover data that otherwise would have been lost. [http://blog.jdpfu.com/2011/06/12/optical-data-recovery-technique-with-ddrescue-and-par2](http://blog.jdpfu.com/2011/06/12/optical-data-recovery-technique-with-ddrescue-and-par2) explains.

---

