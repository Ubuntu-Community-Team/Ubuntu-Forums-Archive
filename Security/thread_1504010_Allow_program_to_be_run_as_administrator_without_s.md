---
title: "Allow program to be run as administrator without sudo"
date: 2010-06-07
forum: Security
---

### Post by c.dubya on 2010-06-07
Certain commands like:
fdisk -l
nmap -sT 192.168.0.1/24
iftop

require administrator privileges to run.  A while ago i read a post(forgot where i read it) about being able to let a user run these commands in a script (that contains the desired command) created by the administrator/root without the user having to do a sudo and entering a password.  Does anyone know how i can go about doing this?

---

### Post by scorp123 on 2010-06-07
> **c.dubya said:**
> without the user having to do a sudo and entering a password. Why?

If you do it right then *"sudo **without** having to enter a password"* is no problem at all. Just use the "NOPASSWD" directive.

Example: I want to be able to reboot and poweroff my desktop whenever I like, without being asked for the password. And I'd like to be able to open my OpenVPN connection and change a few needed routes without having to enter any password.

So I'd open the "sudoers" list by invoking this command:
```
sudo visudo
```

And then add these entries at the bottom:

```
# Members of admin group may open VPN's via tuncfg
%admin ALL=NOPASSWD: /sbin/tuncfg
%hamachi ALL=NOPASSWD: /sbin/tuncfg

# OpenVPN
ron     ALL=NOPASSWD: /usr/sbin/openvpn --config /etc/openvpn/oracle/client.conf
ron	ALL=NOPASSWD: /usr/sbin/oracle_openvpn_routes.sh
ron	ALL=NOPASSWD: /sbin/route add -net 10.95.0.0 netmask 255.255.255.128 gw 10.8.100.9
ron     ALL=NOPASSWD: /sbin/route add -net 10.168.20.0 netmask 255.255.255.0 gw 10.8.100.9
ron     ALL=NOPASSWD: /sbin/route add -net 10.168.21.0 netmask 255.255.255.0 gw 10.8.100.9

# User ron may poweroff the system if he wants to
ron     ALL=NOPASSWD: /sbin/poweroff
ron	ALL=NOPASSWD: /sbin/reboot

```

Taddaaa!

Now when I enter e.g. **"sudo poweroff"** then the system will instantly poweroff and I never ever get to see the password prompt because of the "NOPASSWD" option up there.

But be cautious ... it's very tempting to use the "NOPASSWD" switch up there for all sorts of rather dangerous commands. You could easily hose your system if you use it with the wrong commands. Sometimes getting nagged by that password prompt is indeed a good thing!

---

### Post by dtfinch on 2010-06-07
I've never tried it, but [http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid)

Not sure if it'd work on scripts too, or only binary executables.

---

### Post by blchinezu on 2010-06-07
if you use it for personal home use you can use this function:

```
[B]
sudo_fc[/B] () { **echo** "_YOUR_PASSWORD_" | **sudo** -S $@; }
```and just call it like this: **sudo_fc ***mkdir /new_dir*
or what command you want to run

however it's not too security friendly... as you're exposing your password

---

