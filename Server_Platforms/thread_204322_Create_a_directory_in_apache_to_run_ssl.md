---
title: "Create a directory in apache to run ssl"
date: 2006-06-26
forum: Server Platforms
---

### Post by stock99 on 2006-06-26
hi,


   I have a web server running apache 1.3.33 and i recently install snort+base. I would like to turn the directory for 'base' to be ssl. So i do little experiment but it always end up my entire site inaccessiable. Can anyone help me with this problem?  


------below are lines i added in my conf file--------

<VirtualHost *>
    ServerName localhost
    DocumentRoot /www/docs
    Redirect /security/ [https://192.168.50.254/security/](https://192.168.50.254/security/)
</VirtualHost>


<VirtualHost _default_:443>
    SSLEngine On
    SSLCertificateFile /etc/apache/ssl.crt/localhost.cert
    SSLCertificateKeyFile /etc/apache/ssl.key/localhost.key

    ServerName localhost
    DocumentRoot /www/docs
</VirtualHost>



--------------------------------------------------

---

### Post by Kurt` on 2006-06-27
[QUOTE=stock99]
<VirtualHost *>
    ServerName localhost
    DocumentRoot /www/docs
    Redirect /security/ [https://192.168.50.254/security/](https://192.168.50.254/security/)
</VirtualHost>
[/QUOTE]
Try this:

<VirtualHost *>
    ServerName localhost
    DocumentRoot /www/docs
    <Directory /www/docs>
      RedirectMatch ^/security/$ [https://192.168.50.254/security/](https://192.168.50.254/security/)
    </Directory>
</VirtualHost>

---

### Post by stock99 on 2006-06-27
ok this work when i type in [http://192.168.50.254/security](http://192.168.50.254/security) where i get direct to [https://192.168.50.254/security](https://192.168.50.254/security).

But now when i type [https://192.168.50.254](https://192.168.50.254) which also prompt me for cert and then allow access. How do i disable https acess on all directory apart from "secuirty"??

---

### Post by LordHunter317 on 2006-06-27
[QUOTE=stock99]But now when i type [https://192.168.50.254](https://192.168.50.254) which also prompt me for cert and then allow access. How do i disable https acess on all directory apart from "secuirty"??[/QUOTE]Write a redirect rule to move them all back?  That's still poor. 

You shouldn't be doing it like this.  Design your webpages so they go to and from SSL correctly.

---

### Post by stock99 on 2006-06-28
[QUOTE=LordHunter317]Write a redirect rule to move them all back?  That's still poor. 

You shouldn't be doing it like this.  Design your webpages so they go to and from SSL correctly.[/QUOTE]


I am not so sure what do you mean exactly. So redirection is not good practice?  What i really want , as mentioned in opening thread, is to have this single dierctory -secure to be ssl , the rest to be normal http.  When you said design webpage, you mean control by some php pages?

---

### Post by LordHunter317 on 2006-06-29
If you hadn't installed base in your webroot, this would be a touch simpler.

Anyway, I'd just leave things like they are.  You will have SSL only access to /security.  The fact everything else is being SSL-served as well nothing to worry about, since you can access it over HTTP.

What I was saying is in whatever pages you write, you should write the links correctly (i.e., http vs. https) instead of relying on the redirects.

---

