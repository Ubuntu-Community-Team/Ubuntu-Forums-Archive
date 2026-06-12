---
title: "LTSP Clients take 3 minutes to log in"
date: 2010-10-06
forum: Server Platforms
---

### Post by Ensign_Expendable on 2010-10-06
I'm running a fairly powerful server (4x 2.4GHz processors, 5GB RAM, Gigabit Ethernet) with fairly decent clients (1.6GHz Atoms). The problem is that LTSP takes forever to start an X session after the user logs in. Auth.log shows that the user authenticates against Kerberos in a second and a half, and then just sits there for 2 minutes and 54 seconds, after which there is a subsystem request for SFTP and the client logs in normally. I tried this with both a thin and fat client setup, but both of them take the exact same amount of time to start up. Getting to the login screen is pretty fast, certainly less than 30 seconds.

SSHing into the server works fine with no delays. I have no idea what could possibly be causing this problem. Is there at least a detailed breakdown of what happens after the LDM login screen that can help me get to the root of the problem?

---

