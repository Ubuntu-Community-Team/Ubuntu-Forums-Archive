---
title: "Apache's log rotation - deleting more than just logs"
date: 2006-12-27
forum: Server Platforms
---

### Post by Samui on 2006-12-27
Hello. I've searched through your forums and Google, and found no answer to this one issue I am having. I am not sure if this is an exclusive problem, maybe I configured something wrong, or something like that. But anyways -- I am wondering why my Apache's log rotation script is deleting literally everything on the server with the word "log" in their filenames.

I'm not quite sure what information you would need - other than the fact that I am running Ubuntu Edgy Eft Server. I acquired Apache (2.0.55), PHP (4.3), and MySQL (4.1) using aptitude. 

This issue came up just recently. Before that, Apache would just spontaneously die on a Sunday morning at 6:25am, and not come back up because port 80 was still open. That problem had been resolved, yet, logrotate would just delete everything (possibly owned by www-data) with the word "log" in it.

Any ideas for solutions to this? If you need to know more information in order to be able to help, let me know.

Thanks in advance.

---

### Post by evilghost on 2006-12-27
That's nuts.  What's the content of /etc/logrotate.d/apache2

This is mine:

```

luser@VMHOST:/etc/logrotate.d$ cat apache2
/var/log/apache2/*.log {
        weekly
        missingok
        rotate 52
        compress
        delaycompress
        notifempty
        create 640 root adm
        sharedscripts
        postrotate
                if [ -f /var/run/apache2.pid ]; then
                        /etc/init.d/apache2 restart > /dev/null
                fi
        endscript
}
luser@VMHOST:/etc/logrotate.d$ 

```

---

### Post by Samui on 2006-12-27
content of the apache2 logrotate script:

/var/log/apache2/*.log {                                                                                                
        weekly                                                                                                          
        missingok                                                                                                       
        rotate 52                                                                                                       
        compress                                                                                                        
        delaycompress                                                                                                   
        notifempty                                                                                                      
        create 640 root adm                                                                                             
        sharedscripts                                                                                                   
        postrotate                                                                                                      
                if [ -f /var/run/apache2.pid ]; then                                                                    
                        /etc/init.d/apache2 restart > /dev/null                                                         
                fi                                                                                                      
        endscript                                                                                                       
}

---

### Post by evilghost on 2006-12-27
What all do you have running in cron/anacron?

---

### Post by Samui on 2006-12-27
If you mean what's in my crontab, this is it:

> 
# /etc/crontab: system-wide crontab                                                                                     
# Unlike any other crontab you don't have to run the `crontab'                                                          
# command to install the new version when you edit this file.                                                           
# This file also has a username field, that none of the other crontabs do.                                              
                                                                                                                        
SHELL=/bin/sh                                                                                                           
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin                                                       
                                                                                                                        
# m h dom mon dow user  command                                                                                         
17 *    * * *   root    run-parts --report /etc/cron.hourly                                                             
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily                                 
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly                                
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly                               
#    


And it would have the standard items in cron -- I've left that well alone, so it should just have the defaults.

> 
cron.d:
php4

cron.daily:
apt  aptitude  bsdmainutils  find  logrotate  man-db  mysql-server  samba  standard  sysklogd

cron.hourly:

cron.monthly:
proftpd  standard

cron.weekly:
man-db  popularity-contest  sysklogd


---

### Post by evilghost on 2006-12-27
I dont' know what to say, this behavior seems very alien.  Are you running any PHP scripts/etc in Apache that may be compromised or doing unexpected things?

---

### Post by Brazen on 2006-12-27
this doesn't really answer your question, but Edgy should not be used if you want a stable server.  Edgy is meant to be more cutting edge by goal of the Ubuntu Foundation, which can introduce buggy behaivor.  Alternatively, Dapper is meant to be Ubuntu's rock solid version.  That was their goal at release and that will be how it is until the next LTS release in another year or two (or more, I don't know).

---

