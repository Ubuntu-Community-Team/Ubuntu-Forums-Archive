---
title: "iptables lockout"
date: 2015-06-24
forum: Security
---

### Post by Drenriza on 2015-06-24
Currently i am working on setting up a Raspberry PI (Raspbian OS / Debian Wheezy) as my new firewall device,
and lets just say that i have locked myself out more than once so far in the project over the ssh connection.

So my question is.
Is their a script / package you can use that prompts or in some other way ask if the user is still present.
Which you need to respond to in some manner, or it after x amount of minutes execute the command
```
sudo iptables-restore < /path/to/rules.txt
```

So i dont loose the connection to the device and need to move a physical screen connection to it.

Thanks on advance.

---

### Post by Lars Noodén on 2015-06-24
You could use an [at](http://manpages.ubuntu.com/manpages/trusty/en/man1/at.1.html) job or [iptables-apply](http://manpages.ubuntu.com/manpages/trusty/en/man8/iptables-apply.8.html) to avoid losing the connection.  If you want the permissions looser than that, just turn off the firewall.  

```

sudo iptables-save > /tmp/good.iptables.rules
sudo sh -c "echo '/sbin/iptables-restore < /tmp/good.iptables.rules' | at now + 4min"

```

That gives you a few minutes to try things.  

Using [iptables-apply](http://manpages.ubuntu.com/manpages/trusty/en/man8/iptables-apply.8.html) is easy too.  

```

sudo iptables-apply /tmp/test.rules

```

See the manual page for all the options including adjusting the timeout.

---

