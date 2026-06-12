---
title: "Evolution not doing STARTTLS"
date: 2006-06-14
forum: Server Platforms
---

### Post by jsemczyk on 2006-06-14
Hi, I have a security concern, I am using Evolution as my IMAP Client and I just saw that it is not doing a TLS encrypted session (until now I thought it was).

I am doing IMAP TLS on port 143 . My server is a Courier-IMAP, I tryied with Thunderbird and everything is working as expected.

It seems like Evolution is making 2 connections for each server. For a non-TLS server both are unecrypted. If you look at this, Evolution is making the first one with a STARTTLS and not the second one.

```

* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA AUTH=CRAM-SHA1 IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2004 Double Precision, Inc.  See COPYING for distribution information.


B00000 CAPABILITY


* CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA AUTH=CRAM-SHA1 IDLE ACL ACL2=UNION STARTTLS

B00000 OK CAPABILITY completed


B00001 STARTTLS


B00001 OK Begin SSL/TLS negotiation now.


.4..d...........s..
......s....b.....c...o..XZ...fy~2r


```


```


* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA AUTH=CRAM-SHA1 IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2004 Double Precision, Inc.  See COPYING for distribution information.


B00000 CAPABILITY


* CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA AUTH=CRAM-SHA1 IDLE ACL ACL2=UNION STARTTLS

B00000 OK CAPABILITY completed


B00001 LOGIN jonathan_semczyk_telecomlille_net password


B00001 OK LOGIN Ok.



```

Has anyone experienced the same thing ?

Thanks,
Jonathan.

---

### Post by asimon on 2006-06-16
It looks like this is [bug 48850](https://launchpad.net/distros/ubuntu/+source/evolution/+bug/48850). It's already fixed upstream, see [Gnome Bug 339939](http://bugzilla.gnome.org/show_bug.cgi?id=339939). So far, Dapper's evolution doesn't include the fix, which hopefully will change soon.

---

