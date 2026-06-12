---
title: "Reboot hang after package install"
date: 2012-07-29
forum: Server Platforms
---

### Post by hozzaconners on 2012-07-29
After installing package updates I do a sudo reboot, and 90% of the time the server hangs at the end of the shutdown process. The screen output shows what looks to be a memory dump, with lots of lines that look like:
[2057735.721305] some string of charcters
the last line is always
[2057735.721305] ---[ end trace b9905cc5d19ca434 ]---
It then sits there and I have to pull the power.

If I issue a sudo reboot normally (without updating packages) it restarts without an issue.

I have no idea how to go about figuring out what's causing the hang. I've tried looking through the logs, but none of them seem to give details of the shutdown process...I can't find "end trace" anywhere...

Does anyone have any ideas/pointers/advice/previous experience on this?

I'm running Ubuntu 12.04 on a HP proliant microserver. If there's any further info I can get to help with this please point me in the right direction?

Cheers!

---

### Post by Laiquendi on 2012-07-29
I have had the same issue few times.
Mounted devices (discs) caused this problem and the solution was to unmount them before shutting down/restarting.
I've seen this issue few times and it was always that, but then I can't be sure if it's the same here ;)

---

### Post by hozzaconners on 2012-07-29
Thanks Laiquendi, I'll give it a go after the next update. Do you know of a quick "unmount everything" command? What's the easiest way of doing that? Excuse my ignorance?!

Cheers

---

### Post by damantei on 2012-10-28
Anyone had any success? I cannot get my server to install on my new build. Installs all the way to 85% and then says that it cannot install any further because of package install errors.  DHCP package install errors

---

