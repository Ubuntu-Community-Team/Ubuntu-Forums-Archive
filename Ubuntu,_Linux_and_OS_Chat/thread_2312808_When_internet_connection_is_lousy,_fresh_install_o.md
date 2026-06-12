---
title: "When internet connection is lousy, fresh install or update thru &quot;...Updates&quot;?"
date: 2016-02-07
forum: Ubuntu, Linux and OS Chat
---

### Post by KayeNg on 2016-02-07
Hi.  Our internet connection is really unreliable--disconnections every now and then on certain days.  Once the new LTS version is released, if I update via terminal or thru "Software and Updates", and got disconnected, would it corrupt my system?  Should I do a fresh install instead to be safe?

Thanks

---

### Post by egeezer on 2016-02-07
My own choice will always be fresh install for any version, but especially so for an LTS version. I also have uncertain connectivity at times, so the reassuring thing about downloading an ISO and installing it is that you have the checksum to assure you it went okay - not available for updates.

---

### Post by Bucky Ball on 2016-02-07
*Thread moved to **Ubuntu, Linux and OS chat**.*

So we presume you are using 15.10 or 14.04 LTS? You can't upgrade to 16.04 LTS from anything else. You don't mention this important information. 

If you upgrade via the net, disable any PPAs you have added manually, try to get the machine as close to 'vanilla' as possible, and update/upgrade your install before you upgrade your release. Make sure you use an ethernet cable and not wireless. 

Apart from that, up to you, really. Good luck. :)

---

### Post by KayeNg on 2016-02-07
Thanks guys. Right now I'm using 14.04.  I believe it's possible to upgrade directly from 14.04 to the next LTS, 16.04. Am I wrong?

Also, upgrading via the net--would it take longer than a fresh install?

---

### Post by Bashing-om on 2016-02-07
KayeNg; Hey ...

Thing here is that 16.04 has not to this time been released ( 16 == 2016 and 4 == April ) the option to release upgrade to this release will not be available until the 16.04.1 is release.

If you really want to install the alpha 16.04 .. there are means to do so .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by kansasnoob on 2016-02-08
> Should I do a fresh install instead to be safe?

Yes! 

Even with a reliable connection the failure rate of release upgrades is far too high. The live DVD/USB does offer a more reliable upgrade option if certain criteria are met:

[ATTACH=CONFIG]267186[/ATTACH]

I realize that's a rather old screenshot but the process has not changed significantly.

**But step #1 for any release upgrade or re-installation should be to create a backup of anything important!** It's rather like insurance - if you have it you'll seldom need it, but if you don't have it you'll undoubtedly end up needing it ;)

---

### Post by monkeybrain20122 on 2016-02-08
Fresh install always. Even if you have an unmodified system (no ppa, no third party software or driver, no customized configurations) it will take a long time during which a lot of things can go wrong, e.g losing internet connection, power failure.. and if your system has been modified significantly it will take you more work to return it to the default configuration than to just do a fresh install, and if your system has been modified and you don't take care to return it to the default condition upgrade will likely fail and leave you with a broken system after waiting for an hour or more.

It is good to make a separate /home partition, that way you only need to format and install into the root partition and leave the /home untouched, that way all your settings and data will be saved.

---

### Post by Bucky Ball on 2016-02-09
I've never ever had trouble with an upgrade via the net. Mind you, I run a fairly vanilla system and rarely add a PPA. Disable them for an update.

Update, switch off manually installed PPAs, use an ethernet cable, not wireless, and go for it. Always backup, as mentioned, so if it for some reason doesn't work, a clean install it is and you have your valuables backed up.

Just throwing that in. An upgrade via the net does take a lot longer, though. About two hours compared to, say, half an hour. Good luck however your roll. ;)

---

