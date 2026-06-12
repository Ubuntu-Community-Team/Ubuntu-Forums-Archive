---
title: "RSA server certificate does not march server name"
date: 2015-07-30
forum: Server Platforms
---

### Post by rmit2 on 2015-07-30
This is regarding a postfix install. I purchased a SSL certificate and combined the domain.crt bundle.crt and domain.key into a single .pem file. When i look into the apache logs i get this error
 [warn] RSA server certificate CommonName (CN) `domain.com' does NOT match server name!?

my mail server name is : main
domain: domain.com

Users access the mail through thr url : mail.domain.com/webapp

In the postfix main.cf file i have pointed to smtpd_tls_cert_file = /etc/keys/domain.com-ssl.pem as well.

When i open google chrome, firefox and IE it says as untrusted site. Can someone point me where i should be looking to sort this

---

### Post by SeijiSensei on 2015-07-30
In the public DNS is the server called main.domain.com?  Does it have reverse DNS set up so its IP address also points to main.domain.com?

If the server is called "main.domain.com" then the certificate needs to be for that specific name.  You could try this to make everything use just domain.com:

In the zone file for domain.com, add an A record at the top for domain.com that points to its IP address:
```

@    IN SOA domain.com. someone.domain.com. (
[stuff]

)
     IN NS first.nameserver.for.domain.com.
     IN NS second.nameserver.for.domain.com.

     IN MX 0 main.domain.com.     

     IN  A  ip.addr.of.server  <== add this

[more stuff]

main    IN   CNAME     domain.com.

[etc.]

```
That associates the name "domain.com" with the server's IP address.

Tell Ubuntu your computer is called domain.com with 
```
sudo hostname domain.com
```

If you can exchange that cert for a new one (doubtful but you can try), then I'd suggest getting a "wildcard" certificate for *.domain.com that matches all names in domain.com.

---

### Post by rmit2 on 2015-07-30
For now the mail server is just being accessed from the lan only. I registered the certificate for domain.com only

I am trying to access the mail server from the lan only. The server is placed within a windows domain. It is not joined to the windows domain but sharing only lan ip.

I have added A record in the domain controller so whenever someone types in domain.com it redirects to mail.domain.com/webapp

I get this error
SSL CTX certificate file error: error:02001002:system library:fopen:No such file or directory
 2015: Error loading SSL context, POP3S and IMAPS will be disabled

---

### Post by SeijiSensei on 2015-08-02
> SSL CTX certificate file error: error:02001002:system library:fopen:No such file or directory
Sounds like it cannot find the certificate.  Check the path.

---

### Post by Henrik_Iivonen on 2015-08-06
The certificate must match the full domain name that is being accessed. In this example it would be mail.domain.com (i'm guessing you are using domain.com as a pseudonym for your real domain)
Unless you bought a wildcard certificate for *.domain.com, each subdomain needs to have their own certificate matching the full domain name.
All of these would need their own cert if you wanted to use them all:

domain.com
[www.domain.com]("http://www.domain.com")
mail.domain.com

---

