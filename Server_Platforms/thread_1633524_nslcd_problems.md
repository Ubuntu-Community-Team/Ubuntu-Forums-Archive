---
title: "nslcd problems"
date: 2010-11-29
forum: Server Platforms
---

### Post by Markus Zimmermann on 2010-11-29
Hi,

we run a kubuntu lucid system as a LTSP terminal server with 7 thin clients. The ltsp-server is in subnet 172.16.16.0/20.

The user authentication is organized via ldap. The ldap-server is in another subnet (172.16.32.0/20).

I have now trouble with authentication. After several hours a

id $USER

leads to no result. After restarting the nslcd-daemon on the ltsp-server authentication works immediately as expected.

Any hints?

Thank you in advance, Markus

---

### Post by terencekent on 2011-06-01
(This post is clearly too late - 8 months later. Hopefully it will help the next person.)

The issue is caused by a bug in the nslcd package. The version that ships with 10.04 is 0.7.2 and a fix is not known to be in place until version 0.7.13 or later.

If you are running into this problem, there are a few possible fixes:

[LIST=1]
[*] Manually install nslcd 0.7.13 or later (Earlier versions may have fixed it, but this one is KNOWN to not have the issue). This is the best solution.


[*] Add a cronjob to regularly restart nslcd at some reasonable interval (say, 5 minutes). This is definitely a hack, but will work reliably. 


[*] Add an idle_timeout to your /etc/nslcd.conf of something really small (for me it was 1 second). If you also tune down bind_timelimit and timelimit to something small, this should square the issue away. (WARNING - this solution did not work in all cases it was tested in, and is only slightly less of a hack than #2)
[/LIST]

Here is the most complete thread I found on it so far:

[http://lists.arthurdejong.org/nss-pam-ldapd-users/2011/msg00082.html](http://lists.arthurdejong.org/nss-pam-ldapd-users/2011/msg00082.html)

---

