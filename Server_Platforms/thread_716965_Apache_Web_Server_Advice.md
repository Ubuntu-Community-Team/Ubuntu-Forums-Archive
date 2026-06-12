---
title: "Apache Web Server Advice"
date: 2008-03-06
forum: Server Platforms
---

### Post by michaelaly on 2008-03-06
I'm just begining to learn about web servers, specifically Apache. But I'm having trouble finding information because I don't know much in the way of terminology or what software packages do what.

I have installed Apache2, PHP, MySQL, gotten a dynamic DNS address, and have sucessfully run CMS software like Joomla and Drupal from my machine. 

What I'd like to do is have a web interface for friends to log in and tranfer files and messages to and from my computer. The forum part is easy, what I don't know how to do is generate a MySQL database of the files I want to make available, and have them show up in a web interface available to be downloaded. And preferable the database should be dynamic and automatically updated with new files.

I'd really appreciate anyone who can direct me to tutorials, books, software, or anything that can get me started with this project. I'd really like to learn how to accomplish this.
thanks to everyone,

---

### Post by insineratehymn on 2008-03-06
Yo. I don't know PHP, but this looks helpful:

[http://www.htmlgoodies.com/beyond/php/article.php/3472551](http://www.htmlgoodies.com/beyond/php/article.php/3472551)

Thats how to do a file upload form in PHP.
Once you get them to the server, it could be as simple as a perl/php script to ls the folder.

I think you may need to get MySQL to listen to a network, so try this out: 
[http://www.phpbuilder.com/board/archive/index.php/t-6630.html](http://www.phpbuilder.com/board/archive/index.php/t-6630.html)

Oh, and for some general LAMP help, which happens to be endorsed by Ubuntu:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Hopefully that will get you on your way. =)

---

### Post by major_rocks on 2008-03-06
not sure if you are interested in wordpress, but this is a cool plugin that may be along the lines of what you are trying to do.

[http://blue-anvil.com/archives/wordpress-download-monitor-plugin-v15]("http://blue-anvil.com/archives/wordpress-download-monitor-plugin-v15")

obviously wordpress uses MySql, so the whole process would be automated for you.

---

### Post by skillet on 2008-03-06
you will not need insineratehymn's second link. If your friends/family were going to run their own webservers or applications that needs a database then that link might be helpful.

---

### Post by insineratehymn on 2008-03-07
> **skillet said:**
> you will not need insineratehymn's second link. If your friends/family were going to run their own webservers or applications that needs a database then that link might be helpful.

If the mysql server and webserver are different computers then it will be needed.

I think it is good to know for anyone setting up a LAMP server that MySQL does not inherently listen to a network, it only talks over lo by default.

---

