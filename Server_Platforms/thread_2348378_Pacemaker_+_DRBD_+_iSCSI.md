---
title: "Pacemaker + DRBD + iSCSI"
date: 2017-01-03
forum: Server Platforms
---

### Post by xemius on 2017-01-03
Hi all,

Was trying to make a HA DRBD setup with pacemaker and then export this with iSCSI.
I've been trying alot but I cannot see my mistake everytime i try to add the iSCSILogicalUnit OCF resource agent it says:

Failed Actions:
```
* p_lu_vg1_lun1_start_0 on NODE02 'unknown error' (1): call=48, status=complete, exitreason='none',
    last-rc-change='Tue Jan  3 13:23:11 2017', queued=0ms, exec=87ms
* p_lu_vg1_lun1_start_0 on NODE01 'unknown error' (1): call=58, status=complete, exitreason='none',
    last-rc-change='Tue Jan  3 13:23:11 2017', queued=0ms, exec=88ms
```

In the logs (/var/log/syslog) I got this:

```
iSCSILogicalUnit(ISCSI-LUN0)[29018]: ERROR: Traceback (most recent call last): File "/usr/bin/targetcli", line 89, in <module> main() File "/usr/bin/targetcli", line 78, in main shell.run_cmdline(" ".join(sys.argv[1:])) File "/usr/lib/python2.7/dist-packages/configshell/shell.py", line 934, in run_cmdline self._execute_command(path, command, pparams, kparams) File "/usr/lib/python2.7/dist-packages/configshell/shell.py", line 899, in _execute_command self.log.error(msg) File "/usr/lib/python2.7/dist-packages/configshell/log.py", line 159, in error self._log('error', msg) File "/usr/lib/python2.7/dist-packages/configshell/log.py", line 112, in _log self.con.display(msg) File "/usr/lib/python2.7/dist-packages/configshell/console.py", line 153, in display self.raw_write(text) File "/usr/lib/python2.7/dist-packages/configshell/console.py", line 141, in raw_write self._stdout.write(text) TypeError: expected a string or other character buffer object
```

Any help would be appreciated :)

---

