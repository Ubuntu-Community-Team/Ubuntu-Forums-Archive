---
title: "ntpd won't update time/date"
date: 2007-01-02
forum: Server Platforms
---

### Post by ikonia on 2007-01-02
Hi,

on a 6.06 server install, I have confiured ntpd to get date/time from one of 4 servers (2 are pools actually).

I have verified that the servers listed are running ntp and available for syncronisation.

I set the date forward a little with 

date --set day 

a few times

and start ntpd via the ubuntu init script. 

The time and date do not get updated.

however if I do ntpdate $name_of _server_in_ntpd.conf the date and time get updated perfectly.



Questions 

1.) What would cause ntpd to not update when ntpdate is verifying that the servers in the ntp.conf are fine

2.) can you make ntpdate read ntp.conf rather than having to supply a server name as an argument.

---

### Post by jazzgossen on 2007-01-05
Have a look in /var/log/syslog.* for entries regarding ntpd.

I also have problems with a rapidly drifting system clock that ntpd won't update properly. I tried running "ntpd -q", and the syslog output was 

Jan  5 23:50:20 undertow ntpd[31400]: sendto(80.240.210.253): Bad file descriptor
Jan  5 23:50:20 undertow ntpd[31400]: sendto(192.36.143.153): Bad file descriptor
Jan  5 23:50:21 undertow ntpd[31400]: sendto(192.36.143.151): Bad file descriptor
Jan  5 23:50:22 undertow ntpd[31400]: sendto(80.240.210.253): Bad file descriptor
Jan  5 23:50:24 undertow ntpd[31400]: no reply; clock not set

---

### Post by rth on 2007-01-05
A quick search on Google for:
```
ntpd "Bad file descriptor"
```
shows that the most common response is that multiple instances of ntpd are running. Can you check and see? If more than one, kill them all, restart ntpd, and make sure only one is running.

---

### Post by terencekent on 2008-03-17
I'm running into the exact same problem, but without the symptoms described above (only one ntpd daemon running, and no error messages about file descriptors)

Any ideas where to look? syslog and daemon.log do not report any trouble and ntpd starts up fine. Even ntpq -p provides a clean bill of health.

I'm stumped and I'd rather not abandon ntpd in favor or ntpdate...

Thanks in advance!
Terence.

---

### Post by MJN on 2008-03-18
You have got to bear in mind that ntpd is designed to **maintain** a clock's accuracy and it does this by making tiny adjustments at a time.
 
Hence, in line with this premise it is not intended to make any large adjustments and as such if the current time/date is significantly different (>1000s ?) than what it thinks is true time then it will make the assumption that there is something seriously wrong (e.g. hardware failure or an NTP error) and so do nothing.
 
Furthermore, time adjustments will not be instantaneous (otherwise you could end up with time apparently running backwards) but rather will be gradually adjusted to converge - this will take some time particularly when you are first up-and-running.
 
Force the clock out by 5 seconds and give ntpd an hour or so - you should find by then that you are back on track (in practice it will be far quicker than this, and of course would never deviate by that much). Alternatively, check out the -g and -x options.
 
Mathew

---

