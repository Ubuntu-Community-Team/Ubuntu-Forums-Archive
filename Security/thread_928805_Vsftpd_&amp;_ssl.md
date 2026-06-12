---
title: "Vsftpd &amp; ssl"
date: 2008-09-24
forum: Security
---

### Post by Aysah on 2008-09-24
Currently at my job we use vsftpd on a redhat machine and we're trying to setup our RSA Certificate.  We've exported our certificate out of our windows server box to a pmx file and then in the terminal we converted it:

```
openssl pkcs12 -in cert_export.pfx -out cert_export.pem
```

Now we are just blinking at the screen trying to figure out what we do next.  We have vsftpd working at the moment but after recent customer demands, our company is now requiring us to transition to FTPS.

I know that in the vsftpd.conf I need to add:
```
 ssl_enable=YES
```

But in terms of authenticating my cert_export.pem are there any additional steps that need to be done or should I just:
```
 rsa_cert_file=/usr/share/ssl/certs/cert_export.pem
```

---

### Post by qstraza on 2008-09-24
Well this doesnt answer your question but why dont you just use sftp?

---

### Post by Aysah on 2008-09-24
> **qstraza said:**
> Well this doesnt answer your question but why dont you just use sftp?

Some of our clients are banks and they are very strict.  Apparently they feel more comfortable with certificates so unfortunately this is the route we have to take.

---

### Post by qstraza on 2008-09-24
too bad, but ssh (sftp) can use auth keys, isnt this kinda the same as certificate?

---

### Post by Aysah on 2008-09-24
> **qstraza said:**
> too bad, but ssh (sftp) can use auth keys, isnt this kinda the same as certificate?

I guess at this point its just a matter of what they prefer and what we still don't know how to setup lol.

**FTPS**

_Pros:_
[LIST]
[*]Widely known and used
[*]The communication can be read and understood by humans
[*]Provides services for server-to-server file transfer
[*]SSL/TLS has good authentication mechanisms (X.509 certificate features)
[*]FTP and SSL/TLS support is built into many Internet communication frameworks
[/LIST]

_Cons:_
[LIST]
[*]Doesn't have a uniform directory listing format
[*]Requires a secondary DATA channel, which makes it hard to use behind the firewalls
[*]Doesn't define a standard for file name character sets (encodings)
[*]Not all FTP servers support SSL/TLS
[*]Doesn't have a standard way to get and change file and directory attributes
[/LIST]


**SFTP**

_Pros:_
[LIST]
[*]Has good standards background that strictly defines most (if not all) aspects of operations
[*]Has only one connection (no need for DATA connection)
[*]The connection is always secured
[*]The directory listing is uniform and machine-readable
[*]The protocol includes operations for permission and attribute manipulation, file locking, and more functionality
[/LIST]

_Cons:_
[LIST]
[*]The communication is binary and can't be logged "as is" for human reading
[*]SSH keys are harder to manage and validate
[*]The standards define certain things as optional or recommended, which leads to certain compatibility problems between different software titles from different vendors
[*]No server-to-server copy and recursive directory removal operations
[*]No built-in SSH/SFTP support in VCL and .NET frameworks
[/LIST]

---

### Post by qstraza on 2008-09-24
well i hope you figure ftps out ;)

---

