---
title: "invalid login attempts not refused using deny hosts and conf of denyhost not working"
date: 2010-10-28
forum: Security
---

### Post by tapas_mishra on 2010-10-28
I am using denyhosts on a server 
so in a config file
/etc/denyhosts.conf
the following value is set
> DENY_THRESHOLD_INVALID = 3

which as per their configuration file says
> DENY_THRESHOLD_INVALID: block each host after the number of failed login
# attempts has exceeded this value.  This value applies to invalid
# user login attempts (eg. non-existent user accounts)

but when I checked the log (I deleted previous entries and disabled
firewall for some time to test denyhosts thing)
and
got following logs
[http://pastebin.com/fyH3qJeR](http://pastebin.com/fyH3qJeR)
I see a last line
> refused connect from 125.46.63.134 (125.46.63.134)
but only after 10 attempts to try to login.
Now the question which is puzzling me is in denyhosts.conf I have set

> DENY_THRESHOLD_INVALID = 3

so after third attempt the script should have denied the IP in
question any request to connect.
Is this not the case.

---

### Post by talent03 on 2010-11-08
I ran into the same thing, except they attempted for an hour before denyhosts daemon blocked it. :-|

---

### Post by tapas_mishra on 2010-11-08
I found one more effective solution in this situation is to rate limit the IPTABLES.

[http://blog.bodhizazen.net/linux/prevent-dos-with-iptables/](http://blog.bodhizazen.net/linux/prevent-dos-with-iptables/)
[http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)
[http://www.linux-noob.com/forums/index.php?/topic/1829-ssh-rate-limit-per-ip-new-method/](http://www.linux-noob.com/forums/index.php?/topic/1829-ssh-rate-limit-per-ip-new-method/)
```

iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j DROP
iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent   --set

```
The above 2 rules will  work well and in case of 4th attempt from same IP the person will have to keep quite for 60 seconds.
So that way in one minute only 3 attempts from same IP will be allowed.This is one more defence to brute force SSH attacks.
But later on I see that denyhosts had blocked the SSH attempts I had tested by stopping above IPTABLES on my server so it at least did its job but may be not as effectively as I had expected.

---

