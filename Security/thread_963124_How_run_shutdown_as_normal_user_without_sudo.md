---
title: "How run shutdown as normal user without sudo"
date: 2008-10-29
forum: Security
---

### Post by amosbatto on 2008-10-29
Can I permit a normal user to execute /sbin/shutdown without using sudo? 

Here is what happens on my computer running Ubuntu 8.04 as the user "vato":
$ shutdown -h now
shutdown: Need to be root

$ sudo chmod +x /sbin/shutdown

$ ls -l /sbin/shutdown
-rwxr-xr-x 1 root root 44312 2008-04-11 09:50 /sbin/shutdown

$ shutdown -h now
shutdown: Need to be root

$ sudo chown vato /sbin/shutdown
chown: changing ownership of `/sbin/shutdown': Operation not permitted

$ sudo chgrp vato /sbin/shutdown

$ shutdown -h now
shutdown: Need to be root


Alright, so Ubuntu doesn't let me change the owner of /sbin/shutdown
and /sbin/shutdown seems to only run if I am root (or I use sudo). I want to run it as a normal user without having to type sudo. Is that possible?

---

### Post by kerry_s on 2008-10-29
just put shutdown with no password in the sudoers file.

example:
user ALL=NOPASSWD: /sbin/shutdown

you can add as many programs as you want.
example:
user ALL=NOPASSWD: /sbin/shutdown, /usr/sbin/synaptic, /usr/bin/nautilus, /usr/bin/gedit, etc...

you can also create a group:

%staff ALL=NOPASSWD: /sbin/shutdown

you'll still have to use sudo, but it won't ask for a password.

example:

sudo shutdown -r now
sudo shutdown -h now

man sudoers for more info

i use jwm, so it's in my menu

---

### Post by ds[de] on 2008-11-01
You could set the s-bit to enable non-superusers to run programs as root, e.g.

```
sudo chmod a+s /sbin/shutdown
```

After that, you can run 'shutdown' as a normal user.


Regards,
ds[de]

---

### Post by ahso4271 on 2011-08-21
can i run a command as normal user after a sudo within a bash script? Even without sudo the following command remains as root started.

---

### Post by madhater on 2011-08-21
No. As far as I know you need root level permissions to issue the shutdown command. It is also very insecure to allow no sudo users to issue the shutdown command (or any other variants thereof, poweroff, halt etc).

- madhater

---

### Post by scorp123 on 2011-08-21
> **ahso4271 said:**
> can i run a command as normal user after a sudo within a bash script?  You can run stuff password-less with sudo if you put all the commands that would require root priviledges and which appear in your bash script into the sudoers file, with a complete path. What I mean is this: this is an example on my own system. This script establishes a VPN connection (using a closed-source product) to a customer of mine:

```
#! /bin/bash
/usr/local/bin/barracudavpn --start -r MyPasswordHere
sudo route add -net 10.20.50.0 netmask 255.255.255.0 gw 192.168.200.254
sudo route add -net 10.20.51.0 netmask 255.255.255.0 gw 192.168.200.254
sudo route add -net 10.20.52.0 netmask 255.255.255.0 gw 192.168.200.254
sudo route add -net 10.20.54.0 netmask 255.255.255.0 gw 192.168.200.254
sudo route add -net 10.15.50.0 netmask 255.255.255.0 gw 192.168.200.254
```

The many route commands up there are needed or else I would still be unable to reach anything. And those route commands need "sudo". And because it's troublesome to remember the exact syntax each time I put all those lines up there into a single script:  **vpn.sh**

The idea is that I can launch that script from a terminal without being asked the password each time. So I put each of those "route" commands into sudoers too:
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# User sysadm may poweroff the system if he wants to
sysadm     ALL=NOPASSWD: /sbin/poweroff
sysadm     ALL=NOPASSWD: /sbin/reboot

# User sysadm may use apt to update the system and clean the APT cache
sysadm     ALL=NOPASSWD: /usr/bin/apt-get clean
sysadm     ALL=NOPASSWD: /usr/bin/apt-get update
sysadm     ALL=NOPASSWD: /usr/bin/apt-get dist-upgrade


# VPN stuff:
sysadm     ALL=NOPASSWD: /sbin/route add -net 10.20.50.0 netmask 255.255.255.0 gw 192.168.200.254
sysadm     ALL=NOPASSWD: /sbin/route add -net 10.20.51.0 netmask 255.255.255.0 gw 192.168.200.254
sysadm     ALL=NOPASSWD: /sbin/route add -net 10.20.52.0 netmask 255.255.255.0 gw 192.168.200.254
sysadm     ALL=NOPASSWD: /sbin/route add -net 10.20.54.0 netmask 255.255.255.0 gw 192.168.200.254
sysadm     ALL=NOPASSWD: /sbin/route add -net 10.15.50.0 netmask 255.255.255.0 gw 192.168.200.254
```

Result: With above lines in place I can shutdown, reboot and update my system or establish VPN connections without ever being asked a password.

Of course you can add other commands too ... But please be aware that this is potentially dangerous (you can hose your system). You shouldn't put too much stuff in there. The powers of "root" should only be used if really really necessary.

EDIT:

Running stuff as normal user after "sudo" has been used could be done using **"su"** (= switch user). Example from my system -- I cut out the irrelevant parts. But this snippet here is from a script that runs as "root". But at the end of the script I'd like to start a VNC session as my normal user, not as root! Hence I use the **"su"** command so that things will get started under my normal user account's priviledges:

```

...
... VPN and routing stuff, all running as "root" ... I cut out that stuff
...

su - sysadm -c "/usr/bin/vnc4server :1 -depth 16 -geometry 1200x768 2>&1"

# end of script; we return a code 0 to signify success
exit 0

``` What happens on that line up there is that the script which is running as "root" uses **"su"** to switch into my normal account and there it starts a virtual VNC4 desktop using a resolution of 1200 x 768 (VNC resolutions don't have to real); the *"2>&1"* bit at the end suppresses any unwanted output (I need the script to run clean without generating unwanted messages).

So the syntax for **su** is:

**su - NAMEOFACCOUNT -c "command-you-want-to-execute"**

Yes, you can use that in scripts that run as "root" or via "sudo".

---

### Post by JRV on 2011-08-21
Adding shutdown to my sodoers file as described above works to shut down locally.

How do I shutdown a computer on my LAN with ssh?

---

### Post by scorp123 on 2011-08-22
> **JRV said:**
>  How do I shutdown a computer on my LAN with ssh? ```
ssh remoteuser@remotehost "sudo shutdown"
``` ... and if you use SSH keys and if you make sure that the "remoteuser" has an entry in the "sudoers" file of the remote system (as explained above) the above command will be password-less for both the SSH connection and "sudo".

This can indeed be useful for system administration.

---

### Post by sheetal064 on 2013-03-26
> **kerry_s said:**
> just put shutdown with no password in the sudoers file.

example:
user ALL=NOPASSWD: /sbin/shutdown

you can add as many programs as you want.
example:
user ALL=NOPASSWD: /sbin/shutdown, /usr/sbin/synaptic, /usr/bin/nautilus, /usr/bin/gedit, etc..

I used the following line, in my /etc/sudoers file

```

# User alias specification
user ALL=NOPASSWD:/sbin/poweroff,/sbin/shutdown

```

then in another terminal

 ```
$ poweroff
poweroff: Need to be root

```
,But no luck... Its not working.. 'm i missing something here
I'm running Precise on my system

---

### Post by wildmanne39 on 2013-03-26
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

