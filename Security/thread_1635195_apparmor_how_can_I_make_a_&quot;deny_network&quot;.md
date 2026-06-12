---
title: "apparmor: how can I make a &quot;deny network&quot; rule work?"
date: 2010-12-01
forum: Security
---

### Post by arrange on 2010-12-01
Hi all,

I'm working on an AA profile. When I use a "deny" rule like this```
deny /etc/hosts r,
```the application is denied read access to that file and this fact _is not logged_ by AA.

But when I use the rule with the "network inet" like this```
deny network inet6 stream,
```the application is denied the access but it _is_ logged.

Why does the deny rule behave differently in these two sample cases? This is a problem for me as AA is spamming the logs with all these DENIED messages. Thanks for any tips... :)

---

### Post by bodhi.zazen on 2010-12-01
If apparmor is NOT logging a denial it is a bug and should be reported on Launchpad.

See also: 

[https://wiki.ubuntu.com/DebuggingApparmor](https://wiki.ubuntu.com/DebuggingApparmor)

---

### Post by arrange on 2010-12-02
Thanks for replying, bodhi.zazen.

> **bodhi.zazen said:**
> If apparmor is NOT logging a denial it is a bug and should be reported on Launchpad.

See also: 

[https://wiki.ubuntu.com/DebuggingApparmor](https://wiki.ubuntu.com/DebuggingApparmor)

I'm sorry, but I don't understand your point. For example [this AA wiki page]("https://apparmor.wiki.kernel.org/index.php/AppArmor_Failures") states that "deny rules - In a profile any rule with the deny prefix will cause quieting of rejects matching the rule." As far as I understand, if I want a denial to be logged I should prepend it with the "audit" keyword like this```
audit deny /etc/hosts r,
```Otherwise, according to AA docs, it should not be logged. Am I missing something here?

---

### Post by bodhi.zazen on 2010-12-02
> **arrange said:**
> Thanks for replying, bodhi.zazen.



I'm sorry, but I don't understand your point. For example [this AA wiki page]("https://apparmor.wiki.kernel.org/index.php/AppArmor_Failures") states that "deny rules - In a profile any rule with the deny prefix will cause quieting of rejects matching the rule." As far as I understand, if I want a denial to be logged I should prepend it with the "audit" keyword like this```
audit deny /etc/hosts r,
```Otherwise, according to AA docs, it should not be logged. Am I missing something here?

Hard to tell from what you have posted.

Apparmor should log a denial by default, you do not need the audit keyword to enable logging.

See:

[http://webapp5.rrz.uni-hamburg.de/SuSe-Dokumentation/manual/sles-manuals_en/manual/sec.apparm.profiles.audit.html](http://webapp5.rrz.uni-hamburg.de/SuSe-Dokumentation/manual/sles-manuals_en/manual/sec.apparm.profiles.audit.html)

When you use the rule "audit" in a profile, the denial is "tagged" with the work audit.

You can then fine these denials (in all the noise) with grep.

I suggest you follow the logs and watch what happens.

---

### Post by arrange on 2010-12-02
I followed your advice and created a profile for /usr/bin/head. Then I tested its behavior with *deny* vs *audit deny* rule. On my system (Ubuntu 10.10, AA 2.5.1-0ubuntu0.10.10.2) **deny** rules are not logged:```

root@mm:/etc/apparmor.d# jobs
[1]+  Running                 tail -f /var/log/syslog &

# `head' is set to deny reading the /tmp/file.txt file
################################
root@mm:/etc/apparmor.d# cat usr.bin.head 
#include <tunables/global>

/usr/bin/head {
  #include <abstractions/base>
  #include <abstractions/nameservice>

  deny /tmp/file.txt r,
}

root@mm:/etc/apparmor.d# aa-enforce usr.bin.head 
Setting /etc/apparmor.d/usr.bin.head to enforce mode.
Dec  2 21:11:52 mm kernel: [ 3303.662743] type=1400 audit(1291320712.890:236): apparmor="STATUS" operation="profile_replace" name="/usr/bin/head" pid=6972 comm="apparmor_parser"

