---
title: "empty log files"
date: 2009-07-01
forum: Server Platforms
---

### Post by graphius on 2009-07-01
I have been pulling my hair out (it is ok, I have lots of hair...) trying to get access monitoring of my small website on my home server. The access.log is blank, the various access.log.# files do not have any new entries since November 2008. Now I have done a lot of tweaking of my site, and I can't remember if I did anything major back in November (I don't think so). I know I have had at least a few visitors, but I cannot get any records.
I have a feeling it is a permissions issue, but I can't figure it out. and no I don't want to chmod 777 everything...
Can anyone help me get on the right track??
Please and Thank You...

---

### Post by pytheas22 on 2009-07-01
I'm not an Apache expert, but I'll try to help.

Where do you have the path to the log file set (e.g. in a VirtualHosts file, in apache2.conf, or somewhere else)?  And what is the 'ls -l' output for the access.log file?

Do you have other sites being logged on this server and do they work alright?

---

### Post by graphius on 2009-07-01
> Where do you have the path to the log file set (e.g. in a VirtualHosts file, in apache2.conf, or somewhere else)?

That may be my problem.I can't find it in apache2.conf. I see an ErrorLog path, but no AccessLog path.

I created a file in /etc/apache2/sites-enabled/ called MyDomain.conf (name changed of course...)
and filled it with;
> VirtualHost *:80>
ServerName [www.MyDomain.com](www.MyDomain.com)
ServerAlias Mydomain.com
DocumentRoot /var/www
CustomLog /var/log/apache2/mydomain-access.log common
</VirtualHost>

and it seems to be working now...

Thanks, sometimes it is the most obvious things that cause the biggest headaches.

---

