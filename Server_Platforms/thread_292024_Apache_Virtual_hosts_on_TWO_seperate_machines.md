---
title: "Apache Virtual hosts on TWO seperate machines"
date: 2006-11-03
forum: Server Platforms
---

### Post by twistedtwig on 2006-11-03
Hi guys,

so i have my main box running dapper as the main webserver with apache.  i have a number of subdomains set up with virtual host all working great :) .. i have recently put a windows 2003 server into the network to play with that environment.  What i want to do is forward requests for the windows (asp type) pages to the windows server.

my thought was to set up a subdomain as windows.example.com and use virtual hosts to forward it to the new machine.  my problem was when trying this it doesnt recognise anything i try:

tried server name (bobby)
tried full dns qualifying (bobby.domain.local)
tied the ip

i always get the following error when i restart apache

Warning: DocumentRoot [192.168.10.100] does not exist

does anyone have an idea or know that i am going about this the wrong way?  the other reason why i thought of doing it this way was it was easy to address it externally.  rather than it running on another port for example.  if i did port forwarding i would have to always use that extra port number which i dont like the idea of really.

thx guys

Twiggy

---

### Post by twistedtwig on 2006-11-03
I guess the next question which is a sort of extension to the previous is what about web services.  i havent created one yet so i dont know how they work (on ports, if so which one) but how would the info be forwarded.  this is not so much of an issues as i will read up more about it when i learn how to do them.  just a by the by question if anyone knows off the top of their head.

:)

---

### Post by twistedtwig on 2006-11-03
so i thought id have a fiddle with the port forwarding while people ponder the options.

exert from my firewall
> 
echo "   Forwarding port 8888 to 192.168.0.100:80 for bobby windows website, to bobby."
$IPTABLES -A FORWARD -p tcp -i $EXTIF --dport 8888 -m state --state NEW -j ACCEPT
$IPTABLES -t nat -A PREROUTING -i $EXTIF -p tcp --dport 8888 -j DNAT --to 192.168.0.100:80


as i understand it this should forward all requests on port "8888" to 192.168.10.100 port 80 (webserver)

when in the local area network i can put "bobby" (that ip) into the browser and the webpage loads.  but if i do 

ponywars.com:8888 i eventually get an error "problem loading page"

anyone know where i am going wrong please?  am i getting this porting issue wrong?

EDIT: could it be getting confused at this point:  i am requesting ponywars.com on port 8888 but that goes somewhere else and it doesnt know waht to do with it?  wooh going round in circles in my head now :p hehe

---

### Post by twistedtwig on 2006-11-04
i had another thought along the virtual hosts, if i mount the windows server web site as a folder in linux i can direct it to it.. but i can not get linux to access its shares yet.

does anyone have thoughts on why the port forwarding isnt working please?

thank you

---

### Post by twistedtwig on 2006-11-08
BUMP!

does anyone have any clues why the port forwarding might not be working please?

i figure i have to have joined the windows domain for the linux box to see the shares on the windows server (bind not playing fully yet so not done kerberos).

any and all help would be amazing.. thx all

Twiggy

---

### Post by Mr. Electric Wizard on 2007-02-28
> **twistedtwig said:**
> so i thought id have a fiddle with the port forwarding while people ponder the options.

exert from my firewall


as i understand it this should forward all requests on port "8888" to 192.168.10.100 port 80 (webserver)

when in the local area network i can put "bobby" (that ip) into the browser and the webpage loads.  but if i do 

ponywars.com:8888 i eventually get an error "problem loading page"

anyone know where i am going wrong please?  am i getting this porting issue wrong?

EDIT: could it be getting confused at this point:  i am requesting ponywars.com on port 8888 but that goes somewhere else and it doesnt know waht to do with it?  wooh going round in circles in my head now :p hehe


