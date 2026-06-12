---
title: "Apache configuration"
date: 2011-12-20
forum: Server Platforms
---

### Post by asai on 2011-12-20
Hi,

I have a question on a configuration in Apache:

I have a aplication running on my server that I can access using a link like this: [http://www.example.com:4010/](http://www.example.com:4010/)
How do I code this into my apache config file so it can be used like this: [http://www.example.com/app/](http://www.example.com/app/)

---

### Post by Lars Noodén on 2011-12-20
Move your app to the virtual host that is listening to port 80 instead of the one listening to port 4010.  Then put it in the directory 'app' inside that virtual server's document root.

---

### Post by satanselbow on 2011-12-20
You will have to change the "Listen" directive in /etc/apache2/httpd.conf to 4010 instead of the standard 80.

Whilst you can run a particular site on pretty much any port you like you can only run one port as the default - so any other sites you might be running currently on the standard port 80 would then have to be accessed via [http://whatever.com:80](http://whatever.com:80)

---

### Post by satanselbow on 2011-12-20
Lars' answer changes the port of your site to the default 80 - mine changes the entire config to 4010...

Is there a particular reason you are running or need to keep your site on the non-standard port?

---

### Post by asai on 2011-12-20
Thanks for your replys.

I have already my default website running on port 80.
This app is running as a service from /usr/share/app/ and a config file in /etc/default
It is this config file that have this line (not 4010 but 4040):
```
APP_ARGS="--port=4040
```

So I cant move anything. Any suggestions?

---

### Post by satanselbow on 2011-12-20
Virtualhosts can be configured to listen on different ports ;) So all is not lost :D

Just follow the templated examples for SSL in the config files :D

---

### Post by asai on 2011-12-20
> **satanselbow said:**
> Virtualhosts can be configured to listen on different ports ;) So all is not lost :D

Just follow the templated examples for SSL in the config files :D

Could you give me a hint? :oops:

---

### Post by Lars Noodén on 2011-12-20
> **asai said:**
> Could you give me a hint? :oops:

You can look here:
[http://httpd.apache.org/docs/2.2/vhosts/examples.html#port](http://httpd.apache.org/docs/2.2/vhosts/examples.html#port)

It's a good place to start.

---

### Post by SeijiSensei on 2011-12-20
> **asai said:**
> Could you give me a hint? :oops:

```

Listen 4040

<VirtualHost *:4040>
DirectoryRoot    /usr/share/app
[stuff]
</VirtualHost>

```

---

### Post by asai on 2011-12-22
Do I put it in the apache2.conf file:
```
Listen 4040

<VirtualHost *:4040>
DirectoryRoot    /usr/share/app
[stuff]
</VirtualHost>
```

---

