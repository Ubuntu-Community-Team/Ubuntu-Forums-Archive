---
title: "Adito invalid credentials problem"
date: 2009-12-03
forum: Server Platforms
---

### Post by bontje on 2009-12-03
Hi,

I've just installed Adito, but it seems my credentials are lost when I restart my pc. I am running Kubuntu Karmic Koala, and the latest version of Adito. When I installed it the first time, I got Adito running and logging in went smoothly. After I restarted my system, my login and password was not accepted, so I reinstalled Adito. Logging in worked till I restarted again. I added a line in wrapper.conf (encoding UTF-8) and in server.conf.

Is there anything I can do next or has anyone else experienced this problem before?

---

### Post by bontje on 2009-12-04
just figured out that restarting the service adito solves the problem. I can then enter my credentials. how can i take care of a correct startup, as I would like to use adito too take over my pc from anywhere else.

---

### Post by trolley on 2010-10-12
Do you still have this problem? I do with Maverick, and also did with Lucid.

I've reported the problem on the OpenVPN ALS mailing list but no one else has corroborated the problem. If you're still having this problem could you report it as well?

---

### Post by thinkdez on 2010-10-25
I too have had this issue.  I have been unable to resolve the issue so when the system reboots I get locked out.  My only way to bypass the problem is I have a cron job running every 6 mins which checks uptime.  If the uptime is less than 5 mins then adito is restarted.  

Any attempts to fix the startup script have failed and I am stuck with the authentication issue.

---

### Post by jiggler on 2010-10-25
Same issue here, adito authentication only works if I manually restart it once the server has been rebooted.

1. even if the login script adds an at job to run 5 min's after reboot, this doesn't work

2. If I log and run the login script manually, everything is fine, using the same scripts init used to restart adito!

Leads me to think about some env variable causing this? will continue to investigate when time permits and post anything new

---

### Post by jiggler on 2010-10-27
This resolved the issue for me.


[LIST=1]
[*] In your adito install dir, find and modify wrapper.conf.base
[*] Locate the line that reads **#wrapper.java.additional.2=-Dfile.encoding=UTF-8**
[*] Remove the # and save
[*] in /etc/init.d/adito, i changed the start section to ant -f /opt/adito/build.xml start (or where ever your build.xml file is
[/LIST]

Idea was from
[http://wiki.amahi.org/index.php/Adito](http://wiki.amahi.org/index.php/Adito)

---

