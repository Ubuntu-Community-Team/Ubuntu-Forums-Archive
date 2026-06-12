---
title: "Ubuntu Server 18.04 sudo hangs for ~15 secs after command"
date: 2018-10-26
forum: Server Platforms
---

### Post by marc58 on 2018-10-26
[COLOR=#242729][FONT=Arial]Im running Ubuntu Server 18.04 on a VM on a 60GB virtual hard drive with 4GB memory and 4 cores total. Everytime i use sudo, it hangs for about 15 seconds before continuing with the command. Ive deleted the server and created a new one, an it still does it.[/FONT][/COLOR]

---

### Post by TheFu on 2018-10-27
Sometimes a name resolution problem causes issues for sudo.  

Check that the /etc/hosts file is correct and that DNS is working.  If the resolution order is DNS before /etc/hosts, then the DNS might need to timeout before it can be resolved.

Just a guess.

You can ask for sudo to be verbose and looking at the system log files is always a good idea whenever there is any issue.

---

### Post by marc58 on 2018-10-27
> **TheFu said:**
> Sometimes a name resolution problem causes issues for sudo.  

Check that the /etc/hosts file is correct and that DNS is working.  If the resolution order is DNS before /etc/hosts, then the DNS might need to timeout before it can be resolved.

Just a guess.

You can ask for sudo to be verbose and looking at the system log files is always a good idea whenever there is any issue.

How would i do sudo in verbose mode?

---

### Post by TheFu on 2018-10-28
Did you figure it out yet?

---

### Post by marc58 on 2018-10-28
Not yet. Not sure how to run sudo in verbose mode. Going to try to figure out if DNS is working and take a look at the hosts file later tonight.

---

### Post by TheFu on 2018-10-28
The task wasn't meant to be difficult.  

Teaching you to fish ... 

Every command on any Unix machine has a manpage which explains the available options and how to use them.  Open a terminal and type **man ssh**<enter>

The order of name resolution is controlled by the /etc/nsswitch.conf file.  You want files before dns or mdns, but this assumes the local hosts file is correct.  It should be, but we never know.

Almost every config file will have a manpage too.   **man nsswitch.conf** , for example.

manpages have a specific layout which is carefully designed to show the most important things first. When you are new, they can be overwhelming.  With time and more experience, you'll come to appreciate the layout.

And many commands also support the **--help** option.  Sometimes that is all you need (I happen to know it doesn't help with ssh, this time.  But try** ls --help** to see what it could show.

---

### Post by marc58 on 2018-10-28
nsswitch.conf is [B][I]hosts:          files dns

[/I][/B]And the /etc/hosts file looks fine:

127.0.0.1       localhost.localdomain   localhost 192.168.116.128
::1             localhost6.localdomain6 localhost6 192.168.116.128


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by TheFu on 2018-10-28
The /etc/hosts does NOT look fine. Is that a typo?

---

### Post by marc58 on 2018-10-29
I think i fixed /etc/hosts - but the issue remains:

*127.0.0.1 localhost.localdomain localhost*
*::1 localhost6.localdomain6 localhost6*

*# The following lines are desirable for IPv6 capable hosts*
*::1     localhost ip6-localhost ip6-loopback*
*fe00::0 ip6-localnet*
*ff02::1 ip6-allnodes*
*ff02::2 ip6-allrouters*
*ff02::3 ip6-allhosts*

---

### Post by TheFu on 2018-10-29
Where is the hostname?  Add that to the end of line with 127.0.1.1

---

### Post by marc58 on 2018-10-29
```
127.0.0.1 localhost.localdomain localhost ubuntu-server
::1 localhost6.localdomain6 localhost6


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```



This is my updated /etc/hosts file. But after changing it and rebooting, the issue is gone. Not sure if that was it, as its been awhile since i rebooted, but regardless, the issue is gone. Thank you.

---

### Post by TheFu on 2018-10-30
sudo is designed to work on a network of systems.  Specific commands that only 1 user or 1 NIS group of users can run on specific machines  can be specified.  Using sudo just to run root commands is only a tiny part of what sudo can accomplish.

All that means is that sudo needs to know and trust the hostname it is running on, hence the reason that having the name resolution correct is important.  

Best not to touch files you don't fully understand without expecting to learn how to fix them. Generally, modifying anything in /etc/ should be proceeded by making a copy of the file first.  **sudo cp hosts hosts.org** is all that is needed.  I've modified the sudoers file in a way that totally broke it a few times.  That meant gaining control of that system required hacking in first, then putting the original file back.

Anyways, please mark this thread as **solved**. There's a thread tools button near the top.

---

