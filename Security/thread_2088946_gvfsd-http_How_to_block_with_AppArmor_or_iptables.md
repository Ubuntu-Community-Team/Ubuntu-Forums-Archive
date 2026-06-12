---
title: "gvfsd-http How to block with AppArmor or iptables?"
date: 2012-11-27
forum: Security
---

### Post by cryptotheslow on 2012-11-27
**note to Moderaters - this is not a dupe of my General Discussion thread - this is specifically about blocking the actions of this process, not what it does :P

I noticed this in my process recently list:
/usr/lib/gvfs/gvfsd-http --spawner :1.6 /org/gtk/gvfs/exec_spaw/2

It seems to make various outbound network requests. So far my searching has failed to educate me as to what it is up to so I want to block its connectivity.

Using either Apparmor or iptables is there a way to deny this process network access?

Thanks in advance :D

---

### Post by chadk5utc on 2012-11-27
Google gvfsd shows this and many others as for blocking services with iptables its very easy 
[http://askubuntu.com/questions/112318/strange-connections-by-gvfsd-http-spawner](http://askubuntu.com/questions/112318/strange-connections-by-gvfsd-http-spawner)

---

### Post by cryptotheslow on 2012-11-28
Thanks for googling for me, unsurprisingly I had already done that and read a great deal including the link you posted. Oddly the bug report link within the page you linked gives me this:
```

https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/571970

Secure Connection Failed
An error occurred during a connection to bugs.launchpad.net.
The OCSP server experienced an internal error.
(Error code: sec_error_ocsp_server_error)

The page you are trying to view cannot be shown because the authenticity of the received data could not be verified.
Please contact the web site owners to inform them of this problem. Alternatively, use the command found in the help menu to report this broken site.
```

Anyway, none of the information I found actually detailed what gvfsd-http does. But that wasn't the point of this thread - I was just asking how to block it.

---

### Post by chadk5utc on 2012-11-30
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

