---
title: "Ubuntu Web Server Resources (14LTS server)"
date: 2015-07-11
forum: Server Platforms
---

### Post by jonjsinger on 2015-07-11
I have a 14.04 LTS server running a couple of websites I'd like to in-house and convert over from running on a Windows platform to Linux. I'm looking for website templates and coming soon banners/pages, etc. in the interim. Can someone point me in the right direction please?

I am capable of editing the index.html file so it says "coming soon", I'm looking for something that is responsive, where I can add my own background & logos, etc. 

Thanks.

---

### Post by SeijiSensei on 2015-07-11
I recommend a "content management system" like [WordPress]("https://help.ubuntu.com/community/WordPress").  You'll need to install the "[LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP")" package and learn a bit about databases.  Once it's up and running you can pick a theme you like and start entering content from the WP "Dashboard."

---

### Post by jonjsinger on 2015-07-12
I haven't been able to find a decent theme I like. Any good ideas/suggestions?

---

### Post by PaulW2U on 2015-07-12
*Thread moved to **Server Platforms**.*

---

### Post by jonjsinger on 2015-07-12
> **SeijiSensei said:**
> I recommend a "content management system" like [WordPress]("https://help.ubuntu.com/community/WordPress").  You'll need to install the "[LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP")" package and learn a bit about databases.  Once it's up and running you can pick a theme you like and start entering content from the WP "Dashboard."
I'm struggling a bit with setting up multiple websites on one LAMP server. Are there any secrets? I can set up multiple static apache websites and one single LAMP website but not multiple LAMP websites. 

Can't find any tutorials either.

---

### Post by CharlesA on 2015-07-12
> **jonjsinger said:**
> I'm struggling a bit with setting up multiple websites on one LAMP server. Are there any secrets? I can set up multiple static apache websites and one single LAMP website but not multiple LAMP websites. 

Can't find any tutorials either.

You need to use name-based virtual hosts:
[http://httpd.apache.org/docs/current/vhosts/name-based.html](http://httpd.apache.org/docs/current/vhosts/name-based.html)

Other than that, you'd need a separate database for each one if you are going to be running Wordpress.

---

