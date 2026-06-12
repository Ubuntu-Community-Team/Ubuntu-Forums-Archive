---
title: "hosts.deny won't block access"
date: 2007-06-10
forum: Server Platforms
---

### Post by TheDoulos on 2007-06-10
I've got the Dapper Server running on an old PC at my house and I've got it set up with typical services (apache2, mail services, ftp, telnet, ssh, nfs, etc.)

In looking through the proftp logs, I noticed some rouge login attempts.  I wrote a simple C program to scan the proftp logs looking for disconnects due to "Maximum login attempts" exceeded, and add the IP address of the offender to the hosts.deny file.  I put this is a crontab, and it seems to work - at least with regard to modifying the hosts.deny file.

I tested it out by making bogus login attempts from my other machine, and even though my IP address ends up in the hosts.deny file, I can still access my server via ftp.  SSH connections *are* blocked, but not ftp.

Let's pretend my main desktop IP address is 192.168.0.2.  Here's the line in /etc/hosts.deny

ALL: 192.168.0.2

I even tried

ALL: 192.168.0.2: DENY

Even after rebooting the server, 192.168.0.2 is allowed to access the server.

I'm obviously missing something fundamental, so please enlighten me :)

Thanks in advance...

---

### Post by Mr. C. on 2007-06-10
See if the proftpd was compiled with TCP Wrappers:

Locate the proftpd program and run:

ldd /path/to/proftpd

and look for "libwrap...".

If there is no libwrap appearing, proftpd was not compiled with tcpwrappers, and /etc/hosts.allow, etc., are not used.

MrC

---

### Post by TheDoulos on 2007-06-10
Thanks for the quick reply.  Here's the output of ldd /usr/sbin/proftpd```
linux-gate.so.1 =>  (0xffffe000)
libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7f7e000)
libcap.so.1 => /lib/libcap.so.1 (0xb7f7a000)
[COLOR="Red"]libwrap.so.0 => /lib/libwrap.so.0 (0xb7f73000)[/COLOR]
libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7f5e000)
libssl.so.0.9.8 => /usr/lib/i686/cmov/libssl.so.0.9.8 (0xb7f21000)
libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7df1000)
libpam.so.0 => /lib/libpam.so.0 (0xb7de9000)
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7cba000)
libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7cb7000)
libz.so.1 => /usr/lib/libz.so.1 (0xb7ca3000)
/lib/ld-linux.so.2 (0xb7fb3000)
```
Looks like libwrap is in there.

---

### Post by Mr. C. on 2007-06-10
Great.

Now is proftp running in stanalone mode, or via inted ?

In inetd mode, inetd is compiled with libwrap, so tcpwrappers is supported by all applications it launches.

If standalone, it needs mod_wrap, and needs to be enabled.

MrC

---

### Post by TheDoulos on 2007-06-10
I've got proftpd running standalone...so I guess it's not as easy as putting a directive in the proftpd.conf file like "WrapEngine on"?

Any guidance as to how to enable mod_wrap (short of getting the source and recompiling)?  Or is it easy to switch it over to run inetd?

---

### Post by Mr. C. on 2007-06-10
It is likely available in Universe, but I have not verified this.

MrC

---

### Post by TheDoulos on 2007-06-11
Actually, it looks as though mod_wrap *is* compiled into my proftpd.  Here's the output of [FONT="Courier New"]proftpd -l[/FONT]```
Compiled-in modules:
  mod_core.c
  mod_xfer.c
  mod_auth_unix.c
  mod_auth_file.c
  mod_auth.c
  mod_ls.c
  mod_log.c
  mod_site.c
  mod_auth_pam.c
  mod_quotatab.c
  mod_ratio.c
  mod_tls.c
  mod_rewrite.c
  mod_radius.c
 [COLOR="Red"] mod_wrap.c[/COLOR]
  mod_quotatab_file.c
  mod_delay.c
  mod_readme.c
  mod_ifsession.c
  mod_cap.c
```Now the question is "how do I enable mod_wrap"?

---

### Post by TheDoulos on 2007-06-11
Got it...I added the following line to my proftpd.conf file:```
TCPAccessFiles     /etc/hosts.allow  /etc/hosts.deny
```All ftp accesses are blocked, but the attacks still show up in the proftp log file.

---

### Post by Mr. C. on 2007-06-12
Sorry I wasn't able to respond earlier.  Glad you got it working.

MrC

---

