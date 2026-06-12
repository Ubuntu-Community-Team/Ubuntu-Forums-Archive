---
title: "Getting Apache and Tomcat to talk"
date: 2007-10-02
forum: Server Platforms
---

### Post by mork on 2007-10-02
Has anyone successfully gotten Apache 2.2 to talk to Tomcat 5.5 or later?

I've been trying to go to Ubuntu, but until I can make sure that my servlets/JSPs will be able to work under Apache, I'm stuck.

I've done searches, but haven't found any relevant up to date documentation. 

Getting these two programs to work together is doable, but, surprisingly, it's not widely documented.

Look forward to any replies.

Thanks.

-- M

P.S. Also, is Ubuntu a good choice for a production server? I only mean this question from the point of view that I'm new to Hosting and want to make sure I can set up a Web Server, email, FTP, and the like in a few days (hopefully!).

---

### Post by HermanAB on 2007-10-02
You need to install a 'connector'.  See this rather old guide for some ideas: [http://www.aeronetworks.ca/tomcat-howto.html](http://www.aeronetworks.ca/tomcat-howto.html)

Cheers,

Herman

---

### Post by gtducati on 2007-10-05
If you type:
[B]sudo apt-get install apache2 tomcat5.5 libapache2-mod-jk
[/B]it should handle all the dependencies ...  connector and all.

However, I believe if you just type:
[B]sudo apt-get install apache2 tomcat5.5
[/B]it will install the libapache2-mod-jk connector package anyway.

---

