---
title: "Teamspeak 3 Server On A Ubuntu Server 12.04"
date: 2012-08-08
forum: Server Platforms
---

### Post by SaturnDrummer on 2012-08-08
Ok, I just put together my Ubuntu server a couple days ago with some spare parts I had laying around. I've since installed OpenSSH so it can be headless, and I get to the terminal using Putty from my Windows 7 laptop. I've installed screen, and everything for a 1.3.1 minecraft server, which I plan on having running 24/7. Also, everything on this server will (eventually) be accessible outside the home network, since it's set up at my parents' house and I'm moving back to school this weekend. So, back to Teamspeak.

I've installed the latest version from their website (3.0.6.1) and by going through the 3-4 tutorials on it I could find, got it to run from my admin username, accessible and all. However, when I tried to run it in a separate screen, so that I could disconnect from said screen and exit putty, I couldn't access my server from my teamspeak client, and when I requested the status of the server in the terminal, it said "the server seems to have died," which sounded bad. So I looked around, changed the startscript to use the init file, made sure the process wasn't still running, and tried again. No go. It does still work when I start it out of a screen, though. Which is nice, but not perfect. So from all that, can anyone help me out? I'm glad to give you whatever else you might need, just bear with me, as I haven't really been messing with any linux before monday lol. Thanks!

EDIT:

Sorry, my first post on this forum is for nothing lol. I ran it in sudo and it ran just fine in the screem I must have accidentally ran it in sudo before. But I guess I do still have a question that's fairly important: Is running it from my main user a security risk if all the files are in a regular users home directory? Or should I run it as the other user? I tried running it as the other user (ts3user) and it didn't give me permission, so I figured I'd be fine running it with mine, but if there's a safer way I'm all over it. Thanks for reading all this! And sorry again lol

---

### Post by brent1975 on 2012-08-09
> **SaturnDrummer said:**
> Ok, I just put together my Ubuntu server a couple days ago with some spare parts I had laying around. I've since installed OpenSSH so it can be headless, and I get to the terminal using Putty from my Windows 7 laptop. I've installed screen, and everything for a 1.3.1 minecraft server, which I plan on having running 24/7. Also, everything on this server will (eventually) be accessible outside the home network, since it's set up at my parents' house and I'm moving back to school this weekend. So, back to Teamspeak.

I've installed the latest version from their website (3.0.6.1) and by going through the 3-4 tutorials on it I could find, got it to run from my admin username, accessible and all. However, when I tried to run it in a separate screen, so that I could disconnect from said screen and exit putty, I couldn't access my server from my teamspeak client, and when I requested the status of the server in the terminal, it said "the server seems to have died," which sounded bad. So I looked around, changed the startscript to use the init file, made sure the process wasn't still running, and tried again. No go. It does still work when I start it out of a screen, though. Which is nice, but not perfect. So from all that, can anyone help me out? I'm glad to give you whatever else you might need, just bear with me, as I haven't really been messing with any linux before monday lol. Thanks!

EDIT:

Sorry, my first post on this forum is for nothing lol. I ran it in sudo and it ran just fine in the screem I must have accidentally ran it in sudo before. But I guess I do still have a question that's fairly important: Is running it from my main user a security risk if all the files are in a regular users home directory? Or should I run it as the other user? I tried running it as the other user (ts3user) and it didn't give me permission, so I figured I'd be fine running it with mine, but if there's a safer way I'm all over it. Thanks for reading all this! And sorry again lol

When you start the script sudo ./ts3server_startscript.sh start   - it starts it as a service and will need to have permissions to do so. sudo is the easy way of doing this. Or if you enabled the Root account which is not necessary.

---

