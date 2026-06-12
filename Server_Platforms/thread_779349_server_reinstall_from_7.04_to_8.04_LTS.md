---
title: "server reinstall from 7.04 to 8.04 LTS"
date: 2008-05-02
forum: Server Platforms
---

### Post by tha_toadman on 2008-05-02
So I decided to reinstall my Ubuntu OS after about a year of service and install 8.04 Server (alternate) from scratch. I like the command line and am getting quite comfortable with it.

Anyway, my boot time was almost 30 seconds with 7.04 Server (alt) but now the 8.04 Server (alt) is taking almost 2 to 3 minutes to boot! I jumped on IRC last night and spoke to someone who thought that first, it was IPv6 slowing it down but after disabling that, it was still slow. That person then said that I might be impatient but I said 'I disagree' as it wasn't an issue in the previous installation/version.

My assumption (correct me if I'm wrong) is that the numbers in [] during the boot are a clock/timer. If that is true, then around the 26 second mark, when my "eth0: link is up" appears, it hangs...and hangs...and hangs...then eventually, at 204 seconds, it'll proceed with the startup BUT...there is a [fail] and I can't seem to figure out what the [fail] is from. There's really no description next to it but then the *Setting up clock* message appears and finally, after about roughly 3 minutes (or so), I have a login prompt.

I have a Gigabyte motherboard and a Core 2 Duo. If any other information is needed, please let me know. Otherwise, I'm lost as to what might be causing this?

---

### Post by tha_toadman on 2008-05-13
CLOSE THIS THREAD!

No one seemed to know what was up...and I'm not entirely happy with 8.04 LTS so reverted back to 7.04 since it "just worked".

---

