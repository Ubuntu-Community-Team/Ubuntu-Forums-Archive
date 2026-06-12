---
title: "Creating a CUPS server, 16.04, setting up compatibly with systemd"
date: 2016-11-10
forum: Server Platforms
---

### Post by jsberg on 2016-11-10
I'm running 16.04 server, trying to set up a CUPS server. I've done this on 12.04/14.04, no troubles.
On 16.04, systemd seems to be creating problems, and I'm trying to understand the correct/intended way to set up a cups server.
What happens is that the cups server starts, then dies after a while. The issue seems to be this on-demand trickery that systemd is now doing.
Right now, systemctl status cups.socket shows

[FONT=courier new]&#9679; cups.socket - CUPS Scheduler
   Loaded: loaded (/lib/systemd/system/cups.socket; enabled; vendor preset: enabled)
  Drop-In: /etc/systemd/system/cups.socket.d
           &#9492;&#9472;cups-socket.public.conf
   Active: failed (Result: resources)
   Listen: /var/run/cups/cups.sock (Stream)
           0.0.0.0:631 (Stream)
           [::]:631 (Stream)
Nov 10 19:04:30 cap04 systemd[1]: cups.socket: Failed to listen on sockets: Address already in use
Nov 10 19:04:30 cap04 systemd[1]: Failed to listen on CUPS Scheduler.
Nov 10 19:04:30 cap04 systemd[1]: cups.socket: Unit entered failed state.


[/FONT]As far as I can tell, what happens is that the cups daemon starts up at the beginning, listens on port 631, cups.socket can't bind to that port, dies, then the cups daemon proceeds to die, with nothing to start it. Note that I've added the following in /etc/systemd/system/cups.socket.d to get socket to listen on the right ports, as suggested in /usr/share/doc/cups-daemon

[FONT=courier new]# This file goes in /etc/systemd/system/cups.socket.d/
# Configures CUPS to listen broadly
[Socket]
FreeBind=true
# IPv4
ListenStream=0.0.0.0:631
# IPv6
ListenStream=[::]:631
[/FONT]
cupsd.conf has Listen lines to listen on the network interface.

Whoever packaged cups-daemon presumably has an idea of the "right" way to set up a cups server to work with systemd. Does anyone know what that right way is? I see no reason to be starting the server on demand, but it looks like the systemd files are set up to always do things on demand (cups.service starts the daemon with '/usr/sbin/cupsd -l').

Thanks for any help.

---

