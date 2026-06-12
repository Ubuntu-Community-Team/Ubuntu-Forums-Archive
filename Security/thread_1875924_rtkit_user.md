---
title: "rtkit user"
date: 2011-11-05
forum: Security
---

### Post by Orcris on 2011-11-05
I was editing /etc/passwd to change my shell from BASH to ZSH, and I noticed that there was a user named rtkit. Is this normal? I know that rootkits are a type of malware, and that they're pretty dangerous, so should I be worried about this?

---

### Post by FuturePilot on 2011-11-05
First, don't change your shell by directly editing passwd. There are tools to do this the proper way. Just use chsh

```
chsh
```

Enter your password, then enter the path to your desired shell. (/bin/zsh)

Yes, rtkit is normal. It does not stand for rootkit. It's part of PulseAudio.

> RealtimeKit is a D-Bus system service that changes the
 scheduling policy of user processes/threads to SCHED_RR
 (i.e. realtime scheduling mode) on request. It is intended to
 be used as a secure mechanism to allow real-time scheduling to
 be used by normal user processes.

---

