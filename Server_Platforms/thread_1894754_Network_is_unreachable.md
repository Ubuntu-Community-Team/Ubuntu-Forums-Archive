---
title: "Network is unreachable"
date: 2011-12-13
forum: Server Platforms
---

### Post by kabeza on 2011-12-13
Hi
I'm beginning server administration and am having a problem

I worked with server last thursday and all was ok. Today I couldn't reach the server (ping), which is 100mts from here. I had to go to the physical location of the server, connect a monitor, keyb and mouse.

Server was on, xfce running, all seemed to be fine, except the ifconfig -a command wasn't showing the manually assigned IP server should have, and I was getting **"network is unreachable"** when trying to ping something from server.

By doing **sudo /etc/init.d/networking restart** all went back to normal, so:

[B]Is there anything I can do to assure the networking service is always running, so I don't have to start it manually from the server?
[/B]
It is a Ubuntu 11.04 server with latest xfce, webmin and lampp installed

---

### Post by Bucky Ball on 2011-12-13
Has the server been on the whole time? Any updates? LTS releases advised for servers and production machine, current being 10.04 LTS and rock solid.

---

### Post by kabeza on 2011-12-13
> **Bucky Ball said:**
> Has the server been on the whole time? Any updates? LTS releases advised for servers and production machine, current being 10.04 LTS and rock solid.


Yes, server has been up for 7 days w/o energy problems.

PS: I wonder if something like this would work (found in other thread):

**_POSSIBLE SOLUTION 1_**
=====================================
Add this to a new network.cron file
> 0 0 * * * root /etc/init.d/networking restart

Then
> sudo crontab network.cron

**_POSSIBLE SOLUTION 2_**
=====================================
> 
#!/bin/bash
x=`ping -c1 google.com 2>&1 | grep unknown`
if [ ! "$x" = "" ]; then
        echo "It's down!! Attempting to restart."
        service network restart
fi


and then adding these lines to cron
> 
*/2 * * * * /usr/local/bin/check_network
0 * * * *    service network restart > /dev/null


---

### Post by bab1 on 2011-12-13
Check the logs.  The networking is designed to work all the time.  If it failed, you should be able to tell why.

I don't like to modify things unless I know what problem I am trying to cure.

---

### Post by kabeza on 2011-12-14
which logs should I check?

---

### Post by ephmanjmm on 2011-12-14
Is this the first time there have been issues with this server?  I would look into the power management settings in Xfce and BIOS as well.  It could be shutting down network due to inactivity.
Just a shot in the dark.

---

### Post by kabeza on 2011-12-14
thanks, but being a server, it would be very stup*d to have an option to shutdown network due to inactivity.
I'll check it, and if it has that option, I'll kick the guy who sold it 2 me

---

