---
title: "Server got &quot;hacked&quot;. Wish some help for cleanup."
date: 2009-02-08
forum: Server Platforms
---

### Post by Mamsaac on 2009-02-08
I'm still not sure if it was just a lamer (which is what I initially thought) or if there is more about it. SSH access was gained for the guest user, which had really weak password security, for it's privileges where small and I didn't think it mattered much.

The intruder seemed to have ran a Perl script downloaded from the Internet, which ran several processes of PSCAN2, a program that drained a lot of bandwidth and CPU.

I don't think it was a complete lamer, for he/she at least cleaned the bash history for the guest account. Only a single command was left, and whatever he ran, it was deleted but left running. It's similar to another case I found in this forum ([LINK]("http://ubuntuforums.org/showthread.php?t=253373")), for there was an "a" process that was spawning the PSCAN2, and in that other case the intruder wasn't careful enough to change the bash logs, and I assume something similar was done in my case.

I've checked auth.log and auth.log.0. I also checked last |grep ffff (to check ssh access to the accounts).

I've search at the auth logs, the only thing that bothers me is this line:

Feb 2 13:26:29 XXXXXXX-laptop polkit-grant-helper[23673]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 23641 [uid=1000] [auth=XXXXXXX]


Where XXXXXXX is the name of the root user. It bothers me because it's right before the following line:

XXXXXXXX-laptop usermod[23740]: change user `guest' password

Thing is, it really bothers me. There's a known bug which I'm not sure if it ever got fixed.

[http://www.juniper.net/security/auto...vuln28702.html](http://www.juniper.net/security/auto...vuln28702.html)

I've closed all access to server.

Weirdly, those two were on February 2nd, while all the SSH access where on Feb 7th and Feb 8th (Feb th was at 13 hours and Feb 8th was 11 hours later, one from India and the other from Kansas, apparently).

I would appreciate help =) I'm not very experienced with server security.

Thanks in advance for taking your time.

---

### Post by jimv on 2009-02-08
The rule of thumb is that when a machine gets compromised, there's no way of knowing exactly what could have been changed/added/removed, so you're best off formatting and reinstalling.  Backup any necessary config files/data first.

---

### Post by HermanAB on 2009-02-08
Usually, it is much quicker to re-install the system than to clean it up.

To protect against future hacking use proper passwords and add this rule to the end of /etc/rc.d/rc.local:
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT

Cheers,

Herman

---

### Post by Mamsaac on 2009-02-08
Thanks for the advices.

But I still really want to know what do the polkit messages in the auth.log mean. Any ideas?

---

### Post by Mamsaac on 2009-02-08
Please, those two lines are the only ones that are bothering me.

```
Feb  2 13:26:29 XXXXXXX-laptop polkit-grant-helper[23673]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 23641 [uid=1000] [auth=XXXXXXX]
Feb  2 13:26:45 XXXXXXX-laptop usermod[23740]: change user `guest' password
```

I've been googling, but I can't really find anything that seems worth it. I don't want to reinstall and get hacked as soon as it's up.

---

### Post by punx45 on 2009-02-08
could be some sort of rootkit tool.

same as the others said, once the system is compromised, no way to know what is lurking.   only way you can be certain is to do a clean install.   ive had to do it before too.   it sucks but its the only way to know.

when you reinstall, disable guest account.   or install from the server cd, im pretty sure that doesnt set up a guest account.   then install fail2ban or denyhosts.   they help to prevent brute force dictionary attacks.

and enforce strong passwords!

---

