---
title: "Problmes with Mininet (xterm - Cannot connect to Display)"
date: 2017-05-20
forum: Virtualisation
---

### Post by engadnan on 2017-05-20
Hi, i am quite new to Mininet. I have installed Mininet and VirtualBox. While i try to use "xterm h1" by using basic mininet custom topology (i.e. sudo mn), it returns the errors, "Cannot connect to Display". Could you please advise what could be the possible problem?

---

### Post by TheFu on 2017-05-20
I've never heard of mininet. Interesting.

"cannot connect to display" is an X11 error.  
* Are you running an X/Server?
* Do you allow remote systems access to that X/Server?

A common way to remotely launch to an X-client on remote machine (or a different virtual machine), is to use ssh X-forwarding.  Here's how I connect to 'hadar' and run an xterm, but display that xterm on my local machine.  
```
$ xterm -geometry 80x25+760+0 $XTERM_OPTS -e ssh -X hadar &
```  Of course, a local X/Server is required.

BTW, xforwarding works over all TCP networking, but is really only practical over 100Mbps and greater links.  Don't expect it to work well over any internet connection - go ahead and try it, once. You'll quickly learn why most admins use straight ssh for their work and not X/Windows.

Don't know what 'h1' is. My manpage doesn't say anything about that option.  If it is a local program, is it an X/client?

---

