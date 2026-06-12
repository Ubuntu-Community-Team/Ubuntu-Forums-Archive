---
title: "reverse DNS lookup doesn't work"
date: 2015-10-06
forum: Server Platforms
---

### Post by lifit on 2015-10-06
Hey guys,

I've a problem regarding reverse DNS lookup.
Beforehand let me say that I'm using an Ubuntu 14.04 Server with Plesk 12 to manage my webspaces.

 The problem is as follows.
I transfered a domain from one server to another by changing the dns records; this worked very well and there were no problems except that reverse DNS lookup via *host xxx.xxx.xxx.xxx* gives me the error message
> [COLOR=#000000][FONT=Liberation Sans]Host xxx.xxx.xxx.xxx.in-addr.arpa not found: SERVFAIL[/FONT][/COLOR]

This of course suggests that there's something wrong with the dns zone file or with in-addr.arpa-file, but I can't find the error...
Here are the the corresponding parts of these files:

named.conf:
```

zone "xxx.xxx.xxx.in-addr.arpa" {
     type master;
     file "xxx.xxx.xxx.in-addr.arpa";
     allow-transfer {
       common-allow-transfer;
     };
};

acl common-allow-transfer {
     none;
};
```

in-addr.arpa:
```

@ IN SOA domin.tld. root.domain.tld. (
         1440175161 ; Serial
         10800 ; Refresh
         3600 ; Retry
         604800 ; Expire
         10800 ) ; Minimum

      IN NS domain.tld.
  xxx IN PTR domain.tld.
```

I replaced the IP by xxx.xxx.xxx.xxx and the domain by domain.tld.

Forward DNS lookup works perfectly well.

Has anyone an idea what's going wrong? I'm grateful for any kind of help!

Best regards!

---

### Post by darkod on 2015-10-06
If you are talking about the public ip, you can't control it with reverse dns. It's not yours, the provider owns it. If the provider panel allows it you can maybe setup a hostname for rdns there, but not with a zone file.

---

