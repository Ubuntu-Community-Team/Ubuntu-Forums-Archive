---
title: "ProFTPd 2 open security issues"
date: 2010-12-03
forum: Security
---

### Post by ygoe on 2010-12-03
Hi,

so ProFTPd currently has 2 open security issues in Ubuntu 10.4 LTS (ProFTPd 1.3.2c-1ubuntu0.1). The [Telnet IAC processing stack overflow](http://bugs.proftpd.org/show_bug.cgi?id=3521) from 2010-10-29, fixed in 1.3.3c, and the newer [mod_sql pre-authentication remote root](http://www.phrack.org/issues.html?issue=67&id=7#article) issue from Mid-November, still unpatched by the ProFTPd authors.

I'm running that FTP server on my system and I'm concerned about my system security. At least the first patch should have been ported a month ago, but the [USN list](http://www.ubuntu.com/usn) doesn't mention ProFTPd for a long time.

Should I consider switching to another FTP server, Pure-FTP has been mentioned elsewhere? Or does Ubuntu have a somehow modified version that didn't have those issues in the first place, but nobody mentioning it?

---

### Post by imbjr on 2010-12-03
> **LonelyPixel said:**
> Hi,

so ProFTPd currently has 2 open security issues in Ubuntu 10.4 LTS (ProFTPd 1.3.2c-1ubuntu0.1). The [Telnet IAC processing stack overflow](http://bugs.proftpd.org/show_bug.cgi?id=3521) from 2010-10-29, fixed in 1.3.3c, and the newer [mod_sql pre-authentication remote root](http://www.phrack.org/issues.html?issue=67&id=7#article) issue from Mid-November, still unpatched by the ProFTPd authors.

I'm running that FTP server on my system and I'm concerned about my system security. At least the first patch should have been ported a month ago, but the [USN list](http://www.ubuntu.com/usn) doesn't mention ProFTPd for a long time.

Should I consider switching to another FTP server, Pure-FTP has been mentioned elsewhere? Or does Ubuntu have a somehow modified version that didn't have those issues in the first place, but nobody mentioning it?

Have a look at vsftpd to see if it will meet your needs.

---

### Post by cariboo on 2010-12-03
You could also stop using an ftp server and use sftp, most ftp clients support sftp.

---

### Post by ygoe on 2010-12-03
> **cariboo907 said:**
> You could also stop using an ftp server and use sftp, most ftp clients support sftp.
I've been thinking about that, but I'm not sure all of my webhosting clients could handle that. Maybe I should just ask them to find out.

---

### Post by CharlesA on 2010-12-03
> **LonelyPixel said:**
> I've been thinking about that, but I'm not sure all of my webhosting clients could handle that. Maybe I should just ask them to find out.
Would be a good idea. :)

sftp > ftp and a whole heck of a lot easier to set up.

---

### Post by ygoe on 2010-12-03
But still, until this is evaluated, ProFTPd remains highly insecure on Ubuntu!

---

### Post by CharlesA on 2010-12-03
> **LonelyPixel said:**
> But still, until this is evaluated, ProFTPd remains highly insecure on Ubuntu!
File a bug report on launchpad referencing the vulnerabilities.

---

### Post by ygoe on 2010-12-03
Oh, it seems that the first bug was already resolved with the current version. There wasn't even a notice about it. Only the [Launchpad entry]("https://bugs.launchpad.net/ubuntu/+source/proftpd/+bug/669862") suggests it.

The second bug is in [mod_sql]("http://www.proftpd.org/docs/contrib/mod_sql.html") which is not a standard module of ProFTPD. So I'm not sure whether we can expect a fix for that.

---

### Post by OpSecShellshock on 2010-12-03
Just read this morning that the source code for ProFTPd was compromised some time prior to last weekend (maybe?). I don't think that would necessarily be a problem for applying updates to an already-installed version, but it might be something to keep at the back of your mind. Looking for a link...

---

### Post by OpSecShellshock on 2010-12-03
> **OpSecShellshock said:**
> Just read this morning that the source code for ProFTPd was compromised some time prior to last weekend (maybe?). I don't think that would necessarily be a problem for applying updates to an already-installed version, but it might be something to keep at the back of your mind. Looking for a link...

Got it:

[http://www.zdnet.com/blog/security/open-source-proftpd-hacked-backdoor-planted-in-source-code/7787](http://www.zdnet.com/blog/security/open-source-proftpd-hacked-backdoor-planted-in-source-code/7787)

---

### Post by ygoe on 2010-12-03
The compromised FTP server is not the problem here. It's been in a limited time and does not affect already installed instances of the server. I'm talking about the mod_sql issue that's been discovered by Prack like 2 weeks ago. See my first posting for further links.

---

### Post by ygoe on 2010-12-19
The mod_sql issue has been fixed in ProFTPd: [http://bugs.proftpd.org/show_bug.cgi?id=3536](http://bugs.proftpd.org/show_bug.cgi?id=3536)

It would now be nice to see this fix in Ubuntu, too.

---

### Post by cariboo on 2010-12-19
I'd suggest you create a bug using:

```
ubuntu-bug proftpd
```

With a link to the fix. Add as much relevant info as you can.

---

