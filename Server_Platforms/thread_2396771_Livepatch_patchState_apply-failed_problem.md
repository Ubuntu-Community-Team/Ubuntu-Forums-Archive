---
title: "Livepatch patchState: apply-failed problem"
date: 2018-07-20
forum: Server Platforms
---

### Post by cross85 on 2018-07-20
Hi, I have a problem applying livepatches.
I just checked 'canonical-livepatch status' and I get that the patches had failed the installation:


```
client-version: 8.0.2
architecture: x86_64
cpu-model: Intel(R) Xeon(R) Gold 6126 CPU @ 2.60GHz
last-check: 2018-07-20T11:23:24.91521006-04:00
boot-time: 2018-07-20T11:00:51-04:00
uptime: 37m40s
status:
- kernel: 4.15.0-23.25-generic
  running: true
  livepatch:
    checkState: checked
    patchState: apply-failed
    version: "40.7"
    fixes: |-
      * CVE-2018-1092
      * CVE-2018-7755
      * CVE-2018-8087

```
After that I checked the system log and I've got this:


```
canonical-livepatch[2109]: No updates available at this time.
canonical-livepatch[2109]: System contains non-livepatch tainted modules.
canonical-livepatch[2109]: Module may have caused kernel crash! Not inserting module.
canonical-livepatch[2109]: To override this warning remove: /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_23_25_generic_40
canonical-livepatch[2109]: during refresh: cannot apply patches: lock file exists: /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_23_25_generic_40_40.7
canonical-livepatch[2109]: failure when getting status: apply-failed
canonical-livepatch[2109]: failure getting status after refresh: apply-failed

```

I haven't found an answer yet. Does anyone have the same problem or knows how to solve this?
or should I just delete /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_23_25_generic_40_40.7?

---

### Post by cross85 on 2018-07-30
Any idea?

---

### Post by Frogs Hair on 2018-07-30
I just received intel and amd microcode and other security updates if that's what you curious about.

---

### Post by barroncm on 2018-07-30
I couldnt get live patch to work at all.

---