What happens if you type in [http://bobby.ponywars.com](http://bobby.ponywars.com) ?

I am actuall wanting to do this same exact thing (run a Windows server on my DMZ along with my main Apache sever).
Sounds like you are close.

---

### Post by twistedtwig on 2007-02-28
I get internet explore can not display the page... or if i just use bobby.ponywars.com it goes to msn search to try and find it :(

---

### Post by Mr. C. on 2007-02-28
If I'm understanding what you want, you want to your current server to redirect to the other server for certain document types.

Look into rewriting or redirecting with mod_rewrite and Redirect:

[http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html](http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html)
[http://httpd.apache.org/docs/2.2/mod/mod_alias.html#redirect](http://httpd.apache.org/docs/2.2/mod/mod_alias.html#redirect)

You can't also used port-based redirection, because at that level, its all just a stream of bits (TCP/IP knows nothing about document types, file suffixes, etc).  You don't want to use your firewall rules to do this either.

---

### Post by twistedtwig on 2007-03-01
Basically I have my ubuntu box as the main server and the passage out to the net.  This server serves html, php etc pages already and all works well.

I also have a windows 2003 server inside the network, (that can see the net through the ubunutu box).  This page servers aspx, asmx pages etc.  I could redirect these types as long as I remember to not do any html pages which is ok.  my main issue is i am going to be having some windows services running on the windows server as well.  So this will be using remoting on a port and I have no idea how to get a computer out on the net to be able to see and comminucate with this port.

Thanks for the help

---

### Post by primski on 2007-03-01
Try this one:

> 
<VirtualHost *>
        ServerName urserver.com
        <Proxy *>
                Order deny,allow
                Allow from all
        </Proxy>

        ProxyPass / [http://ponywars.com:8888/](http://ponywars.com:8888/)
        ProxyPassReverse / [http://192.168.10.100/](http://192.168.10.100/)
</VirtualHost>


---

### Post by twistedtwig on 2007-04-02
Sorry its taken me so long to come back things have gotta out of hand.

Its been so long my linux is SOOOO rusty I can hardly remember a thing!!! :(

I tried adding the suggested Proxy part:

```
################## windows forwarding #####################

<VirtualHost *>
ServerName windows.ponywars.com
<Proxy *>
Order deny,allow
Allow from all

ProxyRequests Off

</Proxy>

ProxyPass / http://ponywars.com:8888/
ProxyPassReverse / http://192.168.10.100/
</VirtualHost>

```

But i got the following output:

```
root@betty:/etc/apache2/conf/vhosts# /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                                                                                                Syntax error on line 159 of /etc/apache2/conf/vhosts/vhosts.conf:
Invalid command '<Proxy', perhaps mis-spelled or defined by a module not included in the server configuration
                                                                                                                                                      [fail]
root@betty:/etc/apache2/conf/vhosts# vi vhosts.conf
root@betty:/etc/apache2/conf/vhosts# /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                                                                                         [fail]
root@betty:/etc/apache2/conf/vhosts# vi vhosts.conf
root@betty:/etc/apache2/conf/vhosts# /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                                                                                         [fail]

```

any thoughts on what I am doing wrong please?

Also what log files can I check to see why its failing! i cant remember which or where they are /blush.  Took me a while to just find where vhosts.conf was again :p

Also I am not 100% sure how I could test if that port was open on my fire wall.  I understand I could use netstat but I don't really understand the output or what switches I should use.

Thank you all for your help

---

### Post by primski on 2007-04-03
Do you have proxy module enabled for apache?

try: 

```

sudo a2enmod proxy

```

 and try again

---

### Post by twistedtwig on 2007-04-03
no joy :(

```
root@betty:/home/jon# a2enmod proxy
Module proxy installed; run /etc/init.d/apache2 force-reload to enable.
root@betty:/home/jon# /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                            [fail]
root@betty:/home/jon#

```

daft question but am I restarting the right process?

---

### Post by primski on 2007-04-04
Yes you are restarting the right process.

Post your last few lines (indicating error)  of /var/log/apache2/error.log

In the meantime try adjusting that proxy settings like this:

First, comment out this line, like this

```

#ProxyRequests Off

```


then adjust the ProxyPass line like this
```

ProxyPass / http://windows.ponywars.com:8888/

```

Also try to comment out last line, ProxyPassReverse.

Also, make sure you have dns set up right so it points to right ip. (ping windows.ponywars.com - and watch the ip).

Let's see if any of these help.

---

### Post by twistedtwig on 2007-04-04
here is the log file.

```
[Mon Apr 02 20:38:20 2007] [error] [client 86.133.179.59] File does not exist: /var/www/root/favicon.ico
[Mon Apr 02 20:43:21 2007] [error] [client 86.133.179.59] File does not exist: /var/www/root/favicon.ico
[Mon Apr 02 21:17:01 2007] [error] [client 86.133.179.59] File does not exist: /var/www/footfaerie/favicon.ico
[Mon Apr 02 21:24:02 2007] [error] [client 86.133.179.59] File does not exist: /192.168.10.100
[Mon Apr 02 21:24:02 2007] [error] [client 86.133.179.59] File does not exist: /192.168.10.100
[Mon Apr 02 21:29:04 2007] [notice] caught SIGTERM, shutting down

```

going to try the other part now

---

### Post by twistedtwig on 2007-04-04
We have progress :D

apache restarted ok.  but now I get error 502 Bad Gateway in the browser:

Bad Gateway

The proxy server received an invalid response from an upstream server.

I tested this from inside and outside my local network and got the same thing.

```
################## windows forwarding #####################

<VirtualHost *>
ServerName windows.ponywars.com
<Proxy *>
Order deny,allow
Allow from all

#ProxyRequests Off

</Proxy>

ProxyPass / http://windows.ponywars.com:8888/
ProxyPassReverse / http://192.168.10.100/
</VirtualHost>

```

---

### Post by primski on 2007-04-05
Check your error.log every time u change a setting. That will help u narrow down the problem.

I think u can comment out the ProxyPassReverse line.

And to what ip does 'windows.ponywars.com' resolve to ?

You need correctly configured dns server to accomplish what you're trying here.

---

### Post by twistedtwig on 2007-04-05
Hi primski,

I will check the error log when I get home but the IP resolves to the same as my main domain name at the moment.

I have easydns providing dynamic dns for my site and use the host file to redirect different subdomains to different areas.

I have set up the windows.ponywars.com to redirect to ponywars.com (as I did with all my other subdomains) on easydns.com

As for internal dns that is not working fully at the moment (something i keep meaning to fix.  it all went wrong when I tried to get the windows server and linux to join the same domain and play nicely together, its now such a mess I need to fully start again).

from memory I can not ping names on the server from the linux box (although I can from each computer).  But the IP address work fine.  The windows box (called SAM) is always set to 192.168.10.100

Thanks again for your help

---

### Post by twistedtwig on 2007-04-05
```
[Thu Apr 05 17:42:06 2007] [error] (111)Connection refused: proxy: HTTP: attempt to connect to 86.149.51.102:8888 (windows.ponywars.com) failed

```

was the error i got.

if i changed the vhosts to:

```
################## windows forwarding #####################

<VirtualHost *>
ServerName windows.ponywars.com
<Proxy *>
Order deny,allow
Allow from all

#ProxyRequests Off

</Proxy>

ProxyPass /192.168.10.100 /
#ProxyPassReverse / http://192.168.10.100/
</VirtualHost>
~

```

i got 404 not found and error:

```
[Thu Apr 05 17:45:06 2007] [error] [client 86.149.51.102] File does not exist: /htdocs

```

---

### Post by primski on 2007-04-09
Hm, this 'File does not exist' error is due to not touching proxy settings at all . It just looks for windows.ponywars.com and there is no DocumentRoot for this VirtualHost defined, so therefore - file does not exist.


Im pretty sure ProxyPass should start with / and then comes the IP like this

ProxyPass / [http://192.168.10.100](http://192.168.10.100)

But hey, maybe we got to a wrong start at the beggining, so i really don't have no ideas left.

hope u get it working

greetz

---

