---
title: "Look at my Rkhunter log please?"
date: 2010-07-02
forum: Security
---

### Post by Bluestars on 2010-07-02
This is my first time running rkhunter, and I am dual booting. The log said there were 0 suspect files and 0 possible rootkits, it did show some warnings however, and I have no idea what they mean.  Hope someone can help me determine if my systems ok. 

perrforming 'shared libraries' checks [02:28:37] Info: Starting test name 'shared_libs' [02:28:37] Checking for preloading variables                 [ None found ] [02:28:37] Info: Found library preload file: /etc/ld.so.preload [02:28:37] Checking for preloaded libraries 

[ Warning ] [02:28:37] Warning: Found preloaded shared library: libesets_pac.so [02:28:37] Info: Starting test name 'shared_libs_path' [02:28:37] Checking LD_LIBRARY_PATH variable                 [ Not found ] [02:28:37]    Checking if SSH root access is allowed          


[ Warning ] [02:29:53] Warning: The SSH and rkhunter configuration options should be the same: [02:29:53]          SSH configuration option 'PermitRootLogin': yes [02:29:53]          Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': 

no  4] Info: SCAN_MODE_DEV set to 'THOROUGH' [02:29:54]   Checking /dev for suspicious file types         [ Warning ] [02:29:54] Warning: Suspicious file types found in /dev: [02:29:54]          /dev/shm/pulse-shm-4169737988: data [02:29:54]          /dev/shm/pulse-shm-2430683490: data [02:29:54]          /dev/shm/pulse-shm-1261243917: data [02:29:54]          /dev/shm/pulse-shm-958406715: data [02:29:54]          /dev/shm/pulse-shm-872540557: data [02:29:54]          /dev/shm/pulse-shm-2430630559: data [02:29:54]          /dev/shm/ecryptfs-john-Private: ASCII text [02:29:54]          /dev/shm/pulse-shm-240927901: data [02:29:55]   Checking for hidden files and directories       [ Warning ] [02:29:55] Warning: Hidden directory found: /etc/.java [02:29:55] Warning: Hidden directory found: /dev/.udev [02:29:55] Warning: Hidden directory found: /dev/.initramfs [02:29:55] [02:29:55] 
Info: Test 'apps' disabled at users request.

---

### Post by sh1ny on 2010-07-02
Looks fine to me.

---

### Post by bodhi.zazen on 2010-07-02
> **Bluestars said:**
> This is my first time running rkhunter

It is poor netiquette to run a security tool and post on the forums to ask for assistance interpreting the output.

Please see the man page / rkhunter manual and try google first.

If, after doing your footwork, you still have a question, feel free to ask.

The reason for this advice is not RTFM, but only you can determine what is normal on your system, and what if anything you installed and modified.

These tools are not mindless tools, if you are unwilling to do the footwork, running them is useless.

---

