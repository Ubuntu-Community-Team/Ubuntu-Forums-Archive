---
title: "Problem with Samba"
date: 2011-08-01
forum: Server Platforms
---

### Post by carballinho on 2011-08-01
Hello,

I'm having a problem with Samba. In log.smbd Im getting this message periodically:

[2011/07/31 07:29:01,  0] lib/util_sock.c:1475(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
[2011/07/31 07:44:01,  0] lib/util_sock.c:1475(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
[2011/07/31 07:59:01,  0] lib/util_sock.c:1475(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
[2011/07/31 08:29:01,  0] lib/util_sock.c:1475(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
[2011/07/31 08:44:01,  0] lib/util_sock.c:1475(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
...

There is someone who knows how to solve this problem?

Thanks.

---

### Post by Doug S on 2011-08-01
Those entries in log.smbd do not really indicate a problem. I have them also in my log.smbd, and they are due to a windows XP machine on my local area network which inquires on both ports 445 and 139. Ultimatley, windows XP only uses one of those ports and it disconnects from the other one, which leads to the samba log entry. While I have never tried it myself, evidently the log entries can be eliminated by having samba only listen on one of the two ports, as long as your server is not a PDC (Primary Domain Controller)(which mine is). I can not remember where, but I read somewhere that having samba only listen on one of the ports can cause a reduction in performance (which I have no idea if that is actually true).

---

### Post by carballinho on 2011-08-02
I have added to smb.conf file the line "smb ports = 139" and no error in logs... but, after your answer, Im afraid if my PDC performance will go down.

I will wait some days with this configuration to check it...

Thanks.

---

