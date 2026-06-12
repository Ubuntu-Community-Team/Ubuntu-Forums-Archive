---
title: "Hybrid HDD firmware update"
date: 2012-01-29
forum: System76 Support
---

### Post by MoebusNet on 2012-01-29
I have some questions about my serp7 HDD:

model: Seagate Momentus XT ST95005620AS
version: SD26
serial: 5YX14LFE
description: 500GB 7200rpm SATA Hybrid Hard Drive with 4GB SSD

Apparently there is a firmware update SD28 available for this drive:

[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=215451](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=215451)

The software for determining model number, serial number and firmware revision is apparently Windows-only.

EDIT: used "sudo lshw" in terminal

1) Is there a preferred method of confirming whether or not I need this firmware update under Ubuntu?

2) If I need this firmware update, is there a preferred method of performing the update under Ubuntu?

Any information would be welcome. TIA

---

### Post by isantop on 2012-01-30
Your drive is affected, given the model number. The preferred way to upgrade would be to use the bootable .iso image, and burn it to a cd as if you were creating an Ubuntu disk. 

That said, I can't find any documentation that says what this update fixes. It may not be an issue for you anyway; a lot of firmware update are generally made to fix issue in Windows.

---

### Post by MoebusNet on 2012-02-03
Marking thread as "solved". Contacting Seagate Support to determine if Ubuntu/Linux issues are addressed in updating the firmware from SD26 to SD28. I'll post results here.

EDIT: Contacted Seagate Support. Bottom line: They could/would not say if the firmware update would address Ubuntu/Linux issues. They did state that the firmware update was "recommended". Downloaded SD28 firmware update & burned to CD. Followed directions, booted from CD, confirmed drive model compatibility from menu, loaded updated firmware. Powered off (pressed power button until shut-off) as per directions. Booted Ubuntu as normal. Initial boot after firmware update seemed about 3 seconds, subsequent boot times returned to about 20 - 25 seconds. The hard drive does not seem to "hang" as it did before.

---

