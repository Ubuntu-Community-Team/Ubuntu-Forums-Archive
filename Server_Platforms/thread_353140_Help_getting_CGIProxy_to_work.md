---
title: "Help getting CGIProxy to work"
date: 2007-02-04
forum: Server Platforms
---

### Post by kjacks on 2007-02-04
I've just installed CGIProxy on my 6.10 LAMP server but I cannot get it to work. When I go to [http://localhost/cgi-bin/nph-proxy.cgi](http://localhost/cgi-bin/nph-proxy.cgi) i just get a blank, white, screen. I'm not getting a screen asking for a URL and I'm  not getting the "404 Not Found" error.  I haven't altered the default nph-proxy.cgi file.

I placed the CGIProxy file in /usr/lib/cgi-bin/

I made a link: sudo ln -s /usr/lib/cgi-bin /var/www/cgi-bin

I changed permissions: sudo chmod 755 /usr/lib/cgi-bin nph-proxy.cgi

This is the first time I've played with cgi so it could be something very basic I'm missing.

Any help you guys could give would be great!

---

### Post by golfing22 on 2007-02-07
CGIProxy requires Perl and NET:SSLeay to run, so you'll have to install them with apt-get, i'm not sure what the exact command is, but I can look them up if you need me to.

I've actually wrote a small howto myself with Suse linux (should be easy to adapt to ubuntu) at [http://golfing22.net/index.php?option=com_content&task=view&id=20&Itemid=34]("http://golfing22.net/index.php?option=com_content&task=view&id=20&Itemid=34")

---

