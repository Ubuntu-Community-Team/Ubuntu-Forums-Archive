---
title: "Check Services / Service Status"
date: 2007-05-09
forum: Server Platforms
---

### Post by Catsworth on 2007-05-09
Hi Guys,

How do I check (via the command line) which services are installed/running on my Ubuntu box?

Also, would this be a generic command that would work on most Linux distro's or is every distro different when it comes to service management?

Thanks

---

### Post by bukwirm on 2007-05-09
If you know the name of the process, you can just use the "ps -e | grep *service_name*".

---

### Post by saxin on 2007-05-09
To see running software try this:
ps aux

---

### Post by Catsworth on 2007-05-10
Ok, background time.

Within Windoze you can go into the Administrative tools and manage the running services.  There doesn't appear to be a list of the processes that are running as services, this is what I need to get to.

I don't know the names of any of them, I need to know what's running as a service.

Thanks.

---

### Post by Highway on 2007-05-30
netstat -a 
is what you need to use.

---

### Post by Catsworth on 2007-05-31
Looks good, thanks :)

---

### Post by arosboro on 2008-01-18
I think the parent is referring to a command similar to Gentoo's 'rc-status'  which shows a list of every script in /etc/init.d/ and the status (running, stopped).  Gentoo (and maybe other distros) also have 'rc-update' which adds services to different runlevels and 'rc' which kicks off the default services that have been stopped.

Netstat -a | grep LISTEN would show listening services but would not list everything running in /etc/init.d/

I'm not sure debian does anything in the command line like rc-status.  You could however check out a runlevel editor such as sysv-rc-conf or bum.

---

