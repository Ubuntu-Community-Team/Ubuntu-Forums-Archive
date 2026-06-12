---
title: "ugh. how can i kill apparmor for apache"
date: 2011-08-20
forum: Server Platforms
---

### Post by inphektion on 2011-08-20
I had tried setting up an apparmor profile for apache but now its just causing all kinds of grief.  My logs are filling up with stuff like:
type=1502 audit(1312435921.994:54686):  operation="file_perm" pid=2305 parent=1797 profile="/usr/lib/apache2/mpm-prefork/apache2//null-c3a" requested_mask="::w" denied_mask="::w" fsuid=33 ouid=0 name="/var/log/apache2/error

I tried aa-complain /usr/sbin/apache2 yet when i save that or scan the log it makes it /usr/lib/apache2/mpm-prefork/apache2 and saves a profile like that.  
I just wanted a generic apache2 profile to maybe for everything inside docroot but with this mpm-prefork its always forcing changehat stuff or errors about the apache hats etc.  

So is there a way to get rid of this new profile and just have a generic apache2 one without the hats etc?  or even just make it so apparmor stops complaining about apache altogether....

---

### Post by PierreRobiquet on 2011-08-21
I wouldn't disable AppArmor completely as ideally on a server you want the highest security. You can tell AppArmor to ignore a single profile but then I still wouldn't think that's the best solution to your problem especially as Apache is one of the more common exploitation routes.

---

