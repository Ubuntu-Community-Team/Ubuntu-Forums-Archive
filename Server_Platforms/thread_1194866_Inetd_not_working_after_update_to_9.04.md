---
title: "Inetd not working after update to 9.04"
date: 2009-06-23
forum: Server Platforms
---

### Post by digitoxin on 2009-06-23
Hello!

inetd worked fine in 8.10, now i updated to 9.04, services and inet.conf were not changed and inetd is running but services are not started.

For example, ftp localhost only gives ftp: connect: Connection refused
Nothing in messages or somewhere else about an error...

What is wrong here?

---

### Post by digitoxin on 2009-06-23
Ok found the solution.. inetd is totally broken in 9.04, config files are not read correctly and also programs are started not as root even if specified in inetd.conf

but xinetd works....

---

### Post by Vegan on 2009-06-23
I use telnetd and vsftpd and those ancient programs seem fine.

I have very little software running on the IBM.

inetd was one that I choked often. So I have it flagged as useless.

I have learned to be very cautious with any given package. I have grown very cynical.

---

