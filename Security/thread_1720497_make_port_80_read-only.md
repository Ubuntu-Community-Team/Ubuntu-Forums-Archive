---
title: "make port 80 read-only"
date: 2011-04-03
forum: Security
---

### Post by supasoaker on 2011-04-03
I am running a ubuntu server for home use and am currently hosting a website for testing purposes..........I am worried because I have to leave my port 80 open for this to work..........

an Idea I have is to make it that port 80 is read only......is this possible?

Are there any best practices for securing my open port for website hosting?

Thanks!

---

### Post by bodhi.zazen on 2011-04-03
Make your files in /var/www ro

---

### Post by supasoaker on 2011-04-03
thanks - that's the standard apace place to put them i think........why is this so?

---

### Post by bodhi.zazen on 2011-04-03
> **supasoaker said:**
> thanks - that's the standard apace place to put them i think........why is this so?

Why is that the standard location ? Not sure, why not ?

---

### Post by supasoaker on 2011-04-03
actually I meant why put it there - why might it be more secure or a better place?

---

### Post by bodhi.zazen on 2011-04-03
Not sure what you are asking or what you think is wrong with /var/www

No matter where you put the html / php files they need at lease r access by apache and I am not sure why you feel location matters.

---

### Post by supasoaker on 2011-04-03
sorry - I don't think u got the question..........

What I am trying to do is make it so that people connecting to port 80 can only read from whatever they find........

I appreciate this might be a mute point due to the way permissions work in linux but would like to know if it can be done..........the firewall closes ports so the system doesn't listen to them no matter what, i now have a port open which will give anyone access to my chip even by asking it a question - what I want to do is make it so that no matter what it will only retrieve data and not allow editing, kind of like a different way to use the firewall.......

This might be achieved by a chroot jail which I am going to look into as to do anything to the system they will need admin access, but I am trying to find out how I can tune my system to react to what is asked of it from a port.............another example would be that it can ONLY accept requests to gather http data from port 80 and any other requests/data/etc is to be ignored as if the port was closed............

---

### Post by bodhi.zazen on 2011-04-03
> **supasoaker said:**
> sorry - I don't think u got the question..........

What I am trying to do is make it so that people connecting to port 80 can only read from whatever they find........

I appreciate this might be a mute point due to the way permissions work in linux but would like to know if it can be done..........the firewall closes ports so the system doesn't listen to them no matter what, i now have a port open which will give anyone access to my chip even by asking it a question - what I want to do is make it so that no matter what it will only retrieve data and not allow editing, kind of like a different way to use the firewall.......

This might be achieved by a chroot jail which I am going to look into as to do anything to the system they will need admin access, but I am trying to find out how I can tune my system to react to what is asked of it from a port.............another example would be that it can ONLY accept requests to gather http data from port 80 and any other requests/data/etc is to be ignored as if the port was closed............

I do not think open ports work the way you envision at the level of the kernel or firewall.

I do not see how a chroot would help you either.

Basically, you have a server, say Apache, listening for http requests on port 80.

Unless there is seriously wrong with the Apache server, it is not going to respond at all to non-http requests nor is it going to have access to anything outside of /var/www

Now it is possible for apache to be compromised, all things are possible, but typically the problems is with apache modules or cgi (php) and not apache.

Your firewall / kernel , at a lower lever, sees traffic on port 80 and delivers it to apache (I know that is somewhat of an over simplification, but netfilter / iptables is not designed to reject traffic on an application level).

You would want to look at hardening apache, possibly adding either apparmor or mod_security. Apparmor is probably the place for you to start, mod_security is nice as well but there is a bit of a learning curve.

From what you posted I do not think a chroot would help you, and using a chroot is somewhat depreciated. People are using tools such as apparmor or LXC (or selinux or openvz or KVM/Virtualbox/VMWare) to do some of the things a chroot would have in the past.

---

### Post by supasoaker on 2011-04-03
ok thanks - I will look into those, I had come across them.

I was thinking along those lines about apache but wasn't sure, as long as it doesn't respond to non-http requests it will satisfy me... :P

---

### Post by Drezard on 2011-04-03
What kind of web applications or code are you going to be running on this apache server? 

I'd probably look at setting up htaccess and adding HTTP Username/Password security to this, if you want to deny access to any of the pages except for yourself. 

This is a basic implementation of htaccess:

```

echo "AuthName \"Go Away\"" > /var/www/.htaccess
echo "AuthType Basic" >> /var/www/.htaccess
echo "AuthUserFile /var/www/.htpasswd" >> /var/www/.htaccess
echo "Require valid-user" >> /var/www/.htaccess
echo "" >> /var/www/.htaccess
echo "<Files .*>" >> /var/www/.htaccess
echo "  deny from all" >> /var/www/.htaccess
echo "</Files>" >> /var/www/.htaccess

htpasswd -c /var/www/.htpasswd admin 

```

References:
> 
[http://www.colostate.edu/~ric/htpass.html](http://www.colostate.edu/~ric/htpass.html)
[http://httpd.apache.org/docs/1.3/howto/htaccess.html](http://httpd.apache.org/docs/1.3/howto/htaccess.html)



That should stop most of the idiots getting into your apache2 server. Make sure when you login you use the username "admin" and what ever you set the password too...

---

### Post by BkkBonanza on 2011-04-03
Wow, that's an ugly way to write that... here's a clean way, that does the same thing 
(and plays nicer with sudo as well).

```

cat > /var/www/.htaccess <<-EOF 
AuthName "Go Away" 
AuthType Basic
AuthUserFile /var/www/.htpasswd
Require valid-user

<Files .*>
  deny from all
</Files>
EOF

```

---

### Post by SeijiSensei on 2011-04-04
It sounds to me like you simply want to limit access to HTTP GET requests and deny all others.  That will allow someone to download files from the webserver directory but not upload anything.  Is that what you're trying to accomplish?

How about this?  In the <Directory> definition for the DocumentRoot, add this:

```

<VirtualHost blah>
   stuff
   DirectoryRoot /path/to/your/site

   <Directory "/path/to/your/site">
      
      <LimitExcept GET>
          Order deny,allow
          Deny from all
          Allow from localhost
          Allow from your.own.ip.addr
      </LimitExcept>
      
      more stuff
      
   </Directory>
</VirtualHost>

```
The two "Allow" directives are optional; they would permit someone on the local machine or from your.own.ip.addr to use all types of requests; everyone else is limited to GET.

See [http://httpd.apache.org/docs/2.2/howto/access.html](http://httpd.apache.org/docs/2.2/howto/access.html) for details.

I will say that I think you're being unduly paranoid.  Web servers run 24/7 with port 80 open to the world.  What matters is how well the web server software enforces security.  Apache has been pushed and prodded for years now.  Any obvious vulnerabilities were fixed ages ago.  In addition, since Apache runs as an ordinary user (the "www-data" user in Ubuntu) and not as root, there's very little someone can do to harm your machine remotely.  I've run Apache for over fifteen years.  I've had one security problem a decade ago, and it was my own fault for not keeping current with security patches.

---

### Post by psusi on 2011-04-04
Ports are neither read nor written, so there is no such thing as one that is "read only".  Ports are just addresses that function as the source or destination of a bidirectional pipe.

---

