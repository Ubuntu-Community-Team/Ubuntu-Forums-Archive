---
title: "Problem vith AutoTools for rutorrent (rtorren)"
date: 2012-04-11
forum: Server Platforms
---

### Post by Fredrik_b on 2012-04-11
System: Virtual Ubuntu 10.04 32bit in Hyper -v Windows 8 server.
Installed rtorrent via script: [http://ubuntuforums.org/showthread.php?t=1652105&highlight=rtorrent+script](http://ubuntuforums.org/showthread.php?t=1652105&highlight=rtorrent+script)

Edited php.ini so that: register_argc_argv = On


I got it partially working

> [11.04.12 13:59:23] AutoLabel: --- begin ---
[11.04.12 13:59:23] AutoLabel: enabled * * * * : 1
[11.04.12 13:59:23] AutoLabel: template * * * *: "{DIR}"
[11.04.12 13:59:23] AutoLabel: get_directory * : /media/server/media/default/
[11.04.12 13:59:23] AutoLabel: d.get_directory : /media/server/media/default/FILE.RELEASE
[11.04.12 13:59:23] AutoLabel: d.get_custom3 * : 
[11.04.12 13:59:23] AutoLabel: d.is_multy_file : 1
[11.04.12 13:59:23] AutoLabel: label * * * * * : ""
[11.04.12 13:59:23] AutoLabel: --- end ---
.
.
.
[11.04.12 14:02:48] AutoMove: --- begin ---
[11.04.12 14:02:48] AutoMove: enabled * * * * *: 1
[11.04.12 14:02:48] AutoMove: path_to_finished : /media/server/media/_cloud/tv
[11.04.12 14:03:48] AutoMove: rXMLRPCRequest() fail (get_directory, d.get_base_path)
[11.04.12 14:03:48] AutoMove: --- end ---


This above resulted in that a few of the files was moved to correct catalog and rest was gone.

Later tested again, with this result

> [11.04.12 14:08:55] AutoLabel: --- begin ---
[11.04.12 14:08:55] AutoLabel: enabled * * * * : 1
[11.04.12 14:08:55] AutoLabel: template * * * *: "{DIR}"
[11.04.12 14:08:55] AutoLabel: get_directory * : /media/server/media/default/
[11.04.12 14:08:55] AutoLabel: d.get_directory : /media/server/media/default/tv/bl/FILE.RELEASE2
[11.04.12 14:08:55] AutoLabel: d.get_custom3 * : 
[11.04.12 14:08:55] AutoLabel: d.is_multy_file : 1
[11.04.12 14:08:55] AutoLabel: label * * * * * : "tv/bl"
[11.04.12 14:08:55] rtExec: d.set_custom1
[11.04.12 14:08:55] AutoLabel: --- end ---
[11.04.12 14:09:15] 
[11.04.12 14:09:15] AutoWatch: --- begin ---
[11.04.12 14:09:15] AutoWatch: enabled * * * * *: 0
[11.04.12 14:09:15] AutoWatch: autostart * * * *: 0
[11.04.12 14:09:15] AutoWatch: --- end ---
.
.
.
[11.04.12 14:11:09] AutoMove: --- begin ---
[11.04.12 14:11:09] AutoMove: enabled * * * * *: 1
[11.04.12 14:11:09] AutoMove: path_to_finished : /media/server/media/_cloud/tv
[11.04.12 14:12:09] AutoMove: rXMLRPCRequest() fail (get_directory, d.get_base_path)


This time nothing was moved but the connection to retorrent was momentarily lost.

---

