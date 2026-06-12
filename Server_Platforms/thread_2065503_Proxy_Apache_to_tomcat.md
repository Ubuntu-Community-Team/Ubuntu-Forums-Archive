---
title: "Proxy Apache to tomcat"
date: 2012-10-02
forum: Server Platforms
---

### Post by Nixforce on 2012-10-02
Hi,

I have my apache running good and my tomcat with my OpenBluedragon CFML Engine running. My problem is i need to point a domain to use the port 8080, but not show the 8080. I think i have to proxy it, but no idea how. Im running webmin to manage the websites, and have install tomcat .

I read somewhere i need to edit the .conf for the website. I Have found it, but dont know what to put in the to forward the port 8080.

Any help would be amazing! Thanks

---

### Post by Nixforce on 2012-10-02
I think im getting closer, lol..

But now im getting this error.

ProxyPass URL must be absolute!

---

### Post by koenn on 2012-10-02
> **Nixforce said:**
> 
ProxyPass URL must be absolute!

it means your target needs to be an URL, you probably want something like

```
ProxyPass   /  http://server.domain.tld:8080/
```

(you alse need ProxyPassReverse, and maybe some rewrites or mod_proxy_html output filtering)


You can also do this with a redirect
```
Redirect 303  /  http://server.domain.tld:8080/ 
```


[http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirect](http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirect)

---

### Post by SeijiSensei on 2012-10-03
> **Nixforce said:**
> My problem is i need to point a domain to use the port 8080, but not show the 8080.

It sounds to me like your provider blocks port 80.  If so, there is nothing you can do to avoid requiring remote users to add :8080 in the URL.  One thing you could try is setting up a truncated URL in a domain like [bit.ly]("https://bitly.com/") that points to your actual URL with the :8080 at the end and distributing the bit.ly version instead.

---

