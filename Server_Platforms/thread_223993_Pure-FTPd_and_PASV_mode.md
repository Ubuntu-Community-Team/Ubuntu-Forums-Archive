---
title: "Pure-FTPd and PASV mode"
date: 2006-07-27
forum: Server Platforms
---

### Post by Swad on 2006-07-27
I, for the life of me, cannot get Pure-FTPd to work with PASV mode.  I have used it for years successfully and setting any clients to active has always worked.  Here is a brief overview of my setup.

The Pure-FTPd standalone daemon runs on my home network on my Ubuntu 6.06 LTS install.  My LAN at home is protected by a m0n0wall firewall.  Masquerading is on so that all internal IPs look like my external DSL IP from the outside world.  I have NAT and packet filter rules setup for Pure-FTPd that forward port 21 as well as a range of about 32 ports above 50000 to the Ubuntu machine hosting the FTP server.  I have the '-p' option in Pure-FTPd set to the port range that is reserved for PASV mode.

From work (behind our PIX firewall) I try to connect to this FTP server.  With passive mode off it works.  When I turn it on, though, it doesn't not.  I am using FileZilla for the client.  When I connect it looks like it's going and then it chokes at the end.  Here are the last 4 lines it returns:

```
Command: PASV
Error  : Disconnected from the server
Error  : Could not retrieve directory listing
Error  : Timeout detected!
```

This is what it does every time after it looks like it is going to connect.  I check the Pure-FTPd server out with 'pure-ftpwho' and I see the instance connected, but not really I guess.  Running a 'netstat --inet -pln' shows that there is a new connection the Ubuntu server, but it's never in the right port range that I specified with the '-p' switch.  It appears like the FTP client is not using the range of PASV ports which I have set aside.

How do I troubleshoot this and make the client use the proper ports for PASV mode?  Are there some firewall settings I need to tweak with?  Or other Pure-FTPd options?  I would appreciate any clues as to what might be causing it not to work.  Thanks.

---

### Post by Swad on 2006-07-31
Shameless bump from many pages buried deep.  Does nobody deal in PASV FTP... especially Pure-FTPd?

---

### Post by alexsandu on 2006-10-25
Here's a tutorial about that
[http://venom.sweblog.net/Pages/Pure-ftpd-On-Openwrt-And-Passive-Mode/239.html](http://venom.sweblog.net/Pages/Pure-ftpd-On-Openwrt-And-Passive-Mode/239.html)

---

