---
title: "Am I walking around with an unsecure server? laptop questions."
date: 2012-10-19
forum: Security
---

### Post by factotum218 on 2012-10-19
I've been dabbling in web development for a while now and have come back to Linux after some time with Windows 7. I've considered a Mac but it's just not in the budget.

My question involves the LAMP setup I have on my laptop for local dev work with Drupal and the like.

With Windows I set up XAMPP or WAMP, installed whatever framework/CMS I was working on and went on from there. Is there any differences between running XAMPP and having a full blown LAMP setup on my laptop? Am I walking around from home to coffee shop to library to school with an insecure server under my arm? I'm not concerned about anything being taken off my laptop, help yourself for all I care. But I wonder if it can lead to other security issues like rootkits and the like. I have passwords for everything like phpmyadmin, and mysql.

I just want to know if there are any other security related things beyond a strong password that I may not be considering for my dev setup.

Thank you.

---

### Post by cariboo on 2012-10-19
If you have port 80 open while your laptop is running, you could get people trying to connect to your web server.

If you have another computer system, you can check it by using nmap (available in the repositories) to see what ports are listening on your laptop.

Running a basic firewall should block anyone from accessing your system. To turn on the firewall, open a terminal and type:

```
sudo ufw enable
```

---

### Post by Ms. Daisy on 2012-10-20
I second what cariboo907 said. 

You also need to understand that a LAMP server runs the web server & the mysql database all on the same machine. That's not the most secure way to do it- you really don't want a sql server directly facing the internet.  There are ways to make it more secure (like iptables, fail2ban, apparmor, probably some others). Read the security sticky in this forum for more on that.

Yes, running the LAMP server can lead to other security issues if you haven't properly secured it. There are automated bots crawling the web looking for poorly-configured web servers.  An attacker could gain access & use it to send spam, include it in a bot-net, use it in a DDoS attack... Aside from the obvious security problems associated with these attacks, that would seriously slow down your dev environment.

Don't know if you could use virtual machines on your computer, but I hope you consider it.  You could have a host-only network- that way you could have a dev environment that's never going to touch the interwebz unless you bridge the network when you need to.

I can't even imagine running a LAMP server from free wifi.  Is that a thing that people actually do?

---

### Post by Cheesemill on 2012-10-20
You can tell Apache to only listen to requests from localhost, this way it won't be accessible from any other machine.

Also running a LAMP server on Ubuntu is way more secure than running XAMPP on Windows, even without taking any additional steps after installation. XAMPP is deliberately configured with an open security policy to aid speed of development. Quoted from the XAMPP website:
> 
     XAMPP is not meant for production use but only for developers in a  development environment. XAMPP is configured is to be as open as  possible and to allow the web developer anything he/she wants. For  development environments this is great but in a production environment  it could be fatal. 
       Here a list of missing security in XAMPP: 
  
[LIST]
[*]The MySQL administrator (root) has no password.
[*]The MySQL daemon is accessible via network.
[*]phpMyAdmin is accessible via network.
[*]The XAMPP demopage is accessible via network.
[*]The default users of Mercury and FileZilla are known.
[/LIST]
       All points can be a huge security risk. Especially if XAMPP is  accessible via network and people outside your LAN. It can also help to  use a firewall or a (NAT-) router. In case of a router or firewall, your  pc is normally not accessible via network. It is up to you to fix these  problems. As a small help there is the "XAMPP Security console". 
           Please secure XAMPP before publishing anything online. A firewall or  an external router are only sufficient for low levels of security. For  slightly more security, you can run the "XAMPP Security console" and  assign passwords.

---

