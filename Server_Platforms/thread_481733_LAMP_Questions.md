---
title: "LAMP Questions"
date: 2007-06-22
forum: Server Platforms
---

### Post by Daiver on 2007-06-22
Hi guys.  Just installed Feisty and I like it.  I've already installed LAMP and it works, but I have a couple of questions:

1) I would like to make a whitelist of allowed users on my FTP.  In fact, I just need two or three of them to be able to even log in.  I'm using proftpd.  How can I go about this?  Also, I want to disable anonymous access, which I think I already did but would like to double check.

2) Right now, Apache points to /var/www/ as DocumentRoot.  I've discovered that inside /etc/apache2/sites-enabled/ I have a 000-default Virtual Host.

How would I go about replicating it?  I don't want sites to be inside /var/www/, I want users to have that www inside their own /home/username.  Does this make any sense?  How would I go about that?

3) I've changed the pass on root of MySQL using phpMyAdmin.  Is this enough to fairly secure MySQL?

4) Any quick tweaks on securing Apache or FTP further?  This is not meant to be a public server.

Thanks!

---

### Post by Bachstelze on 2007-06-22
1. Don't know, vsftpd for me ;)

2. Yes, you can let all the users on a system have a public dir on your webserver. Just tell each user to create a public_html (by default, it can be changed) dir in their home dirs. it can then be reached at [http://domain.org/~user](http://domain.org/~user)

3. Yes, if you have a strong enough password. It is also a good idea to forbid remote root logins and to store phpMyAdmin in a non-obvious location (i.e. not [http://domain.org/phpmyadmin](http://domain.org/phpmyadmin)).

4. If it's not meant to be a public server, the defaults should be secure enough. No need to chroot Apache as OpenBSD does ;)

---

### Post by Daiver on 2007-06-23
Hi.  Thank you for your reply.  What's the difference between proftpd and vsftpd?

Regarding point #2, do I need to change anyhing in apache.conf so that it knows that it has to read off these /html dirs?

How do I change phpmyadmin's place?  I don't suppose I just have to rename the dir...

---

### Post by Wardazo on 2007-06-23
> I don't want **sites** (public?) to be inside /var/www/

> This is not meant to be a public server.

Hi

Don't meen to sound pedantic, but this sounds kind of *public * to me. Could you clarify what you mean by public? Are you wanting to host public sites with dynamic content (ie php) and grant ftp to only a couple of users. If this is the case, you need more in the way of security.

vsftpd = very secure FTP daemon ... very secure, and easy to configure.

---

### Post by Daiver on 2007-06-23
Hi.  You didn't sound pedantic.  I can see where the double message is. =)

I meant that I'm running this using DynDNS and it is something the very few people will know about.  It will be public but hidden in a way.

How will Apache know to read of /home/user/html?

---

### Post by Wardazo on 2007-06-23
Hi

1. I'm assuming that you're running apache2. Make a xxx.com file available in /etc/apache/sites-available. (xxx is the name of your site). A simple one would be like this: 

> <Virtualhost *>
ServerName [www.xxx.com](www.xxx.com)
ServerAlias xxx.com
DocumentRoot /home/[username]/xxx/public_html/
</VirtualHost>

Also you'll have to make the /xxx/public_html/ directories in you home directory. Then enable it:

a2ensite xxx.com

and then restart apache.

2. Security... you should also change you php.ini to php.ini-recommended. Running Bastille and nessus are both great programs that help you secure your server and teach you at the same time.

Good luck

---

### Post by Daiver on 2007-06-23
Thanks!  This sounds quite simple to do.  I'll give it a shot.

---

