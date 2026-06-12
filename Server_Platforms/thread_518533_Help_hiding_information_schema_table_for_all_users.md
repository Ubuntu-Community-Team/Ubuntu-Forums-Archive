---
title: "Help hiding information_schema table for all users"
date: 2007-08-06
forum: Server Platforms
---

### Post by iezugod on 2007-08-06
Hello,

I'm very very new to Linux/Ubuntu. I've been managing websites hosted on linux servers for many years however this is my first attempt at learning how to make my own server. To explain how new to this I am, I purchased a computer for running Ubuntu 6.06 Server Edition just two days ago.

Anyways, I've made what I consider to be faily good progress so far. I have installed LAMP, I can connect to my server from the internet. I setup PHP and my FTP server so I can upload files. After many tries I finally figured out how to get a user login to go directly to the folder I wanted.

Anyways, that's beside the point. I am in the process of setting up my MySQL permissions and phpMyAdmin. I've got phpMyAdmin working and I've created a new MySQL user account as well as a database for that username so I can test things out. I've given that user permission to access only the specific database I designated for testing and nothing else.

The problem I'm having is no matter what user I create and what permissions I give them, they can ALWAYS see the information_schema database. I don't want this to happen and I was hoping someone could help me fix it.

I am using Webmin to manage my servers and I have followed the setup documentation exactly as listed here: [http://doxfer.com/Webmin/MySQLDatabaseServer#Managing_database_host_table_and](http://doxfer.com/Webmin/MySQLDatabaseServer#Managing_database_host_table_and)

So, if you get a chance, please help a poor noob out.

Thanks,

Mark

---

### Post by Vlet on 2007-08-06
You might want to consult #mysql on irc.freenode.net

---

