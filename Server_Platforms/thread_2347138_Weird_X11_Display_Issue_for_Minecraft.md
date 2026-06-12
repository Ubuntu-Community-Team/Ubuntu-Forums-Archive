---
title: "Weird X11 Display Issue for Minecraft"
date: 2016-12-21
forum: Server Platforms
---

### Post by Black Regulator on 2016-12-21
Hey everyone,

I tried to update my Minecraft server using the latest available jar file from the mc website. Whenever I update my start script accordingly, I receive this error
"No X11 DISPLAY variable was set, but this program performed an operation which requires it."

I've tried following some suggestions on the web, including unsetting my display variable, enabled x11 forwarding, etc. (all with varying errors. If it helps, I can recreate and list them) but none of that helped. This is a headless server - it's a cloud server and I'm accessing it via SSH on Putty. But for the old version of Minecraft 1.8.9, everything works flawlessly. But the latest version is giving me issues. 

It doesn't appear anyone else is having this problem. Any clues as to what I can do get run the latest version for a server?

EDIT: I'm running Ubuntu 16.04.1 Server, x64.

Thank you.

---

### Post by Black Regulator on 2017-07-17
I figured it out. :)

I was originally downloading Minecraft.jar from the front page of their website. What I really needed was the minecraft_server.x.xx.jar file. [https://minecraft.net/en-us/download/server](https://minecraft.net/en-us/download/server)

---

### Post by sisco311 on 2017-07-17
Cool!

Thanks for posting the solution.

Please also mark this thread as solved.

Regards,
sisco311

---

