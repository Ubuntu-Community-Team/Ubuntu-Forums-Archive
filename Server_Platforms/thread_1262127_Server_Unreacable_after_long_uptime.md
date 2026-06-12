---
title: "Server Unreacable after long uptime"
date: 2009-09-09
forum: Server Platforms
---

### Post by Cardale on 2009-09-09
I use dyndns as my domain host and dns service and it works fine on a fresh reboot, but after about 20-30 minutes it stops working.

I have a LAMP server with OpenSSH Shorewall firewall and DenyHosts installed.  What could be preventing the internet from accessing my server?

---

### Post by cariboo on 2009-09-09
Sometimes, it's the little things, is [ddclient]("http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html") running?

---

### Post by Cardale on 2009-09-09
No, I actually have a update client on my router and if the ip hasn't changed for months the updater is really pointless right?  Or does it update other information?

I did a small test to make sure it wasn't a domain issue I think this can rule out dyndns issues.  I have a XP laptop and I install xampp real fast and opened port 80 and on my router forwarded the traffic to that workstation and it came up instantly.

I'm not sure if this completely rules out a domain issue, but it makes me think it is a server related setting.  What do you think?

---

### Post by thephoenixvampire on 2009-09-09
i have the same problem...was running the latest 9.04, ran an update, and it just suddenly started cutting internet or something. so i updated to Karmic....still the same thing...any help would be appreciated.

---

### Post by cariboo on 2009-09-09
Doesn't your server come up instantly when you restart networking? My ip address changed for the first time in 2 years wnen I got a new modem from my isp, but when I was using no-ip, things did seem to slow down when the client wasn't reporting back every 15 minutes.

---

### Post by Cardale on 2009-09-10
The thing is my router does the updating and no where in the "updater" for Dyndns does it ask the local lan ip address that I will be connecting to the url it simply asks for my name and password and it automatically gets my IP and sends it off.  So if this "server" reboots or gos down it doesn't even matter I would think.  Unless the operation for this feature is to update when ever a new system connects to the router.

Not sure..will see if I can't dig up information on how to change the settings since there are none on the web interface.

---

### Post by Cardale on 2009-09-10
bump

---

### Post by grantemsley on 2009-09-11
Maybe check denyhost's log files?  If it were setup improperly, it could block everything after a hacking attempt.

---

### Post by Cardale on 2009-09-11
if it was to block it would place a entry in the hosts.deny file correct?  That doesn't explain the fact it works when I reboot then stops after a hour or so.

---

