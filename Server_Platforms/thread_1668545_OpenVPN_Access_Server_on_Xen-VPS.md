---
title: "OpenVPN Access Server on Xen-VPS"
date: 2011-01-16
forum: Server Platforms
---

### Post by Thomas22 on 2011-01-16
Hello,
I have installed open VPN on a XEN-VPS. I'm using Ubuntu 9.10 karmic x86, but if I try to start the Vpn, I get following error:

Service deferred error: IPTablesServiceBase: failed to run  iptables-restore [status=2]: ['FATAL: Could not load  /lib/modules/2.6.31.6/modules.dep: No such file or directory',  "iptables-restore v1.4.4: iptables-restore: unable to initialize table  'filter'", '', 'Error occurred at line: 1', "Try `iptables-restore -h'  or 'iptables-restore --help' for more information."]:  internet/base:1175,internet/base:752,internet/process:45,internet/process:306,internet/_baseprocess:48,internet/process:775,internet/_baseprocess:60,svc/pp:116,svc/svcnotify:26,internet/defer:238,internet/defer:307,internet/defer:323,sagent/ipts:105,sagent/ipts:39,util/error:52,util/error:32
service failed to start due to unresolved dependencies: set(['user', 'iptables_openvpn'])
service failed to start due to unresolved dependencies: set(['user', 'iptables_openvpn'])
service failed to start due to unresolved dependencies: set(['iptables_openvpn'])

I already searched with google, but found nothing. I hope you can help.

---

