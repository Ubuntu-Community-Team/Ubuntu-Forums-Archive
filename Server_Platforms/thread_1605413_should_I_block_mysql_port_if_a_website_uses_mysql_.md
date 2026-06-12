---
title: "should I block mysql port if a website uses mysql backend"
date: 2010-10-25
forum: Server Platforms
---

### Post by tapas_mishra on 2010-10-25
I am not clear with this situation if a website is running and uses  mysql as a backend the place where I apply IPTABLES,if I block mysql  port would that hinder with working of my website.

---

### Post by koenn on 2010-10-25
you might want to rewrite your post in 2 to 4  sentences, because as it is now it's rather difficult to understand what your trying to say.

In any case. your webserver needs to be able to talk to your mysql, the clients (ie the browsers that visit your site) do not. So you set up iptables accordingly.

---

### Post by SeijiSensei on 2010-10-26
Usually the SQL server is bound to the 127.0.0.1 interface in applications like this.  It's not visible on other network interfaces like eth0.  This arrangement enables the web server software to talk to the SQL server, but no one outside the box can connect.

---

### Post by tapas_mishra on 2010-10-26
> **SeijiSensei said:**
> Usually the SQL server is bound to the 127.0.0.1 interface in applications like this.  It's not visible on other network interfaces like eth0.  This arrangement enables the web server software to talk to the SQL server, but no one outside the box can connect.
Ok how can I verify this any idea or suggestions for this?

---

### Post by SeijiSensei on 2010-10-26
> **tapas_mishra said:**
> Ok how can I verify this any idea or suggestions for this?

Well, if it's your website, perhaps you wrote the code that connects to the database?  How does it accomplish this?  Does it talk to "localhost" or 127.0.0.1, to a different address, or does it not use a host at all (using what's known as a "local socket" instead)?  

By default, MySQL on Ubuntu listens only on 127.0.0.1.  You can verify this by looking at the bind-address entry in /etc/mysql/my.cnf.

---

### Post by BobVila on 2010-10-26
Given what's been posted so far, block it. If you didn't modify the default setup, nothing will break.

---

### Post by koenn on 2010-10-26
> **BobVila said:**
> Given what's been posted so far, block it. If you didn't modify the default setup, nothing will break.

hm - it would depend on whether the dbms and the web server are on the same machine or not, and possibly also on where the firewall is located.
but assuming database and web server are on the same machine and talking through the localhost address or an other local ipc mechanism, yes, only access to the webserver needs to be allowed.

---

### Post by hawk2010 on 2010-10-27
If you mysql db and the web site is on the same server this is not an issue since it only listens to the loopback address. even if you block the default port from the eth0 interface it won't hinder the ops. but if the mysql db is physically or virtually in another server then you may need to create IP & port based rules.

---

### Post by tapas_mishra on 2010-10-27
> **hawk2010 said:**
> If you mysql db and the web site is on the same server this is not an issue since it only listens to the loopback address. even if you block the default port from the eth0 interface it won't hinder the ops. but if the mysql db is physically or virtually in another server then you may need to create IP & port based rules.
Ok that  makes it clear but how to know which service depends upon loopback address and which not?

---

### Post by hawk2010 on 2010-10-27
Simply type netstat -a which gives the service ports

---

### Post by tapas_mishra on 2010-10-27
I want to know if it is documented some where how is it decided the services running on loopback address.

---

### Post by yesrno on 2010-10-27
If you don't have any special set-up where sql connects to a remote server... You'll be fine blocking it. Even if you block it and the websites looks 'screwed up' you can just unblock it ? Takes less than 10 seconds to find out it's is screwed or not.

---

### Post by tapas_mishra on 2010-10-27
> **yesrno said:**
> If you don't have any special set-up where sql connects to a remote server... You'll be fine blocking it. Even if you block it and the websites looks 'screwed up' you can just unblock it ? Takes less than 10 seconds to find out it's is screwed or not.

I was expecting this reply from some one.
The current setup does not have mysql configured I would be blocking in coming time so I asked.
Also I want to block many more ports so I want to know if there is a comprehensive list such as 
/etc/protocol or /etc/services 
some thing similar to above files which can tell me what service or daemons use loopback address.

---

### Post by the_original_billq on 2010-10-27
When it comes to firewalls, rather than determine what needs to be closed, it's usually much easier to determine what needs to be open.

Block everything, then open only what you need:

22 sshd (if you ssh in remotely)
80 httpd
443 https

Do you provide your own services to the internet?

21 ftp
25 smtp
53 dns
110 pop3
115 sftp
119 nntp
143 imap

See /etc/services for more.  If you're only serving up a website, 80 and 443 are likely the only ports you need open.

-Bill

---

### Post by koenn on 2010-10-27
> **tapas_mishra said:**
> 
Also I want to block many more ports so I want to know if there is a comprehensive list such as 
/etc/protocol or /etc/services 
some thing similar to above files which can tell me what service or daemons use loopback address.

The address(es) a service binds to (= "listens on") is a configurable option. So this may vary by how the software was compiled, or the default config that came with the package. If you're setting up a service, you 'd usually have at least 1 look at its config file to see what the software will behave like and whether there's something you want different. 
So, as this depends on decisions by developers, distro's, and package maintainers, there's no one grand list. 


Besides that, the_original_billq is right - usual practice for firewalling a server is block everything, then allow access to the service  ports that are relevant for that server

---

