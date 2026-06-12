---
title: "Canonical Internal Error (Livepatch)"
date: 2019-08-20
forum: Security
---

### Post by matyd918 on 2019-08-20
Livepatch is not working and says "Canonical Livepatch has experienced an internal error. Please refer to [https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues](https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues) for further information."
  
status give me:

```
sudo canonical-livepatch statusclient-version: 9.4.1
architecture: x86_64
cpu-model: Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz
last-check: 2019-08-20T22:01:39-05:00
boot-time: 2019-08-20T13:03:24-05:00
uptime: 9h13m0s
status:
- kernel: 4.15.0-54.58-generic
  running: true
  livepatch:
    checkState: checked
    patchState: apply-failed
    version: "54.2"
    fixes: |-
      * CVE-2011-1079
      * CVE-2019-10126
      * CVE-2019-11477
      * CVE-2019-11478
      * CVE-2019-11815
      * CVE-2019-11833
      * CVE-2019-11884
      * CVE-2019-12614
      * CVE-2019-12818
      * CVE-2019-12819
      * CVE-2019-12984
      * CVE-2019-13272
      * CVE-2019-2101
      * CVE-2019-3846
```

I have looked at: [https://ubuntuforums.org/showthread.php?t=2420465](https://ubuntuforums.org/showthread.php?t=2420465) but that didn't seem to have an answer that was applicable to my problem.

grep livepatch /var/log/syslog/ gives me a host of errors:

```
grep livepatch /var/log/syslogAug 20 13:09:34 matthew-15-3567 kernel: [  370.042440] audit: type=1400 audit(1566324574.882:55): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.canonical-livepatch" pid=5734 comm="apparmor_parser"
Aug 20 13:09:34 matthew-15-3567 kernel: [  370.049748] audit: type=1400 audit(1566324574.890:56): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.canonical-livepatch.hook.configure" pid=5737 comm="apparmor_parser"
Aug 20 13:09:34 matthew-15-3567 kernel: [  370.050242] audit: type=1400 audit(1566324574.890:57): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.canonical-livepatch.canonical-livepatchd" pid=5736 comm="apparmor_parser"
Aug 20 13:09:34 matthew-15-3567 kernel: [  370.050953] audit: type=1400 audit(1566324574.890:58): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.canonical-livepatch.canonical-livepatch" pid=5735 comm="apparmor_parser"
Aug 20 13:09:44 matthew-15-3567 kernel: [  379.965840] audit: type=1400 audit(1566324584.806:67): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.canonical-livepatch.hook.configure" pid=5916 comm="apparmor_parser"
Aug 20 13:09:44 matthew-15-3567 kernel: [  380.029196] audit: type=1400 audit(1566324584.870:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.canonical-livepatch.canonical-livepatch" pid=5914 comm="apparmor_parser"
Aug 20 13:09:44 matthew-15-3567 kernel: [  380.040460] audit: type=1400 audit(1566324584.882:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.canonical-livepatch.canonical-livepatchd" pid=5915 comm="apparmor_parser"
Aug 20 13:09:44 matthew-15-3567 kernel: [  380.043072] audit: type=1400 audit(1566324584.882:70): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.canonical-livepatch" pid=5918 comm="apparmor_parser"
Aug 20 13:13:00 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 20:56:11 matthew-15-3567 canonical-livepatch[1039]: Client.Check
Aug 20 20:56:11 matthew-15-3567 canonical-livepatch[1039]: Checking with livepatch service.
Aug 20 20:56:31 matthew-15-3567 canonical-livepatch[1039]: Module may have caused kernel crash! Not inserting module.
Aug 20 20:56:31 matthew-15-3567 canonical-livepatch[1039]: To override this warning, remove /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2
Aug 20 20:56:31 matthew-15-3567 canonical-livepatch[1039]: during refresh: multiple failures
Aug 20 20:56:31 matthew-15-3567 canonical-livepatch[1039]: during refresh: cannot check: cannot send status to server: cannot send request: Put https://livepatch.canonical.com/api/machine/caea93e0ffe24f6fa3baeeb897ac1fb4: dial tcp: lookup livepatch.canonical.com on 127.0.0.53:53: read udp 127.0.0.1:58982->127.0.0.53:53: i/o timeout
Aug 20 20:56:31 matthew-15-3567 canonical-livepatch[1039]: during refresh: cannot apply patches: lock file "/var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2" already exists
Aug 20 20:56:59 matthew-15-3567 gsd-housekeepin[3797]: Failed to enumerate children of /tmp/snap.canonical-livepatch: Error opening directory '/tmp/snap.canonical-livepatch': Permission denied
Aug 20 20:57:01 matthew-15-3567 canonical-livepatch[1039]: Client.Check
Aug 20 20:57:01 matthew-15-3567 canonical-livepatch[1039]: error in livepatch check state: check-failed
Aug 20 20:57:01 matthew-15-3567 canonical-livepatch[1039]: Checking with livepatch service.
Aug 20 20:57:02 matthew-15-3567 canonical-livepatch[1039]: updating last-check
Aug 20 20:57:02 matthew-15-3567 canonical-livepatch[1039]: touched last check
Aug 20 20:57:02 matthew-15-3567 canonical-livepatch[1039]: No updates available at this time.
Aug 20 20:57:02 matthew-15-3567 canonical-livepatch[1039]: Module may have caused kernel crash! Not inserting module.
Aug 20 20:57:02 matthew-15-3567 canonical-livepatch[1039]: To override this warning, remove /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2
Aug 20 20:57:02 matthew-15-3567 canonical-livepatch[1039]: during refresh: cannot apply patches: lock file "/var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2" already exists
Aug 20 20:57:04 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 20:57:04 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 20:57:04 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 21:22:37 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 21:22:38 matthew-15-3567 canonical-livepatch[1039]: message repeated 3 times: [ failure when getting status: apply-failed]
Aug 20 21:41:54 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 21:42:28 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 21:42:28 matthew-15-3567 canonical-livepatch[1039]: failure getting status before refresh: apply-failed
Aug 20 21:42:28 matthew-15-3567 canonical-livepatch[1039]: Client.Check
Aug 20 21:42:28 matthew-15-3567 canonical-livepatch[1039]: Checking with livepatch service.
Aug 20 21:42:29 matthew-15-3567 canonical-livepatch[1039]: updating last-check
Aug 20 21:42:29 matthew-15-3567 canonical-livepatch[1039]: touched last check
Aug 20 21:42:29 matthew-15-3567 canonical-livepatch[1039]: No updates available at this time.
Aug 20 21:42:29 matthew-15-3567 canonical-livepatch[1039]: Module may have caused kernel crash! Not inserting module.
Aug 20 21:42:29 matthew-15-3567 canonical-livepatch[1039]: To override this warning, remove /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2
Aug 20 21:42:29 matthew-15-3567 canonical-livepatch[1039]: during refresh: cannot apply patches: lock file "/var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2" already exists
Aug 20 21:42:29 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 21:42:29 matthew-15-3567 canonical-livepatch[1039]: failure getting status after refresh: apply-failed
Aug 20 21:42:31 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 21:42:31 matthew-15-3567 canonical-livepatch[1039]: message repeated 2 times: [ failure when getting status: apply-failed]
Aug 20 21:42:52 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 21:42:52 matthew-15-3567 canonical-livepatch[1039]: message repeated 3 times: [ failure when getting status: apply-failed]
Aug 20 21:56:59 matthew-15-3567 gsd-housekeepin[3797]: Failed to enumerate children of /tmp/snap.canonical-livepatch: Error opening directory '/tmp/snap.canonical-livepatch': Permission denied
Aug 20 21:57:02 matthew-15-3567 canonical-livepatch[1039]: Client.Check
Aug 20 21:57:02 matthew-15-3567 canonical-livepatch[1039]: Checking with livepatch service.
Aug 20 21:57:03 matthew-15-3567 canonical-livepatch[1039]: updating last-check
Aug 20 21:57:03 matthew-15-3567 canonical-livepatch[1039]: touched last check
Aug 20 21:57:03 matthew-15-3567 canonical-livepatch[1039]: No updates available at this time.
Aug 20 21:57:03 matthew-15-3567 canonical-livepatch[1039]: Module may have caused kernel crash! Not inserting module.
Aug 20 21:57:03 matthew-15-3567 canonical-livepatch[1039]: To override this warning, remove /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2
Aug 20 21:57:03 matthew-15-3567 canonical-livepatch[1039]: during refresh: cannot apply patches: lock file "/var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2" already exists
Aug 20 21:57:06 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 21:57:06 matthew-15-3567 canonical-livepatch[1039]: message repeated 2 times: [ failure when getting status: apply-failed]
Aug 20 21:57:33 matthew-15-3567 canonical-livepatch[1039]: Client.Check
Aug 20 21:57:33 matthew-15-3567 canonical-livepatch[1039]: Checking with livepatch service.
Aug 20 21:57:34 matthew-15-3567 canonical-livepatch[1039]: updating last-check
Aug 20 21:57:34 matthew-15-3567 canonical-livepatch[1039]: touched last check
Aug 20 21:57:34 matthew-15-3567 canonical-livepatch[1039]: No updates available at this time.
Aug 20 21:57:34 matthew-15-3567 canonical-livepatch[1039]: Module may have caused kernel crash! Not inserting module.
Aug 20 21:57:34 matthew-15-3567 canonical-livepatch[1039]: To override this warning, remove /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2
Aug 20 21:57:34 matthew-15-3567 canonical-livepatch[1039]: during refresh: cannot apply patches: lock file "/var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2" already exists
Aug 20 21:57:37 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 21:57:37 matthew-15-3567 canonical-livepatch[1039]: message repeated 2 times: [ failure when getting status: apply-failed]
Aug 20 21:59:42 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 21:59:43 matthew-15-3567 canonical-livepatch[1039]: message repeated 3 times: [ failure when getting status: apply-failed]
Aug 20 21:59:44 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 21:59:44 matthew-15-3567 canonical-livepatch[1039]: failure getting status before refresh: apply-failed
Aug 20 21:59:44 matthew-15-3567 canonical-livepatch[1039]: Client.Check
Aug 20 21:59:44 matthew-15-3567 canonical-livepatch[1039]: Checking with livepatch service.
Aug 20 21:59:45 matthew-15-3567 canonical-livepatch[1039]: updating last-check
Aug 20 21:59:45 matthew-15-3567 canonical-livepatch[1039]: touched last check
Aug 20 21:59:45 matthew-15-3567 canonical-livepatch[1039]: No updates available at this time.
Aug 20 21:59:45 matthew-15-3567 canonical-livepatch[1039]: Module may have caused kernel crash! Not inserting module.
Aug 20 21:59:45 matthew-15-3567 canonical-livepatch[1039]: To override this warning, remove /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2
Aug 20 21:59:45 matthew-15-3567 canonical-livepatch[1039]: during refresh: cannot apply patches: lock file "/var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2" already exists
Aug 20 21:59:45 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 21:59:45 matthew-15-3567 canonical-livepatch[1039]: failure getting status after refresh: apply-failed
Aug 20 21:59:48 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 21:59:48 matthew-15-3567 canonical-livepatch[1039]: message repeated 2 times: [ failure when getting status: apply-failed]
Aug 20 22:01:31 matthew-15-3567 canonical-livepatch[1039]: Client.Check
Aug 20 22:01:31 matthew-15-3567 canonical-livepatch[1039]: Checking with livepatch service.
Aug 20 22:01:31 matthew-15-3567 canonical-livepatch[1039]: updating last-check
Aug 20 22:01:31 matthew-15-3567 canonical-livepatch[1039]: touched last check
Aug 20 22:01:31 matthew-15-3567 canonical-livepatch[1039]: No updates available at this time.
Aug 20 22:01:31 matthew-15-3567 canonical-livepatch[1039]: Module may have caused kernel crash! Not inserting module.
Aug 20 22:01:31 matthew-15-3567 canonical-livepatch[1039]: To override this warning, remove /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2
Aug 20 22:01:31 matthew-15-3567 canonical-livepatch[1039]: during refresh: cannot apply patches: lock file "/var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2" already exists
Aug 20 22:01:33 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 22:01:34 matthew-15-3567 canonical-livepatch[1039]: message repeated 6 times: [ failure when getting status: apply-failed]
Aug 20 22:01:38 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 22:01:38 matthew-15-3567 canonical-livepatch[1039]: failure getting status before refresh: apply-failed
Aug 20 22:01:38 matthew-15-3567 canonical-livepatch[1039]: Client.Check
Aug 20 22:01:38 matthew-15-3567 canonical-livepatch[1039]: Checking with livepatch service.
Aug 20 22:01:39 matthew-15-3567 canonical-livepatch[1039]: updating last-check
Aug 20 22:01:39 matthew-15-3567 canonical-livepatch[1039]: touched last check
Aug 20 22:01:39 matthew-15-3567 canonical-livepatch[1039]: No updates available at this time.
Aug 20 22:01:39 matthew-15-3567 canonical-livepatch[1039]: Module may have caused kernel crash! Not inserting module.
Aug 20 22:01:39 matthew-15-3567 canonical-livepatch[1039]: To override this warning, remove /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2
Aug 20 22:01:39 matthew-15-3567 canonical-livepatch[1039]: during refresh: cannot apply patches: lock file "/var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2" already exists
Aug 20 22:01:39 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 22:01:39 matthew-15-3567 canonical-livepatch[1039]: failure getting status after refresh: apply-failed
Aug 20 22:01:41 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 22:01:41 matthew-15-3567 canonical-livepatch[1039]: message repeated 2 times: [ failure when getting status: apply-failed]
Aug 20 22:01:59 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 22:16:24 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 22:18:37 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 20 22:18:38 matthew-15-3567 canonical-livepatch[1039]: message repeated 3 times: [ failure when getting status: apply-failed]

```

sudo canonical-livepatch refresh

```
Before refresh:

kernel: 4.15.0-54.58-generic
fully-patched: false
version: "54.2"


After refresh:


kernel: 4.15.0-54.58-generic
fully-patched: false
version: "54.2"

```

---

### Post by matyd918 on 2019-08-20
I should add that I HAVE disabled and re enabled without it fixing the issue (have not rebooted)

---

### Post by deadflowr on 2019-08-21
I don't like this line
> Module may have caused kernel crash! Not inserting module.

Perhaps heed the advice in the next line
> To override this warning, remove /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_54_58_generic_54_54.2
Which in and of itself is an issue since the lock file should have been removed/cleared out, but it hasn't.
Try moving it (just rename it something else)
And see if livepatch can refresh properly.

If it still fails a reboot may be needed.
(Sometimes, even with livepatching, a reboot is inevitable)

---

### Post by matyd918 on 2019-08-21
Thank you for the reply. I have rebooted and that seemed to have fixed the issue... I have not done anything prior to rebooting which is peculiar..

another view of the syslog:

```
grep livepatch /var/log/syslogAug 21 18:58:28 matthew-15-3567 canonical-livepatch[1039]: failure when getting status: apply-failed
Aug 21 19:03:12 matthew-15-3567 canonical-livepatch[1039]: stopping client daemon
Aug 21 19:03:12 matthew-15-3567 canonical-livepatch[1039]: stopping service "mitigation loop"
Aug 21 19:03:12 matthew-15-3567 canonical-livepatch[1039]: service "mitigation loop" stopped
Aug 21 19:03:12 matthew-15-3567 canonical-livepatch[1039]: stopping service "socket servers"
Aug 21 19:03:12 matthew-15-3567 systemd[1]: Stopping Service for snap application canonical-livepatch.canonical-livepatchd...
Aug 21 19:04:33 matthew-15-3567 systemd[1]: Mounting Mount unit for canonical-livepatch, revision 81...
Aug 21 19:04:33 matthew-15-3567 systemd[1]: Mounting Mount unit for canonical-livepatch, revision 77...
Aug 21 19:04:33 matthew-15-3567 systemd[1]: Mounted Mount unit for canonical-livepatch, revision 77.
Aug 21 19:04:33 matthew-15-3567 systemd[1]: Mounted Mount unit for canonical-livepatch, revision 81.
Aug 21 19:04:46 matthew-15-3567 systemd[1]: Started Service for snap application canonical-livepatch.canonical-livepatchd.
Aug 21 19:04:55 matthew-15-3567 canonical-livepatch[1038]: starting client daemon version 9.4.1
Aug 21 19:04:55 matthew-15-3567 canonical-livepatch[1038]: starting svc "mitigation loop"
Aug 21 19:04:55 matthew-15-3567 canonical-livepatch[1038]: service "mitigation loop" started
Aug 21 19:04:55 matthew-15-3567 canonical-livepatch[1038]: starting svc "socket servers"
Aug 21 19:04:55 matthew-15-3567 canonical-livepatch[1038]: service "socket servers" started
Aug 21 19:04:55 matthew-15-3567 canonical-livepatch[1038]: starting svc "refresh loop"
Aug 21 19:04:55 matthew-15-3567 canonical-livepatch[1038]: service "refresh loop" started
Aug 21 19:04:55 matthew-15-3567 canonical-livepatch[1038]: client daemon started
Aug 21 19:04:55 matthew-15-3567 canonical-livepatch[1038]: Client.Check
Aug 21 19:04:57 matthew-15-3567 canonical-livepatch[1038]: Checking with livepatch service.
Aug 21 19:04:57 matthew-15-3567 canonical-livepatch[1038]: during refresh: multiple failures
Aug 21 19:04:57 matthew-15-3567 canonical-livepatch[1038]: during refresh: cannot check: cannot send status to server: cannot send request: Put https://livepatch.canonical.com/api/machine/caea93e0ffe24f6fa3baeeb897ac1fb4: dial tcp: lookup livepatch.canonical.com on 127.0.0.53:53: server misbehaving
Aug 21 19:04:57 matthew-15-3567 canonical-livepatch[1038]: during refresh: cannot apply patches: Payload does not match current kernel version.
Aug 21 19:05:27 matthew-15-3567 snapd[960]: storehelpers.go:436: cannot refresh: snap has no updates available: "canonical-livepatch", "core", "firefox", "onlyoffice-desktopeditors"
Aug 21 19:05:27 matthew-15-3567 canonical-livepatch[1038]: Client.Check
Aug 21 19:05:27 matthew-15-3567 canonical-livepatch[1038]: error in livepatch check state: check-failed
Aug 21 19:05:27 matthew-15-3567 canonical-livepatch[1038]: Checking with livepatch service.
Aug 21 19:05:29 matthew-15-3567 canonical-livepatch[1038]: updating last-check
Aug 21 19:05:29 matthew-15-3567 canonical-livepatch[1038]: touched last check
Aug 21 19:05:29 matthew-15-3567 canonical-livepatch[1038]: No updates available at this time.
Aug 21 19:05:29 matthew-15-3567 canonical-livepatch[1038]: No payload available.
Aug 21 19:07:23 matthew-15-3567 gnome-shell[2561]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.86/org/ayatana/NotificationItem/livepatch



```

---

### Post by ahmad11 on 2019-08-23
Hi everyone and thank you for showing how to solve this issue which applied to me too.
However, checking the status showed this without version:

```

Z580:~$ sudo canonical-livepatch status --verboseclient-version: 9.4.1
machine-id: a97046d18c674d098a74805253515c54
machine-token: d161df8544e146df87fc16d8ca56f4d0
architecture: x86_64
cpu-model: Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz
last-check: 2019-08-23T09:44:47+03:00
boot-time: 2019-08-23T09:39:58+03:00
uptime: 5m1s
status:
- kernel: 4.15.0-58.64-generic
  running: true
  livepatch:
    checkState: checked
    patchState: nothing-to-apply
    version: ""
    fixes: ""
```

:-k

---

### Post by deadflowr on 2019-08-23
> **ahmad11 said:**
> Hi everyone and thank you for showing how to solve this issue which applied to me too.
However, checking the status showed this without version:
<snip>


You have a brand new kernel so there is nothing to apply for it yet.
It's fully patched on it's own.

---

