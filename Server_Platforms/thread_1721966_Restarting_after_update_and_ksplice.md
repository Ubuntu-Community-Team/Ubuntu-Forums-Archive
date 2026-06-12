---
title: "Restarting after update and ksplice"
date: 2011-04-05
forum: Server Platforms
---

### Post by Kljuka on 2011-04-05
I'm wondering if it is always necessary after dist-upgrade (when new img gets installed) to restart server and start using new kernel? Which page tells me if there were security holes patched or just bugs? For example: what has been patched in 2.6.32-28-server in comparisson to 2.6.32-30-server (and are there any holes in 2.6.32-28-server)?

Are you, server administrators, using **ksplice** for ubuntu 10.04 LTS server? Is it safe for production environment? And can you install it just by:
```
apt-get install ksplice
```
(or do you need to make some account at their page?

Thank you for your help

---

### Post by Kljuka on 2011-04-22
I have found kernel changelog file in:
```
/usr/share/doc/linux-image-2.6.32-31-server/changelog.Debian.gz
```It has entries like:
```
linux (2.6.30-2.3) karmic; **urgency=low**

  [ Tim Gardner ]

  * [Config] Enabled CC_STACKPROTECTOR=y for all x86en
    - LP: #369152
  * SAUCE: Default to i915_modeset=0 if CONFIG_DRM_I915_KMS=y
  * [Config] CONFIG_DRM_I915_KMS=y
  * [Config] Set CONFIG_SECURITY_DEFAULT_MMAP_MIN_ADDR to appropriate ARCH
    minimums

  [ Upstream Kernel Changes ]

  * rebased to 2.6.30-rc4

 --  Tim Gardner <tim.gardner@canonical.com>  Thu, 30 Apr 2009 09:17:05 -0600

etc.

```So: does that mean that kernel version 2.6.30-2.3 only fixes some minor bugs (urgency=low) and that I needn't bother restarting unless there is some more urgent update of kernel?

---

### Post by CharlesA on 2011-04-22
You need to pay to use it on anything except for Ubuntu Desktop and Fedora.

See [here]("http://www.ksplice.com/pricing").

---

### Post by Kljuka on 2011-04-22
Yes I've tried evaluation version. But are all these restarts really necessary?

---

### Post by CharlesA on 2011-04-22
I always reboot into the new kernel, but that's just me. :)

If they are really necessary, or not, that would be up to you to decide by reading the change logs.

---

### Post by Kljuka on 2011-04-22
That's true. But these change logs are like some strange language :D
The only part that I understand is:
```
urgency=low
```
Which comforts me that I needn't update (actually restart) yet. Or am I missing something?

---

### Post by CharlesA on 2011-04-22
You can always check the security notices to see if anything was a security update. :)

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

---

