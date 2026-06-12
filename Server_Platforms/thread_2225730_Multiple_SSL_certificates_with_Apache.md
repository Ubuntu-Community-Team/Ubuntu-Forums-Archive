---
title: "Multiple SSL certificates with Apache"
date: 2014-05-22
forum: Server Platforms
---

### Post by SchnappiJedi on 2014-05-22
Familiar with SNI but can one use multiple SSL certificates with Apache on the same server if multiple ports are used?

For example: 
SSL certificate 1...[https://www.example.com](https://www.example.com)
SSL certificate 2...[https://www.example.com:12345](https://www.example.com:12345)

---

### Post by SeijiSensei on 2014-05-23
I would think so given that you would need two virtual host definitions to handle both connections.  
```

<VirtualHost *:443>
[include one SSL definition]
</VirtualHost>

<VirtualHost *:12345>
[include another SSL definition]
</VirtualHost>

```

---

### Post by slickymaster on 2014-05-23
Moved to the **Server Platforms** sub-forum.

---

### Post by SchnappiJedi on 2014-05-25
For anyone interested using a different port allowed use of a second SSL certificate.

On another but similar note have a server with multiple sites. One site needs SSL certificates. The rest don't. If you access any of the sites hosted on the server with HTTPS it will redirect to the one site that needs the SSL certificate. Is there anyway to return a "This page can&#8217;t be displayed" (same as for sites that don't use a SSL certificate) instead?

---

### Post by CharlesA on 2014-05-25
> **schnappi2 said:**
> For anyone interested using a different port allowed use of a second SSL certificate.

On another but similar note have a server with multiple sites. One site needs SSL certificates. The rest don't. If you access any of the sites hosted on the server with HTTPS it will redirect to the one site that needs the SSL certificate. Is there anyway to return a "This page can’t be displayed" (same as for sites that don't use a SSL certificate) instead?

Are you using that as your default site or something else? It's always had it not work unless I have a redirect in place.

Post your virtual host config and we should be able to help you further.

Sidenote: I run multiple SSL sites on different IPs cuz I have run into issues with stuff not support SNI and having things blow up isn't fun.

---

### Post by SchnappiJedi on 2014-05-29
The SSL site is not the "default" site. Neither default site nor default-ssl site are enabled.

All sites are hosted on the same IP. The goal is to geta "server cannot be reached" message when accessing all but one site via HTTPS. Would post the config files but I really don't see a way to accomplish only allowing one apache virtual host to HTTPS. All the domains point to the same IP. So any domain accessing HTTPS is accessing the same server port 443.

---

### Post by SeijiSensei on 2014-05-29
Because of the problem with encrypted server names I think the only way to handle this would be a script running as the index in the SSL-enabled DocumentRoot.  Something like this:

[size=1]**index.php**[/size]
```

<?php
$myname=$_SERVER['SERVER_NAME'];

switch ($myname) {
    case "realhttpshost.example.com":
          include("/path/to/realhost/index.php");
          break;

    default:
          echo "This site does not use HTTPS; please use HTTP instead";
   
}
?>

```

---

### Post by SchnappiJedi on 2014-06-08
The script is an interesting idea. However if the index file was already "actively" serving another site (assuming I understand the suggestion) this would not work.

Still though a great alternative approach idea!

---

### Post by SeijiSensei on 2014-06-09
If you follow the one IP means one SSL certificate method, then I'd put the script in the directory served by the SSL connection.  The point is for it to handle multiple requests.

If you mean the site can also be reached over port 80, then you'd need separate DocumentRoot declarations for the SSL and non-SSL sites.

---

