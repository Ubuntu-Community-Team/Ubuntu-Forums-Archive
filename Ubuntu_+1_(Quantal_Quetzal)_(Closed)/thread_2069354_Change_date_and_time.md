---
title: "Change date and time"
date: 2012-10-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Penguin360 on 2012-10-10
I set my date and time to sync with the Internet time, but it does not show the right time. How can I set the time zone so it will show the right time?

Right now I set the location to Dallas, Texas to try to use the Central Time zone, but the time does not change.

Thanks.

---

### Post by TheFu on 2012-10-10
$ sudo dpkg-reconfigure  tzdata

Is the time off just in the hour or is it off in the minutes and seconds too?

---

### Post by wojox on 2012-10-10
> **CodingBeaver said:**
> 
Right now I set the location to Dallas, Texas to try to use the Central Time zone, but the time does not change.


I set mine to Chicago and it syncs rather well.

---

### Post by Penguin360 on 2012-10-10
The hour is off. 

I would like to set my time zone to America/Central Time, but there is no such time zone in the drop down list. I recall that I can change the time zone in the previous version of Ubuntu after the installation, but I can't find it in 12.10.

---

### Post by Frogs Hair on 2012-10-10
In time / date the world map has grid lines and you click on the map to change the zones.

---

### Post by Penguin360 on 2012-10-11
Just found out not only the hour is off, but also the minute. If I set me time zone to Dallas, if my time is 9:30AM, then Ubuntu shows the time is 4:35AM. It seems that the time zone offset didn't apply, and the minute is 5 minutes earlier. Is it a bug or is it just me?

---

### Post by TheFu on 2012-10-11
> **CodingBeaver said:**
> Is it a bug or is it just me?

I'm inclined to think it is just your system, but it could be a bug of some type that only you are seeing.

I've never seen anything like that which couldn't be traced back to a firewall blocking NTP or a virtual machine host providing the wrong time or some other time-server being incorrect.  Hibernating or putting a machine into standby has caused time issues for me too, until I rebooted.

Could your CMOS battery be dead?  This is often why system time is incorrect after a machine has been powered off.  Also, be certain that your BIOS and system time are set to store GMT/UTC, not local time.

NTP doesn't change the time immediately, it takes hours to slowly migrate the time to be correct without a clear disruption.  We can force a time using the **rdate** function.

OTOH, I haven't used the GUI to control time ... ever. I'm a CLI person.  After setting the TZ during OS install, I install the **ntp** package and point the NTP towards my LAN time server. I can't imagine this should be necessary, but I'm more comfortable with this time management. Most issues that I have with time is on Windows machines.

---

### Post by wojox on 2012-10-11
Really nothing?

---

### Post by Penguin360 on 2012-10-11
> **wojox said:**
> Really nothing?

Really nothing. See the attached screen shots for Dallas and Chicago time zone. If I use UTC time, then the hour shows the current hour, but it is 5 minutes earlier than the actual time.

My CMOS shows the current date and time. It could be our company's firewall is blocking the port.

---

