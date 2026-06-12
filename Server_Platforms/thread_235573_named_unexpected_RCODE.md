---
title: "named unexpected RCODE"
date: 2006-08-13
forum: Server Platforms
---

### Post by lvanderree on 2006-08-13
Dear all,

Since some days I'm having a problem with my named server.

Logcheck constantly mails me with the following message:

```

named[5418]: unexpected RCODE (REFUSED) resolving 'ubuntu-forums.com/NS/IN': 66.117.40.198#53

```

My server is setup as a router, and I think this message started appearing after a workstation visited the ubuntu-forums pages (like I'm doing now).

I searched on the internet, but couldn't find an answer anywhere of how to solve this, or what this means. So if someone knows, I would greatly appreciate it to let me know.

I could ofcourse remove (and purge) my bind installation (which I think is the source of this) and reinstall it, which would probably solve this, but I don't think this should be the way to do this...

Thanks in advance!

---

### Post by lvanderree on 2006-08-15
I now tried to remove --purge and (re)install the bind9 application, but I still get this same error every hour.

Isn't there anyone here who knows a little more about what this error is, and what I can try to do about it?

I can't find an answer using google either.

Thanks in advance

---

### Post by lvanderree on 2006-09-17
I still don't know what this error is all about, And I took some time to find out how to change the regular expression in logcheck to ignore it in the future, because it apparantly isn't that important, but for some reason I can't figure out how to change it correctly either.

The line to change is:

```

^\w{3} [ :0-9]{11} [._[:alnum:]-]+ named\[[0-9]+\]: unexpected RCODE \((REFUSED|SERVFAIL)\) resolving '[^[:space:]]+': [.[:digit:]]+#[0-9]+$

```

And I first thought the following line would fix it, but unfortunately **IT DOES NOT!**

```

^\w{3} [ :0-9]{11} [._[:alnum:]-]+ named\[[0-9]+\]: unexpected RCODE \((REFUSED|SERVFAIL)\) resolving '[^ [\t\n\r\f\v]]+': [.[0-9]]+#[0-9]+$

```

The only thing I really changed was:
changing 
[^[:space:]]+
to 
[^[ \t\n\r\f\v]]+

which is just rewriting [:space:]
and then move the space from within the brackets to outside the brackets:
[^ [\t\n\r\f\v]]


I think it's really strange why errors keep on appearing

---

### Post by orange on 2008-01-09
> **lvanderree said:**
> Dear all,

Since some days I'm having a problem with my named server.

Logcheck constantly mails me with the following message:

[code]
named[5418]: unexpected RCODE (REFUSED) resolving 'ubuntu-forums.com/NS/IN': 66.117.40.198#53
<SNIP>
I could ofcourse remove (and purge) my bind installation (which I think is the source of this) and reinstall it, which would probably solve this, but I don't think this should be the way to do this...

Thanks in advance!

Over a year in replying :(

Basically, your server is probably set (in /etc/resolv.conf) to use 66.117.40.198 as a resolving nameserver. However 66.117.40.198 is not allowing your server to use it as a resolver - so - you should either contact the admin of 66.117.40.198 and ask them to allow your server to use it as a resolver or use another resolver.

Hopefully this helps others than run into this problem.

---

