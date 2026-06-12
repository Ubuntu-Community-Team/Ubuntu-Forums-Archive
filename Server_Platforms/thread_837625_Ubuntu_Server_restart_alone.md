---
title: "Ubuntu Server restart alone"
date: 2008-06-22
forum: Server Platforms
---

### Post by ricardo.landim on 2008-06-22
Hi,

set up server with the following Hardware:
motherboard: Intel DG33BU
Processor: Intel(R) Core(TM)2 Duo CPU     E4600  @ 2.40GHz
Memory: 2Gb
HD: 160Gb SATA

I set up Ubuntu 8.04 LTS Server Edition for 32 bits processors in this machine. The installation its OK, but the server restart ALONE!

Logs from: /etc/log/messages

...
Jun 22 08:28:05 ubuntu -- MARK --
Jun 22 08:48:05 ubuntu -- MARK --
Jun 22 09:07:49 ubuntu syslogd 1.5.0#1ubuntu1: restart.
Jun 22 09:07:49 ubuntu kernel: Inspecting /boot/System.map-2.6.24-16-server
Jun 22 09:07:49 ubuntu kernel: Loaded 28738 symbols from /boot/System.map-2.6.24-16-server.
Jun 22 09:07:49 ubuntu kernel: Symbols match kernel version 2.6.24.
Jun 22 09:07:49 ubuntu kernel: Loaded 15923 symbols from 61 modules.
...

...
Jun 22 11:07:49 ubuntu -- MARK --
Jun 22 11:27:49 ubuntu -- MARK --
Jun 22 11:34:45 ubuntu syslogd 1.5.0#1ubuntu1: restart.
Jun 22 11:34:45 ubuntu kernel: Inspecting /boot/System.map-2.6.24-16-server
Jun 22 11:34:45 ubuntu kernel: Loaded 28738 symbols from /boot/System.map-2.6.24-16-server.
Jun 22 11:34:45 ubuntu kernel: Symbols match kernel version 2.6.24.
Jun 22 11:34:45 ubuntu kernel: Loaded 15923 symbols from 61 modules.
...

As you can see, the operation appears to be normal and without explanation of the machine restarts.

Someone went through it or know how to fix this problem?

Regards,
Ricardo Landim

---

### Post by cariboo on 2008-06-23
Is the computer actually restarting, because from your small snippet it looks like syslogd is restarting.

Jim

---

### Post by ricardo.landim on 2008-06-23
> **cariboo907 said:**
> Is the computer actually restarting, because from your small snippet it looks like syslogd is restarting.

Jim

Jim, 

I believe that is not syslogd. That line appears to restart normal.

Jun 21 12:55:05 ubuntu -- MARK --
Jun 21 13:15:05 ubuntu -- MARK --
Jun 21 13:41:46 ubuntu exiting on signal 15
Jun 21 13:45:15 ubuntu syslogd 1.5.0#1ubuntu1: restart.
Jun 21 13:45:15 ubuntu kernel: Inspecting /boot/System.map-2.6.24-16-server
Jun 21 13:45:15 ubuntu kernel: Loaded 28738 symbols from /boot/System.map-2.6.2
Jun 21 13:45:15 ubuntu kernel: Symbols match kernel version 2.6.24.
Jun 21 13:45:15 ubuntu kernel: Loaded 14583 symbols from 52 modules.

still unsolved problem!

---

### Post by MJN on 2008-06-23
Is their any apparent pattern to the reboot? Going back through the logs does it only happen when, say, you're using it at the time?

You need to try and eliminate potential causes as the way things stand there's nothing to go on. Could it be overheating? It might be worth booting from an install CD and using that for a while to see if you still get reboots (which *may* suggest a hardware issue, even more so if you use a different distro).

Mathew

---

### Post by ricardo.landim on 2008-06-23
I had the same problem when installed Debian Etch. I believe it is a problem BIOS.

---

### Post by cariboo on 2008-06-24
could you ssh into your server, then from the command line type:

```
cat /var/log/messages > message.txt
```

and attach the full log output to your next post?

Jim

---

### Post by gtdaqua on 2008-06-24
> **cariboo907 said:**
> could you ssh into your server, then from the command line type:

```
cat /var/log/messages > message.txt
```

and attach the full log output to your next post?

Jim

That would actually not give any output. The output will be recorded straight to message.txt instead of showing up on the console.

Basically, post the contents of the file "messages.txt". And when posting please use the 'code' tags so that the post is not too lengthy.

---

### Post by ricardo.landim on 2008-06-24
Put the file 'messages' in a folder publishes on the Internet. He is in:

[http://ricardo.pksolutions.com.br/messages.txt](http://ricardo.pksolutions.com.br/messages.txt)

---

