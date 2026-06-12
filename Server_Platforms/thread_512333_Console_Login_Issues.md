---
title: "Console Login Issues"
date: 2007-07-29
forum: Server Platforms
---

### Post by techstop on 2007-07-29
I have installed 7.04 as a VMWare VM. I have a slightly annoying issue where the VM boots, displays the login prompt and continues to load modules / run scripts. Therefore the login prompt is not the last thing displayed on screen. See screenie;

I can still login, but it is slightly irritating that the login is not the last thing displayed. Any hints? Cheers...

---

### Post by koenn on 2007-07-29
just a hunch : 

on most linux systems use, the startup procedure is described in the inittab, and eg booting to runlevel 2 would have the system wait for all rl2 scripts to finish before letting you login.

With upstart (Ubuntu 6.10 and newer), the startup scripts (can) run asynchronously / in parrallel - maybe what you're seeing is a reult of that, and if so, I'm inclined to consider it a bug, or you've been messing with the upstart config ...

---

### Post by hggdh on 2007-07-29
I do not see it as a bug: The idea is to have the system available for local usage as soon as possible.

The services that are being started after you get the login prompt are not required for local usage (mysql, apache, etc).

If you need them, then you can wait -- this will be no worse than what we had before, and it will take about the same time as before.

So: you can login while the system finishes startup, or you can wait.

---

### Post by koenn on 2007-07-29
Well, I haven't really thought about it, since for me (6.06) it's not yet an issue. It just struck me as odd that you'd login while the system isn't "ready" yet - Like, you (re)boot, login, and start doing something that, say, requires database access (a wiki maybe ?) - but you'r mysql is still starting ...  Would feel wrong, I think.

---

### Post by techstop on 2007-07-29
> **koenn said:**
> just a hunch : 

on most linux systems use, the startup procedure is described in the inittab, and eg booting to runlevel 2 would have the system wait for all rl2 scripts to finish before letting you login.

With upstart (Ubuntu 6.10 and newer), the startup scripts (can) run asynchronously / in parrallel - maybe what you're seeing is a reult of that, and if so, I'm inclined to consider it a bug, or you've been messing with the upstart config ...

I haven't done anything to the upstart config (wouldn't know how). I really think the login prompt should only be displayed when everything else is done and the machine is "ready", so I agree with koenn. Hmmm, another mystery...

---

### Post by hggdh on 2007-07-30
You should have a login prompt when the system initialisation has reached a point when it is possible to login. The services after this point should be auxiliary services, not critical system services [1].

For example, if SSH has not yet been started, then *remote* users will not be able to SSH in the box -- and they will be no wiser, since it will look to them as the machine is not yet started.

But, if you are in front of the console, you would be able to login -- since you do not need SSH for that.

Samewise for MySQL, Apache, etc.

[1] On Feisty we found that dbus startup was being done after gdm startup -- and THIS was really bad, since a lot of user services under Gnome depend on dbus having started. So... dbus startup was moved before gdm.

---

### Post by koenn on 2007-07-30
I understand the reasoning and it's not at all bad. 
I also assume that on a desktop, with a graphical login, you'll just be shown the login screen while services continue to startup without the user seeing it. 
However, on a server (or any CLI system), it looks kinda weird, and at least 1 user got a bit confused (re the OP). Then again, you don't reboot servers all that often so it's not really a big deal to me. It just feels a bit weird.

---

### Post by techstop on 2007-07-30
OK, so for the anally retentive among us, how do you *force* the login prompt to be the last thing displayed in the boot sequence? This is a virtual machine, so it does get rebooted quite often.

Cheers...

---

### Post by koenn on 2007-07-30
Sorry, no idea. I know next to nothing about upstart

---

### Post by tribaal on 2007-08-23
I'm having the same problem here - anybody digged a little further down into upstart?

Thanks

- trib'

---

### Post by cenwesi on 2007-11-30
i am having the exact same issue. No "login prompt" I can login to the server through ssh or "NX" but not directly on the server.

---

### Post by techstop on 2007-12-01
> **cenwesi said:**
> i am having the exact same issue. No "login prompt" I can login to the server through ssh or "NX" but not directly on the server.

Well, that's not the same issue then. See the screenshot in the first post. I get a login prompt, it's just not the last thing displayed. I can log in from the terminal.

---

### Post by portalcake on 2007-12-01
This worked like a charm for me (7.10 server), and it was an easy fix that made sense.  Found [here](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/65230/comments/13)
> To accomplish this task, edit /etc/event.d/tty1 and replace:

  ```
start on runlevel 2
```

with:

  ```
start on stopped rc2
```

---

### Post by cenwesi on 2007-12-01
lol, alt-f2 showed my login prompt. I recall hitting that to see the boot process when i rebooted my server after HardDrive issue.

---

