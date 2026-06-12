---
title: "Forbidden  You don't have permission to access / on this server."
date: 2011-01-11
forum: Server Platforms
---

### Post by Neo@Matrix on 2011-01-11
This is my first post at this forum and I'll try to make it as simple as I can.
Running few servers of my own and now I faced a problem I wasn't able to solve.
On Apache server I have installed EHCP for my domains.For some a time it worked smoothly. Now two of my hosted domains  gave > **Forbidden**

 You don't have permission to access / on this server.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.6 with Suhosin-Patch Server at xxx.xx.xxx..x Port 80


 for visitors.
Also the mail server ( on my default domain ) refuses to accept the domain ,but works like charm on > [http://my.ip.xx.xx./ehcp/webmail/src/login.php](http://my.ip.xx.xx./ehcp/webmail/src/login.php) .  
Main domain works fine and accepts connection on [http://exampledomain.info](http://exampledomain.info)

Do anyone have some idea where to start? I checked the error log and found nothing related to the issue. 

Thank U all in advance for taking time to read my post & for good will. 

> [SIZE=2]**Operating system**[/SIZE] [SIZE=2]Ubuntu Linux 9.10[/SIZE]   [SIZE=2]**Webmin version**[/SIZE] [SIZE=2]1.530[/SIZE]   [SIZE=2]**Time on system**[/SIZE] [SIZE=2][Wed Jan 12 01:32:43 2011]("https://192.168.1.6:10000/time/")[/SIZE]   [SIZE=2]**Kernel and CPU**[/SIZE] [SIZE=2]Linux 2.6.31-22-server on x86_64[/SIZE]   [SIZE=2]**Processor information**[/SIZE] [SIZE=2]AMD Athlon(tm) 64 X2 Dual Core Processor 4800+, 2 cores[/SIZE]   [SIZE=2]**System uptime**[/SIZE] [SIZE=2]11 hours, 12 minutes[/SIZE]   [SIZE=2]**Running processes**[/SIZE] [SIZE=2][224]("https://192.168.1.6:10000/proc/")[/SIZE]   [SIZE=2]**CPU load averages**[/SIZE] [SIZE=2]0.07 (1 min) 0.15 (5 mins) 0.12 (15 mins)[/SIZE]   [SIZE=2]**CPU usage**[/SIZE] [SIZE=2]1% user, 1% kernel, 0% IO, 99% idle[/SIZE]   [SIZE=2]**Real memory**[/SIZE] [SIZE=2]3.87 GB total, 764.32 MB used[/SIZE]

---

### Post by wongo888 on 2011-01-11
First thing to do is to look at your apache error logs and post the entries returning 403 errors. 

Did you add or change any .htaccess entries?

---

### Post by James78 on 2011-01-12
> **wongo888 said:**
> **First thing to do is to look at your apache error logs and post the entries returning 403 errors.** 

Did you add or change any .htaccess entries?
Located at /var/log/apache/error.log OR the log file pointed to by the ErrorLog directive in your VirtualHost.

---

### Post by Neo@Matrix on 2011-01-12
Thanks for advices. 
It took quit some time to go through error log , but at the end non of that is related to 403!!!!! not a single line :confused:
I had a Power supply failure on the server but I don't  think it has affect on .htaccess files.
The beckup server took over temp and at the moment the log shows problems with resolving hostname.
I'll check the .htaccess files manually now , to make sure that are ok.](*,)

---

### Post by Neo@Matrix on 2011-01-12
:confused: One more thing... Any new added domain goes under forbidden ...:twisted:

---

### Post by bsntech on 2011-01-12
sounds like the root folder you have does not allow the www-data user to access it.

As an example - I have all of my domains in the /home folder and their folder would be /home/domain-tld

I received the forbidden errors as well.  You need to ensure that the root path, that /home folder in my case - allows at least read permissions for the www-data user.

In addition to this - is it possible you have directory listings shut off in your apache2.conf file?  If you do, there will be a line like this:

Options -Indexes

This will disallow directory listings.  So if you do not have the "DirectoryIndex" attribute set correctly for your virtual hosts, you will also receive this message.

As an example - "Options -Indexes" is set in the config and "DirectoryIndex index.htm" is set.  So, that means Apache will open the index.htm page and supply it to the visitor if they just type in domain.com/directory/ without a page name.  Now if index.htm is not in that folder and the real index file is say - index.php, you will also receive this message.

I may be off-base with this last recommendation - been too long since I've seen the error message - but the error message in this case may say directory listing denied.

Brian S.
[BsnTech Networks]("http://www.bsntech.com")

---

### Post by Neo@Matrix on 2011-01-19
The problem was a missing .htaccess file  :evil:
Now seams everything working fine.

Servers are still up and running ever since. 

Thank You all for assistance.

---

