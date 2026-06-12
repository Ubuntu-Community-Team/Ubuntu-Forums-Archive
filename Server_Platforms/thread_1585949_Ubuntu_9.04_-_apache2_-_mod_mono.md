---
title: "Ubuntu 9.04 - apache2 - mod_mono"
date: 2010-10-01
forum: Server Platforms
---

### Post by MaedMaex on 2010-10-01
Hello! I already searched the forum but wasn't able to find a solution for my problem.
 
According to some tutorials I try to set up an apache2 server with mod_mono.
 
The Problem is that whatever procedure I try, at the end the browser tells me:
[INDENT]Service Temporarily Unavailable
[/INDENT]apache2 error.log says:
[INDENT]Failed to connect to mod_mono_sever after several attemps to spawn the process.
[/INDENT]I'm running an apache 2.2.11 whith mod_mono 2.0
 
Actually I tried to configure according to [https://help.ubuntu.com/community/ModMono](https://help.ubuntu.com/community/ModMono) via AutoHosting as well as Non-AutoHosting.
 
Best working , until now, seemed to be the tut on [http://www.smithvoice.com/ubuntu-810-server-apache-mono](http://www.smithvoice.com/ubuntu-810-server-apache-mono) -> running up to the end of part 7 -> after conf in part 9 -> same errors.
 
Anyone who can help me? :confused:

---

### Post by directhex on 2010-10-02
Okay.

1) do you have apt:mono-apache-server and apt:mono-devel installed?

2) can you paste all lines from your apache log near the one you mentioned?

3) can you paste your config files?

---

### Post by MaedMaex on 2010-10-04
1)
 
I've installed mono-apache-server-2
 
2)
 
[Fri Oct 01 16:17:40 2010] [notice] caught SIGTERM, shutting down
[Fri Oct 01 16:17:41 2010] [error] Failed running '/usr/bin/mod-mono-server --filename /tmp/mod_mono_server_global --nonstop --master (null) (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory
[Fri Oct 01 16:17:41 2010] [notice] Apache/2.2.11 (Ubuntu) mod_mono/2.0 configured -- resuming normal operations
[Fri Oct 01 16:17:50 2010] [error] Failed to connect to mod-mono-server after several attempts to spawn the process.
[Fri Oct 01 16:17:50 2010] [error] [client 192.168.66.37] File does not exist: /var/www/favicon.ico
[Fri Oct 01 16:18:04 2010] [error] Failed to connect to mod-mono-server after several attempts to spawn the process.
[Fri Oct 01 16:18:04 2010] [error] [client 192.168.66.37] File does not exist: /var/www/favicon.ico
[Fri Oct 01 16:18:23 2010] [notice] caught SIGTERM, shutting down
[Fri Oct 01 16:19:23 2010] [error] Failed running '/usr/bin/mod-mono-server --filename /tmp/mod_mono_server_global --nonstop --master (null) (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory
[Fri Oct 01 16:19:23 2010] [notice] Apache/2.2.11 (Ubuntu) mod_mono/2.0 configured -- resuming normal operations
[Fri Oct 01 16:20:47 2010] [error] Failed to connect to mod-mono-server after several attempts to spawn the process.
[Fri Oct 01 16:35:35 2010] [notice] caught SIGTERM, shutting down
[Fri Oct 01 16:36:33 2010] [notice] Apache/2.2.11 (Ubuntu) mod_mono/2.0 configured -- resuming normal operations
[Fri Oct 01 16:37:53 2010] [error] Failed to connect to mod-mono-server after several attempts to spawn the process.
[Fri Oct 01 16:44:52 2010] [error] Failed to connect to mod-mono-server after several attempts to spawn the process.
[Mon Oct 04 08:05:34 2010] [notice] caught SIGTERM, shutting down
[Mon Oct 04 08:05:36 2010] 
[notice] Apache/2.2.11 (Ubuntu) mod_mono/2.0 configured -- resuming normal operations

3)
 
which config files exactly would you like to see?

---

### Post by MaedMaex on 2010-10-04
At least i tried to set it again from buttom up.
 
1. I installed apache2
2. libapache2-mod-mono
3. mono-apache-server2
4. made symlink from gmcs2 to gmcs
 
5.1. One said to make entry in httpd.conf
[INDENT]MonoAutoApplication enabled
[LIST]
[*]without my browser tells me that the XML-Page cannot be shown.
[/LIST][INDENT]->Ok! Apche cannot handle the aspx-page.
[/INDENT]
[LIST]
[*]with the entry i get th error:
[/LIST][INDENT]Service Temporarily Unavailable
[/INDENT][/INDENT]5.2 made entry in mod_mono.conf
[INDENT]1. edited Include to mono-server2
2. pasted at the end
[INDENT]Alias /test "/var/www"
AddMonoApllications default "/test:/var/www"
<Location /test>
SetHandler mono
</Location>
[/INDENT][/INDENT]But my error.log now just says: ".... mod_mono/2.0 ... configured -- resuming normal operation
 
[INDENT][INDENT] 
[/INDENT] 
 
[/INDENT]

---

### Post by directhex on 2010-10-04
> **MaedMaex said:**
> 4. made symlink from gmcs2 to gmcs

Argh.

Undo that, install apt:mono-devel.

Then try running "mod-mono-server" in a console, see if it spits out an error.

---

