---
title: "Ubuntu 20.04.4 ssh help."
date: 2022-04-25
forum: Server Platforms
---

### Post by naravatu on 2022-04-25
Hello, 

I'm trying to get a minecraft server up and running on a dedicated box running 20.04.4. 
When I run the script to start up the server the machine will kick me from the ssh session. 
I'm trying to figure out what logs I need to look at in order to troubleshoot this. 

Could someone please point me in the right direction. I'm not sure if this is a problem with my machine or the server. 
Thank you.

---

### Post by TheFu on 2022-04-25
All logs are in /var/log/.  I'd use **grep** to search all of the current logs for errors and warnings.  But you can do it however you like.
If you like, you can also use **journalctl** to review logs by the process, time, systemname. That's a little more complex, but the manpage for that program is fairly good.

In no way should ssh be impacted by any other daemon.  I'd guess that something in mindcraft startup is causing a system reboot. This is just a guess. Check the **uptime** for the server or use **last** to see when it was rebooted.

You can also run the ssh client using multiple verbose levels.  This is easiest if ssh is started from a Unix/Linux terminal.

---

### Post by LHammonds on 2022-04-25
Make sure nothing in Minecraft is using port 22 which is the port used for SSH communication.

I assume you are using a screen session to start the java app in the background?   Does Minecraft actually start running once it kicks you or are you seeing a reboot of the server?  Minecraft has it's own log to let you know what it is doing if you get booted off the server and can only power it off to regain control.

LHammonds

---

