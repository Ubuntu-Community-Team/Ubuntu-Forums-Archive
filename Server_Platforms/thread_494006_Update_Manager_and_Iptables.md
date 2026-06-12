---
title: "Update Manager and Iptables"
date: 2007-07-06
forum: Server Platforms
---

### Post by hlmuller on 2007-07-06
**[COLOR="Blue"][SIZE="4"]Question Background:[/SIZE][/COLOR]**

[LIST]
[*]Installing version 7.04
[*]Not connecting to internet while installing
[*]Using iptables to create firewall to restrict traffic to and from servers providing updates
[*]Connecting to internet, running update manager, successfully updating install
[*]Disconnecting from internet for further hardening chores
[/LIST]

The update performs almost flawlessly.  The only discrepancy is the changes are NOT identified in the bottom pane of the update manager.

First, I add the IP addresses to the /etc/hosts file, otherwise the commands below will fail.

```
sudo gedit /etc/hosts
```

I add these lines:
```

82.211.81.138  security.ubuntu.com
91.189.88.31   us.archive.ubuntu.com
91.189.89.6    us.archive.ubuntu.com
91.189.89.8    us.archive.ubuntu.com
```

These are the commands used to create the firewall:

```
sudo iptables -F
sudo iptables -L
sudo iptables -A OUTPUT -d 82.211.81.138 -p tcp --dport 80 -j ACCEPT
sudo iptables -A OUTPUT -d 82.211.81.138 -p udp --dport 80 -j ACCEPT
sudo iptables -A OUTPUT -d 91.189.88.31 -p tcp --dport 80 -j ACCEPT
sudo iptables -A OUTPUT -d 91.189.88.31 -p udp --dport 80 -j ACCEPT
sudo iptables -A OUTPUT -d 91.189.89.6 -p tcp --dport 80 -j ACCEPT
sudo iptables -A OUTPUT -d 91.189.89.6 -p udp --dport 80 -j ACCEPT
sudo iptables -A OUTPUT -d 91.189.89.8 -p tcp --dport 80 -j ACCEPT
sudo iptables -A OUTPUT -d 91.189.89.8 -p udp --dport 80 -j ACCEPT
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A INPUT -p icmp -j ACCEPT
sudo iptables -A INPUT -j LOG
sudo iptables -A OUTPUT -j LOG
sudo iptables -P INPUT DROP
sudo iptables -P FORWARD DROP
sudo iptables -P OUTPUT DROP
sudo iptables -L
```

I can only take partial credit for the code.  The general idea comes from the Securing Debian Manual, Appendix F - Security update protected by a firewall.  

After entering the code above, I then connect to the internet and run Update Manager.  It runs without flaw, updating 72 packages.  **But what I notice is that it does not indicate what the changes are, and the error indicates that there may be something wrong with the connection.**

I am admittedly not an expert on iptables, and this is my first debian distribution, and have little experience with gnome and its applications.  I've spent the last couple years learning Gentoo and Linux From Scratch, and didn't get into the Desktop much (i.e. almost all the time spent on console, and not in X).

**[COLOR="Blue"][SIZE="4"]Question:[/SIZE][/COLOR]**

If I run the Update Manager from the LiveCD, without a firewall, it not only updates the applications, but it also indicates what the changes were. So this leads me to believe I am either missing an IP address, or a protocol.  Can anyone shed some light on this?

Kind regards,

Harvey

---

### Post by koenn on 2007-07-06
> and the error indicates that there may be something wrong with the connection.
post the error, then.

---

### Post by hlmuller on 2007-07-06
> post the error, then.

Although I appreciate the response, I was hoping for a more substantive one.  The original post was fairly clear, but I will post the exact error message received.

In the "Description of update" section of the form, "Changes" tab, the following is indicated:

```
Failed to download the list of changes.
Please check your Internet connection.
```

As a reminder, all of the updates were successful, in that they were downloaded and applied to the system.  To restate the original question: **"Am I missing something in the iptables rules, or am I missing an IP address that I don't know I need to be aware of, or is there another protocol I should be considering?**

I am respectfully and kindly looking for a definitive answer.

---

### Post by turinglabs on 2007-07-06
You are logging INPUT and OUPUT drops, tail your syslog during an update and see what is going on. You can also try a tcpdump on your outbound interface during the update if the log doesn't show anything. If you have no other traffic, a raw capture of all traffic will do:

```

tcpdump -i eth0 -n -v

```

Or perhaps just port 80:

```

tcpdump -i eth0 -n -v port 80

```

Or to and from the given host:

```

tcpdump -i eth0 -n -v host 82.211.81.138

```

One hint about iptables, if you use fully-qualified hostnames in the ruleset, when it is loaded into the kernel, one rule will be created for each IP address the hostname resolves to.

Also, you don't need UDP port 80 in your rules, TCP will suffice.

If you need help decoding the logs or packet captures, feel free to post them.

---

### Post by koenn on 2007-07-06
> **hlmuller said:**
> Although I appreciate the response, I was hoping for a more substantive one.   ... 
I was thinking the error in question would say something like "failed to connect to ..." or so - which would give us a clue towards a more substantive answer. 
However, I overlooked the fact that GUI progs leave out "technical details"

Consider doing the upgrade by running (in a terminal)
```
apt-get update
apt-get upgrade

```
and see where it hangs / returns errors / complains about a missing file / ....

---

### Post by hlmuller on 2007-07-06
Doug and koenn,

Thanks to you both for good input.  I do not have the resolution yet, but when I do get one, I'll share it here.  The problem isn't critical, more of an annoyance because I don't understand something yet.

Doug, I had to laugh when I read your suggestion.  The simplicity of checking the logs...  Unfortunately, syslog did not provide any real clues, but I'll take a closer look tomorrow.  Your suggestions regarding iptables were dead on, I confirmed them of course.  I'm not familiar with tcpdump, yet.  I'll learn it and give it a try.

koenn, I apologize if my first reply back wasn't the happiest.  Your last suggestion may bring some illumination to the issue.  I'll test this out in the morning.  And it looks like I'll have to go find and learn the Debian specific console commands.  Thanks for the pointer.

Best regards,

Harvey

---

### Post by hlmuller on 2007-07-07
The solution was eventually found in the logs.  82.211.81.132 popped up.  Further research identified the ip address as rookery.ubuntu.com.  So in total, these are the lines added to /etc/hosts:

```
82.211.81.132  rookery.ubuntu.com
82.211.81.138  security.ubuntu.com
91.189.88.31   us.archive.ubuntu.com
91.189.89.6    us.archive.ubuntu.com
91.189.89.8    us.archive.ubuntu.com
```

To repeat for future readers, this is necessary to enter the iptables rules before DNS is up and running.

Thanks to Doug of Turing Labs, and further homework on my part the iptables commands are simplified also:

```
iptables -F
iptables -L
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -p tcp -d rookery.ubuntu.com --dport 80 -j ACCEPT
iptables -A OUTPUT -p tcp -d security.ubuntu.com --dport 80 -j ACCEPT
iptables -A OUTPUT -p tcp -d us.archive.ubuntu.com --dport 80 -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p icmp -j ACCEPT
iptables -A INPUT -j LOG
iptables -A OUTPUT -j LOG
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP
iptables -L
```

Hope other paranoiacs find this useful.

Harvey

---

