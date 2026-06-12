---
title: "a small testimonial"
date: 2007-04-20
forum: Testimonials &amp; Experiences
---

### Post by srt4play on 2007-04-20
I've used Ubuntu at home for about 2 years and at work on my laptop for about 1 year now.  It is such a great tool that has allowed me to be more productive and more efficient at solving problems.  I'm a technician for Macy's and just wanted to share this email I recently sent to another technician on my team.  He uses Ubuntu at home and is considering running it on his laptop like I do.

> The manager's PC at regency furniture would not boot up after a power failure. The windows splash screen would appear for a few seconds and the PC would then reboot.  Safe mode, last known good configuration, normal startup, none of these would boot Windows.  First attempt to fix was with a Windows XP install cd using recovery console. It could not even display the contents of the drive.

Went home, got a feisty beta cd, came back and booted it up.  Created a connection to the public netowrk drive for data backup. Opened a terminal and mounted the windows partition, Ubuntu had no problem seeing the data, but could not copy it to the network drive. I had to install 'ntfs-3g' in synaptic, create /mnt/windows with 'sudo mkdir /mnt/windows', and mount it with 'sudo ntfs-3g /dev/sda1 /mnt/windows -o force'.  I then could copy his data to the network drive.  I then ran 'sudo ntfsfix /dev/sda1' and it reported fixing some errors.  Rebooted the PC and Windows booted right up.

Lesson learned, ALWAYS carry an Ubuntu live cd. 

---

### Post by earobinson on 2007-04-20
Thanks! Always nice to see feedback!

---

