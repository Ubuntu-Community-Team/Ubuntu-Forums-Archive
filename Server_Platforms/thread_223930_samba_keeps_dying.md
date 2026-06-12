---
title: "samba keeps dying"
date: 2006-07-27
forum: Server Platforms
---

### Post by indeed on 2006-07-27
I am using Samba 3.0.22 on Ubuntu 6.06 to authenticate and serve files to two windows machines. If both machines are off for a period of time nmbd seems to decide it's not wanted anymore and quits with
> [2006/07/27 03:44:52, 2] nmbd/nmbd.c:reload_interfaces(257)
  Deleting dead interface 192.168.2.2
[2006/07/27 03:44:52, 0] nmbd/nmbd.c:reload_interfaces(266)
  reload_interfaces: No subnets to listen to. Shutting down...


smbd exits shortly afterwards saying
> [2006/07/27 03:56:13, 3] smbd/connection.c:yield_connection(69)
  Yielding connection to
[2006/07/27 03:56:13, 3] smbd/server.c:exit_server(655)
  Server exit (normal exit)


Now when the machines come back on there's no server ready to handle them and I have to restart samba manually.

I would be very grateful for any suggestions.

My smb.conf is attached

---

### Post by davidsxls on 2006-07-27
It seems that samba can't bind, probably because the network interface was not ready. Perhaps this can be solved by reordering the init script.

Or just start samba "manually" through rc.local

---

### Post by indeed on 2006-07-27
Thanks davidsxls, but samba works quite merrily on that interface for long periods of time - so I don't think it has a problem binding initially. It seems to be only after a period of inactivity on that interface that nmbd quits.

---

### Post by dbyrne on 2008-02-18
Anyone ever find the answer to this one ? I have the same problem ... 

As an aside, these kinds of frustrating problems that seem (from google searches) to have been around for ever are the main reason why I'd never run a system that needed to be dependable on linux, especially commercially. I've been a great fan of linux for nearly 15 years, but it really bugs me that I have Windoze systems at home with uptimes of hundreds of days, while the services on my linux box die within weeks :(:(

---

### Post by astrotech226 on 2008-02-18
Could you try to upgrade Samba to a newer version.  I've found numerous bug reports about what you are describing and it looks to be fixed after 3.0.25-1.  Here's the link:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=265577]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=265577")

There's a lot in there not relating to your problem, but look at the bottom of the page.  They discuss some other bugs and how nmbd handles situations like ifdown and ifup.

I've run Samba 3.x since it was alpha and beta and have never seen this particular problem.  Is there anything in your other /var/log files of interest when nmbd stops?  It appears that samba thinks the interface has been brought down which would surely be causing other problems as well.

---

### Post by dbyrne on 2008-02-23
Hi, thanks for your help. Unfortunately I'm already running 3.0.26a. I've trawled the logs but nothing else reports problems at the same time.

I'll keep looking, probably just put a hack to check for the nmbd process and re-start if it's not there.

I hate these cruddy work-arounds though - feels like Windows all over again :(

---

