---
title: "pulling MRTG bandwidth into Nagios"
date: 2008-02-05
forum: Server Platforms
---

### Post by christy7669 on 2008-02-05
:confused:Here is what is happening in Nagios:

check_mrtgtraf: Unable to open MRTG log file 

Here is what my last line of my MRTG check looks like:

check_local_mrtgtraf!/var/lib/mrtg/192.168.1.253_1.log!AVG! 1000000, 2000000! 5000000, 5000000!5

I am not sure if I need to change anything, and if I do what.  Can some one break it down for me?  What each section is, and which ones need changes, if at all.

I know UBUNTU puts things in different folders, since it is UNIX based.  When I went to the /var/lib/mrtg folder there was nothing in there but a file named:

_etc_mrtg.cfg

And I have looked and looked and only found /var/log/mrtg/mrtg.log.

Please Advise.  Thank you for your help.

---

### Post by ice_queem on 2008-05-03
Try changing ```
check_local_mrtgtraf!/var/lib/mrtg/192.168.1.253_1.log!AVG! 1000000, 2000000! 5000000, 5000000!5
```

to 

```
check_local_mrtgtraf!/var/www/mrtg/192.168.1.253_1.log!AVG! 1000000, 2000000! 5000000, 5000000!5
```

---

