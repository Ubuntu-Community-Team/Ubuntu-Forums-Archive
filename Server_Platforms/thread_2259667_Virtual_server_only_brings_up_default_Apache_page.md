---
title: "Virtual server only brings up default Apache page"
date: 2015-01-06
forum: Server Platforms
---

### Post by bizres on 2015-01-06
Hi,

I've setup a subdomain and would like it to point to a folder on an Ubuntu server instance on EC2.

I have followed instructions here: [http://tutorials.securesignup.net/vps-hosting/creating-new-sites-and-sub-domains-with-webmin.html](http://tutorials.securesignup.net/vps-hosting/creating-new-sites-and-sub-domains-with-webmin.html)
but it's 2 weeks now that anytime I go to the respective subdomain.mydomain.com I just get the default Apache page.

I have attached a snapshot of my settings.

Thanks in anticipation.
[ATTACH=CONFIG]259029[/ATTACH]

---

### Post by SeijiSensei on 2015-01-06
Do you have shell access to this server, or just a web interface? If you can open a shell, you should follow the instructions in the [Ubuntu Server Guide]("https://help.ubuntu.com/14.04/serverguide/httpd.html").

Basically you need a "ServerName" declaration inside the <VirtualHost> container:
```

<VirtualHost *:80>
ServerName www.example.com
[stuff]
</VirtualHost>

```
Apache will use this definition for any request whose URL matches ServerName.  You can expand the list of matching names with the ServerAlias directive.

---

### Post by volkswagner on 2015-01-06
You should change you virtual servers port to 80. Apache generally complains about a assigning vhosts to ports and non ports.

As mentioned if you have access to the terminal, don't use webmin as it can mangle your config and may not fully comply with your version of Ubuntu.

---

### Post by mastablasta on 2015-01-07
afte reading about webmin issues and after plenty of testing I decided to go with Ajenti. works fine as a webGUI to admin server and offer easy access to config files and all that right form browser.

---

### Post by bizres on 2015-01-07
Thanks everyone.
problem solved - changed the port to 80 and on all addresses.
[ATTACH=CONFIG]259074[/ATTACH]

---

### Post by Votuduc on 2015-01-18
it work for me too. Thank you for your solution.

[Thoi trang tre em]("http://cookie-jar.net") | [Quan ao tre em]("http://cookie-jar.net/shop")

---

