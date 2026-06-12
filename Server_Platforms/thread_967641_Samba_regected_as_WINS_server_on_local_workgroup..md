---
title: "Samba regected as WINS server on local workgroup."
date: 2008-11-02
forum: Server Platforms
---

### Post by gexcko on 2008-11-02
I've set up samba on ubuntu 8.04 server as a local & domain master browser serving WINS to my subnet. It appears to work fine for a while, until one of the pcs (almost always running Win XP Pro) rejects it. Shortly afterward I'll start seeing errors about __MSBROWSE_ missing (I have no idea what this means) and none of the other computers on the network (Win, Mac, or Linux) can browse the workgroup, although they can directly connect to shares on the server or any other computer.

Note that the PC at 10.10.10.192 rejecting the server is a XP Pro.

Any ideas on a starting point to troubleshoot this would be great.

result of: tail /var/log/samba/log.nmbd
```
[2008/11/02 11:21:34, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/11/02 11:21:34, 0] nmbd/asyncdns.c:start_async_dns(151)
  started asyncdns process 5718
[2008/11/02 11:21:34, 0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_wins(335)
  become_domain_master_browser_wins:
  Attempting to become domain master browser on workgroup GOSAHARA, subnet UNICAST_SUBNET.
[2008/11/02 11:21:34, 0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_wins(349)
  become_domain_master_browser_wins: querying WINS server from IP 10.10.10.245 for domain master browser name GOSAHARA<1b> on
workgroup GOSAHARA
[2008/11/02 11:21:34, 0] nmbd/nmbd_become_dmb.c:become_domain_master_stage2(113)
  *****
  
  Samba server SERVER is now a domain master browser for workgroup GOSAHARA on subnet UNICAST_SUBNET
  
  *****
[2008/11/02 11:21:34, 0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_bcast(290)
  become_domain_master_browser_bcast:
  Attempting to become domain master browser on workgroup GOSAHARA on subnet 10.10.10.245
[2008/11/02 11:21:34, 0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_bcast(303)
  become_domain_master_browser_bcast: querying subnet 10.10.10.245 for domain master browser on workgroup GOSAHARA
[2008/11/02 11:21:42, 0] nmbd/nmbd_become_dmb.c:become_domain_master_stage2(113)
  *****
  
  Samba server SERVER is now a domain master browser for workgroup GOSAHARA on subnet 10.10.10.245
  
  *****
[2008/11/02 11:21:55, 0] nmbd/nmbd_nameregister.c:register_name_response(130)
  register_name_response: server at IP 10.10.10.192 rejected our name registration of GOSAHARA<1d> IP 10.10.10.245 with error
code 6.
[2008/11/02 11:21:55, 0] nmbd/nmbd_become_lmb.c:become_local_master_fail2(417)
  become_local_master_fail2: failed to register name GOSAHARA<1d> on subnet 10.10.10.245. Failed to become a local master
browser.
[2008/11/02 11:21:55, 0] nmbd/nmbd_namelistdb.c:standard_fail_register(304)
  standard_fail_register: Failed to register/refresh name GOSAHARA<1d> on subnet 10.10.10.245
```
...
```
[2008/11/02 10:58:40, 1] nmbd/nmbd_incomingrequests.c:process_node_status_request(328)
__MSBROWSE_<01> from IP 10.10.10.146 on subnet UNICAST_SUBNET - name not found._  process_node_status_request: status request for name 
[2008/11/02 10:58:42, 1] nmbd/nmbd_incomingrequests.c:process_node_status_request(328)
__MSBROWSE_<01> from IP 10.10.10.146 on subnet UNICAST_SUBNET - name not found._  process_node_status_request: status request for name 
```

---

### Post by gexcko on 2008-11-02
I should also point out it's not always the same PC that rejects the server as local master browser.

---

### Post by Iowan on 2008-11-03
One option *might* be to boost the "oslevel" of the server.

---

### Post by gexcko on 2008-11-04
I had the os level at 35 -- I'll try bumping it up to 65 and see if it reappears. Isn't samba supposed to by default win elections over any windows box expect for nt server 2000+?

---

