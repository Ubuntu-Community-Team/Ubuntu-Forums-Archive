---
title: "Apache2 on 6.06 LTS Server: IP No Host"
date: 2007-02-15
forum: Server Platforms
---

### Post by GoJimbo on 2007-02-15
Just installed 6.06 LTS Server on a new Dell PowerEdge 1950 and I can't seem to get apache2 configured properly.  I know its something silly that I'm overlooking because I have a test machine configured more or less the same and it works.  I'm only hosting one site on this machine.

When I browse to [http://xxx.xx.xxx.xx/](http://xxx.xx.xxx.xx/) I get a 403 Forbidden.
When I browse to [http://hostname.edu/](http://hostname.edu/) I get Server Not Found.

If I browse to [http://xxx.xx.xxx.xx/index.php](http://xxx.xx.xxx.xx/index.php) I retrieve my index page.
If I browse to [http://hostname.edu/index.php](http://hostname.edu/index.php) I get Server Not Found.

Tried changing the permissions (chmod 755).

My /etc/apache2/sites-available is below.  Thanks in advance for any advice.

```
NameVirtualHost  hostname.edu:80 
<VirtualHost hostname.edu:80>
           Document Root /var/www
<Directory />
           Options FollowSymlinks
           Allow Override None
</Directory>
<Directory /var/www/hostname.edu>
           Options Indexes FollowSymLinks MultiViews
           Allow Override None
           Order allow, deny
           allow from all
</Directory
```

---

### Post by jtc on 2007-02-15
Are you sure this line is correct?

> <Directory /var/www/hostname.edu>

It doesn't really match well with your DocumentRoot. By the way, it seems as if you have aspace inside DocumentRoot, (Document Root) which shouldn't be there.

Those things ought to explain why you get diffrent results with your ip-number, with or without index.php, since you don't get the options Indexes enabled properly. I'm less sure why it won't work with your hostname.

---

### Post by Brazen on 2007-02-15
> **jtc said:**
> Are you sure this line is correct?



It doesn't really match well with your DocumentRoot. By the way, it seems as if you have aspace inside DocumentRoot, (Document Root) which shouldn't be there.

Those things ought to explain why you get diffrent results with your ip-number, with or without index.php, since you don't get the options Indexes enabled properly. I'm less sure why it won't work with your hostname.

Yeah OP, my guess is you want to change that line to```
<Directory /var/www>
```and then your index page should be returned automatically.

As for getting Server Not Found when using the domain name, try pinging hostname.edu and see if it returns the ip address of xxx.xx.xxx.xx.  If it doesn't, then you have a dns problem.

---

### Post by GoJimbo on 2007-02-16
I changed the directory line and documentroot then restarted apache but the result is the same.

Did not get a response when I pinged the hostname.  Going to email the network manager and ask him to look into it.

Thanks.

---

### Post by Brazen on 2007-02-16
add this directive: ```
DirectoryIndex index.php
```

It can either go under your Directory section or just anywhere within the virtualhost.

---

### Post by jtc on 2007-02-16
I wonder if this might be the issue.

> NameVirtualHost  hostname.edu:80 
<VirtualHost hostname.edu:80>

Have you tried replacing hostname.edu with the ip-address, or simply a * as a wildcard?

This of course won't make [http://hostname.edu/](http://hostname.edu/) work, but it might have something to do with your virtualhost being properly read.


...and just to be sure. When you lookup your hostname.edu, you do get the same ip-address you think you should get, right?

---

### Post by GoJimbo on 2007-02-21
Turned out to be a DNS issue, spoke to the network manager on campus and we resolved the problem.  I had been using this hostname and IP configuration on an earlier machine that crashed and just assumed they would work on the new server.

It makes sense now because when I first setup the machine I could not ssh to it via the hostname, only by IP.  Shortly after he made the necessary DNS entry I was able to browse to the hostname and ssh also.

Thanks for all your suggestions.

---

