---
title: "Change default port"
date: 2011-03-04
forum: Server Platforms
---

### Post by Code9 on 2011-03-04
I changed the default port under etc/apache2/ports.conf and now I cannot connect to my server under my local network. Any help?

---

### Post by Vegan on 2011-03-04
Why do you need to change the port?

---

### Post by Code9 on 2011-03-04
My ISP blocks the default port of 80, so I always change it to 8080.

---

### Post by Code9 on 2011-03-04
Is it possible that Apache didn't start when I rebooted? How do I start it, or see if it's running

---

### Post by wongo888 on 2011-03-04
Restart or start Apache:

```
S sudo apache2ctl -k graceful
```

---

### Post by Code9 on 2011-03-04
It said:


Syntax error on line 207 of /etc/apache2/apache2.conf
httpd not running, trying to start
Action -k graceful failed

---

### Post by wongo888 on 2011-03-04
You should fix the syntax error. This command will run a syntax check for you:

```
apache2ctl -t
```

---

### Post by hawkmage on 2011-03-04
If you have not changed the default user for Apache you use this command to show the processes running under the user www-data:
```
ps -fu www-data
```To see what IP and Port Apache is bound to run this command:
```
sudo lsof -u www-data -a -i -n -P
```

---

### Post by Code9 on 2011-03-04
Just ran it:

Syntax error on line 207 of /etc/apache2/apache2.conf
Invalid Command 'Idocumebntnclude', perhaps misspelled or defined by a module not included in the server configuration 
Action -t failed

---

### Post by Code9 on 2011-03-04
> **hawkmage said:**
> If you have not changed the default user for Apache you use this command to show the processes running under the user www-data:
```
ps -fu www-data
```

To see what IP:Port Apache is bound to run this command:
```
sudo lsof -u www-data -a -i -n -P
```

1st one:
I don't see anything

2nd one:
Nothing again

---

### Post by hawkmage on 2011-03-04
That with the fact you got the error "Invalid Command 'Idocumebntnclude'" tells me that Apache is not starting.  What is the directive you trying to use?

---

### Post by wongo888 on 2011-03-04
I'm guessing that there is a spelling error on line 207 of the following file:

*/etc/apache2/apache2.conf*

BTW, your customizations should be put into:

*/etc/apache2/httpd.conf*

Back in the day someone told me to keep *apache2.conf *pristine because your updater thing could overwrite it during a future upgrade.

---

### Post by Code9 on 2011-03-04
> **hawkmage said:**
> That with the fact you got the error "Invalid Command 'Idocumebntnclude'" tells me that Apache is not starting.  What is the directive you trying to use?

I am assuming you mean directory? home/user

---

### Post by Code9 on 2011-03-04
> **wongo888 said:**
> I'm guessing that there is a spelling error on line 207 of the following file:

*/etc/apache2/apache2.conf*

BTW, your customizations should be put into:

*/etc/apache2/httpd.conf*

Back in the day someone told me to keep *apache2.conf *pristine because your updater thing could overwrite it during a future upgrade.

On that line it says

# Include all the user configurations:
Idocumebntnclude httpd.conf

so there seems to be a spelling error

---

### Post by wongo888 on 2011-03-04
If you are trying to pull in conf files from your home directory then the syntax is "Include" not "DocumentInclude":

[http://httpd.apache.org/docs/current/mod/core.html#include](http://httpd.apache.org/docs/current/mod/core.html#include)

Apache is trying to help you.

---

### Post by hawkmage on 2011-03-04
I meant "directive" not directory.  

That line should be:
```
Include httpd.conf
```not 
```
Idocumebntnclude httpd.conf
```

---

### Post by Code9 on 2011-03-04
> **wongo888 said:**
> If you are trying to pull in conf files from your home directory then the syntax is "Include" not "DocumentInclude":

[http://httpd.apache.org/docs/current/mod/core.html#include](http://httpd.apache.org/docs/current/mod/core.html#include)

Apache is trying to help you.

Thanks dude, changing that one line worked. Do you have any idea how it changed?

---

### Post by Code9 on 2011-03-04
Let me change the port back to 8080 and see if I can connect.

---

### Post by Code9 on 2011-03-04
Kinda worked, I can access it when I type 192.168.0.105 but I can't get to it with 192.168.0.105:8080

---

### Post by wongo888 on 2011-03-05
You could try putting this into your httpd.conf, it would open both port 80 and 8080:

```
Listen 80
Listen 8080
```

Restart Apache

```
$ sudo apache2ctl -k graceful
```

---

### Post by Code9 on 2011-03-05
The restart command said:

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

I don't need to do something to the apache.conf file do I?

---

### Post by wongo888 on 2011-03-05
You can add a ServerName directive to httpd.conf or just ignore it. I usually ignore it.

[http://httpd.apache.org/docs/2.2/mod/core.html#servername](http://httpd.apache.org/docs/2.2/mod/core.html#servername)

---

### Post by Code9 on 2011-03-05
I noticed your telling me to edit httpd.conf instead of ports.conf. Should I remove the values in ports.conf and put them in httpd.conf instead?

Do I just type them into httpd.conf like I see it in ports.conf?

---

### Post by wongo888 on 2011-03-05
I always just put my Apache directives in httpd.conf. I believe it is included last. I also work with RHEL/CentOS, so sometimes there is crosstalk in what I think I know. 

If it is working then I'd say you're done.

---

### Post by Code9 on 2011-03-05
Nevermind, I was putting Listen: 8080 instead of Listen 8080. Thanks for your help

---

