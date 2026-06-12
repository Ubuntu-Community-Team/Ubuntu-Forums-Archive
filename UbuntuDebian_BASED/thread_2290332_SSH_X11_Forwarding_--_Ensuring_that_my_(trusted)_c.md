---
title: "SSH X11 Forwarding -- Ensuring that my (trusted) computer remains secure"
date: 2015-08-11
forum: Ubuntu/Debian BASED
---

### Post by s3a on 2015-08-11
There are two computers in the scenario I would like to talk about; those computers are my (trusted) computer and another (non-trusted) computer.

I would like to use graphical programs from the (non-trusted) other computer in my (trusted) computer and have them feel like they're running natively in my (trusted) computer by ssh-ing from my (trusted) computer into the (non-trusted) other computer. Having said that, I do not want the (non-trusted) other computer to potentially pose a security risk to my (trusted) computer.

Furthermore, in the man page of ssh_config, it says:
> ForwardX11

             Specifies whether X11 connections will be automatically redirected over the secure channel and DISPLAY set.  The argument must be “yes” or “no”.  The default is “no”.

             X11 forwarding should be enabled with caution.  Users with the ability to bypass file permissions on the remote host (for the user's X11 authorization database) can access the local X11 display through the forwarded connection.  An attacker may then be able
             to perform activities such as keystroke monitoring if the ForwardX11Trusted option is also enabled.

and

> ForwardX11Trusted

             If this option is set to “yes”, remote X11 clients will have full access to the original X11 display.

             If this option is set to “no”, remote X11 clients will be considered untrusted and prevented from stealing or tampering with data belonging to trusted X11 clients.  Furthermore, the xauth(1) token used for the session will be set to expire after 20 minutes.
             Remote clients will be refused access after this time.

             The default is “yes” (Debian-specific).

             See the X11 SECURITY extension specification for full details on the restrictions imposed on untrusted clients..

I was just hoping someone here could confirm whether or not it is the case that, in my scenario, “remote X11 clients” refers to the X server of the (non-trusted) other computer and “trusted X11 clients” refers to the X server of my (trusted) computer.

I ask because I intend to set ForwardX11 to yes and ForwardX11Trusted to no in order to achieve what I want, but I just wanted to make sure that I did not misunderstand the documentation.

Any input would be GREATLY appreciated!

---

### Post by TheFu on 2015-08-11
Security of X11 is weak.  Any use of this protocol reduces overall system security. This has been known for 40-ish years. Why else would Unix/Linux admins be adamant NOT to load a desktop GUI onto a server?

Using X11 forwarding over the internet doesn't work well, not enough bandwidth. It is really only useful on the same LAN segment or with 100Mbps connections. For any lower speed connections, some sort of remote desktop is needed and none of those have real security built-in except NX (which uses ssh).  Sadly, NX has their own security issues because they run X11 code from 2009 which has known flaws too.  It is a trade-off that I'm willing to make to get 2-3x more desktop GUI performance.

So - you have to decide which network is secure or not and avoid allowing any X11 clients to connect to the server on the machine you sit behind without careful consideration. We cannot calculate those risks for you.

OTOH, plain ssh doesn't bring this same level of risk.

---

### Post by s3a on 2015-08-11
Thanks for your response.

What I'm trying to ask is:
Was using X remotely intended to be secure in theory by the people who designed it, but isn't in practice just because of bugs, or was the remote use of X not intended to be secure even theoretically?

I'm planning to do this on a local network with at least 100 Mbps of bandwidth., so assuming that there are no bugs in X (I know that's not realistic), is what I said the best way to proceed?

---

### Post by CharlesA on 2015-08-12
I was going to suggest NX, but TheFu already pointed out that it has its own issues. I usually use console access via encrypted VNC to my Ubuntu VM, but I could just as easily SSH in. VNC is nice for when I actually need the GUI, though. I'm using Proxmox, and I think VNC is tunneled over SSH but I'm not 100% since I haven't really looked into it.

---

### Post by TheFu on 2015-08-12
X11 was created before security really mattered. It used UDP, not TCP and nobody would call it secure today. 

When I was younger and just learning to be an X/Windows programmer, we'd screw around with each other's workstations from other systems on the LAN. This was on a government, secured, network, air-gapped network and every one there had DoD clearances.  Even there, with all the logging they did, it wasn't possible to trace who was screwing with whom.  The security guys were not happy.  OTOH, when you put 500 developers on a secure network writing UNIX programs without any internet connectivity, what do you expect?  Of course, we stopped as the systems got closer to being used for production.

See my point?  There are risks for all behaviors.  I suspect X11 is about the 5th most dangerous program running on any Unix/Linux workstation.  ftpd, sendmail, bind, apache, are in the group of more dangerous services.

IMHO.

---

