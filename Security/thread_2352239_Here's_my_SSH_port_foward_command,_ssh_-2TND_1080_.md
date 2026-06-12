---
title: "Here's my SSH port foward command, ssh -2TND 1080 user@ip-or-hostname"
date: 2017-02-10
forum: Security
---

### Post by MechaMechanism on 2017-02-10
A special note about option -C.  Unless you are on a dial-up modem connection, the -C option only hurts you on virtually all modern network connections.  I would not use the -C unless your speed is slower than about 1Mbps.  It really is designed for 56K dial-up modems and other similar slow connections like ISDN.  Here is the man page entry for -C;

-C      Requests compression of all data (including stdin, stdout,
             stderr, and data for forwarded X11 and TCP connections).  The
             compression algorithm is the same used by gzip(1), and the
             “level” can be controlled by the CompressionLevel option for pro&#8208;
             tocol version 1.  Compression is desirable on modem lines and
             other slow connections, but will only slow down things on fast
             networks.  The default value can be set on a host-by-host basis
             in the configuration files; see the Compression option.

Most SSH advice concerning -C is incorrect.  Unfortunately too many people blindly use the -C option without understanding the option.  Most people just copy and paste the command from some web site and don't bother to read the man page.  As you can see it's a pet peeve of mine.

ssh -2TND 1080

I'll break it down for you.

-2 Forces ssh to try protocol version 2 only.

T Disable pseudo-tty allocation.

N Do not execute a remote command.  This is useful for just for forwarding ports (protocol version 2 only).

D [bind_address:]port
             Specifies a local “dynamic” application-level port forwarding.
             This works by allocating a socket to listen to port on the local
             side, optionally bound to the specified bind_address.  Whenever a
             connection is made to this port, the connection is forwarded over
             the secure channel, and the application protocol is then used to
             determine where to connect to from the remote machine.  Currently
             the SOCKS4 and SOCKS5 protocols are supported, and ssh will act
             as a SOCKS server.  Only root can forward privileged ports.
             Dynamic port forwardings can also be specified in the configura&#8208;
             tion file.

1080 I'd use this port as it's the socks port.  Use of another port is fine, but will not give you any security advantage.  So I use this port.  The only reason not to use this port is if you already have another application using 1080.

I'm interested in hearing from anybody about their commands.  Just so you know I use keys without a password.  My keys have a bit strength of 8192 bits and I maintain strict control over the devices that have keys, so devices are all encrypted with very strong passwords.

---

