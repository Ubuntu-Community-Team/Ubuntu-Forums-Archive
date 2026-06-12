---
title: "pam_limits on groups granted by pam_group"
date: 2011-08-12
forum: Security
---

### Post by ptitpoul on 2011-08-12
Hi,
It seems that the groups granted by pam_group don't work with the limits set to a group in /etc/security/limits.conf and applied by pam_limits.

In my case, I want LDAP users to benefit from limits granted to the audio group.

In particular, the JACK audio server adds real-time priority to audio group:
```
cat /etc/security/limits.d/audio.conf             
# Provided by the jackd package.
#
# Changes to this file will be preserved.
#
# If you want to enable/disable realtime permissions, run
#
#    dpkg-reconfigure -p high jackd

@audio   -  rtprio     95
@audio   -  memlock    unlimited
```

At gdm login, pam_group is configured to give audio membership to any user:
```
$ cat /etc/security/group.conf | grep gdm
gdm;*;*;Al0000-2400;fax,voice,cdrom,floppy,audio,video,plugdev,games,users,scanner,fuse

$ groups | sed s/.*audio.*/audio/
audio

```

However, the user don't get the limits from audio group:
```
$ ulimit -l -r
max locked memory       (kbytes, -l) 64
real-time priority              (-r) 0
```

To show that the problem is specific to groups given by pam_group, I applied the limits to a user, for example, "guillaume -  rtprio     95" and guillaume was given the right limit, that is real-time priority 95.

Is it a bug in pam_limits or a wanted limitation?

---

### Post by nicolasavru on 2011-10-28
Did you ever find a solution to this? I am currently experiencing the same issue.

---

### Post by ptitpoul on 2011-10-28
Unfortunately, I haven't received any response to the problem. I hoped to get an answer before reporting it as a bug. Feel free to report it, maybe people involved in pam will see it and will provide an answer.

---

