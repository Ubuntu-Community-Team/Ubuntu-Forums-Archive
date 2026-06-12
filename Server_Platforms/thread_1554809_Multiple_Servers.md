---
title: "Multiple Servers"
date: 2010-08-17
forum: Server Platforms
---

### Post by da3533 on 2010-08-17
hi..

i have 1 server which can be accessed through one main direct ip address. i want another server to be used as well this one. how do i somehow, gain access to the new server externally? 

so basically,  for now, if i type in my current IP, it will show the main default page on server 1..  is there any way i can do the following:- configure- 82.34.232.33:566  (port 566 to forward to lan ip of server 2)   .. so if some one types in 82.34.232.33:566 in their web browser, they will be directed to server 2...?

might sound stupid,  sorry.

---

### Post by LightningCrash on 2010-08-17
Yeah that is definitely within the realms of standard port forwarding.

is your router doing the port forwarding, or is the server on a public IP?

---

### Post by da3533 on 2010-08-17
hey..

i configured DMZ pointed to my servers local LAN IP address. so the real ip is direct to my server.  i have a netgear router...  i tried to add a service in but it doesnt work.   how shall i configure this?   i want it so that if anyone types in IP is 80.43.343.20:233 , it will go where i want it to go. (server2)..  i know how to configure server2 so that it will respond if this ip and port of 233 is called..  

diagram of what i want:

