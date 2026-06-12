---
title: "Local (development) LAMP stack security"
date: 2011-09-23
forum: Server Platforms
---

### Post by newish_to_linux on 2011-09-23
I have the LAMP stack installed on Ubuntu 11.04.  I want to make sure this local development environment is secure from outside my home wireless network (on which I enable WPA2 personal).  

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

At the above link, under "Securing Apache", it says all I need to do is add "Listen 127.0.0.1:80" to "ports.conf".  Is there a way I can test that does the job?  And is there anything else you would recommend? Are no changes required to httpd.conf/.htaccess files?

Also, I work with multiple CMS's like Drupal, Magento, etc.  Will this interfere with any CMS backend codebase updates, such as "update.php" with Drupal.

I'd be grateful for any insight into these questions from those who have a similar setup.

---

### Post by Dangertux on 2011-09-23
> **newish_to_linux said:**
> I have the LAMP stack installed on Ubuntu 11.04.  I want to make sure this local development environment is secure from outside my home wireless network (on which I enable WPA2 personal).  

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

At the above link, under "Securing Apache", it says all I need to do is add "Listen 127.0.0.1:80" to "ports.conf".  Is there a way I can test that does the job?  And is there anything else you would recommend? Are no changes required to httpd.conf/.htaccess files?

Also, I work with multiple CMS's like Drupal, Magento, etc.  Will this interfere with any CMS backend codebase updates, such as "update.php" with Drupal.

I'd be grateful for any insight into these questions from those who have a similar setup.

I'm not sure the question is so much about the security of the LAMP stack, because by your logic if your local network is secure, and Apache is confined within the local network so is Apache.

That being said, you can use .htaccess to limit access only to localhost, if you are only accessing the server from the system that is running it.

But honestly I would focus on the security of the network over the security of the LAMP stack, if it is only bound locally.

---

### Post by CharlesA on 2011-09-23
You can also tell apache to only listen on localhost.

Otherwise, if your local network is secure, you're fine.

---

### Post by newish_to_linux on 2011-09-23
Thanks for the response Dangertux.

I'm probably not explaining my goal properly.  Basically, I want to ensure no one can access the server from another machine, whether that be another machine on my home network or from the internet.

If I tell Apache to only listen to 127.0.0.1:80, will I achieve my goal?  And can you recommend how I might test this?  Thanks again for any insight.

---

### Post by CharlesA on 2011-09-23
You can do that, yep.

Otherwise firewall whatever port it's listening on the external address with iptables.

---

### Post by newish_to_linux on 2011-09-23
> **CharlesA said:**
> You can also tell apache to only listen on localhost.

Otherwise, if your local network is secure, you're fine.

Thank you Charles.  Being the relative noob that I am, could you elaborate (such as any online tutorials/resources) a bit as to what is implied by a "secure network" with regard to the Ubuntu OS?

---

### Post by CharlesA on 2011-09-23
> **newish_to_linux said:**
> Thank you Charles.  Being the relative noob that I am, could you elaborate (such as any online tutorials/resources) a bit as to what is implied by a "secure network" with regard to the Ubuntu OS?
It's mostly making sure that no unauthorized people are on your network.

---

