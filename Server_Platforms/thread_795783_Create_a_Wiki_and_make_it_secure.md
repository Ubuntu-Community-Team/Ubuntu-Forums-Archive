---
title: "Create a Wiki and make it secure"
date: 2008-05-15
forum: Server Platforms
---

### Post by TorchlightJay on 2008-05-15
Hello,

So i am trying to make a wiki for my organization and am not sure where to start. What are some good packages to make your own wiki? On another note, i want to secure my wiki to where you have to authenticate yourself before you get onto the wiki. The information is sensitive and i only want certain people allowed to see the wiki. Anyone have any suggestions as to how to pull this off?

---

### Post by hyper_ch on 2008-05-16
mediawiki is probably the best known wiki software out there... so you'll need a LAMP installation... as for unauthorized access there are many ways to accomplish that... most simple would be, if it's in your organization, to deny access from outside organisation (if you host the server inside the lan)... another way would be .htaccess where only users with username/pwd could access....

---

### Post by TorchlightJay on 2008-05-17
Makes sense. I am going to try mediawiki. ever heard of MindTouch Deki Wiki? I came across it and it looks decent. I am not an expert on the wikis but I was wondering if that was a good one too. Maybe it's just a Pepsi & Coke debate but I was curious. 

I am not an expert on .htaccess but I am sure I can learn it. As far as setting a user name or password, how does the computer store that. Is it stored in the .htaccess file or do I need some kind of database/directory like LDAP or stored in SQL database? 

Thanks.

---

### Post by woland on 2008-05-18
I've installed MediaWiki for the same purpose, and used the same security solution as advised by hyper_ch.

When using basic authentication, user names and passwords are saved in a file, that is created by htpasswd command.

```
sudo htpasswd -c file username
```

```
<Directory "/var/www/html/wiki/">
    AuthType Basic
    AuthName "My secure wiki"
    AuthUserFile /etc/apache2/conf/vhosts/users.passwd

    # only authenticated users may access the wiki
    Require valid-user
</Directory>
```

---

### Post by Barriehie on 2008-05-31
I too am interested in creating a wiki to document my Ubuntu learning and have found this site that may be helpful to some in comparing the myriad of wiki packages available.  [[COLOR="Blue"]Click here[/COLOR]](http://www.wikimatrix.org/) for a side by side comparison. [B](will open in same window :( )
[/B]
Barrie

? How do I make it so the link opens in a new window???  I know about target= but how/where do i put it in relation to the URL tags!  TIA

---

