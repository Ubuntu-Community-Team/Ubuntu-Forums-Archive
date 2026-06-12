---
title: "Lightning Calendar"
date: 2010-10-31
forum: Ubuntuzilla
---

### Post by Krister Hallergard on 2010-10-31
Have just installed Kubuntu 10.10 Maverick 64-bit - works fine. Using xul-ext-lightning (lightning 1.0b2) with a symlink for local.sqlite to the same on the Windows 7 64-bit partition, I can have the same calender on both partitions.

I also have a Kubuntu 10.04 Lucid LTS 32-bit partition and I would like to do the same, but cannot do it. When trying to install lightning 1.0b2 I get the message "not compatible with Thunderbird 3.0.10". So I disable the compatibilityCheck and it installs okay. But the calendar does not show any data with the symlink. Why is that? Different sqlite versions?? Or is it so that the 64-bit data cannot be read by a 32-bit program??

So I try older versions of lightning.xpi - no luck. After some additional googling I try installing Thunderbird 3.1.6 32-bit using Ubuntuzilla. Compatibility OK with 1.0b2 but still no calendar data using the symlink.

Help would be very much appreciated.

---

### Post by Krister Hallergard on 2010-11-01
Solved by changing the format from sqlite to ics

---

