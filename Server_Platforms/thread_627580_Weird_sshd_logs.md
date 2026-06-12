---
title: "Weird sshd logs"
date: 2007-11-30
forum: Server Platforms
---

### Post by maerlma on 2007-11-30
I found this in my auth.log this morning and I 've never seen entries like this. These entries follow some unsuccessful login attempts for root, so I know they're malicious. (Yes, root logins are disallowed in sshd_config)

Nov 30 06:42:59 pariah sshd[9941]: Received disconnect from x.x.x.x: 11: Bye Bye
 Nov 30 06:42:59 pariah sshd[9942]: warning: /etc/hosts.allow, line 15: can't verify hostname: getaddrinfo(static-x-x-x-x.bdsl.verizon.net, AF_INET) failed


The weird part is that I don't even have 15 lines in /etc/hosts.allow .

Should I be worried about this? Google was no help.

---

### Post by HermanAB on 2007-11-30
This kind of schtuff is going on all the time.  You can easily do a number of things: Change your SSH port to a non-standard port to throw the script kiddies off; disallow password access to SSH and only use public keys; add a rate limiter line to iptables...

There are many threads on doing the above.

---

### Post by MJN on 2007-11-30
Post your /etc/hosts.allow file - are you sure you don't have 15 lines? (Remember the comments at the top are counted as lines)

Mathew

---

### Post by maerlma on 2007-12-03
you're right, it does have 15 lines:

# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
=

---

### Post by MJN on 2007-12-03
What does you *mis-typed user name for valid user *comment mean?

Incidentally, presumably you have ALL: ALL (or similar <service>: ALL) listed in hosts.deny?

Mathew

---

### Post by maerlma on 2007-12-05
I have ALL: UNKNOWN in hosts.deny.

---

