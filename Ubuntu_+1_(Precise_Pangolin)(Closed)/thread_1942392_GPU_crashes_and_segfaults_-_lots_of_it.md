---
title: "GPU crashes and segfaults - lots of it"
date: 2012-03-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry.k on 2012-03-17
Since i updated to precise, stuff keeps crashing. On bootup,I'm greeted b y a dialog box saying "System problems detected." It gets worse in a few minutes. everything starts crashing, including unity. everything blames the crashes as follows:

```
home-pc kernel: [ 4577.457135] unity-2d-shell[3422]: segfault at bb460911 ip 05b1a318 sp bfd76afc error 4 in lib<something like c or SDL>-2.15.<some number>.so[5aa0000+19e000]
```

It seems my i915 GPU is the problem. Although, oneric did not have any troubles and worked fine with unity 3d. In precise, I cant even run unity2d smoothly. In both I have the same xorg.conf, used to make X detect my intel brookdale. Just when the GPU crash occurs, the screen gets scrambled, and on becoming normal, everything seems to lag. windows wipe out and in, same goes for changing tabs in applications. Videos become unplayable, and games dont start. audio is still fine though. Here is the most relevent information i could get from the syslog

```
Mar 17 20:17:02 home-pc CRON[3228]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 17 20:34:37 home-pc kernel: [ 3192.400457] unity-2d-shell[1752]: segfault at 21 ip 008a9a25 sp bfd460a0 error 4 in libQtDeclarative.so.4.8.0[674000+377000]
Mar 17 20:34:43 home-pc gnome-session[1678]: WARNING: Application 'unity-2d-shell.desktop' killed by signal
Mar 17 20:49:48 home-pc pulseaudio[9537]: [pulseaudio] authkey.c: Failed to open cookie file '/etc/timidity/.pulse-cookie': No such file or directory
Mar 17 20:49:48 home-pc pulseaudio[9537]: [pulseaudio] authkey.c: Failed to load authorization key '/etc/timidity/.pulse-cookie': No such file or directory
Mar 17 20:49:48 home-pc pulseaudio[9537]: [pulseaudio] client-conf-x11.c: xcb_connection_has_error() returned true
Mar 17 20:49:48 home-pc pulseaudio[9537]: [autospawn] core-util.c: Home directory /etc/timidity not ours.
Mar 17 20:49:48 home-pc pulseaudio[9537]: [autospawn] lock-autospawn.c: Cannot access autospawn lock.
Mar 17 20:49:48 home-pc pulseaudio[9537]: [pulseaudio] main.c: Failed to acquire autospawn lock
Mar 17 20:56:33 home-pc kernel: [ 4508.652042] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Mar 17 20:56:34 home-pc kernel: [ 4508.652072] [drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 374030 at 374028, next 374031)
Mar 17 20:56:34 home-pc kernel: [ 4508.668067] render error detected, EIR: 0x00000010
Mar 17 20:56:34 home-pc kernel: [ 4508.668077] [drm:i915_report_and_clear_eir] *ERROR* EIR stuck: 0x00000010, masking
Mar 17 20:56:34 home-pc kernel: [ 4508.668088] render error detected, EIR: 0x00000010
Mar 17 20:56:34 home-pc udevd[13212]: failed to execute '/usr/share/apport/apport-gpu-error-intel.py' '/usr/share/apport/apport-gpu-error-intel.py': Permission denied
Mar 17 20:56:34 home-pc udevd[13213]: failed to execute '/usr/share/apport/apport-gpu-error-intel.py' '/usr/share/apport/apport-gpu-error-intel.py': Permission denied
Mar 17 20:56:34 home-pc udevd[13217]: failed to execute '/usr/share/apport/apport-gpu-error-intel.py' '/usr/share/apport/apport-gpu-error-intel.py': Permission denied
Mar 17 20:56:34 home-pc udevd[13218]: failed to execute '/usr/share/apport/apport-gpu-error-intel.py' '/usr/share/apport/apport-gpu-error-intel.py': Permission denied
Mar 17 20:56:35 home-pc udevd[13221]: failed to execute '/usr/share/apport/apport-gpu-error-intel.py' '/usr/share/apport/apport-gpu-error-intel.py': Permission denied
Mar 17 20:56:35 home-pc kernel: [ 4510.480039] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Mar 17 20:56:35 home-pc kernel: [ 4510.480076] [drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 374032 at 374028, next 374033)
Mar 17 20:56:35 home-pc kernel: [ 4510.480207] [drm:i915_reset] *ERROR* GPU hanging too fast, declaring wedged!
Mar 17 20:56:35 home-pc kernel: [ 4510.480212] [drm:i915_reset] *ERROR* Failed to reset chip.
Mar 17 20:56:35 home-pc udevd[13222]: failed to execute '/usr/share/apport/apport-gpu-error-intel.py' '/usr/share/apport/apport-gpu-error-intel.py': Permission denied
Mar 17 20:57:27 home-pc AptDaemon.PackageKit: INFO: Get updates()
Mar 17 20:57:37 home-pc AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/61c43a8e1764499cbf635ba325e38f05
Mar 17 20:57:42 home-pc kernel: [ 4577.457135] unity-2d-shell[3422]: segfault at bb460911 ip 05b1a318 sp bfd76afc error 4 in libc-2.15.so[5aa0000+19e000]
Mar 17 20:57:46 home-pc gnome-session[1678]: WARNING: Application 'unity-2d-shell.desktop' killed by signal
```

