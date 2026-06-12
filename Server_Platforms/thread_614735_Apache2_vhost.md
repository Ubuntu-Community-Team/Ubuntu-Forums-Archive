---
title: "Apache2 vhost"
date: 2007-11-16
forum: Server Platforms
---

### Post by hockey97 on 2007-11-16
Hi I got  the vhost working only on my computer that has apache2 on it.

the ohter computers on my network can't type [www.mydomain.com](www.mydomain.com) and get the webpage from the vhost on apache2.

I also have a paid domain name,  how can I point that domain name that I paid for to point to my computer that has the apache2 server to the vhost that's hosting the webpage  for that domain name???

---

### Post by hockey97 on 2007-11-16
do anyone know  how to point a domain name that's paid to one of my vhost in apache2???

I have the domain name working on my own computer but not working for other computers.

what's the difference between host and realname???

---

### Post by conjur3r on 2007-11-16
You have to go into your domain hosting administration and create A records pointing to the IP address of your apache server.  Note that the IP address must be a publicly available address for others to be able to access it.  If it is on your LAN, specify your IP address and then do some port forwarding in your router.

When the networking side of it is working properly, apache will start receiving the requests and depending on how you have set up your virtual hosts, will serve the appropriate content.  If there was an error in your virtual host configuration, it would serve the default vhost instead of the desired one.

---

### Post by hockey97 on 2007-11-16
when you say hosting administration do you mean the people that are providing me with the dns service?? 

my domain provider, they do have an interface for me to add A records and mx records however they have already have pre-made a records and mx records I can add or delete records. 
their is a a record of  host www  and then they have it pointed to their server.

so sould I delete everything in their and just make new a record pointing to my server ip??


when you  say the public ip addres, are you saying my external ip address??

UPDATE: I went to where my domain managed the people that are hosting it , I made an a record, and then tested the domain name by typing it in vtunnel a proxy server website. 

and I get a cgi error.

---

### Post by conjur3r on 2007-11-17
Yes the DNS hosting service.  Before you delete what's already there, you should write the details down just in case you need to revert back.  This is only if you also bought a web hosting package too.

Yes, your external IP address otherwise no one outside of your LAN will be able to access it.  If you purchased a domainname just for internal usage, then that defeats the purpose of having a domainname in the first place.

Try seeing what your domain address points to with:

# host YOURDOMAIN

or even
# host [www.YOURDOMAIN](www.YOURDOMAIN)

Is the ip address it brings back your one you put in?  If you don't see your ip address, give it a little bit more time to update.  DNS changes can take between a couple of minutes to a couple of days to update!

---

### Post by hockey97 on 2007-11-17
Thanks for the replies.

I got it to work, yesterday, however today I have a cgi error yesterday I had it but it would after like evey 15 min the domain would work and then dish out an cgi error cannont find [www.mydomain.com](www.mydomain.com) : 

today it become more perment, I can't see my site at all todday.

I also get when I type my internal ip address I am suppose to get the default server,  and I get a apche2 not found error.

any idea what could be messed up?

ya my domain name is for public.

---

### Post by conjur3r on 2007-11-17
Try creating a dummy index file in /var/www/index.html and testing your internal IP address again.  This will test the functionality of your apache server.

You can also try to watch the apache access and error logs /var/log/apache2/ (or somewhere there) to confirm apache is working properly.

---

### Post by hockey97 on 2007-11-21
I took a look at the error log, and it shows nothing.

I done that index thing didn't change a bit still have the same problem.

I had a friend try to get on my website he typed it in and it work, but when he tried doing that through vtunnel.com he get's a cgi error.

and that is that same thing that happens on my computer the one that has the servers on it.

but the computers on my own internal network can't even find the webpages I get an apache error 404 not found.

Do I need to specifi where the cgi files are at??

I only done the doc root to where the websites resorces would be found which is in the directory of home .

but any computer on my internal network can't see my webpages they just get a 404 error,  the computer that I have the servers on can see the websites with no problem, until I test it with vtunnel a proxy server website.
I was trying to test what people outside my network on if they could see the webite.
isn't their websites with tools that like help you debug the connection problmes??

