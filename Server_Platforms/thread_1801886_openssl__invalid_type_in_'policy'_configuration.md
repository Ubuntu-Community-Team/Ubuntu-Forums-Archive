---
title: "openssl  :invalid type in 'policy' configuration"
date: 2011-07-11
forum: Server Platforms
---

### Post by Tsega on 2011-07-11
I want to have a self-signed SSL Certificate for my local development server. I was following the guide on [https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL) and at the last step where you issue the command to sign the certificate by issuing the following command:

```

 openssl ca -in tempreq.pem -out server_crt.pem 

```

I get the following error: [COLOR="Red"]marked in red[/COLOR]

```

Using configuration from /home/user_name/.ssl/caconfig.cnf
Enter pass phrase for /home/user_name/.ssl/private/cakey.pem:
Check that the request matches the signature
Signature ok
The Subject's Distinguished Name is as follows
commonName            :PRINTABLE:'localhost'
stateOrProvinceName   :PRINTABLE:'AA'
countryName           :PRINTABLE:'ET'
emailAddress          :IA5STRING:'user@example.com'
organizationName      :PRINTABLE:'Example Inc'
organizationalUnitName:PRINTABLE:'Development'
[COLOR="Red"]localhost:invalid type in 'policy' configuration[/COLOR]

```

What can I do to solve it? Just to serve as a back ground, I don't have a domain name for my server, so I just used localhost to be the commanName. Is that the problem?

Thanks for your help.

---

