---
title: "Bizarre:  htop shows all cpus maxed, but no process is using cpu"
date: 2014-07-30
forum: Server Platforms
---

### Post by lykwydchykyn on 2014-07-30
Something went really wrong with my 12.04 LTSP server today.

The clients wouldn't boot.  When I ssh into the server and run htop, all the CPU cores (there are 8) appear maxed or near maxed.  Yet, no process appears to be using a lot of cpu.  There are no errors showing in syslog or dmesg.   The server was just rebooted yesterday because the clients froze up.

I rebooted the server and htop is now appearing normally, but I wonder for how long.

I haven't changed anything on the server in recent months.  Has anyone seen behavior like this?

EDIT: 

It's happening again this morning.  Clients are still working ok, but htop is showing crazy cpu activity.  Here's a screenshot:

---

### Post by lykwydchykyn on 2014-07-31
With help from the kind folks at #ubuntu-server, I was able to figure out that my .xsession script for the clients had a bug that was causing "ps" to be run in an infinite loop.  The processes were respawning so fast they couldn't show up in top, but were killing the cpus.

---

