---
title: "Ubuntu Server on a laptop -- auto suspending on AC power loss?"
date: 2015-11-07
forum: Server Platforms
---

### Post by Roasted on 2015-11-07
Hello friends. In an effort to segregate some items on my network I split ownCloud off of my main server, effectively making my server a regular NAS with nothing facing the outside. This allows me to put what few external things I have (namely ownCloud and ZNC) on a separate box altogether. The ownCloud server in question was installed on an old laptop. So far everything has been great, as ownCloud is wildly zippy on this older i5/4GB RAM/500GB HDD laptop and sips only a few watts of power. Okay, great.

Thing is, I had assumed (...ha) that it being a laptop would help serve it as a UPS with the battery. After setting it up over SSH (laptop-server was sitting here with the lid closed), I yanked the power to reroute it to its permanent home. In that process, the laptop-server went to sleep. I assume an acpi function auto-suspended it when AC power was lost. Naturally this isn't my end goal, as I want the laptop-server to just keep running on battery after that with no intervention needed from me.

What can I alter/edit/install to change this behavior? If AC power is lost, I simply want this laptop to continue on using battery power as long as it can. Any ideas?

Thanks much!

---

### Post by TheFu on 2015-11-07
[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

---