I sure hope i wont have to downgrade. Not after the bandwidth i spend on keeping precise up-to-date. Any help appreciated.

---

### Post by Harry.k on 2012-03-17
Bump

---

### Post by neu5eeCh on 2012-03-17
Did you read [here]("https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Alpha2")?

> Sandy Bridge power regression still present (30% more power at idle) ([818830]("https://bugs.launchpad.net/bugs/818830"))  -- Platforms affected by this power consumption regression are sixth  generation i915 GPUs having the following PCI identifiers: 8086:0102,  8086:0112, 8086:0122, 8086:0106, 8086:0116, 8086:0126, 8086:010A.  A  nice summary of the issue written by Eugeni Dodonov of Intel can be read  [here]("http://phoronix.com/forums/showthread.php?68199-Intel-Wants-YOUR-Linux-Questions-Feedback&p=246785#post246785").   **RC6 will remain disabled by default for 12.04 due to the potential  issues such as hangs or graphics corruption.** If you do choose to enable  RC6 (ie boot with i915.i915_enable_rc6=1) please let us know if you  experience any problems. 

---

### Post by dcstar on 2012-03-17
> **Harry.k said:**
> Since i updated to precise, stuff keeps crashing. On bootup,I'm greeted b y a dialog box saying "System problems detected." It gets worse in a few minutes. everything starts crashing, including unity. everything blames the crashes as follows:
...........
I sure hope i wont have to downgrade. Not after the bandwidth i spend on keeping precise up-to-date. Any help appreciated.

This is a unfortunate outcome of using pre-release software that is still in the process of having issues like this sorted out.

This version is obviously not yet ready for your system.

---

### Post by Harry.k on 2012-03-18
Thanks guys. Appearantly, my choice to live on the edge was a dumb one. Although, ive learned much more about linux's internal organs because of it.

---

### Post by Harry.k on 2012-03-18
Is there any way to downgrade to oneric without loosing all the stuff i installed, like 0.a.d and tuxguitar?

---

### Post by cariboo on 2012-03-18
> **Harry.k said:**
> Is there any way to downgrade to oneric without loosing all the stuff i installed, like 0.a.d and tuxguitar?

Unfortunately, there isn't a way to revert to a previous version, without doing a complete re-install.

There are couple of ways of making the re-install a little less painless.

Give [oneconf]("https://wiki.ubuntu.com/OneConf") a try. I haven't tried it, except to create the list and add it to Ubuntu One.

The method I use on occasion can be found in this post:

[http://ubuntuforums.org/showpost.php?p=1521615&postcount=1](http://ubuntuforums.org/showpost.php?p=1521615&postcount=1)

---

### Post by Harry.k on 2012-03-22
I just got an ubuntu 11.10 iso along with a magazine. Somehow, it has an upgrade option to 'upgrade' from precise. It says the home folder and packages will be kept if possible. Is this a good idea?

---

### Post by cariboo on 2012-03-23
If I remember correctly, the upgrade option from the Live CD does an in place install, it deletes everything, but what's in /home, so you may be OK, I'd just bite the bullet, and do a fresh install, including /home, as there may be some residual configuration files that won't work well with 11.10.

---

### Post by Harry.k on 2012-03-23
Well, i bit the bullet and did a fresh install. The segfaults have reduced, but not gone. When i launch caster, it starts off fine, but crashes at the part where 3d graphics starts, with error 0 in i915_dri.so. If anyone knows what that means, please enlighten me.

 Xorg has trouble to. Occasionally, screens start tearing when being dragged. It gets fixed when i restart x through alt.prtsc.k. Perhaps its time this thread is moved to main support categories.

---

### Post by Harry.k on 2012-03-25
Still looking for any info on i915_dri.so 
bump

---

### Post by williammanda on 2012-03-25
I too have noticed alot more kernel panic errors within the last couple of updates. It was once every week, today I have had three so far. I'm have a sandy bridge setup.

---

### Post by Harry.k on 2012-03-27
Strangely, this happens on the siny new sandybridge and my jurasic era pentium 4.
I still am looking for any information about i915_dri.so. I assume that thing is the graphics chipset's driver. It would be much appreciated if anyone could shed some light on it.

---

### Post by Harry.k on 2012-03-30
Bump

---

