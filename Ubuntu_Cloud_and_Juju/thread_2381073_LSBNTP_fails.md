---
title: "LSB/NTP fails"
date: 2017-12-26
forum: Ubuntu Cloud and Juju
---

### Post by fabiansc on 2017-12-26
Hello everybody,

I am facing an issue at Ubuntu MAAS, as my NTP is not booting up. You can find my whole setup (starting by making a bootable device) on my [blog]("https://cloud.fas-consulting.de/drupal/page/cloud-computing/metal-service-maas/maas-operating-system-configuration").

[IMG]https://cloud.fas-consulting.de//drupal/sites/default/files/imce_uploads/cloud/maas/2017-12-26%20Ubuntu%20MAAS%20NTP%20Issue.png[/IMG]

```
[COLOR=#696969][FONT=Menlo]fabiansc@Nexus:~$ sudo systemctl status ntp.service[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][COLOR=#c33720]**&#9679;**[/COLOR] ntp.service - LSB: Start NTP daemon[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   Loaded: loaded (/etc/init.d/ntp; bad; vendor preset: enabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   Active: [COLOR=#c33720]**failed**[/COLOR] (Result: exit-code) since Di 2017-12-26 14:13:38 CET; 19s ago[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]     Docs: man:systemd-sysv-generator(8)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  Process: 27073 ExecStart=/etc/init.d/ntp start (code=exited, status=5)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:13:38 Nexus systemd[1]: Starting LSB: Start NTP daemon...[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:13:38 Nexus systemd[1]: **ntp.service: Control process exited, code=exited status=5**[/FONT][/COLOR]
[COLOR=#C33720][FONT=Menlo][COLOR=#000000]Dez 26 14:13:38 Nexus systemd[1]: [/COLOR]**Failed to start LSB: Start NTP daemon.**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:13:38 Nexus systemd[1]: **ntp.service: Unit entered failed state.**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:13:38 Nexus systemd[1]: [B]ntp.service: Failed with result 'exit-code'.
[/B][/FONT][/COLOR]

[COLOR=#696969][FONT=Menlo]fabiansc@Nexus:~$ journalctl -xe[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- Subject: Unit ntp.service has failed[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- Defined-By: systemd[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- Unit ntp.service has failed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- The result is failed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:05 Nexus systemd[1]: **ntp.service: Unit entered failed state.**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:05 Nexus systemd[1]: **ntp.service: Failed with result 'exit-code'.**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:05 Nexus sudo[27183]: pam_unix(sudo:session): session closed for user root[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus maas.service_monitor[1577]: **[error] Service 'ntp_region' failed to restart: Job for ntp.service failed because the control process exited with error code. **[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]: 2017-12-26 14:14:06 maasserver.regiondservices.ntp: [critical] Failed to update NTP configuration.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]: Traceback (most recent call last):[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:   File "/usr/lib/python3/dist-packages/twisted/internet/defer.py", line 434, in errback[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:     self._startRunCallbacks(fail)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:   File "/usr/lib/python3/dist-packages/twisted/internet/defer.py", line 501, in _startRunCallbacks[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:     self._runCallbacks()[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:   File "/usr/lib/python3/dist-packages/twisted/internet/defer.py", line 588, in _runCallbacks[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:     current.result = callback(current.result, *args, **kw)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:   File "/usr/lib/python3/dist-packages/twisted/internet/defer.py", line 1184, in gotResult[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:     _inlineCallbacks(r, g, deferred)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]: --- <exception caught here> ---[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:   File "/usr/lib/python3/dist-packages/twisted/internet/defer.py", line 1126, in _inlineCallbacks[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:     result = result.throwExceptionIntoGenerator(g)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:   File "/usr/lib/python3/dist-packages/twisted/python/failure.py", line 389, in throwExceptionIntoGenerator[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:     return g.throw(self.type, self.value, self.tb)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:   File "/usr/lib/python3/dist-packages/provisioningserver/utils/service_monitor.py", line 318, in restartService[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:     yield self._performServiceAction(service, "restart")[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:   File "/usr/lib/python3/dist-packages/twisted/internet/defer.py", line 1128, in _inlineCallbacks[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:     result = g.send(result)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:   File "/usr/lib/python3/dist-packages/provisioningserver/utils/service_monitor.py", line 422, in _performServiceAction[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]:     raise ServiceActionError(error_msg)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dez 26 14:14:06 Nexus sh[1574]: provisioningserver.utils.service_monitor.ServiceActionError: Service 'ntp_region' failed to restart: Job for ntp.service failed because the contr[/FONT][/COLOR]

```

After setting up the Raspberry Pi I and updating the package I noticed an issue with APT-GET; the python libraries had issues. I removed them from the APT cache and re-installed them afterwards, which worked out. I would be very glad, if you could help me to get NTP back online.

Thanks in advance!

---

### Post by fabiansc on 2017-12-29
Anyone has a hint?

---

### Post by cariboo on 2017-12-29
Moved here, as this is a better place to get your question answered.

---

### Post by fabiansc on 2018-02-07
Any hint?

---

