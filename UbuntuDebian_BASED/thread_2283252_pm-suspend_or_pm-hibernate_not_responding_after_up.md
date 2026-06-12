---
title: "pm-suspend or pm-hibernate not responding after upgrade to 14.04"
date: 2015-06-20
forum: Ubuntu/Debian BASED
---

### Post by Jyrki_Majamki on 2015-06-20
Well my "upgrade" to 14.04 went balls up - so it's rather new installation. I installed kodibuntu, but AFAICS it's lubuntu?
Never mind the problem is rather general. In my former installation with xbmcbuntu the suspend and hibernate worked
just fine, so I know that my hardware is up to it.

Now I get nothing when I give pm-suspend or pm-hibernate into terminal.
However, if I go for example to 
sudo -s
echo -n "platform" > /sys/power/disk  
echo -n "mem" > /sys/power/state

I get a nice suspend or with "disk" I get hibernate. Only lirc would not be working but that's minor. 
What is it that is bugging pm-suspend and pm-hibernate commands - aren't those commands not exactly 
what they are doing?

I see no hints in dmesg or in /var/log/pm*** why it is not working and I have no idea where to look next

---

### Post by howefield on 2015-06-20
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by thenh813 on 2015-06-22
Hmm... those commands are scripts, are they not? (someone correct me if wrong)
Maybe different hibernate executable versions, usage syntax changes or filename changes caused it.
If all else fails, I would suggest commenting out every line in those scripts or the parts causing problems.
Or just replace the scripts with new ones containing the hibernate/suspend command and noting else. XD

I know it's a evil hack, but it sure helped me make my custom OS work till I finished it and ironed out the bugs.
Rewrote all the scripts myself bit by bit after figuring out their functions and custom compiled stuff till I made it perfect.
Would only recommend this as a last resort or debugging method, by overriding the default script actions.

I am nearly certain it's caused by updated files, or ones who were moved/removed that it expects to have.

---

