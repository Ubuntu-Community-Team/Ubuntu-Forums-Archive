---
title: "Denyhosts and Custom Regex"
date: 2008-11-08
forum: Security
---

### Post by anthro398 on 2008-11-08
I'm running SSH on both port 22 and port 80. Denyhosts works fine blocking multiple login attempts on port 22. I've written a custom regular expression to add to hosts.deny addresses that visit port 80 more than once. It doesn't work though.

An example of the target string in /var/log/auth.log:
```

Nov  5 20:52:06 server sshd[26186]: Bad protocol version identification 'GET / HTTP/1.0' from 999.999.999.999

```

The custom regex added to /etc/denyhosts.conf:
```

USERDEF_FAILED_ENTRY_REGEX=sshd.*Bad protocol version identification.* from (::ffff:)?(?P<host>\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})

```
The target string is matched by SSHD_FORMAT_REGEX, so the user defined regex should be applied. I've verified the matches in Kodos.

Any idea what I'm doing wrong?


Additional information:
It would not be useful to point out the following as a potential solution: iptables, specifying allowed users in sshd_config, specifying allowed hosts in hosts.allow, SSH key authentication, using a less obvious port, etc.  I asked about denyhosts because I'd like to use it.  If you don't think you know the answer to question- how to use denyhosts to match the log string above, your answer won't be helpful.

Thanks.

---

### Post by jdong on 2008-11-08
> **anthro398 said:**
> 
Any idea what I'm doing wrong?


Please do not re-post after your thread has been closed.


[http://ubuntuforums.org/showthread.php?t=973641](http://ubuntuforums.org/showthread.php?t=973641)

---

