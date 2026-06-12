---
title: "WebDav user permissions problem"
date: 2009-11-04
forum: Server Platforms
---

### Post by babba on 2009-11-04
Hello everybody,

I have some issues with my webdav configuration. I have set up correctly my ubuntu 9.10 with apache2 and webdav is working.

I have setup Digest authentification and I will add later ssl encryption, but for now http is fine for testing. The 2 users access the folder and can write in it with default configuration, so webdav is working.

Now I want to finetune the permissions for users. So here is what I want to do.

I have a folder webdav and 2 users, bobby and sammy. I want to give for example bobby read-only access to the folder webdav and sammy can also write to the folder.

Is there a possibility to do this with <LimitExcept> in apache2 on ubuntu?

I have found a configuration where it works, but you have to do this with Limit and LimitExcept keywords, so I have a problem to understand why it works when you add Limit to the LimitExcept and it does not work when you set LimitExcept alone.

```

<VirtualHost *:80>
         ServerAdmin webmaster@localhost

         DocumentRoot /var/www
         <Directory />
                 Options FollowSymLinks
                 AllowOverride None
         </Directory>

         alias /webdav /var/www/webdav
         <Directory /var/www/webdav>
                 Options Indexes
                 AllowOverride None

                 DAV On
                 AuthType Digest
                 AuthName webdav
                 AuthDigestProvider file
                 AuthUserFile /var/www/.passwd.dav

                 <Limit GET HEAD PROPFIND OPTIONS>
                         Require user bobby
                 </Limit>
                 <LimitExcept GET HEAD PROPFIND OPTIONS>
                         Require user sammy
                 </LimitExcept>
         </Directory>

         ErrorLog /var/log/apache2/error.log

         # Possible values include: debug, info, notice, warn, error,  
crit,
         # alert, emerg.
         LogLevel debug

         CustomLog /var/log/apache2/access.log combined

</VirtualHost>

```

Thanks in advance, I hope I explained the problem well, when not feel free to ask me questions, thank you very much.

babba

---

### Post by babba on 2009-11-04
Hello,

nobody has any idea what i can do.

Is it not possible to fix user permissions read-only only with <LimitExcept>?

Can anybody explain me the concept behind <LimitExcept>, how to use it?

Thank you very much.

babba

---

### Post by babba on 2009-11-05
* push

Does somebody knows how LimitExcept and Limit are working in detail to restrict access?

Thanks

babba

---

### Post by babba on 2009-11-06
no idea by nobody? I will thank you very much for all input.

babba

---

