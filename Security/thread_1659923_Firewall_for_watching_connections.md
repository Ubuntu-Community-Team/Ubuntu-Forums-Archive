---
title: "Firewall for watching connections?"
date: 2011-01-04
forum: Security
---

### Post by cipherboy_loc on 2011-01-04
Yes, I know that GNU/Linux does not need a firewall (due to iptables), but I would like a basic firewall that would watch incoming and outgoing connections. I would prefer it to have a try icon and be able to run as a regular user, such that I can add it to my .fluxbox/startup file. Anyone know of any good ones? They don't actually have to interface into iptables (because I would do that myself), but if they do it would be a bonus.


Thanks,
Cipherboy

---

### Post by hudsonl on 2011-01-04
Are you wanting to monitor incoming / outgoing traffic ?  If so look at Wireshark or EtherApe.

If you are just want to implement / use firewall ... then look at ufw ...

> sudo ufw status

> man ufw

---

### Post by cipherboy_loc on 2011-01-04
I guess what I imaged should be available is something that would monitor the traffic, but only show the connections that were deemed a threat. Like firestarter does, except without needing to be run with sudo/gksudo.

I have used Wireshark before, but the flow of information on my network makes it hard to use unless you know what you are looking for. I knew what I was looking for when I was syncing my iPod (there is a port that gets opened on the iPod touches), but in this case, I would not know what to look for.


Cipherboy

---

### Post by bodhi.zazen on 2011-01-04
> **cipherboy_loc said:**
> I guess what I imaged should be available is something that would monitor the traffic, but only show the connections that were deemed a threat. Like firestarter does, except without needing to be run with sudo/gksudo.

I have used Wireshark before, but the flow of information on my network makes it hard to use unless you know what you are looking for. I knew what I was looking for when I was syncing my iPod (there is a port that gets opened on the iPod touches), but in this case, I would not know what to look for.


Cipherboy

firestarter, wireshard, ehterape are poor tools for this task as they merely log packets and it is then up to you to sort through the thousands of packets to find problems.

logging dropped packets and reviewing such packets is a waste of time and effort, as is a little flashing icon as you envision.

The best tool for the task is snort.

Please see the sticky at the top of this page

[http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)

If snort is too complicated for you, quit while you are ahead, relax, and enjoy Linux.

---

### Post by cipherboy_loc on 2011-01-05
Thank you. That appears to be what I wanted.


Marking this thread as solved,
Cipherboy

---

