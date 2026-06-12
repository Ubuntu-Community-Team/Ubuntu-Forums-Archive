---
title: "NX Server connections from outside"
date: 2006-11-20
forum: Server Platforms
---

### Post by robert@debian on 2006-11-20
Hi folks,

I've set up an NX Server, by installing the .debs provided by nomachine.com. I used partly the HowTo's from ubuntuforums.org and the installationguide @ nomachine.com.
The Server runs perfect. I can connect from every PC in the LAN, unfortunally if i try to reach the NX Server from outside I just get errors.

_What have i done so far:_

1. On a fresh XUbuntu installation I've installed the OpenSSH Server, nxclient, nxnode and nxserver package. All works fine 
2. I made userconfigurations and set up the clientsoftware for windows. (Port 22 is forwarded)
3. First I tryed to connect within the LAN and it worked. Then from outside and i get this msg:

I stuck on **negotiating link parameters ** and under Details this output:

```

Info: Proxy running in client mode with pid '2736'.
Session: Starting session at 'Mon Nov 20 19:52:58 2006'.
Info: Connecting to remote host 'xxx.xxx.xxx.xxx:**5015**'.
Info: Connection to remote proxy 'xxx.xxx.xxx.xxx:**5015**' established.
Error: The remote NX proxy closed the connection.
Error: Failure negotiating the session in stage '7'.
Error: Wrong version or invalid session authentication cookie.
Session: Terminating session at 'Mon Nov 20 19:53:03 2006'.
Session: Session terminated at 'Mon Nov 20 19:53:03 2006'.

```

I'm puzzled because of the Port 5015 :confused: 
Everytime i connect this Port seems to change, unpredictably ;-(
Somewhat 50xx 

I can however connect from outside via Putty @ Port 22, thus i'll guess the problem isn't port forwarding.

---

### Post by Macchi on 2006-11-20
Strange behavior on your system because by default everything should be handled by the ssh port 22 if you choose forwading through SSH. Did you choose that on the server configuration and on the client?

I was able to install directly from the packages provided by NoMachine and everything worked "out of the box". The ports for external connections can be later customized on the openssh-server configuration file on /etc/ssh/sshd.conf.

Later, when you get the system to work with NX I would really recommend to use strong passwords and change the port 22 to some other value. This is important in order to avoid attacks to your server! Later you may authenticate SSH & NX through keys. You may also add an excellent security tool called DenyHosts, that blocks succcessive unauthorized login attempts, thus avoiding dictionary attacts to your server. DenyHosts may also share a database to block known attackers from establishing any connections to your system.

Probably the fastest way to get NX to work would be to remove (and importantly --purge) the nx and openssh-server packages, restart the system and then install again the nx(server,client,node) and also openssh-server. It worked for me!

---

### Post by Roddles on 2006-11-20
Hi

I have had this problem with NX server before as well - You have to make sure that the connection you are establishing is encrypted - then that message goes away and its all good. The option to check is "Enable SSL on all traffic".

Hope this helps

Cheers

Rod.

---

### Post by robert@debian on 2006-11-21
Thanks for your help,

I forget to enable SSL in Advanced Options

> "Enable SSL on all traffic"

Now it works :KS

---

### Post by B0ND on 2007-01-26
I realize this is an old thread, but I seem to be having the same problems as the original poster. I recieve nearly the same error message when trying to log into an NX server that my university has set up. I'll post the error message here just incase someone might be able to see a significant difference:

[FONT="Courier New"]Info: Display running with pid '1728' and handler '0x1f069a'.
NXPROXY - Version 2.0.0

Copyright (C) 2001, 2006 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '3876'.
Session: Starting session at 'Fri Jan 26 14:18:08 2007'.
Error: The remote NX proxy closed the connection.
Error: Failure negotiating the session in stage '7'.
Error: Wrong version or invalid session authentication cookie.
Session: Terminating session at 'Fri Jan 26 14:19:07 2007'.
Session: Session terminated at 'Fri Jan 26 14:19:07 2007'.[/FONT]


I've had quite a few people look at my computer and try to figure out what is wrong, but no one seems to be able to figure it out.

I have selected "Enable SSL encryption of all traffic" which seemed to be the problem of the original poster.

Here's some general info about some of the things I've tried:
-uninstalling and reinstalling using various versions (2.1.0, 2.0.0, 1.5.0), this includes deleting all the .nx stuff both on my local machine and my account on the nx server
-installed and run nx on another computer of mine which works fine
-turning off my windows firewall and antivirus software


There seem to be some very knowledgeable people on this forum, I would appreciate any help! If you need more information please let me know and I'll do my best to provide it.

Eric

---

### Post by dmonty on 2007-02-06
> **B0ND said:**
> I realize this is an old thread, but I seem to be having the same problems as the original poster. I recieve nearly the same error message when trying to log into an NX server that my university has set up. I'll post the error message here just incase someone might be able to see a significant difference:


I'm having the same problem.  It works fine on one computer but not on another.  Same configuration for both.


[INDENT]
Package: freenx
Version: 0.4.4+0.4.5-4ubuntu3
Package: libxcomp1
Version: 1.4.92+1.5.0-11ubuntu1
Package: libxcompext1
Version: 1.4.92+1.5.0-11ubuntu1
Package: nxagent
Version: 1.4.92+1.5.0-11ubuntu1
Package: nxlibs
Version: 1.4.92+1.5.0-11ubuntu1
[/INDENT]


One thing i did notice if I capture the client session directory on the server just before it crashes and gets deleted  .nx/C*

[INDENT]
[email]root@melakah:~/.nx[/email]/c# cat errors
Loop: PANIC! Refusing connection from '192.168.0.53' on port '40123'.
[email]root@melakah:~/.nx[/email]/c# cat session

Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'

NXAGENT - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Agent running with pid '21049'.
nxagentProcessOptionsFile: Option file is [/home/dmonty/.nx/C-melakah-1001-661AA695366309F509737ABAC648B207/options].
nxagentProcessOptionsFile: Option file is 213 bytes long.
nxagentParseOptionString: Warning ignored option 'cache' = '8M'.
nxagentParseOptionString: Warning ignored option 'images' = '32M'.
nxagentParseOptionString: Warning ignored option 'link' = 'adsl'.
nxagentParseOptionString: Warning ignored option 'type' = 'unix-kde'.
nxagentParseOptionString: Warning ignored option 'cleanup' = '0'.
nxagentParseOptionString: Warning ignored option 'accept' = '127.0.0.1'.
nxagentParseOptionString: Warning ignored option 'cookie' = '633517b494183186d90e2599630b2da9'.
nxagentParseOptionString: Warning ignored option 'samba' = '0'.
nxagentParseOptionString: Warning ignored option 'media' = '0'.
Info: Proxy running in server mode with pid '21049'.
Info: Waiting for connection from '127.0.0.1' on port '5001'.
Error: Refusing connection from '192.168.0.53' on port '40123'.
[email]root@melakah:~/.nx[/email]/c#

[/INDENT]

It looks like there is a problem when the server tries to connect to itself through 192.168.0.53.

---

### Post by B0ND on 2007-02-06
I got the problem fixed on my computer, it ended up being a conflict with my anti-virus software (NOD32). I had tried disabling the AV before, but apparently it needs to be completely shut down or removed. I uninstalled NOD32, installed some other AV software and everything works great. Hope this helps other people that were having similar problems.

---

