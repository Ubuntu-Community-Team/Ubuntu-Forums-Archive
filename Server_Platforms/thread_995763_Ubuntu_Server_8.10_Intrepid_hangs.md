---
title: "Ubuntu Server 8.10 Intrepid hangs"
date: 2008-11-28
forum: Server Platforms
---

### Post by dimitar_g_g on 2008-11-28
I am using Ubuntu Server 8.10 Intrepid on a brand new PC. Working as a NAT router in a production environment.
When working for several hours it just hangs and it is not responsive to pings nor ssh. Unfortunately I can't see what is on the display. Going through the logs shows nothing strange.
Can anybody confirm any hangs with Ubuntu Server 8.10  or  is it just me ?
Do you think it is worth trying Ubuntu Server 8.04 LTS ?
Or can you point me to good OS for NAT router with support for ICH10R southbridge?

---

### Post by Philio on 2008-11-28
Which logs did you check?

---

### Post by dimitar_g_g on 2008-11-28
/var/log - All of them

---

### Post by andguent on 2008-11-29
A few ideas & questions:

* Can you try leaving an SSH session connected and see if it survives the hang? SSH & NAT can lock up new connections, but sometimes leave existing connections up?
* What needs to be done to get physical monitor & keyboard access to this box? You really need to check its own connectivity status in this frozen state.
* What software are you using to do the NAT/firewall functionality? Raw iptables commands, shorewall, or something else?
* How many interfaces does the router have? Are you using VPN for anything?
* Is there anything you can disable (VPN?) to see if it still hangs?

Good luck.

---

### Post by dimitar_g_g on 2008-12-01
This is regarding another server running LAMP.
All SSH connections freeze.
I sorted the monitor and keyboard, I am attaching a picture.. It is completely frozen, keyboard doesn't react.
No VPN on neither of the servers.
This one has ping but none of the services is working.

---

### Post by andguent on 2008-12-01
Are these boxes by chance running slapd for LDAP authentication? I've seen the log rotator & slapd take down the box hard because the log file was pulled out from underneath slapd's feet and it didn't like it.

---

### Post by dimitar_g_g on 2008-12-01
No slapd.
This server was running 8.04 for about 3 weeks then upgraded to 8.10. It was running fine for 1 week and then it crashed. I had 4 crashes in 3 weeks maybe.
That's why I am thinking it is something to do with 8.10.

---

### Post by andguent on 2008-12-01
Can you post the last ten lines prior to the crash from /var/log/syslog and /var/log/messages? Even if there are no errors, it would give some clues as to what was working at the time.

Also, can you give us an idea of what time of day, and what day of week these crashes are occuring? If they happen exactly at 6:25 am system time or something, we can then investigate what does the most work at that time.

I agree with you there is a chance that 8.10 is causing some of your problems. The last thing to be changed should be the first thing investigated. Unfortunately we don't have much detail to go on currently. Your screenshot is nice to have, but it doesn't help me out much.

---

### Post by dimitar_g_g on 2008-12-01
I will post them as soon as I got the server restarted because it crashed again and I don't have physical connection to the server.

Crashes happen any time 1 am,  10 am, 3 pm, 9 pm. Not the same minutes.

I used to run Slackware on the machine but decided to go for Ubuntu to take advantage of the 64 bit build. Software running is the same no difference.

Now I remembered I have RTL8111B gigabit card using  r8169 module (lots of posts regarding this module and card). I will try changing it with r8168 . I didn't suspect it because network is running fine but I will give it a try.

---

### Post by dimitar_g_g on 2008-12-03
Still the same problem.
I will have to change Ubuntu with a more stable distribution.

---

### Post by andguent on 2008-12-04
Depending on the server needs, you could actually boot a knoppix disc and load your firewall/web server settings there. It would be an interesting test if knoppix shows the same issues.

---

### Post by LarsW_Tierp on 2008-12-07
I have had a similar problem, it turned out to be the later kernel. I downgraded to a previous version and now the servers are steady as rocks.

---

### Post by markmid on 2008-12-18
How did you downgrade?  I am having problems also.

---

### Post by gtdaqua on 2008-12-18
Did you check your BIOS or other firmware version for latest updates/fixes? Is the hardware certified for Ubuntu?

---

