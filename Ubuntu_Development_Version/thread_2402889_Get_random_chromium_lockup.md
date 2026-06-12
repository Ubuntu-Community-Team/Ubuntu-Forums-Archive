---
title: "Get random chromium lockup"
date: 2018-10-05
forum: Ubuntu Development Version
---

### Post by dino99 on 2018-10-05
Usually it happen with some live streaming (tv) and five/six opened tabs. Suddently sound is looping and the whole system is frozen (even cant use the desktop reset, i have to turn off the alim)

Glancing at log show:

```
oem@oem-desktop:~$ journalctl -b -1 | grep chromium
oct. 05 06:49:07 oem-desktop dbus-daemon[744]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service' requested by ':1.511' (uid=1000 pid=3720 comm="/usr/lib/chromium-browser/chromium-browser --enabl" label="unconfined")
oct. 05 06:49:07 oem-desktop chromium-browser.desktop[2212]: [3758:3758:1005/064907.283385:ERROR:sandbox_linux.cc(379)] InitializeSandbox() called with multiple threads in process gpu-process.
oct. 05 06:51:07 oem-desktop chromium-browser.desktop[2212]: [1:1:1005/065107.759835:ERROR:webthread_impl_for_utility_thread.cc(19)] Not implemented reached in virtual blink::ThreadScheduler *blink::scheduler::WebThreadImplForUtilityThread::Scheduler() const
oct. 05 11:50:36 oem-desktop chromium-browser.desktop[2212]: [1:1:1005/115036.085387:ERROR:webthread_impl_for_utility_thread.cc(19)] Not implemented reached in virtual blink::ThreadScheduler *blink::scheduler::WebThreadImplForUtilityThread::Scheduler() const
```

Seems to be that upstream report: [https://bugs.chromium.org/p/chromium/issues/detail?id=866138&desc=2](https://bugs.chromium.org/p/chromium/issues/detail?id=866138&desc=2)

---

### Post by dino99 on 2018-10-05
Upstream says: Will be fixed in version 70.
[https://bugs.chromium.org/p/chromium/issues/detail?id=873207](https://bugs.chromium.org/p/chromium/issues/detail?id=873207)

Hopes Ubuntu team will propose it very soon (FFe)  ;)

---

