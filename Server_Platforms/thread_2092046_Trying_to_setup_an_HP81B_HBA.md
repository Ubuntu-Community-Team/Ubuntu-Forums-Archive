---
title: "Trying to setup an HP81B HBA"
date: 2012-12-06
forum: Server Platforms
---

### Post by le_jawa on 2012-12-06
All,

I posted this in the Hardware forum, and thought I ought to put it in the server forum, as this is probably a better place for this question...

I'm setting up new Ubuntu servers (12.04) on a couple of HP DL385 G7s with HP  81B HBAs  (they're Brocade 815s with a different SFP).  Does Ubuntu  include a driver for that HBA that I can install, or does anybody know  where I can grab a driver for it?   I've already downloaded the driver  pack from Brocade, but it depends on X, and I'm trying to avoid  installing a GUI if possible.  I'm also not 100% sure that the Brocade driver would work.

Thank you,

Jason

---

### Post by darkod on 2012-12-06
I would say boot with the server cd and start the install. Whenyou reach the partitioning step select manual partitioning and see if the disks are recognized and listed.

If the card is not recognized, there will be no disks.

It would be much faster then waiting for someone that has experience with exactly the same card. Only if you confirm you have a problem, you need to start looking for a solution for it.

---

### Post by le_jawa on 2012-12-12
Thanks for the reply, darkod, but I'm already way past that.  The installer never did pick up the HBAs or the LUNs attached to them.  I've seen drivers online for RedHat and its variants, but nothing for Debian-based systems.  I switched to CentOS and got what I needed.

---

