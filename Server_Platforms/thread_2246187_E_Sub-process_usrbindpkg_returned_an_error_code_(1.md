---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1) when installing Red5"
date: 2014-09-29
forum: Server Platforms
---

### Post by meligira on 2014-09-29
Hi, 

I have Ubuntu Server 14.04.1 running in VMWare, and when I execute sudo apt-get install red5-server, it always ends in the same error:

E: Sub-process /usr/bin/dpkg returned an error code (1)

Can you please help me?

Thanks in advance.

---

### Post by ian-weisser on 2014-09-29
Please try installing red5-server using the command line (sudo apt-get install red5-server),
and please show us the *entire* output.

The actual dpkg error message, and the context, are necessary.
The mere fact of failure (error code 1) isn't helpful enough. The cause could be almost anything.

---

### Post by meligira on 2014-10-01
Hi, 

Thanks for replaying... I already tried that command and here it's the result with error:

[SIZE=2][COLOR=#000000][FONT=Verdana]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Building dependency tree  [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Reading state information... Done[/FONT][/COLOR]
[FONT=Verdana][COLOR=#000000]red5-server is already the newest version[/COLOR][/FONT]
[COLOR=#000000][FONT=Verdana]0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
[/FONT][/COLOR]1 not fully installed or removed.
[COLOR=#000000][FONT=Verdana]After this operation, 0 B of additional disk space will be used.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Do you want to continue? [Y/n] Y[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Setting up red5-server (1.0~svn4374-3) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]* Starting Flash streaming server red5-server  [/FONT][/COLOR][COLOR=#000000][FONT=Verdana][fail] [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]invoke-rc.d: initscript red5-server, action "start" failed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]dpkg: error processing package red5-server (--configure):[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]subprocess installed post-installation script returned error exit status 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Errors were encountered while processing:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]red5-server[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]E: Sub-process /usr/bin/dpkg returned an error code (1)

Let me know what can I do.

Thanks in advance.[/FONT][/COLOR][/SIZE]

---

### Post by ian-weisser on 2014-10-01
> **meligira said:**
> [SIZE=2][COLOR=#000000][FONT=Verdana][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Setting up red5-server (1.0~svn4374-3) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]* Starting Flash streaming server red5-server  [/FONT][/COLOR][COLOR=#000000][FONT=Verdana][fail] [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]invoke-rc.d: initscript red5-server, action "start" failed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]dpkg: error processing package red5-server (--configure):[/FONT][/COLOR][COLOR=#000000][FONT=Verdana][/FONT][/COLOR][/SIZE]

So the package installs and configures, but won't start. And dpkg, due to that failure to start, won't consider it fully configured.
What error message occurs if you try to start it manually?
```
sudo /etc/init.d/red5-server start
```

---

### Post by meligira on 2014-10-02
Hi,

I tried what you suggested and this is what I got:

[COLOR=#000000][COLOR=#000000][FONT=Verdana]* Starting Flash streaming server red5-server  [/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Verdana][fail][/FONT][/COLOR][/COLOR]

---

### Post by ian-weisser on 2014-10-02
Well, now we know why the config script is failing.

I think you have been bitten by an already-reported bug:
[https://bugs.launchpad.net/ubuntu/+source/red5/+bug/1123483](https://bugs.launchpad.net/ubuntu/+source/red5/+bug/1123483)

While you can easily edit the post-install script to report success (and free up the package manager), it won't get any closer to running the software.
My best recommendation is to uninstall/remove red5-server.

---

### Post by meligira on 2014-10-02
Thanks for your help!

But do you think there is a way I can install red5, even if it is another version of ubuntu?

---

