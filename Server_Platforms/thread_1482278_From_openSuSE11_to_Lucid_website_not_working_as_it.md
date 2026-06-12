---
title: "From openSuSE11 to Lucid: website not working as it should..."
date: 2010-05-13
forum: Server Platforms
---

### Post by foisys on 2010-05-13
Hi,

I googled around and can't seem to find the solution to this problem... Ok, I have a server that used to run openSuSE until last week ;-). From it, I ran my shop's website as well as a dokuwiki installation in the same folder as the basic web site:

- DocumentRoot is /var/www/htdocs
- The wiki is /var/www/htdocs/dokuwiki

So, this worked:

[http://www.myshop.com](http://www.myshop.com) => a-ok
[http://www.myshop.com/dokuwiki](http://www.myshop.com/dokuwiki) => a-ok, with the home page of the wiki showing

Than I move to 10.04 Server... I transfer my web material into /var/www/htdocs, modify the default config in sites-availables and restart apache. What I now see:

[http://www.myshop.com](http://www.myshop.com) => a-ok
[http://www.myshop.com/dokuwiki](http://www.myshop.com/dokuwiki) => no good with connection timeout
[http://www.myshop.com/dokuwiki/doku.php?id=Home](http://www.myshop.com/dokuwiki/doku.php?id=Home) => a-ok, with the home page of the wiki showing

When I try from my LAN, I get this:

[http://localIP](http://localIP) => a-ok
 [http://localIP/dokuwiki](http://localIP/dokuwiki) =>  a-ok, with the home page of the wiki showing
[http://localIP/dokuwiki/doku.php?id=Home](http://localIP/dokuwiki/doku.php?id=Home) => a-ok, with the home page of the wiki showing.

This has me stumped...I am a bioinformatician by trade, not an Apache and/or Network guru so I am asking for inputs on this.

Best regards

Sylvain Foisy, Ph. D.
BioIT

---

### Post by cdenley on 2010-05-13
Run these commands on your server and post the output.
```

echo -e "GET /dokuwiki/ HTTP/1.1\nHost: www.myshop.com\n"|nc -q 1 -w 4 127.0.0.1 80|head -n 20
echo -e "GET /dokuwiki/doku.php HTTP/1.1\nHost: www.myshop.com\n"|nc -q 1 -w 4 127.0.0.1 80|head -n 20
echo -e "GET /dokuwiki/doku.php?id=Home HTTP/1.1\nHost: www.myshop.com\n"|nc -q 1 -w 4 127.0.0.1 80|head -n 20

```

---

### Post by foisys on 2010-05-14
Hi,

Thanks for the input; I'll keep this in my troubleshooting archives. As a matter of fact, I was looking at the wrong end of the problem: my problem stans from not having looked at how to do a dokuwiki migration:

 [http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

Following these instructions fixed the problem. Let that me a warning for people like me...

Sylvain

---