---

### Post by hockey97 on 2007-11-22
I tried the host command in terminal, and found my domain name is pointing to 2 different ip address.

also  my ISP has their domain name attached to my domain name that I paid for.

the error I get is   CGI Error  Couldn't find address [www.mydomain.com:](www.mydomain.com:).   that's what I get when I type in my domain on vtunnel.com webpage.

---

### Post by hockey97 on 2007-11-23
I googled around and found some pages talking about similar problem,  and the solution they gave was  to reinstall all the add-on mods moduals, which I followed with they suggested, nothing happened  and so I still get the same error.

when I test my website domain name using vtunnel.com I get that cgi error address not found on [www.mydomain.com:](www.mydomain.com:) 

but only on the computer that has apache2 server on it well all the servers ect like mysql, bind9 and more ect.  Well on that computer  when I type [www.mydomain.com](www.mydomain.com) in my webrowser I get my webpage with no problems, no errors or nothing shows up. However when I try it on another computer in my house on the same network I get website not found 404  it's a error that the web browser shows not apache.
 
When I  test my domain name going on vtunnel.com and typing in my domain name i get a cgi error and I tried doing that on all the computer in my house, and they have the same error when using vtunnel.com 

but I asked my friend again to try it again  and he said that when he typed my domain name it directed him to a search engine , and said that the website cannont be found.

I done the setup right.

I pointed my paid domain name to my external ip address,  in apache2 server I have the vhosts  pointed to my internal IP address 
and had bind 9 point my domain requests to my internal ip address.

so I don't really know why I am getting a cgi error???

---

### Post by hockey97 on 2007-11-24
here is my error log.

