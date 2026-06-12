---
title: "Unable to see (apparmor) audit.log in messages files."
date: 2011-10-15
forum: Security
---

### Post by newhere_m on 2011-10-15
If I use the following commands, should I expect to see the audit.log corresponding to apparmor in the system log viewer (messages)?
```

sudo aa-audit /etc/apparmor.d/usr.bin.firefox
sudo apparmor_parser -r /etc/apparmor.d/usr.bin.firefox

```I do not see any and that is my problem. Someone hinted that "audit" file is to be installed for this to happen but I have no idea how to install that. Can anybody please advise?

---

### Post by bodhi.zazen on 2011-10-15
Neither of those commands does what you think it does.

The first command audits the profile and the second reloads it. Neither show you (display) the logs.

I suggest you read the apparmor sticky or [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

---

### Post by newhere_m on 2011-10-15
I wrote the second command precisely to mean that the firefox profile would have to be reloaded (not as an effort to view log messages directly, but as an intermediate step). 
Now as far as I understand: when a profile is in audit mode, security policy will be enforced and apparmor will give a log-message for each action taken by apparmor (permit/deny). The messages are to be found in these files:
```

/var/log/kern.log
/var/log/messages
/var/log/audit/audit.log

```The third is possible if "audit" is installed (this remains my doubt). Finally one can check using grep command, messages with "allowed"/"denied" in those files. Perhaps "sudo aa-logprof" will also do. However this last option also updates profile whose implication is not clear to me. Typical response:
```

Reading log entries from /var/log/messages.
Updating AppArmor profiles in /etc/apparmor.d.

```

---

### Post by bodhi.zazen on 2011-10-15
I am not sure I am understanding your question.

You can follow your logs with tail

```
tail -F /var/log/messages
```

aa-logprof reads the logs, reviews any denials, and prompts you for any changes you might wish to make to the profile.

See if this bolg help you: [http://blog.bodhizazen.net/linux/apparmor-privoxy-profile/](http://blog.bodhizazen.net/linux/apparmor-privoxy-profile/)

---

