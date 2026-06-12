---
title: "Domain Setup | Home Based  Web Server"
date: 2011-01-17
forum: Server Platforms
---

### Post by cold.nut on 2011-01-17
Hey guys ;)

I have setup a home based web server to host a photo blog for myself and my friends. I will be running wordpress and possibly a phpbb3 forum. I'd like to open this to discuss server administration, server setup, and server maintenance. However, I have a pretty good start on all of those but serving a domain name to my static ip.

Here my static ip is 24.10.202.144. I registered a domain through godaddy.com (coldnut.com). It appears that I have the domain working to forward to my ip. However, I am still getting this output file from apache.

```
administrator@server:~$ sudo /etc/init.d/apache2 restart
sudo: unable to resolve host coldnut.com
 * Restarting web server apache2                                                apache2: apr_sockaddr_info_get() failed for coldnut.com
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
 ... waiting apache2: apr_sockaddr_info_get() failed for coldnut.com
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ OK ]
administrator@server:~$
```**Notice: **Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

I have tested the domain name across a few different computers on different ips. It works appropriately. I just want to make sure I have it set correctly on the (apache) server side of things. Then I can get more into Zone Editing etc..

But for now, how about some input!

Thanks in advance guys! Great community over here \\:D/

---

### Post by cold.nut on 2011-01-18
bump for assistance! ;)

---

### Post by volkswagner on 2011-01-18
What's the output of the following commands?

```
hostname
```

```
hostname -f
```

```
cat /etc/hosts
```

You can try to simply edit /etc/hosts by adding one line such as the following.

```
xxx.xxx.xxx.xxx servername servername.coldnut.com
```

Replace the above with your static ip, output from hostname, and output from hostname -f.  If both hostname and hostname -f yield the same result, you only need one entry with the ip above.

Having hostname and hostname -f, match is recommended by some, but is beyond my expertise to tell you how to accomplish it.

---

### Post by cold.nut on 2011-01-19
hostname & hostname -f were the same. however, i made this adjust and it doesn't give me the error anymore! :D

Old Code:
```
127.0.0.1       localhost
127.0.1.1       [www.coldnut.com]("http://www.coldnut.com") server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```New Code:
```
127.0.0.1       localhost
127.0.1.1       server.coldnut.com

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```worked like a charm! easy fix, thanks!

---

### Post by cold.nut on 2011-01-19
Now I need to figure out how to create variables to forward my domain to a subdomain. So I can access blog through blog.coldnut.com etc..
 
I will stay in touch! :)

---

### Post by volkswagner on 2011-01-19
For a subdomain you will make a DNS entry at godaddy.  Make an A record or CNAME for your sub, pointing to your static ip.

Then create an Apache2 virtual host for the sub domain, Apache2 will sort the requests.

---

### Post by volkswagner on 2011-01-19
For a subdomain you will make a DNS entry at godaddy.  Make an A record or CNAME for your sub, pointing to your static ip.

Then create an Apache2 virtual host for the sub domain, Apache2 will sort the requests.

---

### Post by volkswagner on 2011-01-19
For a subdomain you will make a DNS entry at godaddy.  Make an A record or CNAME for your sub, pointing to your static ip.

Then create an Apache2 virtual host for the sub domain, Apache2 will sort the requests.

---

### Post by volkswagner on 2011-01-19
EDIT: Ouch... server error... Did not mean to post sooooo many times.

---

### Post by cold.nut on 2011-01-20
> **volkswagner said:**
> For a subdomain you will make a DNS entry at godaddy. Make an A record or CNAME for your sub, pointing to your static ip.
 
Then create an Apache2 virtual host for the sub domain, Apache2 will sort the requests.
 
thanks! sounds good ;)
 
shouldn't be too difficult. just need to get my wordpress blog working now.
 
i have wordpress 3.0.4 uploaded to my default website directory /var/www. it won't let me update or install themes though. it asks for my ftp credentials. however, i have all ports blocked but 22 (SSH) and 80 (HTTP). So, ftp obviously wont work. But I shouldn't need ftp credentials to auto update or to install themes. I have also tried giving 777 permissions to the wp-content folder and subfolders.

---

### Post by cold.nut on 2011-01-21
wordpress correctly configured!

```
sudo chown -R www-data: /var/www
```

worked like a charm! i was a little confused on the use of chown. got it all figured out now though. check it out if you would like! [www.coldnut.com](www.coldnut.com)

if you find any security risks etc.. let me know! from here i plan on making a static link on my blog to my forums. [www.coldnut.com/forums](www.coldnut.com/forums)

i am pumped! :) thanks for the help guys!

cold.nut

---

