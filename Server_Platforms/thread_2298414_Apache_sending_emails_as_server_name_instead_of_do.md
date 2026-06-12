---
title: "Apache sending emails as server name instead of domain name"
date: 2015-10-10
forum: Server Platforms
---

### Post by michaelebsch on 2015-10-10
I have tried searching for the way to resolve this problem before posting here, but honestly I am just having a brain-fart when it comes to the search parameters to use to find my answer. So, my apologies if this question has been answered dozens of time already.

I have a server running in a small office for a group of sales associates, its primary functions are as a samba file server and to host a Joomla based project management system. Originally this project management site was not intended to be accessed outside the office so all email functions from the site where disabled and access to the server was blocked by the firewall. Recent changes have required access to the site from outside the office and email notifications to be sent via the internally hosted site. Everything has been working great so far, but the problem I have run into is this. When the site is accessed from the internal network they browse the page using the server name ex: [http://localservername](http://localservername) and outside the office it would be the domain name tied to the IP for the office. Anytime there are changes to a project, the group is notified via email and it provides a link back to the specific project that the changes where made in. When changes are made from inside the office, the server sends an email with a link like so:
[http://*localservername](http://*localservername)*/project/2015-10-10/projectname, when changes are made while accessing via the domain name then it sends the email with a link like so: [http://outsideofficeaccess.com/project/2015-10-10/projectname](http://outsideofficeaccess.com/project/2015-10-10/projectname)

How do I force the system to send the email using only the domain name and never the local server name?

The server is running Ubuntu server 14.04 x64 and I am using Apache to host the page.

---

### Post by SeijiSensei on 2015-10-11
You can use the same name inside and outside if you either (a) set up a local DNS server in your office to handle requests for your domain, or, easier, (b) add an entry to /etc/hosts on any relevant machines that links the server's internal IP address to its public named. Make sure the server's own name is identical to its public name.

In Apache you should have a virtual host configuration in /etc/apache2/sites-available/ that uses the public hostname as well.  

If you're using Postfix, you may need to make some changes to its configuration as well.  Read this: [http://www.postfix.org/ADDRESS_REWRITING_README.html](http://www.postfix.org/ADDRESS_REWRITING_README.html)

---

### Post by michaelebsch on 2015-10-12
Sorry, I see I forgot to mention that the office IP is actually tied to a sub-domain, so DNS and email are handled by the main domain's hosting. The office server connects to the hosted email through SMTP, no local email server running currently.

Can I configure the sub-domain name into the Apache virtual host configuration so that it sends links based on that config and not based on browser data?

---

### Post by SeijiSensei on 2015-10-12
Use the "ServerAlias" directive in the Apache configuration to give the server alternative names.  That only applies to how Apache knows which configuration to use, though.  What matters more is the server's actual hostname.  

Assign the hostname you want to use to 127.0.1.1 in /etc/hosts:
```

127.0.0.1       localhost
127.0.1.1       myhost.example.com

```
Then run "sudo service hostname restart".  If you run the command "hostname -f" you should see the fully-qualified name "myhost.example.com".  The command "hostname" by itself should return just "myhost".

That may or may not be enough to force the hostname on outbound messages.  Give that a try, then see what happens.

---

### Post by michaelebsch on 2015-10-12
I will try that, thank you.

---

