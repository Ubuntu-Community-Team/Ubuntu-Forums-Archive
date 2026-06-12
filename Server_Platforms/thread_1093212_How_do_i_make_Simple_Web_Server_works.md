---
title: "How do i make Simple Web Server works??"
date: 2009-03-11
forum: Server Platforms
---

### Post by Grey08 on 2009-03-11
I m running Ubuntu Server 8.10, and installed Apache2, but i have the following problems;

1. The index.html under /var/www doesn't let me edit, it says i m not the owner, so i can not change it. What's wrong with this??? Who is the owner then?? (with command whoami, i m not root, so i have created root and i can only login under terminal)

2. I have solved dyndns, but port forwarding seems not working, this is because when i type [ [http://myip/index.html](http://myip/index.html) ] at web browser, it goes to my router. I m using DSL605EW, and i have followed all the instructions on how to set port forwarding that i searched from google. I have enable UFW as well, and i have allowed port 80.

3. All the configurations i followed already, but yet, it still goes to my router, WHY????

HELP ME PLEASE~!!!!!!! 

Thanks!

---

### Post by cdenley on 2009-03-11
Some routers will not port forward connections from a LAN address to the WAN IP. Some require you to enable a setting like "local loopback" and/or a firmware upgrade. It may still work for people connecting from outside your LAN.

The default index.html and /var/www are owned by root, I believe. You can change ownership or permissions on /var/www and index.html, or you can edit your web-accessible files as root by using the "sudo" command.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Grey08 on 2009-03-11
Thanks cdenley, i have solved the /var/www problem with login into root, and at firewall keeps showing " WARN /var is accessible"

The problem now, [ [http://myip/index.html]](http://myip/index.html]) is still showing my router's web config.

---

### Post by jojo1224 on 2009-03-11
> **Grey08 said:**
> Thanks cdenley, i have solved the /var/www problem with login into root, and at firewall keeps showing " WARN /var is accessible"

The problem now, [ [http://myip/index.html]](http://myip/index.html]) is still showing my router's web config.

The best way to check if your site is accessible is to check with a web based proxy (ex. [anonypath.com]("https://anonypath.com/")), so check there and if it still isnt then your router is blocking it.

---

### Post by Grey08 on 2009-03-11
Thanks jojo, i will try now.

---

### Post by Grey08 on 2009-03-11
Jojo, i have tried with web based proxy, and the index.html is accessible!!

What do i do now???

---

### Post by Grey08 on 2009-03-11
someone who knows this help please!!

---

### Post by cdenley on 2009-03-11
> **Grey08 said:**
> someone who knows this help please!!

Help how? As I already explained, your router probably will not port forward connections coming from inside the LAN. You can call the manufacturer of your router and attempt to see if there is a setting or firmware upgrade that can fix that, replace the router, or use the LAN IP from within your LAN.

---

### Post by Grey08 on 2009-03-11
What do u mean by using LAN IP from within my LAN? Do u mean use LAN IP to browse the site? If that's the case, users outside my LAN wouldn't able to browse my site then, right??

Ah, then i should have change my router then???

---

### Post by neilevan814 on 2009-03-12
Grey08, you can just access your site via your local network or your localhost 127.0.1.1 or 127.0.0.1 instead of using your WAN address to access from inside your local network.  Do you have a commercially purchased domain name?  I ask because if you are using a freename, you could use a service like dyndns.org to port forward your address from your router.  I did this because I have to use a dynamic host address because of my internet provider.  My router supports port forwarding and I am using a free domain name, or you can port forward if your router supports that function with a paid name...Do you know if your router can be configured to port forward?  Not sure if I am clear on all this myself, but maybe someone else can pick up from here.

---

### Post by cariboo on 2009-03-12
I would check [canyouseeme]("http://www.canyouseeme.org/")  to make sure your isp isn't blocking the ports you need. If port 80 is open, I would close it until your web site is ready to go live, then open up port 80 again.

Jim

---

### Post by amac777 on 2009-03-12
> **neilevan814 said:**
> Grey08, you can just access your site via your local network or your localhost 127.0.1.1 or 127.0.0.1 instead of using your WAN address to access from inside your local network.

If you have a real domain name (not just using your IP address), another solution is to edit the file /etc/hosts to point your domain to the local host. This way, you can still use your domain name in your browser like normal. (might be important if your website requires the proper domain name)

---

### Post by Grey08 on 2009-03-12
> **cariboo907 said:**
> I would check [canyouseeme]("http://www.canyouseeme.org/")  to make sure your isp isn't blocking the ports you need. If port 80 is open, I would close it until your web site is ready to go live, then open up port 80 again.

Jim


I have checked at the site canyouseeme, and it says [ Success: I can see your service on xxxxx on port (80) Your ISP is not blocking port 80 ]

this means the router is done with port forward now, right?

Then is that something wrong at ufw?? or what other possibility??

---

### Post by Grey08 on 2009-03-12
> **neilevan814 said:**
> Grey08, you can just access your site via your local network or your localhost 127.0.1.1 or 127.0.0.1 instead of using your WAN address to access from inside your local network.  Do you have a commercially purchased domain name?  I ask because if you are using a freename, you could use a service like dyndns.org to port forward your address from your router.  I did this because I have to use a dynamic host address because of my internet provider.  My router supports port forwarding and I am using a free domain name, or you can port forward if your router supports that function with a paid name...Do you know if your router can be configured to port forward?  Not sure if I am clear on all this myself, but maybe someone else can pick up from here.

Yes, i have applied and im using Dyndns now, whenever i type the URL, it goes to my router's config web instead of go to my index.html.

and, i have tried Webbased proxy, canyouseeme, both of them says that file under /var/www can be browse and isp not blocking, but still can't
browse the index.html

hmm, whats the problem actually???

---

### Post by cdenley on 2009-03-12
> **Grey08 said:**
> and, i have tried Webbased proxy, canyouseeme, both of them says that file under /var/www can be browse and isp not blocking, but still can't
browse the index.html

hmm, whats the problem actually???

What do you mean? Can users connect to apache from outside your LAN or not? Either run this command from OUTSIDE your LAN
```

echo -e "HEAD / HTTP/1.0\n" | nc [WAN IP] 80

```
or post your WAN IP or domain so someone else can. If you can connect to your apache server (not your router's admin page) from outside your LAN, then your router simply doesn't handle port forwarding for LAN users. If you can't connect from outside your LAN to apache (not your router's admin page), then you probably haven't configured your router properly. If you can connect from outside your LAN but get an apache error, then you have a server configuration problem.

---

### Post by Grey08 on 2009-03-12
i have checked the page [ [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) ]

Virtual Hosts

Apache2 has the concept of sites, which are separate configuration files that Apache2 will read. These are available in /etc/apache2/sites-available. By default, there is one site available called default this is what you will see when you browse to [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1). You can have many different site configurations available, and activate only those that you need.

As an example, we want the default site to be /home/user/public_html/. To do this, we must create a new site and then enable it in Apache2.

To create a new site:

    *

      Copy the default website as a starting point. sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite 
    *

      Edit the new configuration file in a text editor "sudo nano" on the command line or "gksudo gedit", for example: gksudo gedit /etc/apache2/sites-available/mysite
    *

      Change the DocumentRoot to point to the new location. For example, /home/user/public_html/
    *

      Change the Directory directive, replace <Directory /var/www/> to <Directory /home/user/public_html/>
    *

      You can also set separate logs for each site. To do this, change the ErrorLog and CustomLog directives. This is optional, but handy if you have many sites
    * Save the file 

Now, we must deactivate the old site, and activate our new one. Ubuntu provides two small utilities that take care of this: a2ensite (apache2enable site) and a2dissite (apache2disable site).

sudo a2dissite default && sudo a2ensite mysite

Finally, we restart Apache2:

sudo /etc/init.d/apache2 restart

If you have not created /home/user/public_html/, you will receive an warning message

To test the new site, create a file in /home/user/public_html/:

echo '<b>Hello! It is working!</b>' > /home/user/public_html/index.html

Finally, browse to [http://localhost/](http://localhost/)





I was wondering, could it be problem with Virtual host? If the answer is YES, then i think i have to follow the instruction above. There are some instructions above i do not understand, which are

1.Change the DocumentRoot to point to the new location. For example, /home/user/public_html/
#

2.Change the Directory directive, replace <Directory /var/www/> to <Directory /home/user/public_html/>
#

How do i change the document root and point to new location?? Where do i change Directory directive??

---

### Post by Grey08 on 2009-03-12
> **cdenley said:**
> What do you mean? Can users connect to apache from outside your LAN or not? Either run this command from OUTSIDE your LAN
```

echo -e "HEAD / HTTP/1.0\n" | nc [WAN IP] 80

```
or post your WAN IP or domain so someone else can. If you can connect to your apache server (not your router's admin page) from outside your LAN, then your router simply doesn't handle port forwarding for LAN users. If you can't connect from outside your LAN to apache (not your router's admin page), then you probably haven't configured your router properly. If you can connect from outside your LAN but get an apache error, then you have a server configuration problem.

With Webbased proxy, i could browsed the index.html, does this mean user outside my network is able to connect to the apache??

The command line [ echo -e "HEAD / HTTP/1.0\n" | nc [WAN IP] 80 ] is for linux, right? I have another pc but it is a windows Vista, what command should i use? [ ping WAN IP 80 ]?

---

### Post by Grey08 on 2009-03-12
Ok, i summarise the route i set up my server.

1.installed apache2
2.port forwarding 192.168.1.8:80 at router (DSL605EW - set PF at Servers, User and Custom PF) 
3.applied DDNS and saved it to router
4.enabled ufw and allowed 80/tcp,80/udp from anywhere

Is there any steps i have missed out??

---

### Post by cdenley on 2009-03-12
> **Grey08 said:**
> With Webbased proxy, i could browsed the index.html, does this mean user outside my network is able to connect to the apache??

The command line [ echo -e "HEAD / HTTP/1.0\n" | nc [WAN IP] 80 ] is for linux, right? I have another pc but it is a windows Vista, what command should i use? [ ping WAN IP 80 ]?

Sounds like everything is working properly to me. As I believe I explained in my first post and every post since, some routers will not obey port forwarding rules for users within your LAN. If the router sees a connection from the internet, such as a proxy server, me, or any random user not on your LAN, it will check your forwarded ports to see where to direct that connection. If you try connecting to your router's WAN IP from within your LAN, your router sees that the same as if connection to your router's LAN IP, and either gives you it's own web server (admin page), or simply doesn't check your port forwarding rules.

Different routers handle this situation differently. As I already said you have a few options:
-Try to find a setting which changes the way the router works in this situation.
-Try to find a firmware upgrade which either adds such an option or changes the way this situation is handled
-Replace your router
-Ignore the situation since it only affects LAN users, and configure your LAN user's to resolve your domain(s) to your server's LAN IP

---

### Post by Grey08 on 2009-03-12
> **cdenley said:**
> If you try connecting to your router's WAN IP from within your LAN, your router sees that the same as if connection to your router's LAN IP, and either gives you it's own web server (admin page), or simply doesn't check your port forwarding rules.


THANKS~!!!!!!

I have asked my friends to browse the index.html over the internet, and he said he sees " It works!!"""

Thanks~!!!!!!!!! again~!!!!!

The problem is SOLVED~!!!

---

### Post by BkkBonanza on 2009-03-12
And if you add a line like,

127.0.0.1 mydomainname.com

to your /etc/hosts file then it will also work on your own machine too.

---

### Post by neilevan814 on 2009-03-13
I had to create a separate file within /etc/apache2/conf.d called /etc/apache2/conf.d/fqdn

All this file contains is 
ServerName localhost

But, I needed that in order to see my stuff locally.

---

### Post by Grey08 on 2009-03-14
> **BkkBonaza said:**
> And if you add a line like,

127.0.0.1 mydomainname.com

to your /etc/hosts file then it will also work on your own machine too.

what does it do?? i only know that 127.0.0.1 is actually referring the machine itself, right?

---