# `head' can't read the file, and the fact is NOT logged
###################################
root@mm:/etc/apparmor.d# head /tmp/file.txt 
head: cannot open `/tmp/file.txt' for reading: Permission denied

# now we change "deny" &#8594; "audit deny"
########################################
root@mm:/etc/apparmor.d# sed -i 's:deny:audit\ deny:' usr.bin.head 
root@mm:/etc/apparmor.d# aa-enforce usr.bin.head 
Setting /etc/apparmor.d/usr.bin.head to enforce mode.
Dec  2 21:12:49 mm kernel: [ 3359.804737] type=1400 audit(1291320769.034:237): apparmor="STATUS" operation="profile_replace" name="/usr/bin/head" pid=7083 comm="apparmor_parser"

# `head' now can't read the file and it IS logged
###################################################
root@mm:/etc/apparmor.d# head /tmp/file.txt 
head: cannot open `/tmp/file.txt' for reading: Permission denied
Dec  2 21:12:56 mm kernel: [ 3367.241958] type=1400 audit(1291320776.470:238): apparmor="DENIED" operation="open" parent=3545 profile="/usr/bin/head" name="/tmp/file.txt" pid=7098 comm="head" requested_mask="r" denied_mask="r" fsuid=0 ouid=0

```Is it a bug? I hope not :)

---

### Post by bodhi.zazen on 2010-12-02
> **arrange said:**
> I followed your advice and created a profile for /usr/bin/head. Then I tested its behavior with *deny* vs *audit deny* rule. On my system (Ubuntu 10.10, AA 2.5.1-0ubuntu0.10.10.2) **deny** rules are not logged:```

root@mm:/etc/apparmor.d# jobs
[1]+  Running                 tail -f /var/log/syslog &

# `head' is set to deny reading the /tmp/file.txt file
################################
root@mm:/etc/apparmor.d# cat usr.bin.head 
#include <tunables/global>

/usr/bin/head {
  #include <abstractions/base>
  #include <abstractions/nameservice>

  deny /tmp/file.txt r,
}

root@mm:/etc/apparmor.d# aa-enforce usr.bin.head 
Setting /etc/apparmor.d/usr.bin.head to enforce mode.
Dec  2 21:11:52 mm kernel: [ 3303.662743] type=1400 audit(1291320712.890:236): apparmor="STATUS" operation="profile_replace" name="/usr/bin/head" pid=6972 comm="apparmor_parser"

# `head' can't read the file, and the fact is NOT logged
###################################
root@mm:/etc/apparmor.d# head /tmp/file.txt 
head: cannot open `/tmp/file.txt' for reading: Permission denied

# now we change "deny" &#8594; "audit deny"
########################################
root@mm:/etc/apparmor.d# sed -i 's:deny:audit\ deny:' usr.bin.head 
root@mm:/etc/apparmor.d# aa-enforce usr.bin.head 
Setting /etc/apparmor.d/usr.bin.head to enforce mode.
Dec  2 21:12:49 mm kernel: [ 3359.804737] type=1400 audit(1291320769.034:237): apparmor="STATUS" operation="profile_replace" name="/usr/bin/head" pid=7083 comm="apparmor_parser"

# `head' now can't read the file and it IS logged
###################################################
root@mm:/etc/apparmor.d# head /tmp/file.txt 
head: cannot open `/tmp/file.txt' for reading: Permission denied
Dec  2 21:12:56 mm kernel: [ 3367.241958] type=1400 audit(1291320776.470:238): apparmor="DENIED" operation="open" parent=3545 profile="/usr/bin/head" name="/tmp/file.txt" pid=7098 comm="head" requested_mask="r" denied_mask="r" fsuid=0 ouid=0

```Is it a bug? I hope not :)

See post #2

---

### Post by arrange on 2010-12-02
Do you happen to have a link which would confirm that, as you say, "Apparmor should log a denial by default, you do not need the audit keyword to enable logging."? I can't find any. The link you gave me ([http://webapp5.rrz.uni-hamburg.de/SuSe-Dokumentation/manual/sles-manuals_en/manual/sec.apparm.profiles.audit.html](http://webapp5.rrz.uni-hamburg.de/SuSe-Dokumentation/manual/sles-manuals_en/manual/sec.apparm.profiles.audit.html)) does not talk about this.

Thanks.

---

### Post by bodhi.zazen on 2010-12-02
No "deny" in the evince profile:

```
bodhi@maverick:~$ grep audit /etc/apparmor.d/usr.bin.evince 
bodhi@maverick:~$ 
```

But when I open evince and browse to / (root) - lots of logs