[Sat Nov 24 14:23:41 2007] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Sat Nov 24 14:23:41 2007] [notice] mod_python: using mutex_directory /tmp 
[Sat Nov 24 14:23:44 2007] [notice] Apache/2.2.4 (Ubuntu) Embperl/2.2.0 mod_python/3.3.1 Python/2.5.1 PHP/5.2.3-1ubuntu6 mod_perl/2.0.2 Perl/v5.8.8 configured -- resuming normal operations
[Sat Nov 24 14:25:32 2007] [error] [client 192.168.1.1**] File does not exist: /home/aaron/WebPages/:guitar:.com/root, referer: [http://www.:lolflag:.com/](http://www.:lolflag:.com/)
[Sat Nov 24 17:47:06 2007] [error] [client 192.168.1.1**] File does not exist: /home/aaron/WebPages/******.com
[Sat Nov 24 17:47:06 2007] [error] [client 192.168.1.1**] File does not exist: /home/aaron/WebPages/******.com
[Sat Nov 24 17:59:55 2007] [error] [client 192.168.1.1**] File does not exist: /home/aaron/WebPages/******.com/favicon.ico
[Sat Nov 24 20:44:18 2007] [notice] SIGHUP received.  Attempting to restart
[Sat Nov 24 20:44:20 2007] [warn] The Alias directive in /etc/apache2/apache2.conf at line 240 will probably never match because it overlaps an earlier Alias.
apache2: apr_sockaddr_info_get() failed for :lolflag:
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Sat Nov 24 20:44:20 2007] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sat Nov 24 20:44:20 2007] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sat Nov 24 20:44:22 2007] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Sat Nov 24 20:44:22 2007] [notice] mod_python: using mutex_directory /tmp 
[Sat Nov 24 20:44:27 2007] [notice] Apache/2.2.4 (Ubuntu) Embperl/2.2.0 mod_python/3.3.1 Python/2.5.1 PHP/5.2.3-1ubuntu6 mod_perl/2.0.2 Perl/v5.8.8 configured -- resuming normal operations


DID you see anything  that could help me solve my problme???

---

### Post by conjur3r on 2007-11-24
We will need to try and isolate what the exact problem is.  Let's first confirm that apache is working for you and it is serving the correct pages on your LAN.  Before doing the following tests, in a terminal, watch your access logs with the following command (change the location to where ever it should be):

# tail -f /loc/of/access_log

1. Open up a browser from a computer on your LAN (both on the server and some other one) and enter the IP address of the server.

2. Same thing as above but use the domain you purchased.

Now if all of the above work, you should see entries getting spitted out in the terminal with your tail command.  This means that apache is working ok.  We'll fix up those warning/error messages you printed out in your error log later.

Now it's onto testing your network connectivity.  The key point here is to ensure your domain details are correct.  If there are any problems here, this is where you will receive those common gateway interface (CGI) errors.  You will need to include your domain name so that we can have a better look at what's going on.  If you do not want to, pm me with it.

---

### Post by hockey97 on 2007-11-24
My paid domain name is  [www.demonicproductions.com](www.demonicproductions.com)

I am still looking over your reply ...

---

### Post by hockey97 on 2007-11-24
ok I just tried that  tail -f  thing,  and I got nothing happening.

I tried my computer with the server and also another computer in my house and it didn't work the other computer gave  me a connot be found and a search engine.

the one on my server I can see my webpage.

but on the access log  it showed no difference  no new  stuff, it only show's old logs.

is has some 404 errors,  but that was a while back which I knew what the problem was,  the internal ip address changes every time I  shutdown so I didn't have the new ip address in apache2 so it gave me a 404 error not found.

that was fixed a while back.

I am looking at both access log  of  my domain name and  my internal ip address server.

the one with mydomain  that one has  no logs of  today the last record was on nov 11nth.

the one on my ip server thing  the last log was nov 24, which is today and seen it update when I type in my ip address.




my main problem is that any other computer weather it's on my lan or from the web people  can't see my website they see a cgi error,  but my computer with the server when I type it , everything works fine I see my webpage.

---

### Post by conjur3r on 2007-11-24
> **hockey97 said:**
> ok I just tried that  tail -f  thing,  and I got nothing happening.

You may have been watching the wrong file?  Double check which file you are supposed to be watching by looking in your apache configuration for your vhost.  Paste the contents of your config here if you would like and we'll let you know which file you should be watching.

> 
I tried my computer with the server and also another computer in my house and it didn't work the other computer gave  me a connot be found and a search engine.

the one on my server I can see my webpage.

but on the access log  it showed no difference  no new  stuff, it only show's old logs.


Is this using the internal IP address or the domain name?  If you are watching the right file, there will be new lines added everytime your apache receives a request and serves it up.

> 
is has some 404 errors,  but that was a while back which I knew what the problem was,  the internal ip address changes every time I  shutdown so I didn't have the new ip address in apache2 so it gave me a 404 error not found.

that was fixed a while back.


Well that's concerning!  You most definitely want to assign a static ip address for your server so that you do not need to keep changing your port forwarding in your modem everytime you reboot!

> 
I am looking at both access log  of  my domain name and  my internal ip address server.

the one with mydomain  that one has  no logs of  today the last record was on nov 11nth.

the one on my ip server thing  the last log was nov 24, which is today and seen it update when I type in my ip address.


Ok, it sounds like the last log with the entries is the file you should be watching.

> 
my main problem is that any other computer weather it's on my lan or from the web people  can't see my website they see a cgi error,  but my computer with the server when I type it , everything works fine I see my webpage.

A whois of your domainname points me to go to the following authoritative name servers:

      NS43.DOMAINCONTROL.COM
      NS44.DOMAINCONTROL.COM
      NS1.DEMONICPRODUCTIONS.COM

A query to both of the top ones returns nothing.  Go to your domain name administration (presumably at domaincontrol.com) and edit your domain details so that it has an A record.  When you've got it sorted out, the following will return an ANSWER section.

# dig demonicproductions.com @ns43.domaincontrol.com

You can compare it with a record which works, such as google:

# dig google.com @ns43.domaincontrol.com

---

### Post by hockey97 on 2007-11-24
ya I got the A record thing in the domain name admin area.

it asks  a hostname and a point to,   I put host name, is [www.demonicproductions.com](www.demonicproductions.com)  and a point to is my external ip address.

---

### Post by hockey97 on 2007-11-25
I have a questions about bind 9.

for the A records I have the domain name pointed to my internal ip address  should that be external ip address??

I have in my domain name  admins or the people that gave me the domain name service,  on their page I  have the A records  with my domain name pointing to external ip address.

is that right???

 I don't think I setup the name servers right,   I have ns1.mydoamin.com  as a ns record and also have an A record of it pointing to my internal ip address.

I really need to know  if all ip addresses I have to point my domain recrods to  my internal ip or external ip.

I just found out  using vtunnel  if I use  demonicproductions.com   without the www.   it takes me to my other vhost, that means people outside my network meaning people from the internet can see my other vhost,  I hve 2 one it demonic productions, the other one is not a registered domain name and don't want it active yet until I buy a domain name for that.

so I now only can see that vhost that is not supposed to show up on demonicproductions.com

and if  I have to use both internal and external ip's at differnet records I  need to know what record needs what type of ip address.

internal /  external???

I am also told that for the name servers  a catch 22 error can occure  since for me mine name servers are going to be ns1,mydomain.com, ns2.mydomain.com

---

### Post by hockey97 on 2007-11-25
Hi I got it to work.

their was a conflict with the other vhost it responding to any requests to my server.

but  now how can I make my internal network,  like the computers at my house how can I get them to be able to just type [www.mydomain.com](www.mydomain.com) in the browser and get my website.

what I get on my internal network is my  router.

becuse my domain that I bought it get's forwarded to my router which deals with the external ip addres and if I type in my external ip address I get that login prompt to my router setttings ect.

---

### Post by conjur3r on 2007-11-26
Glad to know it's working.

Re your question with internal machines typing the domain but receiving the router's admin page, well unless you want to purchase a new modem which is aware of the port forwarding and should also redirect internal requests, then there's a couple of strategies.

1. Edit each of your internal machine's host file and map demonicproductions.com to the internal server's ip address.  Or

2. Add that same mapping into your **local** dns server (if you are running one!), then you do not have to worry about each machine attached to your LAN.  I would suggest this approach if you area running a local dns server.

---

### Post by hockey97 on 2007-12-02
I have bind 9 dns server,  for my internal machines should I use the ip address 127.0.0.0  meaning local host, or should I use my internal ip address.

If it's internal ip address I already have the domain names pointing to the internal ip address of my server. 

Basically I want to have my internal computers to be able to just type my domain name in the web browser and left them able to see the website just like if it was someone from the internet looking at it.

The people that sold me the domain I made, they have a place where I can make an A record and point the domain name to an ip address.

and I got only one which was the domain name pointing to my external ip address.

on the computer that is my server,  that computer I could type in my domain name in the web browser and it would give me my webpage but for other computers on my lan network, when you type my domain name it then would  prompt a login window for my router and then it would when I  give the password and stuff it would take me to my router config area,  this is on other computers on my lan network internal network.

but one laptop on my lan network  it would get the routers login window when you put the password and user name it would then take you to my website.

but other computers on my lan it would just login to my router, that's only for internal computers.

people outside my network could see my page and have no problem just want my internal computers to get to my website with typing my domain name.

otherwise I have to use vtunnel.com to test my website and to see it.

---

### Post by hockey97 on 2007-12-02
sorry just fixed it.

---

### Post by pneaveill on 2007-12-29
> **hockey97 said:**
> sorry just fixed it.

Sorry for the semi-newb question here, but how did you resolve this issue?

---

### Post by hockey97 on 2007-12-30
it was my internal ip address it changed on me. 

if you having problems with apache2 with vhosting.  or getting a name for it I can help. 


what I did I edited my hostfile in /etc on ubuntu linux.

that only allows you to type in the domain name that you just created in that host file and it will direct you to that domain website.  only local meaning internal.

but if you want it to be for external you need someone to be able to sell you the domain. 

and if you think their is a way around buying a domain their isnt'.  All you will find is the sorce of why we pay for a domain.

ICANN is a federal organization their responsible for  us paying for domain names to be public.

I hear it's not easy nore cheap to buy a doamin space from them direct.
their the people that allow or give permission to people that want to resell the domain service.  They make you take a test and you pay a monthly fee. according to what I hear.

good luck.

---

