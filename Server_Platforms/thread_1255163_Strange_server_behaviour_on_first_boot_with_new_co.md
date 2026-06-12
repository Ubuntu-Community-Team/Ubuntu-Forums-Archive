---
title: "Strange server behaviour on first boot with new config files"
date: 2009-09-01
forum: Server Platforms
---

### Post by PryGuy on 2009-09-01
Good day to you all!

My problem is really strange!
I have made a Server postinstall CD that has it all, hand made config files, deb packages and installer. The install process goes this way:
1. Script installs .deb files.
2. Script copies config files.
3. Script reboots.

So on the next (first with new configs) boot I get the following problems:
- Bind's does not update the view for the internal network if a new computer registers over DDNS. It does it for the localhost view only.
- Squid users with bandwidth limit exceed their full-speed quota and Squid starts ignoring their PCs instead of cutting the speed. Everything's fine for the users without the bandwidth limitation.

Reboot solves the problem completely. It works fine on the second boot!
But why it occurs when I boot the machine for the first time? Is it normal?

I've noticed one thing, the time gets shifted by +4 hours when I perform install and postinstall 'cause installer probably thinks that PC time is GMT, but it's not. It updates only on the first boot with Internet access, and probably after the Bind and Squid daemons start. The timestamps on the config files are +4 also. 

Another thing I suspect is DHCP server. I don't even know what output should I post here. Any ideas would be great! Thank you in advance!!!

---

### Post by PryGuy on 2009-09-01
UPDATE: It appears that the time is the problem. What I've done:
I set BIOS time to GMT.
Reinstalled Ubuntu Server.
Rebooted.
Ran my postinstall script.
After it finished I did 'date' and it was really strange: Say the GMT is 10.00, my zone is +4, so it had to be 14.00, but it was 18.00!!! So it appears that I've found a bug by the way.

Will check and recheck again, but it really looks like it all happens because of the incorrect time settings.

---