> Dec  2 21:27:21 maverick kernel: [  693.304375] type=1400 audit(1291350441.726:15): apparmor="DENIED" operation="open" parent=1820 profile="/usr/bin/evince" name="/boot/initrd.img-2.6.35-23-generic" pid=1843 comm="evince" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Dec  2 21:27:21 maverick kernel: [  693.313591] type=1400 audit(1291350441.734:16): apparmor="DENIED" operation="open" parent=1820 profile="/usr/bin/evince" name="/boot/vmlinuz-2.6.35-23-generic" pid=1843 comm="evince" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

IMO documentation on apparmor is not always what you might like.

See this page :

[https://apparmor.wiki.kernel.org/index.php/AppArmor_Failures#What_if_there_are_no_log_messages_but_there_should_be.3F](https://apparmor.wiki.kernel.org/index.php/AppArmor_Failures#What_if_there_are_no_log_messages_but_there_should_be.3F)

---

### Post by bodhi.zazen on 2010-12-02
> **bodhi.zazen said:**
> No "deny" in the evince profile:

```
bodhi@maverick:~$ grep audit /etc/apparmor.d/usr.bin.evince 
bodhi@maverick:~$ 
```

But when I open evince and browse to / (root) - lots of logs



IMO documentation on apparmor is not always what you might like.

See this page :

[https://apparmor.wiki.kernel.org/index.php/AppArmor_Failures#What_if_there_are_no_log_messages_but_there_should_be.3F](https://apparmor.wiki.kernel.org/index.php/AppArmor_Failures#What_if_there_are_no_log_messages_but_there_should_be.3F)

From that page:

> deny rules - In a profile any rule with the deny prefix will cause quieting of rejects matching the rule. 

audit rule - If the audit keyword is prefixed to any rule it forces that rule to output audit log messages for any event matching it. 

Audit mode - In audit mode AppArmor will output a log message for each event mediated by the AppArmor module whether it is allowed or rejected

---

### Post by arrange on 2010-12-03
I'm afraid we are talking about two different things...

In your example```
Dec 2 21:27:21 maverick kernel: [ 693.304375] type=1400 audit(1291350441.726:15): apparmor="DENIED" operation="open" parent=1820 profile="/usr/bin/evince" name="/boot/initrd.img-2.6.35-23-generic" pid=1843 comm="evince" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```

AA denied access to */boot/initrd.img-2.6.35-23-generic* because you _explicitly_ did not allow the application to access that file in its AA profile. This is of course logged.

But what I'm talking about is this: if I add this line to *usr.bin.evince*```
deny /boot/initrd.img-2.6.35-23-generic r,
```and then attempt to open the initrd file using *evince*, the access will be denied AND it will not be logged. BTW the quote you gave ("deny rules - In a profile any rule with the deny prefix will cause quieting of rejects matching the rule. ") IMO confirms this.

My original question was: can this behavior be applied to the **network** rule as well?

---

### Post by bodhi.zazen on 2010-12-03
> **arrange said:**
> I'm afraid we are talking about two different things...

In your example```
Dec 2 21:27:21 maverick kernel: [ 693.304375] type=1400 audit(1291350441.726:15): apparmor="DENIED" operation="open" parent=1820 profile="/usr/bin/evince" name="/boot/initrd.img-2.6.35-23-generic" pid=1843 comm="evince" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```

AA denied access to */boot/initrd.img-2.6.35-23-generic* because you _explicitly_ did not allow the application to access that file in its AA profile. This is of course logged.

But what I'm talking about is this: if I add this line to *usr.bin.evince*```
deny /boot/initrd.img-2.6.35-23-generic r,
```and then attempt to open the initrd file using *evince*, the access will be denied AND it will not be logged. BTW the quote you gave ("deny rules - In a profile any rule with the deny prefix will cause quieting of rejects matching the rule. ") IMO confirms this.

My original question was: can this behavior be applied to the **network** rule as well?

It should work yes, and if it does not, please file a bug report, lol.

---

### Post by register88 on 2013-04-02
Yes, I'm new to ubuntu and apparmor, I have same problem now.

I added "deny network inet6", but the aa-notify still popup the message to tell me, firefox try to "create inet6 stream".
the deny keywork look like not work on network's rule.

anyone know that?
any workaround?

thank you.

---

### Post by oldos2er on 2013-04-02
If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

---

