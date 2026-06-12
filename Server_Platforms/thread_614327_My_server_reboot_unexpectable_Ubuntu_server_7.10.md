---
title: "My server reboot unexpectable Ubuntu server 7.10"
date: 2007-11-15
forum: Server Platforms
---

### Post by pajarraco on 2007-11-15
I have couple of days with ubuntu, I install server 7.10 and i configure LAMP and Darwin Streaming Server, everything work fine but my machine is reboot it unexpectable.

When I working with it is fine, but when I leave it along thru the night, in the morning. I found that it was rebooting all night. 

I don’t get any error message 

If anybody have the same problem?
please I need some help or if somebody can tell me How can I see what is the problem?
:confused:

---

### Post by prezbedard on 2007-11-15
could be a hardware problem 

bad/lose memory
overheating

just to name a couple

---

### Post by MJN on 2007-11-16
What do your logs (/var/log/syslog in particular) say around the time of the reboot?
 
You're not falling for the common **syslogd 1.4.1#17ubuntu7: restart **confusion where it's actually syslogd restarting (to roll the logs) and not the server itself?
 
Mathew

---

### Post by pajarraco on 2007-11-16
I not sure if the hardware has problems because i had windows server installed before and never reboot.

I'm going to check the log. I let you know

Thanks.

---

