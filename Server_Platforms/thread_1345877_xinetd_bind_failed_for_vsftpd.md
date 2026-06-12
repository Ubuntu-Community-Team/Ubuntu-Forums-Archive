---
title: "xinetd bind failed for vsftpd"
date: 2009-12-04
forum: Server Platforms
---

### Post by abhidg on 2009-12-04
**solved**: I had a duplicate ftp section in /etc/xinetd.d/dict which was causing the problem

I was trying to setup xinetd with vsftpd and used the default config from /usr/share/doc/vsftpd/.../vsftpd.xinetd after copying to /etc/xinetd.d/ftp and changing the server line to /usr/sbin/vsftpd. When I had only ftp enabled, it was working fine. Now I enabled samba and dict services and xinetd gives the following errors:

Port not specified and can't find service: ftp with getservbyname
bind failed (Address already in use (errno = 98 )). service = ftp
Service ftp failed to start and is deactivated.

The port not specified error appears even when I manually specify the port (port = 21).

Any ideas as to why this weird error is coming? ftp is listed in /etc/services, I checked. Also I've listen=NO in vsftpd.

My xinetd.d/ftp file is

```

# vsftpd is the secure FTP server.
service ftp
{
	port			= 21
        disable                 = no
        socket_type             = stream
        wait                    = no
        user                    = root
        server                  = /usr/sbin/vsftpd
        per_source              = 5
        instances               = 10
        banner_fail             = /etc/vsftpd.busy_banner
}


```

---

