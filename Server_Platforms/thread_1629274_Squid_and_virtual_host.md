---
title: "Squid and virtual host"
date: 2010-11-23
forum: Server Platforms
---

### Post by tad1073 on 2010-11-23
I am sitting behind squid and when I try to access my sites I get the error page
```
 **ERROR**

 **The requested URL could not be retrieved**

 
    The following error was encountered while trying to retrieve the URL: [http://www.tdtconsulting1.com/](http://www.tdtconsulting1.com/)
  [INDENT] **Unable to determine IP address from host name [www.tdtconsulting1.com](www.tdtconsulting1.com)**
 [/INDENT]  The DNS server returned:
 [INDENT] Name Error: The domain name does not exist. [/INDENT]  This means that the cache was not able to resolve the hostname presented in the URL. Check if the address is correct.
  Your cache administrator is
 
 
    Generated Tue, 23 Nov 2010 21:08:16 GMT by servthom (squid/2.7.STABLE9)

```

I have added entries in /et/hosts that point to them.
What so I need to do in squid so I will be able to access them?

---

### Post by tad1073 on 2010-11-24
bump

---

### Post by SeijiSensei on 2010-11-24
Did you add them to the server running squid?  It has to be able to resolve the names since it's the process that does the actual hostname lookup.

---

### Post by tad1073 on 2010-11-24
No, I haven't added them to squid.conf, I also am using webmin to manage my server, could you walk me through how to add those host.

They are local only with aliases.

---

### Post by SeijiSensei on 2010-11-24
> **tad1073 said:**
> No, I haven't added them to squid.conf, I also am using webmin to manage my server, could you walk me through how to add those host.

They are local only with aliases.

Just use sudo and your favorite editor to add the entries to the squid server's /etc/hosts like you did for the clients.  The problem is that squid cannot resolve the hostnames so it doesn't know where to forward the request.

---

### Post by tad1073 on 2010-11-24
> **SeijiSensei said:**
> Just use sudo and your favorite editor to add the entries to the squid server's /etc/hosts like you did for the clients.  The problem is that squid cannot resolve the hostnames so it doesn't know where to forward the request.

didn't work

---

### Post by SeijiSensei on 2010-11-24
> **tad1073 said:**
> didn't work

Can you open the sites with a browser from the squid server?  Squid is doing essentially the same thing.  Maybe you have a routing problem.

---

### Post by tad1073 on 2010-11-24
> **SeijiSensei said:**
> Can you open the sites with a browser from the squid server?  Squid is doing essentially the same thing.  Maybe you have a routing problem.

haven't tried...

---

### Post by tad1073 on 2010-12-08
I figured it out. i added those sites to "No Proxy For" option in the browser.

---

