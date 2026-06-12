---
title: "FTP user permissions"
date: 2009-11-10
forum: Server Platforms
---

### Post by kingv on 2009-11-10
Hi guys,

I'm using ProFTPD and I want to setup an FTP user that will be able to download/upload/change files on the website's directory. However, I want this user only to be able to see the directory he's assigned to. For example, 
let's say I add a user "ftpuser" like this: 
sudo useradd ftpuser -p password -d /var/www/ -s /bin/false

Now my question is, is there a way to limit this ftpuser to ONLY see /var/www/? I don't want this user to be able to list other dirs outside /var/www/.

Thanks in advance!

---

### Post by Ilalmi on 2009-11-10
Hi,

have a look at the DefaultRoot directive: [http://www.proftpd.org/docs/directives/linked/config_ref_DefaultRoot.html](http://www.proftpd.org/docs/directives/linked/config_ref_DefaultRoot.html) 

I hope that is what you are looking for.

---

### Post by kingv on 2009-11-10
Thanks for the reply Ilalmi! You've definitely pointed me in the right direction. 
What I did is I edited /etc/proftpd/proftpd.conf, and uncommented the following line:

# Use this to jail all users in their homes
 DefaultRoot                    ~

hehe such an easy fix. I cant believe I missed that line when I was looking at the conf file. Anyways, thanks again!

---

