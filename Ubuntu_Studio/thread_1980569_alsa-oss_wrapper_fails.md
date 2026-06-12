---
title: "alsa-oss wrapper fails"
date: 2012-05-15
forum: Ubuntu Studio
---

### Post by ITPhoenix on 2012-05-15
I have this app that was written in c for use with OSS.  alsa-oss installed successfully from the Software Ceter, and the app attempts to start, but aborts.  Here is the output:
```
pocketsphinx_continuous : mixer.c:220: oss_mixer_open: Assertion 'fd >= 0' failed.
Aborted (core dumped)
```
I found this from Linux From Scratch, but the ld.so.conf.d folder is a little more complicated than that:
                    
> As with most libraries, there is no configuration to do, save             that the library directory, i.e., /opt/lib or /usr/local/lib should appear in /etc/ld.so.conf so that **ldd** can find the shared             libraries. After checking that this is the case, **/sbin/ldconfig** should be run             while logged in as root. 

**aoss** is a simple wrapper script which facilitates the use of                     the ALSA OSS compatibility library. It just sets the                     appropriate LD_PRELOAD path                     and then runs the command.Here is the contents of my  ld.so.conf.d:

       # libc default configuration
/usr/local/lib

# Multiarch support
/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu

/usr/lib/x86_64-linux-gnu/mesa  (inside the link to etc/alternatives/x86_64-linux-gnu_gl_conf)

Nothing has been done according to this how-to, out of abject fear.  If anyone could shed some light on this, it would be greatly appreciated.  Running 12.04 LTS updated to 5/13/12 with security and recommended updates including backports (the default setup).

---

