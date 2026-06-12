---
title: "Setting up RAID on Bonobo Extreme"
date: 2012-12-13
forum: System76 Support
---

### Post by bdensmore on 2012-12-13
I just got my Bonobo Extreme delivered a couple of hours ago. 

Because this is a work machine, they asked me to enable RAID and mirror the 2 750GB drives that we had put in the machine.

Once I mirrored the drives, it wiped all data on the machine.

Can I install just plain ole Ubuntu 12.10 or is there a System76 specific disc I should use for the install?

Thank you,

Ben

---

### Post by isantop on 2012-12-13
> **bdensmore said:**
> I just got my Bonobo Extreme delivered a couple of hours ago. 

Because this is a work machine, they asked me to enable RAID and mirror the 2 750GB drives that we had put in the machine.

Once I mirrored the drives, it wiped all data on the machine.

Can I install just plain ole Ubuntu 12.10 or is there a System76 specific disc I should use for the install?

Thank you,

Ben

You should use a plain Ubuntu disk, then use the System76 Driver available [here](http://planet76.com).

Our full restore instructions are available on our knowledge base, here: [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

I should also point out that we don't officially support RAID on the Bonobo, since you have to use a software RAID.

---

### Post by bdensmore on 2012-12-13
Thank you for the info.

Are you saying I need to do additional steps for RAID other than using the utility that set up the RAID mirroring or saying you don't support it because of that utility?

---

### Post by isantop on 2012-12-13
> **bdensmore said:**
> Thank you for the info.

Are you saying I need to do additional steps for RAID other than using the utility that set up the RAID mirroring or saying you don't support it because of that utility?

No, we don't support software RAID setups because they're highly unstable and likely to cause data loss, compared to hardware RAID setups. They don't meet our quality standards. The System76 Driver won't change your RAID at all, and it should work just fine with the RAID. We just don't do any testing on it, and don't recommend that configuration.

---

