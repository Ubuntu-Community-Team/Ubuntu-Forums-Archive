---
title: "Ubuntu 14.04 why is my VPS sometimes unreachable?"
date: 2018-02-01
forum: Ubuntu, Linux and OS Chat
---

### Post by gnappoman on 2018-02-01
I am a sysadmin and quite expert in dealing with ubuntu configurations, but this is puzzling me:

I have a OpenVZ VPS with Ubuntu 14.04 minimal freshly installed, configured as LAMP server and teamspeak 3 server. No networking / hardware issues of any sort. I think the following issue is dependant on ubuntu OS misconfiguration.

And here is the issue, while webserver is working greatly, it looks like teamspeak doesn't allow connections until the client ip opens another kind of connection to the server.

For example:

When a Client tries a connection to teamspeak, it receives a "Failed to connect to server", no matter how many tries (tested with multiple clients and different IPs).
Teamspeak server log looks "quiet".
Teamspeak client log looks also quiet (no errors, no warnings) like the following:

    31/01/2018 09:50:58    ClientUI    Info    Lookup finished: ip=xxx.xxx.xxx.xxx port=9987 query=ts3.domain.com error=0    
    31/01/2018 09:50:58    ClientUI    Info    Resolve successful: xxx.xxx.xxx.xxx:9987    
    31/01/2018 09:50:58    ClientUI    Info    Initiating connection: xxx.xxx.xxx.xxx:9987    
    31/01/2018 09:50:58    ClientUI    Info    Connect status: Connecting    
    31/01/2018 09:51:03    ClientUI    Info    Connect status: Disconnected    

But if the client makes any other kind of connection to the server (either visiting a page hosted there, or logging via ssh, downloading file via ftp) prior to trying a teamspeak connection, it connects flawlessly.

I think the issue does not depend on teamspeak configuration, but on some sort of "sleep" ubuntu takes.

---

### Post by TheFu on 2018-02-01
Welcome to the forums.

I don't use teamspeak, openvz or any VPS providers, so everything is a guess.  I do use lots of different server tools and lots of virtualization.

Does openvz "sleep"?  Didn't think that happened, but if the VPS provider doesn't like their clients, they could easily overload the physical system with too many paravirtual clients.  Can you see how busy the host system is?  Maybe moving to a different physical host will solve the issue?

Are there any outside firewalls that expect well-known ports to be used before opening access to a client for other ports?
Are there any netfilter rules getting in the way? If you enable logging, do client requests even show up in the firewall logs?
You didn't really say this, but have you checked all the other logs for warnings/errors? Not just teamspeak, but syslog, auth.log and others?

That's all I got. Sorry it isn't much.

BTW, I'm in the process of moving all our 14.04 systems to 16.04 now.  Did 2 yesterday and I'm fighting with some dumb issues.

---

