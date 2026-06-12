---
title: "Ubuntu Apache2 nordic charsets"
date: 2007-06-04
forum: Server Platforms
---

### Post by Ibane on 2007-06-04
I have installed Ubuntu server 6.0.6 LTS with the LAMP option in a DELL machine Pentium 4 3.00 GHz.

Everything went smoothly but when I loaded a static web page under /var/www with Nordic charsets like ä,å,ö...they are not displayed properly in the web browser.

Things I have checked:

- It is not a browser problem because I can see other Nordic web pages just fine.
- The web page was used in other Windows-Apache and it was working fine.

Any ideas where I should look at?

---

### Post by jtc on 2007-06-04
Well, I have a pretty good idea what the problem might be :-)

In what charset are your html (etc) pages coded?
What charset does does your Apache present them as?

---

### Post by Ibane on 2007-06-04
I see, the charset is iso8859-1in my web page. For apache2 I have the default one UTF-8. 

I have commented the line in the folder /etc/apache2/conf.d/charset.

It seems not working. DO i need to toucht other config file?

---

### Post by jtc on 2007-06-04
If your html is coded in iso-8859-1 the visting webbrowsers need to be told that.

Instead of just commenting out the AddDefaultCharset in conf.d/charset you ought to change it, to the charset your pages are using.

```
AddDefaultCharset      ISO-8859-1
```

Of course, if the webbserver isn't sending any charset info you could always specify the charset as a html-header. Still, I'd say it is better to let the webbserver provide that kind of header data.

---

