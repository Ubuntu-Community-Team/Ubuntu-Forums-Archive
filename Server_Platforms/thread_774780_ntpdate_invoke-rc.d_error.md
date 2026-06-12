---
title: "ntpdate invoke-rc.d error"
date: 2008-04-29
forum: Server Platforms
---

### Post by sjaakmans on 2008-04-29
Hello,

Yesterday i upgraded my server to ubuntu 8.04 after that ever our i get this error:
> /etc/network/if-up.d/ntpdate: line 26: invoke-rc.d: command not found
/etc/network/if-up.d/ntpdate: line 30: invoke-rc.d: command not found

I googled and didn't found the right answer... Does somebody else knows it?

Greets,

Sjaakmans

---

### Post by sjaakmans on 2008-04-30
Anybody? It is really annoying every our i get a mail

---

### Post by njparton on 2008-04-30
[SIZE=2]That looks like something to do with NTP automatic time synchrionisation. Try turning it off by clicking on the clock and adjusting the settings.[/SIZE]

---

### Post by bluefrog on 2008-04-30
Is invoke-rc.d installed?

in a terminal
which invoke-rc.d
should give
/usr/sbin/invoke-rc.d

You use it for example instead of sudo /etc/init.d/ gdm restart
sudo invoke-rc.d gdm restart

James Dupin

---

### Post by sjaakmans on 2008-04-30
I get this error from my server... the only thing i can think about is removing it but then i will not get the right time :p so....

BTW I looked at the lines 26 and 33 and i can run them manual so...

I tried to run dpkg-reconfig ntp nothing happened.

But when possible i still want to run the ntp service

This where the results of the 'Which invoke-rd.c'
> root:~# which invoke-rc.d
/usr/sbin/invoke-rc.d
root:~# invoke-rc.d ntp start
 * Starting NTP server ntpd                                              [ OK ] 
root:~# invoke-rc.d ntp restart
 * Stopping NTP server ntpd                                              [ OK ] 
 * Starting NTP server ntpd                                              [ OK ] 
root:~# 


---

### Post by bluefrog on 2008-04-30
Apparently ntpdate is supposed to run once a day not every hour which ntp should do. ([https://help.ubuntu.com/7.10/server/C/NTP.html](https://help.ubuntu.com/7.10/server/C/NTP.html))

Do you have only /etc/cron.daily/ntp or ntpdate as well?

---

