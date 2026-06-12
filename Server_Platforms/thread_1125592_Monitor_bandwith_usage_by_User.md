---
title: "Monitor bandwith usage by User"
date: 2009-04-14
forum: Server Platforms
---

### Post by Baversjo on 2009-04-14
I have a server setup with ssh. I let my friends connect to the server and use it as a proxy. 

What I need is to monitor bandwith usage by user, exactly like the application nethogs. The problem is that nethogs only stores bandwith usage in the local session and each time a user reloggs the usage statistics resets. 

I need a tool that logs bandwith usage for each user and let me display it in a web-ui or something, anyone know of such thing?

---

### Post by bluefrog on 2009-04-14
[http://freshmeat.net/projects/wshaper/](http://freshmeat.net/projects/wshaper/)

have a look, might suit you

---

### Post by BkkBonanza on 2009-04-15
I don't know of another program as simple as nethogs for tracking users. Most of them (like ntop) give you oodles of protocol/host info but ignore users. I can see if you are mostly interested in ssh proxy usage that user detail is the key otherwise it all gets merged together.

Here's one thing you can explore that I just did a couple tests with. You can start nethogs as a background task by adding & to the command line. It will start and run in the background. Then you can bring it up any time by typing fg 1 (or some other number, use jobs command to see what job numbers are active). To push it to the background again use ctrl-z. It doesn't exit but disconnects from the console. I'm not sure at the moment if it's still attached to the console and will die when you logout. 

If this works ok then you could possibly start it in your /etc/rc.local at boot. Or maybe better use /etc/events.d as that can restart it if it fails using respawn. It is kind of a shame that it doesn't provide a way to log info.

ps. Just tried closing session and coming back. nethogs is still running but unfortunately I don't know any way to attach to it's process now. Maybe starting it with "screen" would work.

---

### Post by BkkBonanza on 2009-04-15
Adding on to my last post - using screen does work even if you log out and come back later. But note it can be confusing because you need to start nethogs as root, which means when attaching later to view it you need to also use screen as root. If you use **screen -ls** to list screens available it only shows those for the current user.

So trying,
**sudo screen -d -m nethogs**
will start nethogs in a screen session detached. This could be done in rc.local.

But to re-attach later you use,
**sudo screen -r**
to get back to the nethogs screen (assuming only one detached screen).

And once on a screen you detach it again with **Ctrl-A** and then typing **d** (for detach). For more info see man screen. There is all sorts of things you can do with screen.

If you use **ps afx** then you will see screen running nethogs there. It seems to use quite a bit of cpu time I noticed.

Edit:
I was interested in this and so had a look at the nethogs source code. The real problem with this program is that it drops process/connection data after some timeout periods. This isn't really what you want I think for collecting usage data. You could alter the timeout period for processes to be large and probably rebuild the source. It would keep info about processes then but even still what you really want, I think, is user based totals. The program could be altered to do that but it would involve more changes.

---

### Post by Baversjo on 2009-07-30
> **BkkBonaza said:**
> 
I was interested in this and so had a look at the nethogs source code. The real problem with this program is that it drops process/connection data after some timeout periods. This isn't really what you want I think for collecting usage data. You could alter the timeout period for processes to be large and probably rebuild the source. It would keep info about processes then but even still what you really want, I think, is user based totals. The program could be altered to do that but it would involve more changes.
Thank you for your research! I also discovered that and by that time I gave up, I just don't have the skills/time to edit the source right now...

---

### Post by R.Bucky on 2009-07-30
if you have a local gui box, you could always install wireshark

---

