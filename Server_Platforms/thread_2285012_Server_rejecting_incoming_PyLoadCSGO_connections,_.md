---
title: "Server rejecting incoming PyLoad/CS:GO connections, allows SSH, others"
date: 2015-07-02
forum: Server Platforms
---

### Post by langhaardack on 2015-07-02
Some time ago my Ubuntu server stopped accepting connections to pyLoad and the CS:GO dedicated while SSH, Samba, netatalk and plex i.e. work fine.
I do not know of any changes I could've made since it worked, and mainly looking for suggestions as to what could be the problem..

Thanks in advance

---

### Post by TheFu on 2015-07-03
* check the firewall to see if it is blocking - **iptables -L**
* check the port being used to see if another process grabbed it before your pyLoad (whatever that is) grabbed it. Only 1 process can bind to a port. Use **netstat**.
* finally, check that the service you expect to run can actually run - run it manually and correct any errors.

**lsof** and **ptree** might be useful too. You can check the manpages for all these command to see the options needed.

This is just the beginning - after all it could be almost anything that prevents any program from working correctly. File and directory permissions could - for example. That applies not just to the program, but to any data, settings, and/or the database being accessed (if any).

---

