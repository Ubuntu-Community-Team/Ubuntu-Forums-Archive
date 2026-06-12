---
title: "problem with basic authentication with virtual host in apache2"
date: 2018-11-25
forum: Server Platforms
---

### Post by blanrok95 on 2018-11-25
I am using an apache2 web  server on ubuntu server 18.04 and the domain is ejemplo.es, where I  have a secure virtualhost https sri.example.es.

when I'm going to configure it in / etc / apache2 / sites-available I make a default-ssl.conf cp to sriseguro.conf

and inside that file sriseguro.conf I have:

[ATTACH=CONFIG]281767[/ATTACH]

After  saving the file, I create the file of the users with the password with  the following command "htpasswd -c / etc / apache2 / htpasswd alumno" and profesor.

then I check the page from the client's browser and it does not perform the basic authentication.

I need help

---

### Post by slickymaster on 2018-11-25
Thread moved to **Server Platforms** for a better fit

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by blanrok95 on 2018-11-25
Already solved,

The solution was that after creating the user file with the password with the command htpasswd -c / path / user1, you have to configure /etc/apache2/apache.conf and within this file, type a new directive <Directory " / path / ">
AuthType Basic
AuthName "Restricted"
AuthBasicProvider file
AuthUserFile "user_file_path"
Require User user1
Require User user2
</Directory>

I hope it helps :)

---

