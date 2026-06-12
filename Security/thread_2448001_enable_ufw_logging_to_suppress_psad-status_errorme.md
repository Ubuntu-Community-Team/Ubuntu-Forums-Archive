---
title: "enable ufw logging to suppress psad-status errormessage"
date: 2020-07-30
forum: Security
---

### Post by xiguus2 on 2020-07-30
Hi Ubuntonians,

I have been getting messages sent to /var/mail/root saying with the subject-line "[psad-status] firewall setup warning on _CHANGEME_!"

```
[COLOR=#3D3D3D][FONT=&amp]You may just need to add a default logging rule to the[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&amp]    'filter' 'INPUT' chain on _CHANGEME_.  For more information,[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=&amp]    see the file "FW_HELP" in the psad sources directory or visit:
[/FONT][/COLOR]
```

with a link to cipherdyne.

The help page does not but a bit of digging has directed my attention to ufw logging: psad analyzes ufw logs, if there are no ufw logs, psad complains and does nothing.

Various sources unanimously assert that while ufw is installed on ubuntu by default and enabled (ie firewall function is active), logging is not automatically enabled and the user must do this manually. 

Continuing, I find that there are two recommended ways to enable ufw logging, which are essentially equivalent in their actions:

Method 1: iptables

```

# iptables -A INPUT -j LOG
# iptables -A FORWARD -j LOG
# ip6tables -A INPUT -j LOG
# ip6tables -A FORWARD -j LOG

```

Method 2: edit rules
The files /etc/ufw/before.rules and /etc/ufw/before6.rules are to be edited directly by inserting two lines into the file immediately before the last line, which is the COMMIT command.

So, for /etc/ufw/before.rules:
```

ln 70 -- # allow MULTICAST UPnP for service discovery (be sure the MULTICAST line above
ln 71 -- # is uncommented)
ln 72 -- -A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j ACCEPT
ln 73 -- 
ln 74 -- # don't delete the 'COMMIT' line or these rules won't be processed
ln 75 -- COMMIT
```

Becomes:
```

ln 70 -- # allow MULTICAST UPnP for service discovery (be sure the MULTICAST line above
ln 71 -- # is uncommented)
ln 72 -- -A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j ACCEPT
ln 73 -- 
ln 74 -- # enable ufw logging and suppress psad error message
ln 75 -- -A INPUT -j LOG
ln 76 -- -A FORWARD -j LOG
ln 77 --
ln 78 -- # don't delete the 'COMMIT' line or these rules won't be processed
ln 79 -- COMMIT
```

In either case follow with
```

# ufw disable
# ufw enable

```

The reboot leaves me without internet access.

From journalctl we have this:
```

ufw-init[495]: iptables-restore v1.8.4 (legacy): no command specified
ufw-init[495]: Error occurred at line: 77
ufw-init[495]: Try `iptables-restore -h' or 'iptables-restore --help' for more information.
ufw-init[565]: Problem running '/etc/ufw/before.rules'
systemd[1]: ufw.service: Main process exited, code=exited, status=1/FAILURE
systemd[1]: ufw.service: Failed with result 'exit-code'.

```

Hence no network.

I have deleted the edits. The network now functions as normal, and psad is again telling me that I should enable logging.

We observe that the fail is at the blank line 77. The original before.rules had 76 lines. It may be that the blank line is the problem, but I am wondering whether there is a file integrity system which needs to be told about the edit and the edited file recognised as allowed. The system logs don't provide any information on this.

It may be relevant that I have tiger running on the system, but there is nothing to show that tiger is active at that stage of the boot.
Alternatively, should I recalculate eg md5sums for the new before.rules?

My questions are:
(1) Why does the recommended enablement fail?
(2) Is there a file integrity system which would be active at the boot when ufw is initialised, and which is blocking the processing of /etc/ufw/before.rules?

Many Thanks & Best Regards,

xiguus2

---

### Post by ecophobia on 2020-08-02
[COLOR=#000000][FONT=Verdana]As a fist step, try running "/usr/share/ufw/check-requirements" to see if you have bits and pieces missing from your firewall installation. [/FONT][/COLOR]

---

### Post by ecophobia on 2020-08-02
[SIZE=3]Additionally, try editing[/SIZE][COLOR=#333333][FONT=monospace] /etc/default/ufw to use IPV6=no [SIZE=3][FONT=arial]to see if it makes any difference.[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by xiguus2 on 2020-08-04
Hello ecophobia,

Thanks very much for your reply.

I have run the 'check-requirements' command as you suggest and it has returned 'pass' for all items for both IPv4 and IPv6. Here is the output:

```

# /usr/share/ufw/check-requirements 
Has python: pass (binary: python3, version: 3.8.2, py3)
Has iptables: pass
Has ip6tables: pass

Has /proc/net/dev: pass
Has /proc/net/if_inet6: pass

This script will now attempt to create various rules using the iptables
and ip6tables commands. This may result in module autoloading (eg, for
IPv6).
Proceed with checks (Y/n)? 

== IPv4 ==
Creating 'ufw-check-requirements'... done
Inserting RETURN at top of 'ufw-check-requirements'... done
TCP: pass
UDP: pass
destination port: pass
source port: pass
ACCEPT: pass
DROP: pass
REJECT: pass
LOG: pass
hashlimit: pass
limit: pass
ctstate (NEW): pass
ctstate (RELATED): pass
ctstate (ESTABLISHED): pass
ctstate (INVALID): pass
ctstate (new, recent set): pass
ctstate (new, recent update): pass
ctstate (new, limit): pass
interface (input): pass
interface (output): pass
multiport: pass
comment: pass
addrtype (LOCAL): pass
addrtype (MULTICAST): pass
addrtype (BROADCAST): pass
icmp (destination-unreachable): pass
icmp (source-quench): pass
icmp (time-exceeded): pass
icmp (parameter-problem): pass
icmp (echo-request): pass

== IPv6 ==
Creating 'ufw-check-requirements6'... done
Inserting RETURN at top of 'ufw-check-requirements6'... done
TCP: pass
UDP: pass
destination port: pass
source port: pass
ACCEPT: pass
DROP: pass
REJECT: pass
LOG: pass
hashlimit: pass
limit: pass
ctstate (NEW): pass
ctstate (RELATED): pass
ctstate (ESTABLISHED): pass
ctstate (INVALID): pass
ctstate (new, recent set): pass
ctstate (new, recent update): pass
ctstate (new, limit): pass
interface (input): pass
interface (output): pass
multiport: pass
comment: pass
icmpv6 (destination-unreachable): pass
icmpv6 (packet-too-big): pass
icmpv6 (time-exceeded): pass
icmpv6 (parameter-problem): pass
icmpv6 (echo-request): pass
icmpv6 with hl (neighbor-solicitation): pass
icmpv6 with hl (neighbor-advertisement): pass
icmpv6 with hl (router-solicitation): pass
icmpv6 with hl (router-advertisement): pass
ipv6 rt: pass

All tests passed


```

You will notice in particular that test for LOG returns 'pass'.

I will make the change you suggest in your follow-up post to see whether that has the effect desired. 

I'm sure you will agree that this is a bit of a weird one, hey?

Best Regards,

xiguus

---

### Post by ecophobia on 2020-08-04
Yeah, but again, Linux is like that - Sensitive. A forgotten dot or comma, incorrect syntax or line ending, then you spend next 2- 3 hours banging your head against the wall trying to resolve the issue. ;)

---

