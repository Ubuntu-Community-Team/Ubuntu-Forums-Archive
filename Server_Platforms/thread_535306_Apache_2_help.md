---
title: "Apache 2 help"
date: 2007-08-26
forum: Server Platforms
---

### Post by angelus_kit on 2007-08-26
Dear all 

i need your help for configuring Apache 2 on my server ubuntu, i just install the web server apache 2 trougth the synaptic, and when i seek the listner por i find the

 tcp tcp        0      0 0.0.0.0:80              0.0.0.0:*    is ok and when i try to connect trough my network the home page apache is ok.

but i need to help how i can to publish my web page or can you indicate me the url 

Best Regard

---

### Post by southernman on 2007-08-26
Not entirely sure I understand the question but will give it a shot anyway.

If you are asking about how to make it so others can see your site, then you need one of two things... maybe both depending where you get a domain from.
1- A domain name of course... or
2- Use a service such as zoneedit or dyndns.

If your asking how to build your webpage, a couple of many alternatives are:
1- Bluefish
2- Gedit

If none of that is what your asking for, please clarify.

---

### Post by freebeer on 2007-08-26
So let me understand:

You've installed apache and you can load the pages from your internal network.  Now you need to be able to have people see your website from the internet?  

There's several ways to do this.  I'm presuming that you want to continue hosting the site on your own machine.  

If you are behind a router, you'll need to forward port 80 (usually) to the server.  And you'll need to give anyone on the internet your IP address.  If you want to be able to use a domain name (ie [www.angelus.org](www.angelus.org) or whatever) you'll need to get a domain name that points to your IP address.  If you have a dynamic IP address, you may want to check out [www.dyndns.org](www.dyndns.org).

I hope that helps some.

---

### Post by angelus_kit on 2007-08-29
hi 

ok sorry for my bad english, i will explaine you the situation, i installed the web server apache2 on my server ubuntu. 
my problem, i need how to configure apache 2 ? could  you please  to help  me how i can configure the Web apache2 with  example step by step or you give me the link 

thanks you for your help 
sorry for my poor english :(
Best Regard

---

### Post by az on 2007-08-29
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by kaloz on 2007-08-29
Hi everyone!

i installed the LAMP server and the browser 
show nothing ([http://localhost/](http://localhost/)). Not responding when i try to start the apache server. 

root@kaloz-desktop:/# /etc/init.d/apache2 start
root@kaloz-desktop:/#
root@kaloz-desktop:/# /etc/init.d/apache2 status
root@kaloz-desktop:/#  
root@kaloz-desktop:/# /etc/init.d/apache2 stop
 * Stopping web server (apache2)...                                                                                      [ OK ] 
root@kaloz-desktop:/# 
root@kaloz-desktop:/# /etc/init.d/apache2 stop
 * Stopping web server (apache2)...                                                                                      [ OK ] 
root@kaloz-desktop:/# 

please help :confused:

---

### Post by freebeer on 2007-08-29
If it's responding to the stop command, as it appears to be, and you're not getting any errors with the start command, then I'd say it's running.

but you can use this command to check which processes are running:

```

ps -e | grep apache2

```
  

Have you use a browser to test?

---

### Post by kaloz on 2007-09-08
root@kaloz-desktop:~# ps -e | grep apache
root@kaloz-desktop:~# ps -e | grep apache2
root@kaloz-desktop:~# 

i'm tried and show nothing. I think the apache doesn't running

---

### Post by kaloz on 2007-09-08
Yes, I use the firefox to testing

---

### Post by kaloz on 2007-09-09
somehow can I uninstall and remove all settings of lamp server?
I thing "apt-get remove ***** " doesn't remove the settings

---

