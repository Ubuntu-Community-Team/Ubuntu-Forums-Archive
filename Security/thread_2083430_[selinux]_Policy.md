---
title: "[selinux] Policy"
date: 2012-11-12
forum: Security
---

### Post by MarcAndreson on 2012-11-12
Hi,

I created my own basic policy:

```
module mypolicy 1.0.0;

require {
    type user_t;
    role user_r;
    class file { getattr execute read open ioctl entrypoint };
    class process { transition sigkill sigstop signull signal getattr };
}

type mytype_t;
type mytype_exec_t;

allow mytype_t mytype_exec_t:file { entrypoint };

allow user_t mytype_t:process { transition sigkill sigstop signull signal getattr };
allow user_t mytype_t:file { getattr execute read open ioctl };

type_transition user_t mytype_exec_t:process mytype_t;

role user_r types mytype_t;
```


When I install it with semodule -i I get an error:

```
libsepol.check_assertion_helper: neverallow violated by allow user_t mytype_t:process { transition sigkill sigstop signull signal getattr };
libsemanage.semanage_expand_sandbox: Expand module failed
semodule:  Failed!
```

What am I doing wrong ? Which rule is preventing me from installing the above policy ?

---

### Post by unspawn on 2012-11-12
> **MarcAndreson said:**
> What am I doing wrong ? 
[You're doing something you just should not do.](http://selinuxproject.org/page/AVCRules#neverallow_Rule) BTW Ubuntu didn't choose SELinux as distro default but AppArmor, consequently the amount and quality of help offered elsewhere may be less limited.

---

