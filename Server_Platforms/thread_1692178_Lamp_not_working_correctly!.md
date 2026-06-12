---
title: "Lamp not working correctly!"
date: 2011-02-21
forum: Server Platforms
---

### Post by eL3ET on 2011-02-21
I'm on Xubuntu 10.04 desktop edition and I just installed LAMP in hopes to start a webserver, I followed this ([https://help.ubuntu.com/community/ApacheMySQLPHP#To%20install%20the%20default%20LAMP%20stack%20in%20Ubuntu%207.04%20%28Feisty%20Fawn%29%20Ubuntu%207.10%20%28Gutsy%20Gibbon%29%20Ubuntu%208.04%20LTS%20%28Hardy%20Heron%29,%208.10%20%28Intrepid%20Ibex%29,%209.04%20%28Jaunty%20Jackalope%29,%209.10%20%28Karmic%20Koala%29%20and%2010.04%20%28Lucid%20Lynx%29](https://help.ubuntu.com/community/ApacheMySQLPHP#To%20install%20the%20default%20LAMP%20stack%20in%20Ubuntu%207.04%20%28Feisty%20Fawn%29%20Ubuntu%207.10%20%28Gutsy%20Gibbon%29%20Ubuntu%208.04%20LTS%20%28Hardy%20Heron%29,%208.10%20%28Intrepid%20Ibex%29,%209.04%20%28Jaunty%20Jackalope%29,%209.10%20%28Karmic%20Koala%29%20and%2010.04%20%28Lucid%20Lynx%29)) guide word for word up until 

"To test the new site, create a file in /home/user/public_html/: 
echo '<b>Hello! It is working!</b>' > /home/user/public_html/index.htmlFinally, browse to [http://localhost/](http://localhost/)"

When I type local host into my browser it has a 403 error (Forbidden) how can I make the files in: /home/myusername/public_html/ viewable in browser?

---

### Post by Rusty au Lait on 2011-02-21
My $0.02
1 check permissions all along the path
2 firewall iptables
3 network routing
good luck

---

### Post by cariboo on 2011-02-21
The instructions are a little on the old side, things have changed quite a bit since Fiesty, by default on recent installations, /var/www is the document root on Ubuntu servers. All you should have to do it enter [http://localhost](http://localhost) in a browser, and you should get the "It Works!" page.

You May be better starting over, and following this [ guide]("https://help.ubuntu.com/8.04/serverguide/C/web-servers.html")

---

