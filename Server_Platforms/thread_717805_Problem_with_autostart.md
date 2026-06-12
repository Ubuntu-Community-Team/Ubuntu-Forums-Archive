---
title: "Problem with autostart"
date: 2008-03-07
forum: Server Platforms
---

### Post by ambo on 2008-03-07
I have been running an Ubuntu server for Freeradius for a number of years in various different configurations. The current one is (IIRC) an apt-get install of the version of freeradius from the repo's (repo's caught up with the features i needed so i didn't need to do my own compiling anymore)

Every since I first setup the box I have had to start the radiusd process manually and this wasn't a problem until my hosts bounced my server 6 times in one week.

I did a little digging and realised that radiusd is actually probably meant to be starting automagically through the wonders of init.d but its not. There appear to be startup scripts in the correct rcX.d directories but they are not doing what they are meant to on bootup.

Since this sort of stuff just *works* on all the other servers that I run - I'm not really sure where to start looking. I have poked through a few log files but I haven't found anything that looks significant.

Any suggestions?

---

### Post by astrotech226 on 2008-03-07
What version of Ubuntu and freeradius are you running?

---

### Post by ambo on 2008-03-07
radiusd -v gives:> radiusd: FreeRADIUS Version 1.1.4, for host i686-pc-linux-gnu, built on Jan 28 2007 at 11:08:59

cat /etc/lsb-release gives> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"


---

