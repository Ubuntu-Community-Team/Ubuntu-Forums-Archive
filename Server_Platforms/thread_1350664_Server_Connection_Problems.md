---
title: "Server Connection Problems"
date: 2009-12-09
forum: Server Platforms
---

### Post by MagnetismXA on 2009-12-09
Greetings.  I just installed Ubuntu Server and installed LAMP & OpenSSH.  After reading through and following the instructions on how to properly setup Apache2, MySQL, PHP, and OpenSSH, everything is going on well.  When I type my IP address in the web browser, it shows the index page of the server.  I'm able to connect to the server via FileZilla to transfer files.

After 10 minutes, the connection is refused and when I type in the same IP address, it is unable to connect to the server.  I restarted the server ("sudo shutdown -r now") and it works again for another 10 minutes and then stops the connection.  I don't know what the problem is because I have another location that uses Ubuntu Server and it is working perfectly.  Any help will be greatly appreciated.

---

### Post by craigp84 on 2009-12-09
EDITED -- reread what you wrote

Is there anything recorded in the system logs (in the /var/log directory, as root user, do an "ls -lrt") from before you reboot the box? Specifically anything in the syslog / messages logfile?

Does the outage occur only if you've been transferring files for X mins, or does it occur in the same time frame even if the server is sitting doing nothing the whole time?

---

### Post by MagnetismXA on 2009-12-09
The outage occurs at the same time frame when the server is just sitting there doing nothing.  I checked the syslog and there is some information there.  Is there something specific that I should look for that could be causing this timeout?

---

### Post by munky99999 on 2009-12-09
This sounds familiar to a few I've seen recently.

[http://ubuntuforums.org/showthread.php?t=1311112](http://ubuntuforums.org/showthread.php?t=1311112)

I suggest checking that thread out. I havent had any issue myself. So I havent read it :(

---

### Post by MagnetismXA on 2009-12-09
Thanks so much!  I really do appreciate your help!

---

