---
title: "How do I join a Windows 2008 Server to a Samba Domain"
date: 2009-05-14
forum: Server Platforms
---

### Post by lumberjackshaw on 2009-05-14
Hey guys,

I have been fighting this problem longer than I care to admit.  While you may say that's crazy and NT is no longer supported, articles such as the following seem to state otherwise.
[URL="http://www.nabble.com/Vista-SP1,-Server-2008-joining-NT4-Samba-Domain-td17881924.html"]
http://www.nabble.com/Vista-SP1,-Server-2008-joining-NT4-Samba-Domain-td17881924.html
[/URL]

We have a very small network here 1 Linux Server and 1 Windows Server.  I have been forced to upgrade our windows server to accommodate our operations software upgrades (requires mssql 2005+).  The linux server pretty much does everything else.  Obviously, samba 4 is not yet an option so I need to make this work until then.

Has anyone been successful in joining a windows 2008 server to a samba domain and most importantly, how?

I have followed the advice of Microsoft for nt joins and created the samba account in advance.  I have removed the invalid users from smb.conf.  I have reduced the security of the windows server to accept LM (even though I entend to use ntlm).

On the windows server I have issued the following command.
```
netdom join winserver /domain:mydomain\smbserver.mydomain /userd:mydomain\root /passwordd:*
```

which returns
The request is not supported.
The command failed to complete successfully.

Thanks in advance for any help you guys have to offer.

---

