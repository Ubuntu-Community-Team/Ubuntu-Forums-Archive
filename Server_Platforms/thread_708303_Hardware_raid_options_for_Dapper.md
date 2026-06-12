---
title: "Hardware raid options for Dapper"
date: 2008-02-26
forum: Server Platforms
---

### Post by winebottle on 2008-02-26
Hi All,

I'm after any/all suggestions for a very robust hardware raid card to Raid 1 (mirror) using two 500Gb Sata discs. Mother board has yet to be spec'd or indeed anything else - I'm primarily concerned about data loss and easy recovery.

I work for a small company hence we're not swimming in Ubuntu'linux know how or the time to research/fix dead equipmement hence the request on hardware raid which I'm hoping will allow us to.

a) seemlessly shift onto the mirror in the event of failure
b) notify us of failure
c) allow a swap or hotswap of possible
d) boot on th mirror if required

- ie we require minimal human intervention in the event of a failure.

The MegaRaid Sata 300-4X looks man enough but knowledge of the experience of others would be very handy.

All sugesstions welcome!!

---

### Post by Brazen on 2008-02-29
I've used several MegaRaid cards with linux and they work wonderfully.  Our 3 most critical servers right now all run linux and all have MegaRaid cards (actually they are Dells with the MegaRaid chip integrated into the motherboard).  They've been in 24/7 operation for a year and a half now with no problems.

I have another critical server with the MegaRaid Sata 300-4X card in it, with 4 harddrives running in Raid 5, that has been in 24/7 operation for over 3 years.  The motherboard was replaced once, but the MegaRaid card is the original and never had a problem.  This server actually runs Windows, but I would be surprised if this card had any problems with Linux.

---

### Post by polmir on 2008-02-29
Read this
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Create_A_Mount_Point_For_The_RAID_Set]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Create_A_Mount_Point_For_The_RAID_Set")

---

