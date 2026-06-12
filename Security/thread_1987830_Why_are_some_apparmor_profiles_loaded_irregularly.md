---
title: "Why are some apparmor profiles loaded irregularly?"
date: 2012-05-26
forum: Security
---

### Post by arroy_0209 on 2012-05-26
I am using ubuntu 10.04.
I have apparmor profile (the one provided by ubuntu) for firefox in enforce mode. After logging into my account I check the messages part of the system log viewer. There I notice that some audit messages related to "profile load" are shown each time I log in, e.g.,
```

....kernel: [    4.251000] type=2313 audit(4238345152.069:1):  operation="profile_replace" pid=624 name="/sbin/dhclient3"

```There are some profiles, to be precise, dhclient3, nm-dhcp-client.action and dhclient-script which are first loaded and then replaced, and the profile on Xsession is loaded each time. It is not clear to me what is meant by "profile replace" in the messages. Only rarely I note that after I log in, the following profiles are loaded and reported in the messages-log:
```

/usr/lib/firefox/firefox{,*[^s][^h]}
/usr/lib/firefox/firefox{,*[^s][^h]}//firefox_java,
/usr/lib/firefox/firefox{,*[^s][^h]}//firefox_openjdk,
/usr/bin/evince-previewer

```
My doubt is why are the firefox profiles not loaded (or may be not reported in the messages) each time I log in? Moreover, on terminal, if I use the command, sudo aa-status, I get the response that:
```

apparmor module is loaded.
13 profiles are loaded.
13 profiles are in enforce mode.

``` and these include the firefox profiles (even if these are not reported to be loaded in messages-log). What do all these mean?

---

