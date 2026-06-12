---
title: "Apache mod_fcgid"
date: 2012-08-16
forum: Server Platforms
---

### Post by dranick on 2012-08-16
Hello,

I was wondering if you could release mod_fcgid 2.3.7 for update as the current mod_fcgid 2.3.6 has a huge memory bug that is crashing the apache2 process.

For reference:

[https://issues.apache.org/bugzilla/show_bug.cgi?id=52282](https://issues.apache.org/bugzilla/show_bug.cgi?id=52282)

and

[https://issues.apache.org/bugzilla/show_bug.cgi?id=51749](https://issues.apache.org/bugzilla/show_bug.cgi?id=51749)

At the moment one can not upload files larger than 1GB using mod_fcgid.

Thank you,

Nick

---

### Post by dranick on 2012-08-19
Bump the thread as it got no replies.

---

### Post by sandyd on 2012-08-20
> **dranick said:**
> Hello,

I was wondering if you could release mod_fcgid 2.3.7 for update as the current mod_fcgid 2.3.6 has a huge memory bug that is crashing the apache2 process.

For reference:

[https://issues.apache.org/bugzilla/show_bug.cgi?id=52282](https://issues.apache.org/bugzilla/show_bug.cgi?id=52282)

and

[https://issues.apache.org/bugzilla/show_bug.cgi?id=51749](https://issues.apache.org/bugzilla/show_bug.cgi?id=51749)

At the moment one can not upload files larger than 1GB using mod_fcgid.

Thank you,

Nick
Please open a bug in [launchpad]("https://launchpad.net/ubuntu") for this request.

---

### Post by dranick on 2012-08-20
Thank you,

Bug reported:

[https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-fcgid/+bug/1038877](https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-fcgid/+bug/1038877)

---

