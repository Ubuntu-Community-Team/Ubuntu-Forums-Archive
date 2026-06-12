---
title: "Apache2 How to"
date: 2005-08-16
forum: Server Platforms
---

### Post by YaAqoB on 2005-08-16
Hello.
Does anyone have a how to so I can host my webpage.
I have installed the lampp package and I have a static IP and my ISP have forwarded the DNS of my domain to my IP.
I just can't find any decent instructions on how to configure apache2 so I can host it.
I would like to use Virtual Hosting so I can host friends websites aswell.

---

### Post by Spudgun on 2005-08-16
Try this:

[Apache HTTP Guide](http://ubuntuguide.org/#apachehttpserver)

---

### Post by Myles3 on 2005-08-16
Will there be alot of users going to you site? If not have you consider getting xampp ([http://xampp.org](http://xampp.org)) it's an easy alternative. Also check out ubuntuguide.org and see the Apache section.

---

### Post by YaAqoB on 2005-08-16
Thanks for that.
I have got that xampp installed.
At the moment I'm only going to be hosting 1 domain, but in a few weeks it may be 3 for 4.
The thing that has me confused is what files I have to edit to make it work.
Do I edit the apache.conf or the httpd.conf or the sites-enabled or the -sites allowed. 
Also what do I put into those files what ever one it may be.
I have a static IP and the dns is sorted.
I have a firewall and the IP of the server is 192.168.1.2
I have port forwarded port 80 in my firewall/router to the IP of my server.
I have read a few guides that say after I have done the above all I have to do is add the following to httpd.conf

NameVirtualHost 192.168.1.2:80

<VirtualHost 192.168.1.2:80>
   ServerName [www.invited.co.nz](www.invited.co.nz)
   DocumentRoot /var/www/invited
</VirtualHost>

If I do the above when I type in [www.invited.co.nz](www.invited.co.nz) in firefox I get a login window asking me to login into the home gateway.

Can anyone tell me what I've done wrong and how to correct this. :)

---

### Post by kwane on 2005-08-16
I'm really curious about that too.
Is there a way for you to disable remote management to your home gateway or change the port number of that to something else. Otherwise the home gateway will probably get priority over port 80. I could do that on one of my internal wireless router, but couldn't seem to get that done on the other router(the one that's connected to the internet). So right now all I do is assign it a different port number(e.g:4646) and access the website by [http://yoururl.com:4646](http://yoururl.com:4646)

But I would like to hear if there are people who have gotten around that.

---

### Post by YaAqoB on 2005-08-17
OK. I have deleted the lampp and installed apache2 and php etc from the package manager.
Now if i type in firefox [http://localhost](http://localhost) my webpage comes up fine.
How do I make it so that the outside world can see that? If I try to go to my webpage it asks for a home gateway password.

---

### Post by CrustyDOD on 2005-08-17
You have opened TCP port 80 in router?
If so, check if you have remote managment turned on in router, turn it off or change port...

As for VH, go to /etc/apache2/sites-enabled and open 000-default, modify it and save it as domainname.com, that's it...

---

### Post by YaAqoB on 2005-08-18
Ok, now its not going to take much for me to throw this server out the window.
I have told my router to allow http server traffic on port 80 and to forward it to 192.168.1.2.
When I enter [www.mydomianname.co.nz](www.mydomianname.co.nz) it goes to 192.168.1.1 which is my router.
I still can't find a nice simple how to for apache 2.
I have tried every thing and still I have got no where.
This is the bottom bit of the apache2.conf file. Whats wrong with it and do I have to do anyting else?

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*

NameVirtualHost 192.168.1.2:80

<VirtualHost 192.168.1.2:80>
ServerAdmin [email]jimboy_@hotmail.com[/email]
ServerName [www.invited.co.nz](www.invited.co.nz)
ServerAlias invited.co.nz
DocumentRoot /var/www/invited.co.nz/public_html
</VirtualHost>


Also what does this mean??
administrator@ubuntu-server:~$ sudo /etc/init.d/apache2 start
 * Starting web server (Apache2)...
apache2: Could not determine the server's fully qualified domain name, using 192.168.1.2 for ServerName
[Fri Aug 19 01:24:24 2005] [warn] NameVirtualHost 192.168.1.2:80 has no VirtualHosts

Cheers

---

### Post by LordHunter317 on 2005-08-18
What it means is your DNS is screwed up.

I'm not sure why you're using the lamp packages.  Kill them, use the raw Ubuntu stuff, which is more or less the same thing, but eaiser to cope with.

Name-based virtual hosting **requires** working DNS.  There's no way around that, so don't even try to attempt it.

If Apache can't lookup [www.invited.co.nz](www.invited.co.nz) and see it's address, it will not host that site.  The eaisest solution is to provide an entry in /etc/hosts.  This makes local testing eaiser as well.

Fix your DNS.

---

### Post by YaAqoB on 2005-08-18
I got rid of the LAMPP package a few days ago and am just running the packages from the package manager.
As far as I'm aware my ISP is looking after my DNS side of things. If I ping my domain name I see it pinging my IP adress.
What would I put in the hosts file?
Sorry for being a total web hosting newb :)

---

### Post by YaAqoB on 2005-08-18
Don't worry I have got it up and running. I'll figure out the virtual hosting later on.
Thanks for all your help :)

---

