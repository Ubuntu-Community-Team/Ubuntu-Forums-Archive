---
title: "[AppArmor] How to find out what is being ptrace'd?"
date: 2017-05-11
forum: Security
---

### Post by &amp;KyT$0P# on 2017-05-11
For a while I've been noticing AppArmor log entries like this one -
```
type=AVC msg=audit(xxxxxxxxxx:xxx): apparmor="AUDIT" operation="ptrace" profile="/usr/lib/virtualbox/VirtualBox" pid=xxxx comm="nspr-2" requested_mask="trace" peer="unconfined"
```
Notice the [FONT=Courier New]peer="unconfined"[/FONT] - I'm not really happy about that.  While I'm sure this event is normal activity, the "unconfined" part doesn't make my VirtualBox AppArmor profile look too secure.

What's odd about that log entry is that there is no file named "nspr-2" anywhere I can find.  So with the help of [this guide]("https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Security_Guide/sec-Understanding_Audit_Log_Files.html"), I did some digging to try and see what this mysterious "nspr-2" is -
```
$ sudo cat /var/log/audit/audit.log | grep --color=always nspr-2
(...snipped...)
type=SYSCALL msg=audit(xxxxxxxxxxxx:xxx): arch=c000003e syscall=89 success=yes (...snipped...) comm="nspr-2" exe="/usr/lib/virtualbox/VBoxSVC"
```
Okay, I thought, so I'll just create a AppArmor profile for VBoxSVC and then this is solved, right?  Nope, an AppArmor profile for VBoxSVC makes no difference.  Not in complain mode, nor in enforce mode.  Still only seeing [FONT=Courier New]peer="unconfined"[/FONT].

Then I tried to download the VirtualBox source code and search for ptrace, but that proved too complicated for me.

Right now I have this in my VirtualBox profile, but like I said this seems too broad for good security.
```
audit allow ptrace (trace),
```

How to find out what VirtualBox is ptracing, so that I can create an AppArmor profile for it, and thus restrict what VirtualBox can ptrace?

---

### Post by &amp;KyT$0P# on 2017-05-18
bump

---

### Post by &amp;KyT$0P# on 2017-05-22
bump

---

### Post by &amp;KyT$0P# on 2017-05-28
bump

---

### Post by &amp;KyT$0P# on 2017-06-06
bump

---

### Post by &amp;KyT$0P# on 2017-06-14
bump

---

### Post by &amp;KyT$0P# on 2017-06-24
bump

---

### Post by &amp;KyT$0P# on 2017-07-02
bump

---

### Post by &amp;KyT$0P# on 2017-07-24
bump

---

### Post by #&amp;thj^% on 2017-07-24
I've seen similar in lxc containers as such:
```
Jan 08 08:17:59 itchy kernel: audit: type=1400 audit(1452237479.028:1469): apparmor="DENIED" operation="ptrace" profile="lxc-container-default" pid=19748 comm="ps" requested_mask="trace" denied_mask="trace" peer="unconfined"
```
I just added this to /etc/apparmor.d/lxc/lxc-default (Now I know it's not the same as yours but maybe a clue for you to use)
```
ptrace peer=@{profile_name},
```
Then reload apparmor and restarted all containers afterwards.
I was using check_mk to find...but no longer running a sever.
Hope that gives you some insights/thoughts here.
If not just kindly disregard.
Oh I found the link that lead me to my above post: [https://penguindroppings.wordpress.com/2014/06/06/application-isolation-with-apparmor-part-iv/](https://penguindroppings.wordpress.com/2014/06/06/application-isolation-with-apparmor-part-iv/)

---

### Post by &amp;KyT$0P# on 2017-07-25
Thanks for the reply.  I had tried that, unfortunately it doesn't work.

---

### Post by &amp;KyT$0P# on 2017-10-13
bump

---

### Post by &amp;KyT$0P# on 2018-06-29
bump

I am now using 18.04 and still looking for an answer to this.

---

