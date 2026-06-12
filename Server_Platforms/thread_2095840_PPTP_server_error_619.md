---
title: "PPTP server error 619"
date: 2012-12-18
forum: Server Platforms
---

### Post by fireboyoman on 2012-12-18
error gating when tried to connect with server throw VPN  PPTP  

Dec 18 08:29:33 ks368776 pppd[12323]: In file /etc/ppp/pptpd-options: unrecognized option 'require-mppe-stateful'
Dec 18 08:29:33 ks368776 pptpd[12322]: GRE: read(fd=6,buffer=80504c0,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Dec 18 08:29:33 ks368776 pptpd[12322]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Dec 18 08:29:33 ks368776 pptpd[12322]: CTRL: Reaping child PPP[12323]
Dec 18 08:29:33 ks368776 pptpd[12322]: CTRL: Client 5.21.82.6 control connection finished
Dec 18 08:30:12 ks368776 pptpd[12325]: CTRL: Client 5.21.82.6 control connection started
Dec 18 08:30:13 ks368776 pptpd[12325]: CTRL: Starting call (launching pppd, opening GRE)
Dec 18 08:30:13 ks368776 pppd[12326]: In file /etc/ppp/pptpd-options: unrecognized option 'require-mppe-stateful'
Dec 18 08:30:13 ks368776 pptpd[12325]: GRE: read(fd=6,buffer=80504c0,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Dec 18 08:30:13 ks368776 pptpd[12325]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Dec 18 08:30:13 ks368776 pptpd[12325]: CTRL: Reaping child PPP[12326]
Dec 18 08:30:13 ks368776 pptpd[12325]: CTRL: Client 5.21.82.6 control connection finished
Dec 18 08:30:18 ks368776 pptpd[12335]: MGR: Maximum of 100 connections reduced to 17, not enough IP addresses given
Dec 18 08:30:18 ks368776 pptpd[12336]: MGR: Manager process started
Dec 18 08:30:18 ks368776 pptpd[12336]: MGR: Maximum of 17 connections available
Dec 18 08:32:11 ks368776 pptpd[12406]: MGR: Maximum of 100 connections reduced to 17, not enough IP addresses given
Dec 18 08:32:11 ks368776 pptpd[12407]: MGR: Manager process started
Dec 18 08:32:11 ks368776 pptpd[12407]: MGR: Maximum of 17 connections available
Dec 18 08:32:35 ks368776 pptpd[12489]: MGR: Maximum of 100 connections reduced to 17, not enough IP addresses given
Dec 18 08:32:35 ks368776 pptpd[12490]: MGR: Manager process started
Dec 18 08:32:35 ks368776 pptpd[12490]: MGR: Maximum of 17 connections available
Dec 18 08:32:58 ks368776 pptpd[12497]: CTRL: Client 5.21.82.6 control connection started
Dec 18 08:32:59 ks368776 pptpd[12497]: CTRL: Starting call (launching pppd, opening GRE)
Dec 18 08:32:59 ks368776 pppd[12498]: In file /etc/ppp/pptpd-options: unrecognized option 'require-mppe-stateful'
Dec 18 08:32:59 ks368776 pptpd[12497]: GRE: read(fd=6,buffer=80504c0,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Dec 18 08:32:59 ks368776 pptpd[12497]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Dec 18 08:32:59 ks368776 pptpd[12497]: CTRL: Reaping child PPP[12498]
Dec 18 08:32:59 ks368776 pptpd[12497]: CTRL: Client 5.21.82.6 control connection finished
Dec 18 08:38:20 ks368776 pptpd[12568]: CTRL: Client 5.21.82.6 control connection started
Dec 18 08:38:22 ks368776 pptpd[12568]: CTRL: Starting call (launching pppd, opening GRE)
Dec 18 08:38:22 ks368776 pppd[12569]: In file /etc/ppp/pptpd-options: unrecognized option 'require-mppe-stateful'
Dec 18 08:38:22 ks368776 pptpd[12568]: GRE: read(fd=6,buffer=80504c0,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Dec 18 08:38:22 ks368776 pptpd[12568]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Dec 18 08:38:22 ks368776 pptpd[12568]: CTRL: Reaping child PPP[12569]
Dec 18 08:38:22 ks368776 pptpd[12568]: CTRL: Client 5.21.82.6 control connection finished
Dec 18 08:38:45 ks368776 pptpd[12577]: CTRL: Client 5.21.82.6 control connection started
Dec 18 08:38:46 ks368776 pptpd[12577]: CTRL: Starting call (launching pppd, opening GRE)
Dec 18 08:38:46 ks368776 pppd[12578]: In file /etc/ppp/pptpd-options: unrecognized option 'require-mppe-stateful'
Dec 18 08:38:46 ks368776 pptpd[12577]: GRE: read(fd=6,buffer=80504c0,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Dec 18 08:38:46 ks368776 pptpd[12577]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Dec 18 08:38:46 ks368776 pptpd[12577]: CTRL: Reaping child PPP[12578]
Dec 18 08:38:46 ks368776 pptpd[12577]: CTRL: Client 5.21.82.6 control connection finished
Dec 18 08:39:01 ks368776 CRON[12581]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Dec 18 08:39:37 ks368776 pptpd[12590]: CTRL: Client 5.21.82.6 control connection started
Dec 18 08:39:39 ks368776 pptpd[12590]: CTRL: Starting call (launching pppd, opening GRE)
Dec 18 08:39:39 ks368776 pppd[12592]: In file /etc/ppp/pptpd-options: unrecognized option 'require-mppe-stateful'
Dec 18 08:39:39 ks368776 pptpd[12590]: GRE: read(fd=6,buffer=80504c0,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Dec 18 08:39:39 ks368776 pptpd[12590]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Dec 18 08:39:39 ks368776 pptpd[12590]: CTRL: Reaping child PPP[12592]
Dec 18 08:39:39 ks368776 pptpd[12590]: CTRL: Client 5.21.82.6 control connection finished
Dec 18 08:39:39 ks368776 pptpd[12599]: MGR: Maximum of 100 connections reduced to 17, not enough IP addresses given
Dec 18 08:39:39 ks368776 pptpd[12600]: MGR: Manager process started
Dec 18 08:39:39 ks368776 pptpd[12600]: MGR: Maximum of 17 connections available

---

### Post by SeijiSensei on 2012-12-18
Did you try removing this from the options file?

```
unrecognized option 'require-mppe-stateful'
```

---

