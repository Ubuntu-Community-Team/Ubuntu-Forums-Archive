---
title: "ubuntu 19.10 wayland blocking synaptic package manager"
date: 2019-11-03
forum: Security
---

### Post by lance bermudez on 2019-11-03
Can not ssh into my other computer to use synaptic package manager. ssh works but not synaptic package manager
```

lance@type40tardis:~$ ssh tardis
Authenticated to 192.168.1.1 ([192.168.1.1]:22).
Welcome to Ubuntu 19.10 (GNU/Linux 5.3.0-19-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage


0 updates can be installed immediately.
0 of these updates are security updates.

Last login: Sun Nov  3 11:32:34 2019 from 192.168.1.9
lance@tardis:~$ sudo synaptic
[sudo] password for lance: 
X11 connection rejected because of wrong authentication.
Unable to init server: Could not connect: Connection refused
Failed to initialize GTK.

Probably you're running Synaptic on Wayland with root permission.
Please restart your session without Wayland, or run Synaptic without root permission

```

how do I fix this?

---

### Post by The Cog on 2019-11-03
That last line says it. As you need root for synaptic, the answer is to not use Wayland. I gather that lack of support for a remote X session is a known shortcoming of Wayland.

Alternatively, use apt on the command line, e.g. apt search packagename, apt install packagename etc.

---

### Post by TheFu on 2019-11-11
I know nothing about 19.10 or Wayland but if you just **ssh remote-host**, no GUI programs can be run on any Unix X/Windows client showing the display  back on the X/Server machine.

On a 16.04 or earlier machine, the correct ssh command would be: ```
ssh -X tardis
``` to enable X/Windows programs to work.

Whenever running any GUI program with sudo, it is best to always force the HOME directory to be changed to that of the userid being elevated. This should prevent permission issues for config files.  The command I'd use is:
```
sudo -H synaptic
```
But I don't use synaptic and haven't tested it.  I did try to get a simple X11 client program running on a remote 19.10 server with a few client X11 libraries to display back on my 16.04 desktop, but it failed.  An xterm wanted 48 packages installed, which seemed a little excessive to me.  Added --no-install-recommends option and it dropped to 16 pkgs and the remote xterm worked fine. Next tried this:
```
$export XAUTHORITY=/home/thefu/.Xauthority  sudo -H xterm -sb 
```
That worked fine.

---

