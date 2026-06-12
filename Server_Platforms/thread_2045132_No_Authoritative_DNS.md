---
title: "No Authoritative DNS"
date: 2012-08-20
forum: Server Platforms
---

### Post by LeftFoot on 2012-08-20
Hi all,

This is not a Ubuntu question, but I posted it here anyway because I like this forum and this concern Bind9 which is pretty used by a lot of ppl here.

Here is what I try to do :

I have a DNS server 'ns1' which is authoritative for 'mydomain.com'

I would like to know if it is possible to set up a second DNS server that when you send it a dns request, it:
- Check locally if it has a record for the host requested.
- If not, forward the request to 'ns1'


I am not even sure if this is possible.
If someone know something about this, please let me know.

Thx

Leftfoot

---

### Post by SeijiSensei on 2012-08-22
A much better solution would be to make the second server a [secondary]("https://help.ubuntu.com/community/BIND9ServerHowto#Secondary_Master_Server_configuration") to the server you have now.  (In fact, the RFCs concerning DNS require you to have two servers.) 

You could add the following zone to named.conf on the second server, which would forward all requests for example.com to the primary, but this isn't the preferred solution:

```

zone "example.com" {
     forward-only;
     forwarders { ip.of.your.server; };
};

```

replacing "ip.of.your.server" with the address of the server that is authoritative for example.com.

---

