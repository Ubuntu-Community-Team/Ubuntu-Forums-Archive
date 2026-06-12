---
title: "Bandwidth Question"
date: 2007-07-04
forum: Server Platforms
---

### Post by notaloafer on 2007-07-04
Does Ubuntu come prepackaged with something that measures bandwidth? All I want is something extremely simple that shows how much bandwidth my one server has used with maybe a customization of the time frame.

I'd prefer to have a GUI / web interface to access my server statistics (either one will work).

Thanks!
-Eric.

---

### Post by firefly2442 on 2007-07-04
I like this:

[http://phpsysinfo.sourceforge.net/](http://phpsysinfo.sourceforge.net/)

You should be able to just apt-get install it.

HTH. :)

---

### Post by notaloafer on 2007-07-05
Will this one not reset it self every time the server restarts? I need to know totals and need it to keep totaling even if my server is restarted (I don't want the thing to reset all in/out , etc if I restart).

Thanks

---

### Post by firefly2442 on 2007-07-05
Every time you restart the machine, it will reset.  Also, there is an issue with keeping the actual amount of bandwidth saved in Linux.  I believe it's because of a limit on the size of the variable that is used to store the information but at a certain point, the bandwidth amount gets reset and starts counting again from zero.  I've seen it happen after transferring gigabytes of data.  If you need to know totals, you might look into this:

[http://cacti.net/](http://cacti.net/)

---

### Post by wirelessmonkey on 2007-07-05
I agree w/. firefly, use cacti or MRTG along with SNMP and keep updated statistics on network traffic, including graphs!!   If you need help with this, please PM me, I have a robust monitoring setup for 800+ nodes.

---

