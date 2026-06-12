---
title: "SSH &amp; keys + SUDO = problem"
date: 2014-06-19
forum: Security
---

### Post by jcllings on 2014-06-19
So what I want to do is something like this W/O a password:
```

ssh -t user@remotemachine sudo /usr/bin/killall synergyc

```

I have the following as the last line of my sudoers file on remotemachine:
```

user ALL=(ALL) NOPASSWD:/usr/bin/killall synergyc,/opt/scripts/restartSynergy.sh

```

Problem is that sudo still prompts me for a password. :-/
Note: if I ssh over there first and then execute it, it's not a problem. 

What am I screwing up?

---

### Post by jcllings on 2014-06-19
It works now that I've moved the sudo commands to inside the scripts. Inefficient, IMHO but maybe there's a security issue here?

---

### Post by CharlesA on 2014-06-19
What's the security issue?

---

