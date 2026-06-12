---
title: "AppArmor issue/bug while finding sshd"
date: 2013-08-29
forum: Server Platforms
---

### Post by kidl33t2 on 2013-08-29
Edit:  Title should read 'AppArmor issue/bug while containing sshd'

While running AppArmor with my sshd profile in complain mode, I suddenly found my status report filling up with thousands of lines of garbage.  I probably have something misconfigured, but after a couple of hours of Googling around I haven't made much progress.  

My /etc/init.d/apparmor status reports:

```

1014 profiles are in complain mode.
... (most are mundane, I am skipping them)
/usr/sbin/sshd//null-111
/usr/sbin/sshd//null-111//null-112
/usr/sbin/sshd//null-111//null-112//null-113
/usr/sbin/sshd//null-111//null-112//null-113//null-114
/usr/sbin/sshd//null-111//null-115
/usr/sbin/sshd//null-111//null-115//null-116
/usr/sbin/sshd//null-153
/usr/sbin/sshd//null-154
/usr/sbin/sshd//null-155
/usr/sbin/sshd//null-156
/usr/sbin/sshd//null-157
/usr/sbin/sshd//null-158
... (this is truncated list, all 1000 or so are similar)

22 processes are in complain mode.
...
/usr/sbin/sshd (7205) 
/usr/sbin/sshd//null-288//null-28c//null-2b9//null-2ba//null-2bd//null-2be//null-2ce//null-2cf//null-2d0 (11910) 
/usr/sbin/sshd//null-349 (12888) 
/usr/sbin/sshd//null-349 (12892) 
/usr/sbin/sshd//null-34d (12895) 
/usr/sbin/sshd//null-34d (12899) 
/usr/sbin/sshd//null-34d//null-351 (12900) 
/usr/sbin/sshd//null-34d//null-351//null-374 (12997) 
/usr/sbin/sshd//null-3b7 (13156) 
/usr/sbin/sshd//null-3b7 (13160) 
/usr/sbin/sshd//null-3b7//null-3bb (13161) 
/usr/sbin/sshd//null-3b7//null-3bb//null-3fd (13293) 
/usr/sbin/sshd//null-3b7//null-3bb//null-3fd//null-3fe (13294) 
/usr/sbin/sshd//null-3b7//null-3bb//null-3fd//null-3fe//null-3ff (13295) 
/usr/sbin/sshd//null-50//null-c2//null-c3//null-c6//null-c7//null-e3//null-e4//null-e8 (7308) 
/usr/sbin/sshd//null-50//null-c2//null-c3//null-c6//null-c7//null-e3//null-e4//null-e8 (7313) 
/usr/sbin/sshd//null-50//null-c2//null-c3//null-c6//null-c7//null-e3//null-e4//null-e8 (7314) 
/usr/sbin/sshd//null-50//null-c2//null-c3//null-c6//null-c7//null-e3//null-e4//null-e8 (7315) 
/usr/sbin/sshd//null-50//null-c2//null-c3//null-c6//null-c7//null-e3//null-e4//null-e8 (7316) 
/usr/sbin/sshd//null-50//null-c2//null-c3//null-c6//null-c7//null-e3//null-e4//null-e8 (7317) 



```

Running aa-logprof doesn't reveal any actions to be taken.  My profile for sshd looks like this:

```

#include <tunables/global>


/usr/sbin/sshd flags=(complain) {
  #include <abstractions/apache2-common>
  #include <abstractions/base>
  #include <abstractions/nameservice>


  capability kill,
  capability setgid,






  /dev/pts/1 rw,
  /dev/pts/3 rw,
  /etc/ssl/openssl.cnf r,
  /home/*/ r,
  /home/*/.bash_logout r,
  /proc/*/fd/ r,
  /proc/*/oom_score_adj w,
  /run/utmp rk,
  /usr/bin/clear_console rix,
  /usr/bin/sudo px,
  /usr/sbin/sshd mrix,


}

```

I think my profile needs something like 

/usr/sbin/sshd/null rw,

Any idea why I have so many profiles and processes being created?  I am open to any suggestions or if any further information is needed please ask. [CENTER][COLOR=#000000]:-k[/COLOR][/CENTER]

---

