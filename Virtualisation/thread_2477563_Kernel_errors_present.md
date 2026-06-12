---
title: "Kernel errors present"
date: 2022-07-29
forum: Virtualisation
---

### Post by trevorwaatti on 2022-07-29
I have been getting Linux kernel errors recently after latest package and build updates on my Ubuntu Linux VM that I use as a file server. I am suspecting that the latest updates may have caused some issues.

Here are the specs:
Virual host: Vmware ESXi 7.0.3, 19193900
OS: Ubuntu Linux 20.04.4
Kernel and CPU:    Linux 5.4.0-122-generic on x86_64
Virtual memory:    7 MiB used / 1.99 GiB total
Real memory:    314.71 MiB used / 823.09 MiB cached / 1.93 GiB total
Processor information:    Intel(R) Xeon(R) CPU E5-2630 v2 @ 2.60GHz, 2 cores
Webmin version:    1.997
Authentic theme version:    19.97 
Local disk space:    52.1 GiB used / 13.5 GiB free / 65.6 GiB total
Running processes:    239

I had updated everything to the latest stable version including all packages, OS build, webmin, etc just last week. The only thing out of date is a webmin update package, currently at 1.997 and will need 1.998.

In the Logwatch email it calls them Kernel errors, and I haven't seen any logs of unexpected restarts or boot issues yet, but it could be some kind of kernel panic or kerneloop, I am not sure which:

 --------------------- Kernel Begin ------------------------

 WARNING:  Kernel Errors Present
    [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:38:crtc-0 ...:  1 Time(s)
    [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [PLANE:34:plane ...:  1 Time(s)

This is the errors from the logs:

Jul 27 09:21:10 (my server name) kernel: [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [PLANE:34:plane-0] flip_done timed out
Jul 27 09:21:00 (my server name) kernel: [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:38:crtc-0] flip_done timed out
Jul 26 13:00:42 (my server name) kernel: [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [PLANE:34:plane-0] flip_done timed out
Jul 26 13:00:32 (my server name) kernel: [drm:drm_atomic_helper_wait_for_dependencies [drm_kms_helper]] *ERROR* [CRTC:38:crtc-0] flip_done timed out

I haven't noticed any boot/restart or unexpected shutdowns on my linux vm

Has anyone seen anything similar and/or know what is causing the issue? Is this something I will need to fix right away (before it causes crashing)?

---

### Post by trevorwaatti on 2022-07-29
[COLOR=#333333][FONT=&quot] Is this defined as a "kernel panic" or "kerneloop" or just a kernel error?[/FONT][/COLOR]

---

### Post by QIII on 2022-07-29
Moved to Virtualisation for a better fit.

---

