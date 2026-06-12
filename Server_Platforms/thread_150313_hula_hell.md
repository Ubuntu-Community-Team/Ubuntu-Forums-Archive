---
title: "hula hell?"
date: 2006-03-25
forum: Server Platforms
---

### Post by gary79 on 2006-03-25
I've spent the better part of two days trying to get SSL working with hula and unfortunately the end result is hula in a completely non operational state.

Yes, I have try following the guide SSL ([http://www.hula-project.org/Setting_Up_TLS_and_SSL](http://www.hula-project.org/Setting_Up_TLS_and_SSL)) and my method of installing was straight from .deb 

After placing certs in what I think is the <prefix> dir, “/var/lib/” hula seems to stall on restarting. Although, I also set up apache SSL at the same time. Below is the data printed in terminal when restarting.

The line "__________restart____________" is add me to show where I stopped hula in another terminal. I forced a stop to see what was happening when stopping.

```
root@bender:/home/gary/hula# /etc/init.d/hula restart
Restarting hula: hula isn't runningLoading Hula agents for server Server Messaging Server.
  loading huladmc
  loading hulanmap
  loading hulasmtp
  loading hulawebadmin
  loading hulaimap
  loading hulaweb
  loading hulacalagent
  loading hulamailprox
  loading hulacalcmd
  loading hulaforward
  loading hulapop3
  loading hulaindexer
  loading hularules
  loading hulaantispam
hulaantispam: spamassassin not enabled and no hosts allowed or disallowed; unloading
hulaantispam: Shutting down.
  loading hulamodweb
WebAdmin: Secure mode - using external certificate
  loading hulaconnmgr
connmgr: loaded module: CMUSER
cmrbl: No RBL zones configured.  RBL check is disabled.
cmlists: No addresses blocked or allowed
hulamodweb: loading templates from /usr/lib/modweb
hulamodweb: loaded module /usr/lib/modweb/libmwcal.so
hulamodweb: loaded module /usr/lib/modweb/libmwmail.so
hulamodweb: did not load module /usr/lib/modweb/libmwtom.so (reason 2: No such file or directory)
hulamodweb: loaded module /usr/lib/modweb/libmwpref.so

Unhandled Exception: System.Net.Sockets.SocketException: Address already in use
in <0x000cb> System.Net.Sockets.Socket:Bind (System.Net.EndPoint local_end)
in <0x00034> Mono.WebServer.XSPWebSource:CreateSocket ()
in <0x00045> Mono.WebServer.ApplicationServer:Start (Boolean bgThread)
in (wrapper remoting-invoke-with-check) Mono.WebServer.ApplicationServer:Start (bool)
in [0x00035] (at /home/alex/hula-package/build/hula-0.1.0+svn862/src/libs/hula-sharp/Hula.Web/HulaXsp.cs:64) Hula.X sp.HulaXsp:Run ()
in [0x00021] (at /home/alex/hula-package/build/hula-0.1.0+svn862/src/libs/hula-sharp/Hula.Web/HulaXsp.cs:78) Hula.X sp.HulaXsp:Main (System.String[] args)
NMAPD: System not shut down properly, verifying queue integrity.
NMAPD: Queue integrity check complete, now cleaning irrelevant entries.
NMAPD: Queue integrity check complete, starting Queue Monitor [0].

________________________restart______________________

hulamanager: Shutting down DMC
huladmc: Shutting down...
hulaconnmgr: Shutting down.
POP3D: Shutting down.
POP3D: Exiting after an accept() failure; error 22
POP3D: SSL Server shutdown.
hulamodweb: Preparing to unload; please be patient, this may take a minute.
SMTPD: Closing server sockets
hulacalendar: Shutting down.
calcmdd: Shutting down.
hulaforward: Shutting down.
hularules: Shutting down.
MAILPROX: Config monitor thread done.
SMTPD: Configuration monitor thread done.
NMAPD: Message queue monitor done.
NMAPD: Disk monitor thread done.
NMAPD: Config monitor thread done.
hulamailprox: Shutting down.
NMAPD: Load monitor thread done.
hulaconnmgr: Shutting down 0 client threads
hulaconnmgr: Shutdown complete
NMAPD: Shutting down 2 client threads
hulacalendar: Shutting down 0 queue threads
calcmdd: Shutting down 0 queue threads
hulaforward: Shutting down 0 queue threads
hularules: Shutting down 0 queue threads
DMC: Closing server sockets
DMCD: Exiting after an accept() failure; error 22
DMCD: SSL Server shutdown.
  killing huladmc
Hula Manager shutdown.
hula.


```

So I decided to start a fresh, I removed the deb packages and all folders and files with hula in the name and reinstalled via apt-get. Now, all the start up scripts are missing. Wrongly or rightly I had assumed that apt-get for hula also installed the startup scripts.

I want to use hula but I need it to be secure. All thoughts or comments are welcome.

---

