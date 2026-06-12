---
title: "cooling fan won't run at the right time"
date: 2024-01-12
forum: System76 Support
---

### Post by Skaperen on 2024-01-12
last night, the power went out, while my old Kudu Pro laptop from 2014 ran on battery.  i shut down my Xubuntu 20.04 LTS system and powered off.  turns out it was just a power flicker but the power supply box shutdown and quit sending 19vDC to the laptop.  i forgot that it is known to do that until after i shutdown the whole system.  i reset the power supply by unplugging and plugging back in.  now the 19vDC was back and the battery was recharging.  i booted up while it was still in recharge.

i was running an ffmpeg process that was using about 300% CPU (according to top) which was also running the cooling fan about 4 or 5 speed steps up.  i have done this a lot over the past year converting hundreds of MP4 videos to WEBM format, which is much smaller.  i presume the recompression is what uses so much CPU.  perhaps ffmpeg is running multiple threads in that one process to make use of the many cores we have these days.

now, the cooling fan does not come on at all.  is it a dead fan?  i think not because it does occasionally come on when i do a few heavier commands.  it just does not come on at all when i do another ffmpeg based recompression.

any ideas why this is?  any BIOS settings i should check?

---

