---
title: "Can I login via SSH if I have the FTP login credentials for a server?"
date: 2012-08-01
forum: Server Platforms
---

### Post by HunterDX77M on 2012-08-01
I need to connect via SSH to my company's server so I can begin on a MySQL project. I have the credentials to connect via FTP (with Filezilla) but I don't know if such credentials would be enough to get me access via SSH.

I have the username, host and password for the FTP and tried using them like this:
```

ssh username@mycompanyswebsite.com

```

I expected it to ask for a password like it always does, but it just locks up and does nothing. So is it possible to connect via SSH given the information I have?

---

### Post by CharlesA on 2012-08-01
It is unlikely you have ssh access if you have regular ftp access. When in doubt ask, but if it is a company's server, I'm sure there will not give just anyone ssh access.

---

### Post by anuvnu387 on 2012-08-01
FTP and SSH work on different ports. For SSH access you need a username and password on the remote system. A FTP username and password may not be an username and password on the remote server. Typically you cannot use your FTP credentials with SSH. But many hosting service providers provide SSH access. HOpe this answers your question.

---

### Post by HunterDX77M on 2012-08-01
Yes, thank you both for answering my question. I will contact my boss to see if we have SSH available for our server. Peace and have a nice day.

---

### Post by anuvnu387 on 2012-08-01
FTP and SSH work on different ports. For SSH access you need a username and password on the remote system. A FTP username and password may not be an username and password on the remote server. Typically you cannot use your FTP credentials with SSH. But many hosting service providers provide SSH access. HOpe this answers your question.

---

