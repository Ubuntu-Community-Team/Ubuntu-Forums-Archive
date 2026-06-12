---
title: "SSL on Apache for Website"
date: 2009-07-21
forum: Server Platforms
---

### Post by ahoffman on 2009-07-21
Hello,

For awhile I had been running Apache on my Ubuntu 8.04 server without any problems. Just recently I had the need to setup SSL for a website that I had created. For some reason, I now seem to be having problems. 

I used the following article to help setup SSL and create self-signed certificate: [http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html](http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html)

I setup HTTP on port 80 for my one website that doesn't need to be secured. Then I also setup HTTPS on port 443 for the other site. I believe I adjusted the virtual host information properly but when I go to the "secure site" it opens the other site on port 80 (as if the document root isn't correct).

One thing that I find odd, when I use the domain name to visit the site it just takes me to the other site as mentioned. However, if I use the direct local IP - [https://192.168.0.4](https://192.168.0.4) the site comes up without a problem. 

Does anyone have any ideas how I can get the secure site to come up properly and not go to my other non-secure site? Also, is there anyway for me to leave the site on port 80 but have just one page kick over to https? Maybe this is becoming too difficult. Any help would be greatly appreciated.

Thank you,
Aaron

---

