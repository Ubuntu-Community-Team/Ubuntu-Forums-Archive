---
title: "lsh-server installation problems"
date: 2006-12-18
forum: Server Platforms
---

### Post by netdicted on 2006-12-18
Using Ubuntu Dapper in a server configuration issued the following command with the following results;

root@XXXXXX:~# apt-get install lsh-server lsh-utils lsh-client
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  lsh-utils-doc
The following NEW packages will be installed:
  lsh-client lsh-server lsh-utils
0 upgraded, 3 newly installed, 0 to remove and 24 not upgraded.
Need to get 0B/1104kB of archives.
After unpacking 2589kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package lsh-utils.
(Reading database ... 17641 files and directories currently installed.)
Unpacking lsh-utils (from .../lsh-utils_2.0.1cdbs-4_i386.deb) ...
Selecting previously deselected package lsh-client.
Unpacking lsh-client (from .../lsh-client_2.0.1cdbs-4_i386.deb) ...
Selecting previously deselected package lsh-server.
Unpacking lsh-server (from .../lsh-server_2.0.1cdbs-4_i386.deb) ...
Setting up lsh-client (2.0.1cdbs-4) ...
Setting up lsh-utils (2.0.1cdbs-4) ...

Setting up lsh-server (2.0.1cdbs-4) ...
Creating lsh host key (this only needs to be done once): /etc/lsh_host_keylsh-keygen: **Too permissive permissions on seed-file.**
lsh-keygen: Failed to initialize randomness generator.
lsh-writekey: Empty key on input, giving up.
invoke-rc.d: initscript lsh-server, action "start" failed.

What in the world does "**Too permissive permissions on seed-file.**"

Any help with this would be greatly appreciated. I've uninstalled using > apt-get remove lsh-server lsh-utils lsh-client to see if it is simply a matter of a temporary file. The machine has been rebooted to clear cache or any temp files generated as well to no avail.

help...

---

### Post by chalex on 2006-12-18
Is there a particular reason you need to use lsh and not ssh?

`apt-get install ssh`?

---

### Post by netdicted on 2006-12-19
I had ssh installed but it didn't seem to be communicating with the OpManager program that I needed it to talk to. After all was said and done, I decided on a different method.

---

