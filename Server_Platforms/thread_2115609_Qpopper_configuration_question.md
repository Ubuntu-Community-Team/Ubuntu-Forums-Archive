---
title: "Qpopper configuration question"
date: 2013-02-13
forum: Server Platforms
---

### Post by JKyleOKC on 2013-02-13
I've recently installed qpopper, via Synaptic, in my 10.04.4 LST system that runs Postfix as my local mail server. Now logwatch gives me the following report every morning:
```
 **Unmatched Entries**
    in.qpopper: PAM adding faulty module: /lib/security/pam_unix_acct.so: 119 Time(s)
    in.qpopper: PAM adding faulty module: /lib/security/pam_unix_auth.so: 119 Time(s)
    in.qpopper: PAM unable to dlopen(/lib/security/pam_unix_acct.so): /lib/security/pam_unix_acct.so: cannot open shared object file: No such file or directory: 119 Time(s)
    in.qpopper: PAM unable to dlopen(/lib/security/pam_unix_auth.so): /lib/security/pam_unix_auth.so: cannot open shared object file: No such file or directory: 119 Time(s)

```Obviously something is incomplete in my qpopper configuration, but I've not been able to pin down just what this something might be. The most recent of the 10 threads returned by searching all forums for "qpopper" dates from 2011 so is too old to use; anyway, none of the 10 seems relevant to my question. And the official qpopper guide is silent on the subject.

There's also another message about "bulletins" that I would like to shut off, but I'll stick with a single question at this point...

---

### Post by JKyleOKC on 2013-02-14
bump?

---

### Post by JKyleOKC on 2013-02-19
anyone else using qpopper?

---

### Post by fwoop on 2013-03-11
Try copying a PAM configuring for a service that works and using that as the Qpopper configuration.  Best to pick as similar a service as you can.

---

### Post by JKyleOKC on 2013-03-11
Any suggestions? I'm not all that familiar with PAM and the names in the /lib/security/pam* listing don't offer much clarity. There's one called /lib/security/pam_unix.so that might be applicable -- or might not!

---

### Post by JKyleOKC on 2013-04-08
Finally solved it, thanks to fwoop's suggestion. I checked the /etc/pam.d directory and found that several of the files had the same four "include" statements and nothing else, so I commented out the two bad lines in the qpopper file, and pasted in that same four include lines. No more error reports!

In searching, I find that the default file created by the repository version of qpopper still includes reference to those two files although they have not been included in the distribution for at least five years, and their use was deprecated for some 10 years before they were dropped! Surely we could do a better job of maintaining the packages in the official repositories!

---

