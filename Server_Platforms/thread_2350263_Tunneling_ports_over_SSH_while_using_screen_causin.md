---
title: "Tunneling ports over SSH while using screen causing reboots"
date: 2017-01-22
forum: Server Platforms
---

### Post by sparkix on 2017-01-22
I am having an unusual problem.  I have a headless server running Ubuntu 16.04.01 LTS which is typically running without interruption for months (or years if updates allow), but recently has been experiencing 1-2 reboots a day.  I have tracked the issue to connecting to the server using SSH while using screen as well as tunneling ports dynamically with PuTTY.

I am using PuTTY v0.67 (the latest as of this post)

I have added the following to my user login .bashrc file to automatically create/re-attach a screen upon login by SSH:

```
# Automatically create a new or attach to existing screen session when logging in by SSH.
if [ -n "$SSH_CONNECTION" ] && [ -z "$SCREEN_EXIST" ]; then
    export SCREEN_EXIST=1
    screen -dRaq ssh-auto
fi
```

This above .bashrc entry has worked well for months.  The problem began when I added dynamic port forwarding in PuTTY so that I could bypass a firewall for browsing with Firefox.

Here is the PuTTY port forwarding setting:
[ATTACH=CONFIG]273333[/ATTACH]

And here are my Firefox browser settings:
[ATTACH=CONFIG]273334[/ATTACH]

I can't track it down, but I know reboots are caused by something to do with this situation because I have not connected to the server using PuTTY in the past 3 weeks but have connected with SSH and there have been no reboots (uptime = 23 days).

Can anybody shed some light on this or tell me where I should look.  Thanks!

---

### Post by raja.genupula on 2017-01-23
As you know when your server got restarted , can you look at /var/log/messages file.

```
less /var/log/messages
```

this file records system events , try to see at restart timestamp and you surely find some information. 

And SSH tunnel setup causing restarts means , I dont know &  to be honest this is the first time I am looking issue like this. 

I hope others can help you.

---

