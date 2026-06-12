---
title: "sybase server not working after upgrade from 10.04 to 10:10"
date: 2010-11-19
forum: Server Platforms
---

### Post by pshaik on 2010-11-19
I had sybase server running on my desktop but after the upgrade it does not seam to start properly. tried to restart the server many times but does not seam to help

Any help greatly appreciated

The logs are displaying as below
00:00000:00001:2010/11/19 13:53:08.21 server  Recovery complete.
00:00000:00010:2010/11/19 13:53:08.26 kernel  Initializing Job Scheduler Task
00:00000:00010:2010/11/19 13:53:08.39 kernel  Installed Job Scheduler sequencer code version 0.27 - 27 tokens
00:00000:00010:2010/11/19 13:53:18.63 kernel  Job Scheduler Task state set to running, startcount 1.
00:00000:00010:2010/11/19 13:53:28.73 kernel  Job Scheduler Task connected with Agent on port 4900
00:00000:00001:2010/11/19 13:53:28.73 server  ASE's default unicode sort order is 'binary'.
00:00000:00001:2010/11/19 13:53:28.73 server  ASE's default sort order is:
00:00000:00001:2010/11/19 13:53:28.73 server      'bin_iso_1' (ID = 50)
00:00000:00001:2010/11/19 13:53:28.73 server  on top of default character set:
00:00000:00001:2010/11/19 13:53:28.73 server      'iso_1' (ID = 1).
00:00000:00001:2010/11/19 13:53:28.73 server  Master device size: 30 megabytes, or 15360 virtual pages. (A virtual page is 2048 bytes.)
00:00000:00010:2010/11/19 13:53:28.84 kernel  Setting console to nonblocking mode.
00:00000:00010:2010/11/19 13:53:28.84 kernel  Job Scheduler Task lost its Agent connection (Connection reset by peer)
00:00000:00010:2010/11/19 13:53:33.83 kernel  Job Scheduler Task failed (re)connecting to its Agent (Connection refused)
00:00000:00010:2010/11/19 13:53:33.85 kernel  Job Scheduler Task state set to stop

---

### Post by cariboo on 2010-11-20
A bump for the move.

---