type --> [http://80.43.343.20](http://80.43.343.20)    --> server1   done!

type --> [http://80.43.343.20:233](http://80.43.343.20:233)    --> server2   not done!

if this works, i can just change the DNs of my domains to point to 80.43.343.20:233  if i want to be hosted from server 2 or 80.43.343.20 if i want it to be hosted from server1..

(all hosting of all servers have been taken care of)

---

### Post by LightningCrash on 2010-08-17
ah well that's pretty easy with xinetd

vim /etc/xinetd.d/other_server

paste
```

# default: off
service other_server
{
        disable = no
        socket_type = stream
        protocol = tcp
        port = 233
        wait = no
        user = nobody
        redirect = 192.168.1.50 80
}

```

vim /etc/services
paste at the end
```

#Local services

other_server        233/tcp

```

Now run:
sudo /etc/init.d/xinetd reload

and connect to [http://80.43.343.20:233](http://80.43.343.20:233) in your web browser

---

### Post by arrrghhh on 2010-08-17
You can do the xinetd method outlined above.

However, you can also easily do that with your router.

Simply disable your DMZ (not a very good idea anyways) and then the router should have a page to forward ports.  If you go to portforward.com, they have pretty good guides on how to do this.  Basically you tell port 80 to forward to one IP, and port 233 (or whatever) to forward to the other server's IP.

I just wouldn't advise keeping that DMZ up.  You should only open up ports your server is listening on.

---

### Post by da3533 on 2010-08-17
bloody hell! thanks!

---

### Post by da3533 on 2010-08-17
> **LightningCrash said:**
> ah well that's pretty easy with xinetd

vim /etc/xinetd.d/other_server

paste
```

# default: off
service other_server
{
        disable = no
        socket_type = stream
        protocol = tcp
        port = 233
        wait = no
        user = nobody
        redirect = 192.168.1.50 80
}

```vim /etc/services
paste at the end
```

#Local services

other_server        233/tcp

```Now run:
sudo /etc/init.d/xinetd reload

and connect to [http://80.43.343.20:233](http://80.43.343.20:233) in your web browser


thanks! it works.

---

### Post by da3533 on 2010-08-17
> **LightningCrash said:**
> ah well that's pretty easy with xinetd

vim /etc/xinetd.d/other_server

paste
```

# default: off
service other_server
{
        disable = no
        socket_type = stream
        protocol = tcp
        port = 233
        wait = no
        user = nobody
        redirect = 192.168.1.50 80
}

```vim /etc/services
paste at the end
```

#Local services

other_server        233/tcp

```Now run:
sudo /etc/init.d/xinetd reload

and connect to [http://80.43.343.20:233](http://80.43.343.20:233) in your web browser


hey.. it works... but my problems not solved :(  ..  i aim was to add this ip with the port number to my account at DynDNS.org . this way i could have had a hostname directing to [80.43.343.20:233]("http://80.43.343.20:233/")   but dyndna.org states that you cant have a port number with the IP as the IP add for this hostname...

so basically, i wanted, serv2.server22.org  to point to [80.43.343.20:233]("http://80.43.343.20:233/")  but no joy


any suggestions?

---

### Post by arrrghhh on 2010-08-17
You need to purchase another IP from your provider, unfortunately.  Dyndns won't redirect based on port numbers, they must be unique IP addresses.

I thought you were going to give out the different port numbers for your site... So site1 was google.com:80 and site2 was google.com:233.  Not pretty, but I thought you knew what you were getting into ;)

I'd still recommend collapsing that DMZ as well.  Just something to think about.

---

### Post by da3533 on 2010-08-17
> **arrrghhh said:**
> You need to purchase another IP from your provider, unfortunately.  Dyndns won't redirect based on port numbers, they must be unique IP addresses.

I thought you were going to give out the different port numbers for your site... So site1 was google.com:80 and site2 was google.com:233.  Not pretty, but I thought you knew what you were getting into ;)

I'd still recommend collapsing that DMZ as well.  Just something to think about.


im on the process of disabling it but need it for this time while installing everything...

purchase another IP... hmm.. this is going to cost.. never looked into it..   there must be way round this though, i tried this  and failed in the last part. i actually thought they would allow port numbers..     so if you have 20 servers, you will need 20 IPs?

---

### Post by arrrghhh on 2010-08-17
If you have 20 servers that each host a separate website?  Then yes, you will need 20 unique IP addresses.

20 servers supporting one site or separate sites under the same domain, you do not.

---

### Post by LightningCrash on 2010-08-17
DynDNS isn't going to be able to hand it to that port.

You would need an additional DynDNS hostname and a vhost in apache to push the traffic for that vhost to the host you want. It's called a reverse proxy.

I have some front-facing DMZ servers that were getting a bit old. I managed to move part of the services to a newer box but my developers couldn't get off their butt to fix the rest. So I proxied the newer services to the new box in the meantime.


from deep in my /etc/httpd/conf.d/ssl.conf

```

ProxyRequests Off

<Proxy *>
Order deny,allow
Allow from all
</Proxy>

ProxyPass /axis/ http://newserver.domain.com/axis/
ProxyPassReverse /axis/ http://newserver.domain.com/axis/
ProxyPass /apptest/ http://newserver.domain.com/apptest/
ProxyPassReverse /apptest/ http://newserver.domain.com/apptest/

```

So when someone goes to [https://oldserver.domain.com/axis](https://oldserver.domain.com/axis), it gets proxied to the newserver.domain.com, etc. There's no reason you couldn't specify port numbers there.

It's something you should look into if you want to do a number of vhosts in the long run.

Link to docs:
[http://httpd.apache.org/docs/current/mod/mod_proxy.html](http://httpd.apache.org/docs/current/mod/mod_proxy.html)

---

### Post by arrrghhh on 2010-08-17
I always forget how flexible vhosts are.  I was thinking something with a vhost could do it, thanks for posting that information!

So to the OP.  I apologize, you can do it with some more trickery :D

---

### Post by da3533 on 2010-08-17
> **arrrghhh said:**
> You need to purchase another IP from your provider, unfortunately.  Dyndns won't redirect based on port numbers, they must be unique IP addresses.

I thought you were going to give out the different port numbers for your site... So site1 was google.com:80 and site2 was google.com:233.  Not pretty, but I thought you knew what you were getting into ;)

I'd still recommend collapsing that DMZ as well.  Just something to think about.


just thought of something else, isnt there a way such a program (proxy) ?  if so, i can just have 1extra pc that has proxy server and will guide all requests to the appropriate server...   like:

[http://80.43.343.20:233]("http://80.43.343.20:233/") >> proxy PC >directs to server1 (lan network)

---

### Post by arrrghhh on 2010-08-17
da3533,

See LightningCrash's post.  vhosts is the "best" workaround IMHO.  Like I said, I always forget how flexible vhosts truly are.

---

### Post by da3533 on 2010-08-17
i know sorry man, i was still refreshing page 1 of this thread lool... so i thought there were no replies. will try it now

---

### Post by da3533 on 2010-08-17
> **LightningCrash said:**
> DynDNS isn't going to be able to hand it to that port.

You would need an additional DynDNS hostname and a vhost in apache to push the traffic for that vhost to the host you want. It's called a reverse proxy.

I have some front-facing DMZ servers that were getting a bit old. I managed to move part of the services to a newer box but my developers couldn't get off their butt to fix the rest. So I proxied the newer services to the new box in the meantime.


from deep in my /etc/httpd/conf.d/ssl.conf

```

ProxyRequests Off

<Proxy *>
Order deny,allow
Allow from all
</Proxy>

ProxyPass /axis/ http://newserver.domain.com/axis/
ProxyPassReverse /axis/ http://newserver.domain.com/axis/
ProxyPass /apptest/ http://newserver.domain.com/apptest/
ProxyPassReverse /apptest/ http://newserver.domain.com/apptest/

```So when someone goes to [https://oldserver.domain.com/axis](https://oldserver.domain.com/axis), it gets proxied to the newserver.domain.com, etc. There's no reason you couldn't specify port numbers there.

It's something you should look into if you want to do a number of vhosts in the long run.

Link to docs:
[http://httpd.apache.org/docs/current/mod/mod_proxy.html](http://httpd.apache.org/docs/current/mod/mod_proxy.html)



hey,

i dont have this directory.. /etc/httpd/conf.d/ssl.conf

i dont have ssl too, not on that stage..  but i still cant locate any of these files.. i use a hosting panel that does the configs for me...  
i have found this etc/apache2/conf.d folder with the following file: charset   ,  javascript-common.conf   localized-error phpmyadmin.conf   security...

where else can this be?

---

### Post by arrrghhh on 2010-08-17
I want to say the file that you want is /etc/apache2/httpd.conf...

Perhaps /etc/httpd/conf.d/ssl.conf is for lighthttpd?

---

### Post by da3533 on 2010-08-17
yes, i got it now...  but i will be honest now, i am so confused.. 

this is it now:


#
# Implements a proxy/gateway for Apache.
# # Required modules: mod_proxy, mod_proxy_http
#

<IfModule proxy_module>
<IfModule proxy_http_module>

#
# Reverse Proxy
#
ProxyRequests Off

<Proxy *>
    Order deny,allow
    Allow from all
</Proxy>

ProxyPass /axis/ [http://newserver.domain.com/axis/](http://newserver.domain.com/axis/)
ProxyPassReverse /axis/ [http://newserver.domain.com/axis/](http://newserver.domain.com/axis/)
ProxyPass /apptest/ [http://newserver.domain.com/apptest/](http://newserver.domain.com/apptest/)
ProxyPassReverse /apptest/ [http://newserver.domain.com/apptest/](http://newserver.domain.com/apptest/)
</IfModule>
</IfModule>



how do i alter it so it will work...    
dyndns hostname  :- [email]s2@domain.com[/email]  points to my main Ip address 83.454.34.34

i want this hostname to be hosted by server2  located on Lan IP: 192.168.1.2

(192.168.1.2 is server 2 , apache2 etc...)

please can you alter it for me.. so it will work..

---

### Post by arrrghhh on 2010-08-17
[http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

That's the documentation on vhosts.  Please read over it, and let us know if you're still having issues.

---

### Post by da3533 on 2010-08-17
> **arrrghhh said:**
> [http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

That's the documentation on vhosts.  Please read over it, and let us know if you're still having issues.


ok. entered this, restarted apache with no errors

ProxyRequests Off
    
    <Proxy *>
           Order deny,allow
      Allow from all
         </Proxy>
    
    ProxyPass  [EMAIL="s2@domain.com"]s2@domain.com[/EMAIL] 192.168.1.2
    ProxyPassReverse  [EMAIL="s2@domain.com"]s2@domain.com[/EMAIL] 192.168.1.2

dns [EMAIL="s2@domain.com"]s2@domain.com[/EMAIL] points to my main ip (DMZ)  

that might look stupid but i am stuck.

---

### Post by arrrghhh on 2010-08-17
Ok, did you read the documentation?  I'm not sure where you're stuck exactly.  I guess I can just whip up the config for you, but you wouldn't really learn much from it.

---

### Post by da3533 on 2010-08-17
> **arrrghhh said:**
> Ok, did you read the documentation?  I'm not sure where you're stuck exactly.  I guess I can just whip up the config for you, but you wouldn't really learn much from it.


i know, thats why i was trying to read all of it to see.   i kind of got..

my isp ip is (eg) 80.45.45.45
dyndns is s2.domain.com point to 80.45.45.45

now i will configure the cname WWW record of [www.mydomain.com]("http://www.mydomain.com") to hostname:s2.domain.com. 

if someone types [www.mydomain.com]("http://www.mydomain.com"),  i want them to be directed to server2 located at my network 192.168.1.2

ProxyRequests Off
    
    <Proxy *>
           Order deny,allow
      Allow from all
         </Proxy>
    
    ProxyPass  [EMAIL="s2@domain.com"]s2.domain.com[/EMAIL] [http://192.168.1.2](http://192.168.1.2)
    ProxyPassReverse  [EMAIL="s2@domain.com"]s2.domain.com[/EMAIL] [http://192.168.1.2](http://192.168.1.2)


i dont want to ProxyPass mydomain.com    as  i have many domains connected to hostname  s2.domain.com. therefore, all domains with this hostname should go to 192.168.1.2 server 2.

---

### Post by LightningCrash on 2010-08-17
This thread might help with vhosts and proxypassreverse:
[http://ubuntuforums.org/showthread.php?t=554194](http://ubuntuforums.org/showthread.php?t=554194)

---

### Post by da3533 on 2010-08-17
k..

i went onto my other server...

this is my httpd.conf

#
# Implements a proxy/gateway for Apache.
# # Required modules: mod_proxy, mod_proxy_http
#

<IfModule proxy_module>
<IfModule proxy_http_module>

#
# Reverse Proxy
#
ProxyRequests Off

<Proxy *>
    Order deny,allow
    Allow from all
    ProxyPass        /google/ [http://www.google.co.uk/](http://www.google.co.uk/)
ProxyPassReverse /google/ [http://www.google.co.uk/](http://www.google.co.uk/)
</Proxy>

</IfModule>
</IfModule>


when i type in.. [http://192.168.1.2/google/](http://192.168.1.2/google/)

it says 
**Object not found!**

        The requested URL was not found on this server.          If you entered the URL manually please check your     spelling and try again.      


it doesnt even reload apache... errors..

---

### Post by arrrghhh on 2010-08-17
Is that the actual config you have in there, or did you replace the google stuff with your own?

What are the errors Apache throws?

---

### Post by da3533 on 2010-08-17
> **arrrghhh said:**
> Is that the actual config you have in there, or did you replace the google stuff with your own?

What are the errors Apache throws?


this is the original...

#
# Implements a proxy/gateway for Apache.
# # Required modules: mod_proxy, mod_proxy_http
#

<IfModule proxy_module>
<IfModule proxy_http_module>

#
# Reverse Proxy
#
ProxyRequests Off

<Proxy *>
    Order deny,allow
    Allow from all
</Proxy>

</IfModule>
</IfModule>



there are no errors.. tthis is an old xampp server...  ithought i could test this proxy..

---

### Post by da3533 on 2010-08-17
this is what the error log says

** [Tue Aug 17 23:58:34 2010] [error] [client 192.168.1.2] File does not exist: C:/xampp/htdocs/google**


for

#
# Implements a proxy/gateway for Apache.
# # Required modules: mod_proxy, mod_proxy_http
#

<IfModule proxy_module>
<IfModule proxy_http_module>

#
# Reverse Proxy
#
ProxyRequests Off

<Proxy *>
    Order deny,allow
    Allow from all
    ProxyPass        /google/ [http://www.google.co.uk/](http://www.google.co.uk/)
ProxyPassReverse /google/ [http://www.google.co.uk/](http://www.google.co.uk/)
</Proxy>

</IfModule>
</IfModule>

---

### Post by arrrghhh on 2010-08-17
It looks like your document root is set incorrectly from that error.

And what about this "it doesnt even reload apache... errors.." - what's the error from that?  Is it that file does not exist error?  Is there any other information you can provide about that error...?

Also, I'm not sure what all this proxy config stuff is.  It seems it may only apply to lighthttpd.

Please read [this](http://httpd.apache.org/docs/2.2/vhosts/name-based.html) document at least.  It should get you going.

---

### Post by da3533 on 2010-08-17
> **arrrghhh said:**
> It looks like your document root is set incorrectly from that error.

And what about this "it doesnt even reload apache... errors.." - what's the error from that?  Is it that file does not exist error?  Is there any other information you can provide about that error...?

Also, I'm not sure what all this proxy config stuff is.  It seems it may only apply to lighthttpd.

Please read [this]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html") document at least.  It should get you going.

this is to do with setting up vhosts etc...  

i give up....  what was you saying about you wipping up the config?

ProxyRequests Off
    
    <Proxy *>
           Order deny,allow
      Allow from all
         </Proxy>
    
    ProxyPass  [EMAIL="s2@domain.com"]s2.domain.com[/EMAIL] [http://192.168.1.2]("http://192.168.1.2/")
    ProxyPassReverse  [EMAIL="s2@domain.com"]s2.domain.com[/EMAIL] [http://192.168.1.2]("http://192.168.1.2/")



going back, what the correct config?

---

### Post by arrrghhh on 2010-08-17
I'm not sure what to tell you.  Based on your responses, you haven't read any of the links I posted.

Please read the vhosts documentation I linked and start from scratch with it.

---

### Post by da3533 on 2010-08-17
> **arrrghhh said:**
> I'm not sure what to tell you.  Based on your responses, you haven't read any of the links I posted.

Please read the vhosts documentation I linked and start from scratch with it.

but isnt it for setting up domains to homedirs etc

i just want to setup the reverse proxy...

---

### Post by da3533 on 2010-08-17
this was the other error after i add the proxy part..


Invalid command 'ProxyPreserveHost', perhaps misspelled or defined by a module not included in the server configuration


i just found this error.

---

### Post by da3533 on 2010-08-17
> **LightningCrash said:**
> This thread might help with vhosts and proxypassreverse:
[http://ubuntuforums.org/showthread.php?t=554194](http://ubuntuforums.org/showthread.php?t=554194)

ok.. it works but...


ProxyPass server26.serveftp.org [http://google.co.uk](http://google.co.uk)
ProxyPassReverse server26.serveftp.org [http://google.co.uk](http://google.co.uk)

this works fine...
ProxyPass /server2/ [http://192.168.1.2](http://192.168.1.2)
ProxyPassReverse /server2/ [http://192.168.1.2](http://192.168.1.2)

but how do i direct s2.domain.org  (dyndns hostname) to go wit 192.169.1.2

i tried the following with no luck

ProxyPass server26.serveftp.org [http://192.168.1.2](http://192.168.1.2)
ProxyPassReverse server26.serveftp.org [http://192.168.1.2](http://192.168.1.2)

what am i doing wrong?

---

### Post by LightningCrash on 2010-08-18
> **da3533 said:**
> ok.. it works but...


ProxyPass server26.serveftp.org [http://google.co.uk](http://google.co.uk)
ProxyPassReverse server26.serveftp.org [http://google.co.uk](http://google.co.uk)

this works fine...
ProxyPass /server2/ [http://192.168.1.2](http://192.168.1.2)
ProxyPassReverse /server2/ [http://192.168.1.2](http://192.168.1.2)

but how do i direct s2.domain.org  (dyndns hostname) to go wit 192.169.1.2

i tried the following with no luck

ProxyPass server26.serveftp.org [http://192.168.1.2](http://192.168.1.2)
ProxyPassReverse server26.serveftp.org [http://192.168.1.2](http://192.168.1.2)

what am i doing wrong?

proxypass will never accept a domain name that way
it only accepts a relative path from the vhost it's in.

so make your vhost, then proxypass /

learn to make the vhost first, then add the proxypass to it

---

### Post by da3533 on 2010-08-18
> **LightningCrash said:**
> proxypass will never accept a domain name that way
it only accepts a relative path from the vhost it's in.

so make your vhost, then proxypass /

learn to make the vhost first, then add the proxypass to it


i am making it now. but apache is not restarting as it wants a directory of the domain i stated...

do i have to make a folder for it? i dont want apache to load the contents from the flder, i just want to go to server 2..

here is my vhost for this:

```
<VirtualHost s1.server.org>
  ServerName s1.server.org

    Options Indexes FollowSymLinks
    AllowOverride All
    Order allow,deny
    Allow from all
  </Directory>
</VirtualHost>
```

---

### Post by arrrghhh on 2010-08-18
Is there an open <Directory> statement above?  I see where you close a directory statement...

---

### Post by da3533 on 2010-08-18
> **arrrghhh said:**
> Is there an open <Directory> statement  above?  I see where you close a directory statement...

i changed it to:

<VirtualHost s1.server.org>
DocumentRoot C:/example1/
ServerName localhost2
ServerAdmin admin@localhost
</VirtualHost>


.. 

ok, this is it, this is my situation.  we have 2 servers in the house because my brother doesnt want to share..

so its server 1 and server2... this was the whole problem.

we only have 1 external IP from ISP...  and when he found out i made my  server the DMZ, he wanted to change it.. so now, i am trying to find  anyway to make both servers be publicly available for hosting our  domains seperatley.

---

### Post by arrrghhh on 2010-08-18
Oh I think we've been assuming there are just two separate sites on one machine...

I'm not sure what to tell you, sounds like some complex NAT may do it for you... I am no expert on this however, and probably should bow out ;)

---

### Post by da3533 on 2010-08-18
> **arrrghhh said:**
> Oh I think we've been assuming there are just two separate sites on one machine...

I'm not sure what to tell you, sounds like some complex NAT may do it for you... I am no expert on this however, and probably should bow out ;)

NAT?  any thing you can provide to get me reading... ?

---

### Post by spynappels on 2010-08-18
Ok, so you could take the server out of the DMZ. Forward port 80 to one of the servers and set up a local virtualhost on it for one of the domains, and set up a reverse proxy pointing to the other server for the other domain. It means combining bits of the different ideas in this thread but should work.

---

### Post by da3533 on 2010-08-18
> **spynappels said:**
> Ok, so you could take the server out of the DMZ. Forward port 80 to one of the servers and set up a local virtualhost on it for one of the domains, and set up a reverse proxy pointing to the other server for the other domain. It means combining bits of the different ideas in this thread but should work.

im on the reverse proxy page... but it just redirects to that domain...

e.g.

ProxyPass /google [http://google.com](http://google.com)
ProxyPassReverse /google [http://google.com](http://google.com)

so if i type in s2.domain.org/google/   it will just go to google.com...

---

### Post by arrrghhh on 2010-08-18
da3533, start with the vhost.  Once you have that setup, then work on the reverse proxy.  One step at a time, these things build upon eachother.

---

### Post by da3533 on 2010-08-18
> **arrrghhh said:**
> da3533, start with the vhost.  Once you have that setup, then work on the reverse proxy.  One step at a time, these things build upon eachother.


hey... u have .. i set s2.server.org  in vhosts...  with docroot "C:/www/s2" and works.. but everytime i add the proxy script, it says this in the error log:

[error] [client 86.xx.xx.xx.xx] File does not exist: C:/www/s2/[COLOR=Red]**server2**[/COLOR]

it keeps adding this part of the proxy script:
ProxyPass /[COLOR=Red]**server2**[/COLOR]/ [http://192.168.1.2](http://192.168.1.2)
ProxyPassReverse /[COLOR=Red]**server2**[/COLOR]/  [http://192.168.1.2](http://192.168.1.2)
you see, server2 is not a directory in the document root in the vhost. in vhost.conf, it says    DocumentRoot "C:/www/s2"

here is the vhost for s2.server.org

```
<VirtualHost *:80>
   ServerName s2.server.org
   ServerAlias s2.server.org
   ServerAdmin webmaster@localhost
   DocumentRoot "C:/www/s2" 
    <Directory "C:/www/s2">
        Options -Indexes FollowSymLinks
        AllowOverride AuthConfig FileInfo
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>
```if i take out the document root, apache doesnt load...  isnt there a way of having no document root for this domain?  so that it will reverseproxy like its told to do.

---

### Post by arrrghhh on 2010-08-18
Uhm... How is it possible that your docroot is "C:/www/s2" - that doesn't make any sense to me.  My docroot is /var/www...

---

### Post by da3533 on 2010-08-18
> **arrrghhh said:**
> Uhm... How is it possible that your docroot is "C:/www/s2" - that doesn't make any sense to me.  My docroot is /var/www...

yeh, your right.. i meant /var/www/s2   

isnt it way to remove the doc root without errors etc...  ? at the moment, its executing reverseproxy but going to the doc toot first then adding another directory to it...

---

### Post by arrrghhh on 2010-08-18
You must have a docroot... Can't get around not having it.  How would apache know where to serve pages from without it being declared?

---

### Post by da3533 on 2010-08-18
> **arrrghhh said:**
> You must have a docroot... Can't get around not having it.  How would apache know where to serve pages from without it being declared?

true but by having this vhost for this s2.server.org hostname, i cant use the reverse proxy at all.... so nothing can be done with reverse proxy...

---

### Post by arrrghhh on 2010-08-18
> **da3533 said:**
> true but by having this vhost for this s2.server.org hostname, i cant use the reverse proxy at all.... so nothing can be done with reverse proxy...

Ok, let's start over.

Did you get the virtual host stuff working, and able to run apache?

---

### Post by da3533 on 2010-08-18
> **arrrghhh said:**
> Ok, let's start over.

Did you get the virtual host stuff working, and able to run apache?


yep.,.. works.. if you type in the  hostname in a browser, it will bring up a sample page found in its doc root found in vhosts...

so that works.... hostname is now hosted my this server... now....

---

### Post by arrrghhh on 2010-08-18
Ok, so does that mean that one hostname/server works and the other doesn't...?

---

### Post by da3533 on 2010-08-18
> **arrrghhh said:**
> Ok, so does that mean that one hostname/server works and the other doesn't...?


i just found something,,  looks promising but gives errors.. im nearly there..

```
<VirtualHost *:*>
        ProxyPreserveHost On
        ProxyPass / http://192.168.1.2/
        ProxyPassReverse / http://192.168.1.2/
        ServerName hostname.example.com
    </VirtualHost>     
```

now that looks nice but apaches throw this error:
[client 86.xx.xxx.xx..] client denied by server configuration: proxy:[http://192.168.1.2](http://192.168.1.2)

---

### Post by arrrghhh on 2010-08-18
Check out [this](http://ubuntuforums.org/showthread.php?t=39328) thread.  It has a little nugget of info that may help at the bottom of the first post.

---

### Post by da3533 on 2010-08-18
> **arrrghhh said:**
> Check out [this]("http://ubuntuforums.org/showthread.php?t=39328") thread.  It has a little nugget of info that may help at the bottom of the first post.


that got me further... should be very close now...


i added this... Allow from 192.168.1 instead of this Allow from all

<Proxy *>

Order deny,allow

Allow from 192.168.1

</Proxy>

another error, better than the last... 
proxy: DNS lookup failure for: 192.168.1.2error returned by /error/HTTP_XAMPP_FORBIDDEN.html.var

DNS lookup failure?

---

### Post by arrrghhh on 2010-08-18
I feel like I'm not getting your complete config files.

Please copy & paste your configs with [ code ] brackets around the text.  Feel free to mask external IPs, but don't mangle anything else please (unless you feel there's something else that compromises security like domain name, etc)

---

### Post by da3533 on 2010-08-18
> **arrrghhh said:**
> I feel like I'm not getting your complete config files.

Please copy & paste your configs with [ code ] brackets around the text.  Feel free to mask external IPs, but don't mangle anything else please (unless you feel there's something else that compromises security like domain name, etc)


it works...all domains with hostname s1.serve.org goes to server 1 (192.168.1.3)

this is perfect... but i have another hostname s2.serve.org   this should go to 192.168.1.2 

when i restart apache and have the following my vhosts.conf... all domains, i mean all domain of mine that has s2 or s2.server.org hostnames, direct to server 1...

its like the error that people get, if apache cannot resolve it , it just uses the first vhost setup on file....



(s1 and s2.serve.org are example hostnames)

```

NameVirtualHost *:80

<VirtualHost *:*>
ProxyPreserveHost On
ProxyPass / http://192.168.1.2
ProxyPassReverse / http://192.168.1.2
ServerName s2.serve.org

</VirtualHost> 

<VirtualHost *:*>
ProxyPreserveHost On
ProxyPass / http://192.168.1.99
ProxyPassReverse / http://192.168.1.99
ServerName s2.serve.org

</VirtualHost> 

```

---

### Post by da3533 on 2010-08-18
why cant i have 2 running at the same time.. why is apache just using the first vhosts for all?

---

### Post by arrrghhh on 2010-08-18
Why are you using <VirtualHost *:*> for both...?

---

### Post by da3533 on 2010-08-18
> **arrrghhh said:**
> Why are you using <VirtualHost *:*> for both...?

lool.. what is it suppose to be.. i just realised this too... when i take out the server name for both vhosts.. it still works, it forwards everything to server 1... !     even though theres no servername 

so this still works even though its not filtered...  (no ServerName )

<VirtualHost *:*>
ProxyPreserveHost On
ProxyPass / [http://192.168.1.2](http://192.168.1.2)
ProxyPassReverse / [http://192.168.1.2](http://192.168.1.2)

</VirtualHost> 

what do i do?

---

### Post by arrrghhh on 2010-08-18
Ok, I'm getting a little bothered here.  You aren't reading thru the vhost doc, and it's pretty obvious.

```
<VirtualHost 10.1.2.3>
ServerAdmin webmaster@host.example.com
DocumentRoot /www/docs/host.example.com
ServerName host.example.com
ErrorLog logs/host.example.com-error_log
TransferLog logs/host.example.com-access_log
</VirtualHost> 
```

From that example doc, you can see they named it something else other than *.

If you use the asterisk, that means "match any IP/domain" basically.

Also, if you did read that doc you would've realized > The character *, which is used only in combination with NameVirtualHost * to match all IP addresses

I'm guessing you're wanting me to write a config for you.  Perhaps you should just pay someone to host your sites... It'd probably be cheaper & a lot less headache/downtime.

I'm going to throw some more examples up from the Apache doc.  Hopefully they will help... I don't think you'll learn anything if I make a config for you - plus I have a feeling I'm not entirely understanding what you're trying to do.

[http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)

---

### Post by da3533 on 2010-08-18
> **arrrghhh said:**
> Ok, I'm getting a little bothered here.  You aren't reading thru the vhost doc, and it's pretty obvious.

```
<VirtualHost 10.1.2.3>
ServerAdmin webmaster@host.example.com
DocumentRoot /www/docs/host.example.com
ServerName host.example.com
ErrorLog logs/host.example.com-error_log
TransferLog logs/host.example.com-access_log
</VirtualHost> 
```From that example doc, you can see they named it something else other than *.

If you use the asterisk, that means "match any IP/domain" basically.

Also, if you did read that doc you would've realized 

I'm guessing you're wanting me to write a config for you.  Perhaps you should just pay someone to host your sites... It'd probably be cheaper & a lot less headache/downtime.

I'm going to throw some more examples up from the Apache doc.  Hopefully they will help... I don't think you'll learn anything if I make a config for you - plus I have a feeling I'm not entirely understanding what you're trying to do.

[http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)


you dont need to respond to posts if it bothers you.  i have over 60 domains. and bothers server is even worse. it saved me alot over 2 yrs hosting it myself.  

anyways, i have completed. everything is running as we speak.  

i was correct too.. it needs to be *:*   it wont work otherwise.

---

### Post by arrrghhh on 2010-08-19
> **da3533 said:**
> you dont need to respond to posts if it bothers you.  i have over 60 domains. and bothers server is even worse. it saved me alot over 2 yrs hosting it myself.  

anyways, i have completed. everything is running as we speak.  

i was correct too.. it needs to be *:*   it wont work otherwise.

Glad to hear you got it workin.  I really hope no body is paying you to host their site... eek.

---

