---
title: "How to block a program from accessing Internet with iptables"
date: 2023-05-29
forum: Security
---

### Post by holmj on 2023-05-29
Hello all, I have searched the web but no really answer found. There is software like Firejail to do this, but I don't want some soft using my resources for this one only. How can this be done with iptables? Please help I wish to block packettracer from access the internet.

---

### Post by TheFu on 2023-05-30
**firejail** would be a good choice and light, but you might like **OpenSnitch** if you want more control over all the applications you use.  I found it too complex to setup, but I may have been over-thinking it.

iptables is a system-level firewall.  While it is possible to make it application or user level, doing that is non-trivial.

---

### Post by Rubi1200 on 2023-05-30
I'd be tempted to ask why not just remove the application?

Are you sure it is accessing the internet?

Please show the output for this:

```
sudo ss -lntp
```

---

### Post by #&amp;thj^% on 2023-05-30
> **holmj said:**
> Hello all, I have searched the web but no really answer found. There is software like Firejail to do this, but I don't want some soft using my resources for this one only. How can this be done with iptables? Please help I wish to block packettracer from access the internet.

Along with all the good advice from both posters {Rubi1200 TheFu}, I have a friend that has come up with a good tool for that: [https://gitlab.com/douaneapp/Douane](https://gitlab.com/douaneapp/Douane)
EDIT:
Maybe that might not be the easiest for some but don't forget bubblewrap Bubblewrap is a nice lightweight wrapper around namespaces that can totally disable all network access, among other things.
```

bwrap --bind / / --unshare-net firefox
```

Firejail and bubblewrap are similar but bwrap is much more simple and a bit lower level, it also provides lots of flexibility.

You can use namespaces directly with the unshare command as well. I don't remember the exact flags but you need to unshare user and network namespaces.

Another way, Create a network namespace, and don't route anything to it:
```

sudo ip netns add offline
```

Then run your command in that namespace as whatever user you want
```

sudo ip netns exec offline su "SOMEUSERNAME" -c "CMD"
```

For firejail, If you don't use firejail you can just use "unshare -r -n". I have it aliased to offline.

---

### Post by #&amp;thj^% on 2023-05-31
I gave this some more thought last nite and came up with this:
Please understand this>>I use firewalld...
If you are running the program as specific user (or group), you can use iptables to filter the traffic to prevent access:
```

iptables -A OUTPUT -m user --user <user> -j DROP
```

Filtering by (primary) group works similarly by replacing --user <user> with --group <group>. If you add your regular user to your no-internet group, you can run the application in that group using sg. A step-by-step answer is provided in serverfault answer.

Firewalld uses iptables to implement the firewall. Iptables rules can be added by using Direct Interface as well.



The solution for me happened to be straight forward.

 [list]
        [*]Create, validate new group; add required users to this group:
        [*]Create: groupadd no-internet
        [*]Validate: grep no-internet /etc/group
        [*]Add user: useradd -g no-internet username

        [*]Note: If you're modifying already existing user you should run: usermod -a -G no-internet userName check with : sudo groups userName[/list]
[list]
    [*]Create a script in your path and make it executable:

    [*]Create: nano /home/username/.local/bin/no-internet
    [*]Executable: chmod 755 /home/username/.local/bin/no-internet
    [*]Content:[/list]
```

#!/bin/bash
sg no-internet "$@"
```

    [list]
        [*]Add iptables rule for dropping network activity for group no-internet:
```
iptables -I OUTPUT 1 -m owner --gid-owner no-internet -j DROP
```

        [*]Note: Don't forget to make the changes permanent, so it would be applied automatically after reboot. Doing it, depends on your Linux distribution.[/list]

    Check it, for example on Firefox by running: no-internet "firefox"

In case you would want to make an exception and allow a program to access local network:
```

    iptables -A OUTPUT -m owner --gid-owner no-internet -d 192.168.1.0/24 -j ACCEPT
    iptables -A OUTPUT -m owner --gid-owner no-internet -d 127.0.0.0/8 -j ACCEPT
    iptables -A OUTPUT -m owner --gid-owner no-internet -j DROP
```

NOTE: In case of spawning the rules will be maintained. For example, if you run a program with no-internet rule and that program will open browser window, still the rules will be applied.

---

### Post by holmj on 2023-06-03
@fallen1
Appreciate your post; I tried solution with bwrap but ain't working:

```
jake@jake-pc:~$ sudo bwrap --bind / / --unshare-net packettracer
[sudo] password for jake:      
Starting Packet Tracer 8.0.0
/usr/local/bin/packettracer: line 7: /dev/null: Permission denied
/usr/local/bin/packettracer: line 8: /dev/null: Permission denied
/usr/local/bin/packettracer: line 9: /dev/null: Permission denied
```

But the solution with namespace works like a dream and allows to run packettracer with no network connectivity. Once we create the new namespace it is set DOWN by default and we are safe to run apps in it. We can simplyfy all and run it as a script. First we create the namespace: 
```
sudo ip netns add offline
```and
```
sudo ip netns exec offline su jake -c packettracer
```

I will also try iptable solution but seems complex right now; need more time to go through it :)

---

