---
title: "Dans wont start"
date: 2007-06-08
forum: Ubuntu Christian Edition
---

### Post by jason_Xtreme on 2007-06-08
Ive done this install about 7 times jus to make sure i was following the read me.

each time the script runs dans guardian complains that it cannot connect to the parent proxy. init.d/ tells me its already running. and i get a dans guardian config error when restarting

any1 else had this problem anyway to fix it

---

### Post by mhancoc7 on 2007-06-08
Are you using the script from Ubuntu CE? 

I have not seen this one before. I will keep my eye on this thread.

Jereme

---

### Post by Jacob.fernandez on 2007-06-10
I had the same problem. The fix for me was to edit the tinyproxy.conf like so:
**sudo gedit /etc/tinyproxy/tinyproxy.conf**

# Name of the user the tinyproxy daemon should switch to after the port
# has been bound.
#
User root
Group root

#
# Port to listen on.
#
Port 3128

then restart tinyproxy with **sudo /etc/init.d/tinyproxy restart**

Finally, reconfigure dansguardian with **sudo dpkg-reconfigure dansguardian**

-Jacob

---

### Post by jason_Xtreme on 2007-06-11
Im sure ive tried that but im willing to do it again 

i just finished setting up a virtual server with all the specs and requirements. installed the the desktop just for this.
BTW what happened to the dapper CE script i still have a couple of dapper machines that this would come in pretty handy for. anybody still has a copy an will it still work?
and since i have manually installed dans g is there a way to just get the gui without having it try to reinstall the system as i dont have a fast connection?

---

### Post by jason_Xtreme on 2007-06-12
> **Jacob.fernandez said:**
> I had the same problem. The fix for me was to edit the tinyproxy.conf like so:
**sudo gedit /etc/tinyproxy/tinyproxy.conf**

# Name of the user the tinyproxy daemon should switch to after the port
# has been bound.
#
User root
Group root

#
# Port to listen on.
#
Port 3128

then restart tinyproxy with **sudo /etc/init.d/tinyproxy restart**

Finally, reconfigure dansguardian with **sudo dpkg-reconfigure dansguardian**



-Jacob

dont know what happened but after serveral tried it works going thru the entire process of download install and setup.
 all the above settings were ok as is but firehol is killing everything where can i find a good firehol tut for allowing ssh and other services

---

