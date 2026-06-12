---
title: "Samba fail register local domain in one network"
date: 2009-06-23
forum: Server Platforms
---

### Post by eufran on 2009-06-23
Hello i have one server with two networks:
1) Network 10.20.30.150
2) Network 192.168.1.250

Samba only set local domain server with network 10.20.30.250, the log file says:
[I][B]
[2009/06/23 18:05:36, 0] nmbd/nmbd_logonnames.c:add_logon_names(163)
  add_domain_logon_names:
  Attempting to become logon server for workgroup INTRANET on subnet 192.168.1.250
[2009/06/23 18:05:36, 0] nmbd/nmbd_nameregister.c:register_name_response(73)
  register_name_response: Answer name INTRANET<00> differs from question name INTRANET<1c>.
[2009/06/23 18:05:38, 0] nmbd/nmbd_logonnames.c:become_logon_server_fail(65)
  become_logon_server_fail: Failed to become a domain master for workgroup INTRANET on subnet 192.168.1.250. Couldn't register name INTRANET<1c>.
[2009/06/23 18:05:38, 0] nmbd/nmbd_namelistdb.c:standard_fail_register(304)
  standard_fail_register: Failed to register/refresh name INTRANET<1c> on subnet 192.168.1.250
[2009/06/23 18:10:36, 0] nmbd/nmbd_logonnames.c:add_logon_names(163)
  add_domain_logon_names:

[/B][/I]

I delete wins.dat and create again blank.


Help

Thanks

---

