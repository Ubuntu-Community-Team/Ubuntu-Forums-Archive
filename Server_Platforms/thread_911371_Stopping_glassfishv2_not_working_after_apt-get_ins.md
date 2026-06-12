---
title: "Stopping glassfishv2 not working after apt-get install glassfishv2"
date: 2008-09-05
forum: Server Platforms
---

### Post by taipeiben on 2008-09-05
I installed glassfish v2 using apt-get and it seems to work fine.  I can log into the admin console on port 4848.  I see the welcome screen on port 8080.  However, when I type: 

[FONT="Courier New"]asadmin stop-domain domain1[/FONT]

I get:

[FONT="Courier New"]GlassFish Default Domain Not Present
Creating in /home/ben/glassfishv2/domain1
Provide admin port for domain1 :[/FONT]

This wasn't what I was expecting to see, but deciding to play along, I type 4848 and press enter and I get:

[FONT="Courier New"]Creating domain domain1 @ admin port 4848
Port 4848 is in use.
CLI130 Could not create domain, domain1[/FONT]

Am I missing a step somewhere?

---

### Post by taipeiben on 2008-09-05
Figured it out, turns out asadmin runs:

[FONT="Courier New"]/usr/bin/asadmin[/FONT]

instead of:

[FONT="Courier New"]/usr/share/glassfishv2/bin/asadmin[/FONT]

as soon as I ran: 

[FONT="Courier New"]sudo /usr/share/glassfishv2/bin/asadmin stop-domain domain[/FONT]1

it worked.

---

