---
title: "Torrentflux"
date: 2005-08-01
forum: Requests
---

### Post by kaktusztea on 2005-08-01
I found this tool for Bittorrent. Very useful, you don't need X to manage torrents remotely on web interface.

[http://www.torrentflux.com](http://www.torrentflux.com)

Is it possible to make a port into Ubuntu?

---

### Post by strikeforce on 2005-08-01
Its PHP based you don't need to port it you just have to install the correct programs. E.g apache2 and php then it should work.  I think you possibly have the gd library as well however thats it.

I'm got it working before.  Once all the prerequisites are installed e.g.

apt-get install apache2 php4 

Then you configure your apache install.

You then put your torrentflux php into your www folder and voila it works.

You might need mysql although I can't remember and I have no power at home at the moment so I can't even tell you exactly.

---

### Post by kaktusztea on 2005-10-18
I'm a little late, but: thank you! ;)

---

