---
title: "Running screen within rc.local"
date: 2016-10-12
forum: Server Platforms
---

### Post by homemadejam-1 on 2016-10-12
I'm trying to run a number of scripts at startup using rc.local. The scripts are running, but they seem to be terminating for no reason.
I'm using autossh to connect to a remote server within a screen session, but when terminates it kills autossh.

The other script we are trying to run starts a Minecraft server within screen too. The server loads, but the moment it finishes loading, it terminates.

A copy of the server connection script:
```
/usr/bin/screen -dmS WebTunnel sshpass -p "<password>" autossh -N -R :4000:localhost:80 <user>@<server>
```

And this is a copy of the minecraft.sh file:
```
/usr/bin/screen -dmS MCServer /usr/bin/java -Xms5120m -Xmx5120m -jar KCauldron.jar nogui
```


Can anyone point us in the right direction? Thanks in advance!

---

### Post by TheFu on 2016-10-13
Didn't think that running any GUI apps from within rc.local worked. Extra steps are needed to connect to an X-session, I believe and since no userid has logged in via X, no session exists.

But I could be wrong.

---

### Post by homemadejam-1 on 2016-10-13
We're running the Minecraft Server in a nogui mode :)
The ssh connection also has no gui.

We can run the commands once we're logged in,and they work just as they should do. the only issue we're having is when we've added them to the rc.local file.

---

### Post by ian-weisser on 2016-10-13
If you want an application to run at startup (like a minecraft server), then do it the expected, safe, and maintainable way: Create a system user to own it, and an upstart job (14.04) or systemd service (16.04) to start it at the appropriate time (like network-up).

EDIT: This is how I successfully and safely ran a minecraft server for several years.

It is very unwise to run an internet-facing server under your personal (admin) login. You bypass several layers of security precautions.

---

### Post by TheFu on 2016-10-14
> **homemadejam-1 said:**
> We're running the Minecraft Server in a nogui mode :)
The ssh connection also has no gui.

We can run the commands once we're logged in,and they work just as they should do. the only issue we're having is when we've added them to the rc.local file.

Non-GUI "mode" may not matter/help. It depends on which libraries the code was linked with. If they included any GUI libraries, then it won't start without a working X-session. I suspect the mindcraft guys **didn't** do that, since lots and lots of people run mindcraft on servers that don't have any GUIs.  But for the other program ... that is a different question. You can look at the symbols and determine if any X/Windows calls are made using the nm command (I vaguely remember).  Also, using "strings" on the program should show symbols too.  If it is linked to GUI libraries, then you'll need to provide a virtual GUI for the program to connect with.  xvfb is normally how that is accomplished. [https://linux.die.net/man/1/xvfb](https://linux.die.net/man/1/xvfb)  You don't need that if there aren't any linked GUI libraries, so don't set it up if it isn't needed.

Things started in rc.local run as root, unless you shift to a different userid - (su -l thefu -c /full/path/to/startup-script-program).  These are not login sessions, so $HOME and other environment variables aren't normally set. For things like JAVA programs, it is possible/likely that JAVA_HOME isn't set, so any programs based on Java won't run either.  Ensure those variables are set.

BTW, you are saying "screen" ... is that a generic term or for the specific "screen" program?  I don't use tmux/screen myself, but understand that some people are completely addicted.

OTOH, this might not have **anything** to do with this issue.

---

