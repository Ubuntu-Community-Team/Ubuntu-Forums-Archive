---
title: "ssh bruteforce ongoing despite fail2ban?"
date: 2017-09-03
forum: Security
---

### Post by veddox on 2017-09-03
Hello all,

I recently set up my first virtual private server, administrating it via SSH. Very soon I found that there were constant brute force attacks on the service with massed attempts to log in as root. Of course I had disabled root login, so I'm not overly concerned about one of those attacks succeeding, but I'm not wild about the situation anyway. So I installed fail2ban and told it to watch sshd.

Now I have the situation that fail2ban says it's working and regularly blocks new malicious IPs, yet my logs show me that the attacks continue anyway. Am I misunderstanding the logs or what's the matter here? Here are some excerpts:

```

*user*@*host*:~$ tail -n 200 /var/log/auth.log | grep "Failed password" | tail -n 5
Sep  3 18:38:22 *host* sshd[6073]: message repeated 4 times: [ Failed password for invalid user root from 222.186.51.138 port 4773 ssh2]
Sep  3 18:38:29 *host* sshd[6112]: Failed password for invalid user root from 222.186.51.138 port 2625 ssh2
Sep  3 18:39:01 *host* sshd[6175]: Failed password for invalid user root from 58.218.198.160 port 43121 ssh2
Sep  3 18:39:03 *host* sshd[6177]: Failed password for invalid user root from 58.218.198.160 port 59279 ssh2
Sep  3 18:39:03 *host* sshd[6175]: Failed password for invalid user root from 58.218.198.160 port 43121 ssh2
```

```

*user*@*host*:~$ sudo fail2ban-client status sshd
Status for the jail: sshd
|- Filter
|  |- Currently failed:    2
|  |- Total failed:    3175
|  `- File list:    /var/log/auth.log
`- Actions
   |- Currently banned:    2
   |- Total banned:    508
   `- Banned IP list:    58.218.198.160 222.186.51.138
```

Could anybody explain to me what's going on? Would be much appreciated :-)

---

### Post by Doug S on 2017-09-03
Do you need to increase your ban time? Make it very long, like a day.

---

### Post by veddox on 2017-09-03
Hm, I don't understand this. I had set the bantime to 86400 seconds (= 24h) in the [default] section of /etc/fail2ban/jail.local, yet ```
fail2ban-client get sshd bantime
``` returns 600. Even when I explicitly added the increased bantime to the [sshd] section and restarted the service, it still didn't change...

---

### Post by Habitual on 2017-09-03
Did you change the "filter =" directive the jail?

**Some manual tests** of the 2 sshd filters I know about, by default.
```

fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf
```
or
```
fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd-dddos.conf
```

should "hit" on the auth.log errors, if not
in terminal 
```
grep -i "Failed password" /etc/fail2ban/filter.d/* -Rl
```
You may be missing a failregex is all in either of those 2 sshd* files, or a custom one,  if used.

What version of f2b please?

---

### Post by veddox on 2017-09-05
No, I didn't change the filter. f2b is at version 0.9.3.

On closer inspection, I'm pretty sure fail2ban is not the problem. I just had a look at iptables:

```
*user*@*host*:~$ tail -n 200 /var/log/auth.log | grep "Failed password" | tail -n 3
Sep  5 10:45:15 helios sshd[21299]: Failed password for invalid user root from 58.218.198.160 port 64881 ssh2
Sep  5 10:45:17 helios sshd[21301]: Failed password for invalid user root from 58.218.198.160 port 32976 ssh2
Sep  5 10:45:17 helios sshd[21299]: Failed password for invalid user root from 58.218.198.160 port 64881 ssh2

*user*@*host*:~$ sudo fail2ban-client status sshd
Status for the jail: sshd
|- Filter
|  |- Currently failed:    1
|  |- Total failed:    2330
|  `- File list:    /var/log/auth.log
`- Actions
   |- Currently banned:    1
   |- Total banned:    345
   `- Banned IP list:    58.218.198.160

*user*@*host*:~$ sudo iptables -L f2b-sshd
Chain f2b-sshd (1 references)
target     prot opt source               destination         
REJECT     all  --  58.218.198.160       anywhere             reject-with icmp-port-unreachable
RETURN     all  --  anywhere             anywhere            
```

So obviously fail2ban picks up on the attempted logins and bans the offending IP via iptables. Nonetheless, the attacks continue...

---

### Post by Habitual on 2017-09-05
What do you think it is then?
Have you inspected the /etc/fail2ban/fail2ban.{log,log.1) files for clues?

What does 
```
fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf
```
produce?

---

### Post by Doug S on 2017-09-05
For context, show us your entire iptables rule set, with packet/byte counters. Do:
 ```
sudo iptables -v -x -n -L
```

---

### Post by Habitual on 2017-09-05
and the sshd jail contents please.

---

### Post by veddox on 2017-09-06
Hm, I should have thought about those log files earlier. Here's what I found:

```
*user*@*host*:~$ grep "WARNING" /var/log/fail2ban.log
2017-09-03 23:45:17,030 fail2ban.transmitter    [8485]: WARNING Command ['set', 'sshd', 'bantime', 'None'] has failed. Received ValueError("invalid literal for int() with base 10: 'None'",)
2017-09-03 23:46:16,295 fail2ban.transmitter    [8652]: WARNING Command ['set', 'sshd', 'bantime', 'None'] has failed. Received ValueError("invalid literal for int() with base 10: 'None'",)
```

So perhaps I had something to do with the bantime after all... I still failed to set the bantime properly via the config files (I suspect I am getting mixed up as to which file to put the directive in), but I did it manually with "sudo fail2ban-client set sshd bantime 86400" and it worked. One day later, the rate of attacks has been drastically reduced, down ~95% from what it was before. That's good enough for me ;-)

Thank you for your help!

---

### Post by Habitual on 2017-09-06
Warnings like that are common when incorrectly utilizing a fail2ban-client <options> from the c-line.
Glad it worked out, and OH YEAH,
f2b is python, so spaces vs evil tabs is a "thing". I chose spaces.
Align everything to the right side of "=" and it's all good.

---

