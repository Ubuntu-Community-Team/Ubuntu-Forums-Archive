---
title: "DNS Check"
date: 2012-08-07
forum: Server Platforms
---

### Post by Nixforce on 2012-08-07
I have my Server live with everything installed.  How can i check that my NS records are correct for my domain, As im not sure the mail is 100%. I havent received mail in a while. The domain is go-systems.co.za. Could someone please check the NS records.

---

### Post by Cheesemill on 2012-08-07
[http://network-tools.com/default.asp?prog=dnsrec&host=go-systems.co.za](http://network-tools.com/default.asp?prog=dnsrec&host=go-systems.co.za)

---

### Post by Nixforce on 2012-08-07
Thanks!

Get an error, doing some research on it now.

This is the error ..

502 5.5.2 Error: command not recognized

Doing some searches for that now

---

### Post by SeijiSensei on 2012-08-07
You can use the [host]("http://linux.die.net/man/1/host") command to look up DNS records. The default is to return the A record for a name, but you can use the "-t" option to query for other records.  Here, for instance, is the query for your domain using the "any" type:

```

$ host -t any go-systems.co.za
go-systems.co.za name server ns2.afraid.org.
go-systems.co.za name server ns3.afraid.org.
go-systems.co.za name server ns4.afraid.org.
go-systems.co.za name server ns1.afraid.org.
go-systems.co.za has address 37.26.107.182
go-systems.co.za mail is handled by 10 mail.go-systems.co.za.
go-systems.co.za has SOA record ns1.afraid.org. glenn.go-systems.co.za. 1208070001 86400 7200 2419200 3600
```

---

