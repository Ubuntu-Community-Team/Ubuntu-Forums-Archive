---
title: "How to determine if certain security patches are in Ubuntu packages?"
date: 2007-09-14
forum: Server Platforms
---

### Post by christian.convey on 2007-09-14
I need to ensure that some Linux systems in my care are not susceptible to certain identified vulnerabilities.

For example:
[http://www.kb.cert.org/vuls/id/927905](http://www.kb.cert.org/vuls/id/927905)

A solution is given here:
   [http://www.isc.org/index.pl?/sw/bind/bind8-eol.php](http://www.isc.org/index.pl?/sw/bind/bind8-eol.php)

but I don't know how to determine whether or not Ubuntu 7.04's version bind9 still has this vulnerability or not.

Does anyone know how to determine, for this package or, even better, an arbitrary package, whether or not a particular vulnerability has been addressed in the latest version to hit the repositories?

Thanks,
Christian

---

### Post by wolfger on 2007-09-14
From the cert page:
> The more definitive solution is to upgrade to BIND 9
So look at the repository and see what version of bind is in use, compare that to the vulnerability notice. Only other way I know of to be sure, is to try to exploit the vulnerability. ;-)

---

### Post by cdenley on 2007-09-14
If you want to know what security patches have been applied to a package, you check the [changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/b/bind9/bind9_9.3.4-2ubuntu2.1/changelog").

Since this vulnerability doesn't apply to bind9, you obviously won't see anything about it in the changelog, though.

---

### Post by christian.convey on 2007-09-14
Thanks for the suggestions, and the changelog issue is certainly helpful.

I'm concerned thought that different packages' changelogs might describe vulnerabilities by referring to different vulnerabilities databases.  

For example the "bind9" changelog refers to vulnerabilities such as "CVE-2007-0493", which is a database hosted by MITRE at cve.mitre.org.

But can I rely on most/all Ubuntu security updates referring to a CVE number, so that I can write a tool to help with this?  Or can I also find changelog entries such as "Fixed that security issue that was mentioned on slashdot two weeks ago - I forget what the bug was called." ?

---

