---
title: "Ubuntu server connection to active direcotry domain"
date: 2009-12-17
forum: Server Platforms
---

### Post by szpuni on 2009-12-17
Hi,

I have a problem with connection to Active directory domain.

I was following howto from this website:
[https://help.ubuntu.com/9.10/serverguide/C/likewise-open.html](https://help.ubuntu.com/9.10/serverguide/C/likewise-open.html)

as I'm running ubuntu 9.10 64 bit version.

Problem I have is:

```
root@xxxdb:/etc# domainjoin-cli join club.local card\x_backup
Joining to AD Domain:   club.local
With Computer DNS Name: xxxdb.club.local

[EMAIL="server_backup@CLUB.LOCA"]server_backup@CLUB.LOCA[/EMAIL]L's password:

Error: Lsass Error [code 0x00080047]

The call to Kerberos 5 failed 
```I don't really know if this is problem with linux server or some configuration issues.

I spoke with admin which is maintaining win 2003 server and he don't see anything in the logs not even connection.

Do somebody have some experience with this?

---

