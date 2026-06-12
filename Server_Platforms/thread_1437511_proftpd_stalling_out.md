---
title: "proftpd stalling out"
date: 2010-03-24
forum: Server Platforms
---

### Post by PrimarchBentley on 2010-03-24
I've installed proftpd, allowed a range of ports access for passive connections, and can log into my ftp setup, navigate the file structure, and create subdirectories.

However, when I try to 'put' a file, I get:
229 Entering Extended Passive Mode (|||49147|)
150 Opening BINARY mode data connection for <filename>
  0% |                                                        |   608 KB    0.84 KB/s  - stalled -

I'll finally see something like this:

  0% |                                                        |   608 KB    0.63 KB/s  - stalled -ftp: netout: Connection timed out
  0% |                                                        |    -1       0.00 KB/s    --:-- ETA
421 Service not available, remote server has closed connection.

The session in /var/log/proftpd/proftpd.log:
Mar 23 22:12:09 <server> proftpd[8573] <server> (<client_ip>[<client_ip>]): FTP session opened.
Mar 23 22:12:16 <server> proftpd[8573] <server> (<client_ip>[<client_ip>]): ANON ftp: Login successful.
Mar 23 21:12:16 <server> proftpd[8573] <server> (<client_ip>[<client_ip>]): Preparing to chroot to directory '/var/ftp'
Mar 23 21:22:32 <server> proftpd[8573] <server> (<client_ip>[<client_ip>]): Data transfer stall timeout: 600 seconds
Mar 23 21:22:32 <server> proftpd[8573] <server> (<client_ip>[<client_ip>]): FTP session closed.

If I cancel the transfer once it slows to a crawl, I'll see something such as this in /var/log/proftpd/xferlog:
Tue Mar 23 21:22:32 2010 600 155.98.20.200 500680 /var/ftp/uploads/<filename> b _ i a <email> ftp 0 * i
But if the transfer stalls/times out itself, there is no log entry in xferlog.


Most of the time when the transfer starts, I'll get a peak (say, >600KB/s), that quickly drops in speed, until it finally stalls out.  The size of the file created on the server will have a file size that matches the original 'peak' speed, for a whole of one second (ie. I'll start at ~603KB/s before it drops speed, the file will be ~603Kb).  This file stays at that size, and is no longer modified while the transfer times out.


Any ideas on what may be causing this?  I'd think, if there were a problem with ip_conntrack_ftp, I wouldn't get the 'Entering Extended Passive Mode (|||<port>|)' for directory listings correctly either.
  It seems to get the initial burst of data (and writes that data to disk), then stalls out from there...

---

