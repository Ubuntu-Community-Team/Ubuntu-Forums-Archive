---
title: "Where is phpmyadmin host file, trassed my host files"
date: 2010-09-16
forum: Server Platforms
---

### Post by oberwil on 2010-09-16
I have done an install of LAMP on my MSXP Desktop & Laptop w/Vista. And recently did an install on Ubuntu. But I did not fully understand the name base host file setup, and thus my symlink got corrupted and I trashed my host files before backing them up.
I have a couple of questions that hopefully answered fully I can then pass on with a Tutorial because  so far most directions at some point have a vague reference or completely omit some important point. I have only found one that didn't omit some step, and was not vague in it's instructions.

So here it go's. 
1. Do I need to create separate host files for each of my local sites?? Is there a way to create 1 host file with several virtualhost directives for each of my web sites like I have on Windows??
2. In /etc/apache2/conf.d/fqdn I have ServerName localhost, and if I type in [http://localhost](http://localhost) I get my 1st site. So what exactly does fqdn do??
3. In ports.conf I have NameVirtualHost *:80 Listen 80. Again clarify this setting.
4.Now that I got my sites up, I'm now just missing how to create another vhost file to point to phpmyadmin, and be able to manage mysql. Where would the default path most likely be?? Since I trashed this file

Thanks, If I get informed on these subjects I'll create a very nice tutorial with full explanations on this topic.

Howard

---

### Post by oberwil on 2010-09-16
Well I just tried [http://phpmyadmin](http://phpmyadmin), and that gave me my 1st site. So then I put in [http://localhost/phpmyadmin,and](http://localhost/phpmyadmin,and) Yes I got the phpmyadmin GUI; Hooray. So then I tried [http://css/phpmyadmin](http://css/phpmyadmin) and [http://sonomasport/phpmyadmin](http://sonomasport/phpmyadmin), and they both worked.

But why?? I know it has something to do with the /etc/conf.d/fqdn file

---

