---
title: "ubuntu install hang"
date: 2007-08-29
forum: Server Platforms
---

### Post by InGunsWeTrust on 2007-08-29
I am installing Ubuntu server on an old p3 and I install with all default options with the entire HD (20 gig) used. I choose LAMP server for additional software. It installs everything fine until it gets to 85%. The installation hangs with the status message at "Installed php5-mysql" or something like that (I'm not right in front of it right now but that is close enough). There are no error messages but I left it at 85% for about 45 minutes and nothing happened (it got up to 85% in about 20 minutes).

---

### Post by Mark Thorne on 2007-09-16
I've run into the exact same issue with 7.04. Did you ever manage to get around it?

---

### Post by LiLoather on 2007-09-22
> **Mark Thorne said:**
> I've run into the exact same issue with 7.04. Did you ever manage to get around it?

I get the same problem likewise, so once more Linux goes back onto the "hope they'll get it right one day" pile and Windows' reign continues.

---

### Post by ftk on 2007-09-27
I had this problem once when I installed specifying an incorrect name server IP and the installer hung in an endless cycle trying to connect to the online repositories. If it hangs again, try looking at the detailed install console output (It's CTRL+F5 or F6 I believe) and see if it keeps trying and timing out connecting to the online repositories. If so you can hop over to CTRL+F2, enable the console, and then manually kill the process (it's been a while since I did it, but ps ax lists all processes, then just check which one keeps connecting [probably aptitude or apt-get] and note the Process ID of it, then kill with "kill ###" with ### being the PID). That should do it. 

If this is your particular problem, you can also just leave the name server blank for now, it won't try to fetch stuff via internet.

---

