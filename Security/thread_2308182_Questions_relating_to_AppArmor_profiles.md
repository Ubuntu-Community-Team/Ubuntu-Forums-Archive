---
title: "Questions relating to AppArmor profiles"
date: 2015-12-31
forum: Security
---

### Post by james188 on 2015-12-31
Hello everyone, 

I'm currently in the process of creating a few AppArmor profiles. The process is relatively easy, I just need some help figuring out what should be allowed. Can someone please take a look at the profile below, and give me some suggestions?

```

# Last Modified: Thu Dec 31 17:00:02 2015
#include <tunables/global>

/usr/sbin/postfix flags=(complain) {
  #include <abstractions/apache2-common>
  #include <abstractions/base>
  #include <abstractions/nameservice>


  capability dac_override,

  /bin/dash r,
  /etc/mailname r,
  /etc/postfix/cacert.pem r,
  /etc/postfix/dynamicmaps.cf r,
  /etc/postfix/main.cf r,
  /etc/postfix/sasl_passwd r,
  /etc/postfix/sasl_passwd.db rk,
  /proc/sys/kernel/ngroups_max r,
  /usr/sbin/postfix mr,
  /var/spool/postfix/active/6617FD814F7 rwk,
  /var/spool/postfix/etc/hosts r,
  /var/spool/postfix/etc/resolv.conf r,
  /var/spool/postfix/pid/unix.smtp rwk,
  /var/tmp/ r,

}

```

Does this postfix profile look ok? And what are abstractions used for? And can someone please tell me what the "k" means at the end of this line:   /var/spool/postfix/active/6617FD814F7 rwk?

Thank you,
James

---

### Post by james188 on 2016-01-02
I did some more research and apparently the "k" means lock access. I'm not entirely sure what this means, can someone please explain further? 

According to this site: [http://linux.die.net/man/7/capabilities](http://linux.die.net/man/7/capabilities) 
[B]
CAP_DAC_OVERRIDE: [/B]Bypass file read, write, and execute permission checks. (DAC is an abbreviation of "discretionary access control".) 

This doesn't seem very secure to me. Can I remove this from the profile, and still have it function correctly?

** I now get this message when I run sudo aa-logprof:**

Reading log entries from /var/log/audit/audit.log.
Updating AppArmor profiles in /etc/apparmor.d.
Traceback (most recent call last):
  File "/usr/sbin/aa-logprof", line 54, in <module>
    apparmor.do_logprof_pass(logmark)
  File "/usr/lib/python3/dist-packages/apparmor/aa.py", line 2280, in do_logprof_pass
    log = log_reader.read_log(logmark)
  File "/usr/lib/python3/dist-packages/apparmor/logparser.py", line 353, in read_log
    self.add_event_to_tree(event)
  File "/usr/lib/python3/dist-packages/apparmor/logparser.py", line 261, in add_event_to_tree
    raise AppArmorException(_('Log contains unknown mode %s') % rmask)
apparmor.common.AppArmorException: 'Log contains unknown mode '

Does anyone have any idea why this is occurring? I ran "sudo aa-logprof" once already for the postfix profile, and this didn't occur.

Thank you,
James

---

### Post by james188 on 2016-01-03
The above message is due to a crash. It is a known bug, and has been fixed in the newest version. Now I just have to figure out how to install AppArmor from source.  I'm really surprised with the lack of replies, I guess very few people use AppArmor.

---

