---
title: "Simple 'open ports' question"
date: 2004-12-21
forum: Server Platforms
---

### Post by jamesdin on 2004-12-21
I can see auth 113 open on my mail server.  netstat -natp gives me this output:

tcp        0      0 0.0.0.0:113             0.0.0.0:*               LISTEN      178/inetd

I can't find anything in inetd.conf that is opening or using this port. I have two questions:

How do I gracefully start/stop the service? and 
How can I find out what's using it?

Thanks.

---

### Post by Juergen on 2004-12-22
Really no entry for identd in /etc/inetd.conf?

Maybe you should post your inetd.conf here.

---

### Post by nemin on 2004-12-22
[QUOTE=jamesdin]I can see auth 113 open on my mail server.  netstat -natp gives me this output:

tcp        0      0 0.0.0.0:113             0.0.0.0:*               LISTEN      178/inetd

I can't find anything in inetd.conf that is opening or using this port. I have two questions:
[/QUOTE]
This port isn't opened by default as far as I know. I'd check inetd.conf twice if I were you ;)

---

### Post by jamesdin on 2004-12-22
[QUOTE=Juergen]Really no entry for identd in /etc/inetd.conf?

Maybe you should post your inetd.conf here.[/QUOTE]


 cat /etc/inetd.conf
# /etc/inetd.conf:  see inetd(8) for further informations.
#
# Internet server configuration database
#
#
# Lines starting with "#:LABEL:" or "#<off>#" should not
# be changed unless you know what you are doing!
#
# If you want to disable an entry so it isn't touched during
# package updates just comment it out with a single '#' character.
#
# Packages should modify this file by using update-inetd(8)
#
# <service_name> <sock_type> <proto> <flags> <user> <server_path> <args>
#
#:INTERNAL: Internal services
#echo           stream  tcp     nowait  root    internal
#echo           dgram   udp     wait    root    internal
#chargen        stream  tcp     nowait  root    internal
#chargen        dgram   udp     wait    root    internal
#discard                stream  tcp     nowait  root    internal
#discard                dgram   udp     wait    root    internal
#daytime                stream  tcp     nowait  root    internal
#daytime        dgram   udp     wait    root    internal
time            stream  tcp     nowait  root    internal
#time           dgram   udp     wait    root    internal

#:STANDARD: These are standard services.
#ftp            stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/in.ftpd

#:BSD: Shell, login, exec and talk are BSD protocols.

#:MAIL: Mail, news and uucp services.
#disabled#smtp          stream  tcp     nowait  mail    /usr/sbin/exim exim -bs
imap2  stream  tcp     nowait        root    /usr/sbin/tcpd  /usr/sbin/imapd
imap3  stream  tcp     nowait        root    /usr/sbin/tcpd  /usr/sbin/imapd
pop-2    stream tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/ipop2d
pop-3    stream tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/ipop3d
#poppassd       stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/poppassd

#:INFO: Info services
ident           stream  tcp     wait    identd  /usr/sbin/identd        identd

#:BOOT: Tftp service is provided primarily for booting.  Most sites
# run this only on machines acting as "boot servers."

#:RPC: RPC based services

#:HAM-RADIO: amateur-radio services

#:OTHER: Other services

---

### Post by nemin on 2004-12-23
[QUOTE=jamesdin]
#:INFO: Info services
ident           stream  tcp     wait    identd  /usr/sbin/identd        identd
[/QUOTE]
My guess is that this line is the problem ;)

---

### Post by jamesdin on 2004-12-23
Can I just comment out inetd? Wouldn't that negate the existance of the config file? I'm a little confused.  :confused:

---

### Post by nemin on 2004-12-24
[QUOTE=jamesdin]Can I just comment out inetd? Wouldn't that negate the existance of the config file? I'm a little confused.  :confused:[/QUOTE]
Yeah, you can simple comment out that line. Let us know if the problem is fixed now :)

---

### Post by jamesdin on 2004-12-24
[QUOTE=nemin]Yeah, you can simple comment out that line. Let us know if the problem is fixed now :)[/QUOTE]

Yes, it worked. I don't understand why though.  I though inetd just opens specified services in its conf file.

---

### Post by nemin on 2004-12-25
[QUOTE=jamesdin]Yes, it worked. I don't understand why though. I though inetd just opens specified services in its conf file.[/QUOTE]I don't completely understand what you mean and I hope I can clear it up. The configuration file of inetd has this line:> #:INFO: Info services
ident stream tcp wait identd /usr/sbin/identd identd
So it opens a port for identd and starts the daemon:) What do you not understand about that?

---

### Post by localzuk on 2005-03-27
I think the confusion comes due to the 2 very similar names: inetd and ident - it is very easy to mis-read one or the other and get them confused...

---

### Post by nemin on 2005-03-28
[QUOTE=localzuk]I think the confusion comes due to the 2 very similar names: inetd and ident - it is very easy to mis-read one or the other and get them confused...[/QUOTE]
Hmm you're right. I just re-read this thread I don't unstand why my solution did work, lol :p

---

