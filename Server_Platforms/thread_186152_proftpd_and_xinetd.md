---
title: "proftpd and xinetd"
date: 2006-06-01
forum: Server Platforms
---

### Post by spvo on 2006-06-01
I'm trying to get a proftpd server set up using xinetd.  I had proftpd configured and working perfectly while in standalone mode, but after switching the type to inetd I can no longer connect to it.

When first checking the xinetd.conf was essentially blank and the xinetd.d directy had no proftpd file in it.  I changed the /etc/xinetd.conf file to look like

defaults
{
}

service ftp
{
        flags           = REUSE
        socket_type     = stream
        instances       = 50
        wait            = no
        user            = root
        server          = /usr/sbin/proftpd
#        bind            = <the-ip-you-wish-to-bind-to>
        log_on_success  = HOST PID
        log_on_failure  = HOST RECORD
}

I had thought that the server option was supposed to point to an in.ftpd file, but I couldn't find it anywhere on my system.  When I try to connect to the server I get a 'connection refused' error.  Also when I try to run proftpd from the command line it tells me 'to run from command line use standalone'.  Can anyone suggest what I should do to get this working?  Its really becoming a frustrating problem.

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=spvo]When first checking the xinetd.conf was essentially blank and the xinetd.d directy had no proftpd file in it.  I changed the /etc/xinetd.conf file to look like[/QUOTE]

add **disable = no** to the options .... see:

[http://www.proftpd.org/docs/faq/linked/faq-ch4.html](http://www.proftpd.org/docs/faq/linked/faq-ch4.html)

> I had thought that the server option was supposed to point to an in.ftpd file, but I couldn't find it anywhere on my system.

in.ftp is not needed for xinetd. But of course the proftpd.conf file must be configured correctly to be able to use proftpd in standalone mode. See config manual.

Thomas

---

### Post by spvo on 2006-06-10
Well I added the 'disable = no' option, and still no luck with it.  Any other suggestions?

---

### Post by linuxone on 2006-06-11
Hi,

[QUOTE=spvo]Well I added the 'disable = no' option, and still no luck with it.  Any other suggestions?[/QUOTE]

did you check the syslog when starting xinetd? It should contain an error notice about the reason why xinetd won't launch.

Thomas

---

