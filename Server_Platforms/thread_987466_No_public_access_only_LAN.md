---
title: "No public access only LAN"
date: 2008-11-19
forum: Server Platforms
---

### Post by LT72884 on 2008-11-19
OK. here is what my environment looks like..

I have a webserver in my office that i built using Ubuntu. I installed LAMP and phpmyadmin on it. I created my DB for wordpress 2.6. I installed wordpress and everything works great LAN side. In the wordpress dashboard(i hope someone here knows what this is) i have my wordpress URL and blog URL set to 192.168.0.225 with Http in front of it

Now in the /etc/apache2/sites-enabled folder resides a file named 000-default. I imagine that is the virtual hosts file. I have edited that file under root user to say that the root document is /var/www/wordpress

LAN side, if i go to any machine with in my LAN and open a browser and i type 192.168.0.225

I get my main wordpress page. Meta login works and everything.

Now here is the issue. i have 14 usable IP's(/28 mask)The router i am using is 66.60.115.62(this is our server testing router) and its LAn is 192.168.0.10. I ping syncrasy.blogsite.org and 100%. I also do a traceroute to make sure my server has the right default GW info.

In the wordpress dashboard i change the URL for both entries to syncrasy.blogsite.org which is registered to point at 66.60.115.62

i set my servers default GW to be 192.168.0.10

and i restart the server. Now i cant even access it locally. 192.168.0.225 does not work any more and neither does typing the domain name and or public IP work.

Something is a miss and i can not seem to figure it out. Wordpress told me to go to a diff forum because they are only word press issues which i am not sure this is.

Thanx.

---

### Post by cdenley on 2008-11-19
If you set the URL correctly (syncrasy.blogsite.org?), then can you access it from outside your network. Some routers will not port-forward connections from 66.60.115.62 to 192.168.0.225 if the connection is coming from the LAN, yet it will for the WAN. Sometimes this feature is missing, or sometimes it is configurable. What happens when you add an entry to the client's /etc/hosts file like
```

192.168.0.225 syncrasy.blogsite.org

```

How exactly does it not work?
```

wget -O /dev/null http://syncrasy.blogsite.org/

```

---

### Post by SpaceTeddy on 2008-11-19
can you please provide the default website configuration that you used in the apache. Usually,the default is NOT edited but kept as a fallback, and each virtual host gets it's own file with it's own distinct hostname (or so i do it)...

Also if your server has the ip 192.168.0.10 this should be configured - the server itself does not now it's external ip unless you specifically configure it...

i've ran wordpress websites on NAT'ed hosts before, and it has not been a problem yet... i guess the problem is somewhere in the apache2 that does not resolve the hostname correctly... thus sending you into the wrong apache2 configuration (or none). 

One other thought - please really verify that the packets reach the right server. A good way to do this (for me) is to have a tcpdump running on the server. Then you should see the packets arrive from your requests. I just want to make sure this is not a network problem...

---

### Post by LT72884 on 2008-11-20
> **cdenley said:**
> If you set the URL correctly (syncrasy.blogsite.org?), then can you access it from outside your network. Some routers will not port-forward connections from 66.60.115.62 to 192.168.0.225 if the connection is coming from the LAN, yet it will for the WAN. Sometimes this feature is missing, or sometimes it is configurable. What happens when you add an entry to the client's /etc/hosts file like
```

192.168.0.225 syncrasy.blogsite.org

```

How exactly does it not work?
```

wget -O /dev/null http://syncrasy.blogsite.org/

```

Sorry for the late reply. I was in class. Im not sure if i can from outside but i know our router can handle because after this router it is hooked to our cisco router which would handle that. Plus our other webserver (windows) for our company is on the same router and i can hit the page just fine.

127.0.1.1       syncrasy.blogsite.org

thats what my hosts file says. I added that the other day. I will try adding that entry to it now.

"How exactly does it not work?"
No webpage is showing. I have a full featured website with music and all that jazz and it does not show up. 

Here is the 000-deafult config

NameVirtualHost *:80
<VirtualHost *>
	ServerAdmin [email]mattswork@comcast.net[/email]
	
	DocumentRoot /var/www/wordpress
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/wordpress>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


Here is part of the apache2.conf that tells me that virtual hosts are in the sites-enabled folder

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:[B]
Include /etc/apache2/sites-enabled/
[/B]



thanx

Matt

---

### Post by cdenley on 2008-11-20
> **LT72884 said:**
> 
No webpage is showing. I have a full featured website with music and all that jazz and it does not show up. 


Is it giving you the "It works!" page? Is it giving you an empty page? Is apache giving you an error page? Is it failing to connect to apache? You're still being too vague. Posting the output of the wget command would help.

---

### Post by LT72884 on 2008-11-20
> **SpaceTeddy said:**
> can you please provide the default website configuration that you used in the apache. Usually,the default is NOT edited but kept as a fallback, and each virtual host gets it's own file with it's own distinct hostname (or so i do it)...

Also if your server has the ip 192.168.0.10 this should be configured - the server itself does not now it's external ip unless you specifically configure it...

i've ran wordpress websites on NAT'ed hosts before, and it has not been a problem yet... i guess the problem is somewhere in the apache2 that does not resolve the hostname correctly... thus sending you into the wrong apache2 configuration (or none). 

One other thought - please really verify that the packets reach the right server. A good way to do this (for me) is to have a tcpdump running on the server. Then you should see the packets arrive from your requests. I just want to make sure this is not a network problem...

I want to say i can assure you its not a network problem but i can see what your kind of up to. So i will do as much as i can to help you help me. LOL if that makes sense. 

My server is 192.168.0.225 and my default GW is 192.168.0.10 Which has a gateway of last resort set. The gateway of last resort is our ISP cisco router here at work. 

I do a traceroute to a outside website such as google and the fisrt ICMP echo reply is from my servers GW, then it hits my ISP cisco router and then on and on and on tell it hits google.

---

### Post by LT72884 on 2008-11-20
> **cdenley said:**
> Is it giving you the "It works!" page? Is it giving you an empty page? Is apache giving you an error page? Is it failing to connect to apache? You're still being too vague. Posting the output of the wget command would help.


Sorry, My bad. I thought my very first post said what the error was. 

As soon as i hit the save button in wordpress to save the URL changes. it says on the bottom left corner of mozilla 

waiting for syncrasy.blogsite.org. then after 3 minutes or so. it gives me a page that says error 110 timeout.

THEN in order for me to change it back to the original since i cant get to my dashboard any more. I have to go to 192.168.0.225./phpmyadmin and change  two entries under options tab in the wordpress DB from [http://syncrasy.blogsite.org](http://syncrasy.blogsite.org) to [http://192.168.0.225](http://192.168.0.225). That will reset my URLs in the dashboard and then i can access the page LAN side again.

I cant give you the output of wget because it redirects it to 127.0.1.1 which is me. So let me see if i have another linux box here at work.
Unles si remove the entries from my hosts file.

ok here is another error

Firefox has detected that the server is redirecting the request for this address in a way that will never complete.

---

### Post by LT72884 on 2008-11-20
now when i type 192.168.0.225 in the browser, i get nothing. two minutes later a timeout 110 error


wget. 
Resolving syncrasy.blogsite.org... 66.60.115.62
Connecting to syncrasy.blogsite.org|66.60.115.62|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.

---

### Post by cdenley on 2008-11-20
> **LT72884 said:**
> now when i type 192.168.0.225 in the browser, i get nothing. two minutes later a timeout 110 error


wget. 
Resolving syncrasy.blogsite.org... 66.60.115.62
Connecting to syncrasy.blogsite.org|66.60.115.62|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.

A 401 reply. That is interesting, especially considering you have not set any authorization restrictions in your vhost or permitted AuthConfig to be overridden. I can only think of 3 possibilities.

-you defined another vhost with ServerName syncrasy.blogsite.org, and set authorization restrictions
-your script for some reason is returning a 401 header (unlikely)
-instead of forwarding the request to the server, the router is sending the request to another web server (possibly it's own admin console), then returning a 401 error.

Try this to verify the 401 reply is coming from the ubuntu server.
```

$ nc syncrasy.blogsite.org 80
HEAD / HTTP/1.0


```
The "HEAD" line followed by an empty line will send the "HEAD" request to the server. The server should reply with a few headers. If it is coming from your ubuntu server, it will look something like this:
```

HEAD / HTTP/1.0

HTTP/1.0 401 Unauthorized
Date: Thu, 20 Nov 2008 16:32:17 GMT
Server: Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch
X-Powered-By: PHP/5.2.6-2ubuntu4
Vary: Accept-Encoding
Connection: close
Content-Type: text/html

```

---

### Post by LT72884 on 2008-11-20
> **cdenley said:**
> A 401 reply. That is interesting, especially considering you have not set any authorization restrictions in your vhost or permitted AuthConfig to be overridden. I can only think of 3 possibilities.

-you defined another vhost with ServerName syncrasy.blogsite.org, and set authorization restrictions
-your script for some reason is returning a 401 header (unlikely)
-instead of forwarding the request to the server, the router is sending the request to another web server (possibly it's own admin console), then returning a 401 error.

Try this to verify the 401 reply is coming from the ubuntu server.
```

$ nc syncrasy.blogsite.org 80
HEAD / HTTP/1.0

```
The "HEAD" line followed by an empty line will send the "HEAD" request to the server. The server should reply with a few headers. If it is coming from your ubuntu server, it will look something like this:
```

HEAD / HTTP/1.0

HTTP/1.0 401 Unauthorized
Date: Thu, 20 Nov 2008 16:32:17 GMT
Server: Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch
X-Powered-By: PHP/5.2.6-2ubuntu4
Vary: Accept-Encoding
Connection: close
Content-Type: text/html

```

how do i crete an empty line with out hitting enter. 
#nc syncrasy.blogsite.org 80 HEAD / HTTP/1.0
#
nothing really happens because im not to sure how to add carriage returns to command line entries.

"you defined another vhost with ServerName syncrasy.blogsite.org, and set authorization restrictions"

were would have i done this. I know when i first installed wordpress. i used phpmyadmin then by accident i used comand line to do the same thing. Sionce it was my first time installing wordpress. the directions from wordpress.org seemed to be really strange to me. So i might have created to mysql DB's

could that be it..

Thanx

---

### Post by cdenley on 2008-11-20
> **LT72884 said:**
> how do i crete an empty line with out hitting enter. 
#nc syncrasy.blogsite.org 80 HEAD / HTTP/1.0
#
nothing really happens because im not to sure how to add carriage returns to command line entries.

"you defined another vhost with ServerName syncrasy.blogsite.org, and set authorization restrictions"

were would have i done this. I know when i first installed wordpress. i used phpmyadmin then by accident i used comand line to do the same thing. Sionce it was my first time installing wordpress. the directions from wordpress.org seemed to be really strange to me. So i might have created to mysql DB's

could that be it..

Thanx

```

nc syncrasy.blogsite.org 80<enter>
HEAD / HTTP/1.0<enter>
<enter>

```

At the command prompt, type "nc syncrasy.blogsite.org 80". Press enter. Type "HEAD / HTTP/1.0". Press Enter. Press Enter again. You will then see the server's response.

Additional vhost configurations should be linked to in the directory /etc/apache2/sites-enabled.

---

### Post by LT72884 on 2008-11-20
root@shortstuff:/home/lt72884/Desktop# nc syncrasy.blogsite.org 80
HEAD / HTTP/1.0

HTTP/1.0 200 OK
Date: Thu, 20 Nov 2008 18:09:11 GMT
Server: Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6
X-Powered-By: PHP/5.2.3-1ubuntu6
X-Pingback: [http://syncrasy.blogsite.org/xmlrpc.php](http://syncrasy.blogsite.org/xmlrpc.php)
Connection: close
Content-Type: text/html; charset=UTF-8

root@shortstuff:/home/lt72884/Desktop#

---

### Post by cdenley on 2008-11-20
> **LT72884 said:**
> root@shortstuff:/home/lt72884/Desktop# nc syncrasy.blogsite.org 80
HEAD / HTTP/1.0

HTTP/1.0 200 OK
Date: Thu, 20 Nov 2008 18:09:11 GMT
Server: Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6
X-Powered-By: PHP/5.2.3-1ubuntu6
X-Pingback: [http://syncrasy.blogsite.org/xmlrpc.php](http://syncrasy.blogsite.org/xmlrpc.php)
Connection: close
Content-Type: text/html; charset=UTF-8

root@shortstuff:/home/lt72884/Desktop#

Well, that's what you should get, but you're not getting the same response as the wget output you posted before. Also, your web request didn't time out like you described. Are you still having a problem with your current configuration? Try the wget command again, except include the command you run when you post the output.
```

wget -O /dev/null http://syncrasy.blogsite.org/

```

---

### Post by LT72884 on 2008-11-20
ok hold on a sec. i need to re-take out 

127.0.1.1     syncrasy.blosite.org
192.168.0.225 syncrasy.blogsite.org

from my hosts file..

root@shortstuff:/home/lt72884/Desktop# wget -O /dev/null [http://syncrasy.blogsite.org/](http://syncrasy.blogsite.org/)
--11:41:49--  [http://syncrasy.blogsite.org/](http://syncrasy.blogsite.org/)
           => `/dev/null'
Resolving syncrasy.blogsite.org... 127.0.1.1
Connecting to syncrasy.blogsite.org|127.0.1.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,214        --.--K/s             

11:41:49 (174.61 MB/s) - `/dev/null' saved [12214]

root@shortstuff:/home/lt72884/Desktop# wget -O /dev/null [http://syncrasy.blogsite.org/](http://syncrasy.blogsite.org/)
--11:43:45--  [http://syncrasy.blogsite.org/](http://syncrasy.blogsite.org/)
           => `/dev/null'
Resolving syncrasy.blogsite.org... 66.60.115.62
Connecting to syncrasy.blogsite.org|66.60.115.62|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
root@shortstuff:/home/lt72884/Desktop# 

ok there you go.

root@shortstuff:~# nc syncrasy.blogsite.org 80
HEAD / HTTP/1.0

HTTP/1.1 401 Unauthorized
WWW-Authenticate: Basic realm="RT311"
Content-Type: text/html
Server: ZyXEL-RomPager/3.02

<HTML>
<HEAD>
<TITLE>Protected Object</TITLE>
</HEAD>
<BODY>
<H1>Protected Object</H1>
This object on the <FONT COLOR="#FF0000">RT311</FONT> is protectedroot@shortstuff:~#

---

### Post by cdenley on 2008-11-20
> **LT72884 said:**
> ok hold on a sec. i need to re-take out 

127.0.1.1     syncrasy.blosite.org
192.168.0.225 syncrasy.blogsite.org

from my hosts file..

root@shortstuff:/home/lt72884/Desktop# wget -O /dev/null [http://syncrasy.blogsite.org/](http://syncrasy.blogsite.org/)
--11:41:49--  [http://syncrasy.blogsite.org/](http://syncrasy.blogsite.org/)
           => `/dev/null'
Resolving syncrasy.blogsite.org... 127.0.1.1
Connecting to syncrasy.blogsite.org|127.0.1.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 12,214        --.--K/s             

11:41:49 (174.61 MB/s) - `/dev/null' saved [12214]

root@shortstuff:/home/lt72884/Desktop# wget -O /dev/null [http://syncrasy.blogsite.org/](http://syncrasy.blogsite.org/)
--11:43:45--  [http://syncrasy.blogsite.org/](http://syncrasy.blogsite.org/)
           => `/dev/null'
Resolving syncrasy.blogsite.org... 66.60.115.62
Connecting to syncrasy.blogsite.org|66.60.115.62|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
root@shortstuff:/home/lt72884/Desktop# 

ok there you go.

root@shortstuff:~# nc syncrasy.blogsite.org 80
HEAD / HTTP/1.0

HTTP/1.1 401 Unauthorized
WWW-Authenticate: Basic realm="RT311"
Content-Type: text/html
Server: ZyXEL-RomPager/3.02

<HTML>
<HEAD>
<TITLE>Protected Object</TITLE>
</HEAD>
<BODY>
<H1>Protected Object</H1>
This object on the <FONT COLOR="#FF0000">RT311</FONT> is protectedroot@shortstuff:~#

That confirms that it is a networking problem. When your hostname resolves to a LAN IP, everything works fine. When your hostname resolves to your router's WAN IP, you get a response from the web server on your Netgear RT311 Internet Access Gateway Router, or the repackaged ZyXEL version.
[http://kbserver.netgear.com/products/RT311.asp](http://kbserver.netgear.com/products/RT311.asp)

---

### Post by LT72884 on 2008-11-20
That doesnt make sense because our other server works fine on it. We do have a proxy server.

see if you can get my site...

[http://syncrasy.blogsite.org](http://syncrasy.blogsite.org)

just does not make sense because we have a rule set up and everything. the cisco should see that 66.60.115.62 is one of its routable IP's. so it send it out the fastethernet port to the rt311. rt311 should see check the packet info against its table and see that its incomming on port 80 for tcp and send it to 192.168.0.225.

---

### Post by cdenley on 2008-11-20
> **LT72884 said:**
> That doesnt make sense because our other server works fine on it. We do have a proxy server.

see if you can get my site...

[http://syncrasy.blogsite.org](http://syncrasy.blogsite.org)

just does not make sense because we have a rule set up and everything. the cisco should see that 66.60.115.62 is one of its routable IP's. so it send it out the fastethernet port to the rt311. rt311 should see check the packet info against its table and see that its incomming on port 80 for tcp and send it to 192.168.0.225.

Well, obviously some step in that theory is failing. I am not able to get a response from syncrasy.blogsite.org (66.60.115.62) on port 80.

---

### Post by cdenley on 2008-11-20
By the way, if I remember correctly, I had used an RT-314 router a while ago. There was a feature that was missing called local loopback. When I connected to my WAN IP from within my LAN, port forwarding would not work. In order to get that feature, I had to upgrade the firmware. However, the newer firmware was not available from the router's brand (ZyXEL or Netgear), so I had to use a hacked version for the identical router packaged by the other company in order to get the newer firmware version with the "local loopback" feature.

You may encounter a similar problem with your RT-311, but that doesn't appear to be your current problem since port forwarding isn't working anywhere.

---

### Post by LT72884 on 2008-11-20
> **cdenley said:**
> Well, obviously some step in that theory is failing. I am not able to get a response from syncrasy.blogsite.org (66.60.115.62) on port 80.

but you can get a response, just not on port 80. 

yeah im lookin in the config as we speak, well my boss is.

i owe you a steak dinner bro.

---

### Post by cdenley on 2008-11-20
> **LT72884 said:**
> but you can get a response, just not on port 80. 

yeah im lookin in the config as we speak, well my boss is.

i owe you a steak dinner bro.

I don't get any response. I only tried port 80. Nmap doesn't find any open ports on that IP, though. I can resolve the domain name, that's about it.

---

### Post by LT72884 on 2008-11-20
thats odd. See i have this same issue when i took my server home to try it there. I couldnt get it to work on a dlink gamerlounge router either. And yes i had the domain pointing to my houses public IP.

try it now one more time please

---

### Post by cdenley on 2008-11-20
> **LT72884 said:**
> thats odd. See i have this same issue when i took my server home to try it there. I couldnt get it to work on a dlink gamerlounge router either. And yes i had the domain pointing to my houses public IP.

try it now one more time please

The hostname syncrasy.blogsite.org still resolves to 66.60.115.62, and I still get no response on port 80. DNS changes can take a few days to propogate. Should I try connecting to a different IP?

---

### Post by LT72884 on 2008-11-20
DANG IT. we had it working for like 2 minutes. but now it wont work. hmmm. give me a few.

---

### Post by LT72884 on 2008-11-20
ok now try

---

### Post by cdenley on 2008-11-20
> **LT72884 said:**
> ok now try

It works!

---

### Post by LT72884 on 2008-11-20
YAY! Thanx for the help. I guess the issue was something with the rt311. he had it port forwarding inward but not outward.

---

### Post by LT72884 on 2008-11-20
If i wanna contact you later on about wordpress and options with in it. how would i do so. Is there a wordpress chat here. Because im complelty new to this and would love some cool tips. Like having people post pics in the leave a comment section.

once again thanx.

If you dont mind. i would like to know what you did to troubleshot this out. and what the commnds are actually doing..

---

### Post by cdenley on 2008-11-20
> **LT72884 said:**
> If i wanna contact you later on about wordpress and options with in it. how would i do so. Is there a wordpress chat here. Because im complelty new to this and would love some cool tips. Like having people post pics in the leave a comment section.

once again thanx.

If you dont mind. i would like to know what you did to troubleshot this out. and what the commnds are actually doing..

Well, I'm probably not the guy to help with wordpress, seeing as I never used it before.

Some useful commands for server troubleshooting:
-nc: allows you to connect to any tcp server, and "talk" with it. Useful for http, ftp, smtp, or anything that uses simple, plaintext commands and output.
-wget: a simpler way to test web servers, if you just want the response code, or don't have a GUI.
-tcpdump: a packet capture utility. It can capture all network traffic to a file.
-wireshark: a graphical packet capture utility. Can be used to analyze files created by tcpdump.
-host: translates hostname to IP or IP to hostname
-dig: sends DNS queries

To find out more about commands, use the "man" command.
```

man nc
man tcpdump

```

Also, for apache, logs are often helpful:
-/var/log/apache2/access.log
-/var/log/apache2/error.log

---

### Post by LT72884 on 2008-11-20
> **cdenley said:**
> Well, I'm probably not the guy to help with wordpress, seeing as I never used it before.

Some useful commands for server troubleshooting:
-nc: allows you to connect to any tcp server, and "talk" with it. Useful for http, ftp, smtp, or anything that uses simple, plaintext commands and output.
-wget: a simpler way to test web servers, if you just want the response code, or don't have a GUI.
-tcpdump: a packet capture utility. It can capture all network traffic to a file.
-wireshark: a graphical packet capture utility. Can be used to analyze files created by tcpdump.
-host: translates hostname to IP or IP to hostname
-dig: sends DNS queries

To find out more about commands, use the "man" command.
```

man nc
man tcpdump

```

Also, for apache, logs are often helpful:
-/var/log/apache2/access.log
-/var/log/apache2/error.log


i will write those down. thanx for the help.

---

### Post by LT72884 on 2008-11-21
Ok another question i forgot to ask. 

I have the ftp service on my server but im not sure how to use it because when i log into it from a web browser  at home i get there but i dont know where there is. if that makes sense. i have no idea what folder im in. 

when i try it from my office computer i get this

An FTP protocol error occurred while trying to retrieve the URL: [ftp://xx.xx.xx.62:21](ftp://xx.xx.xx.62:21)

Squid sent the following FTP command:

    NLST

and then received this reply

    Use PORT or PASV first.

Your cache administrator is webmaster. 

then when i use a client it asks for user name and password. 

So what i would like to do is set up the ftp site so i can go to any folder in  the server or at least the wp-content folder for more wordpress themes. Also how do i set up user names and passwords. 

But i guess the first thing is is to make sure i have ftp. i think i do...

thanx

---

### Post by cdenley on 2008-11-21
> **LT72884 said:**
> Ok another question i forgot to ask. 

I have the ftp service on my server but im not sure how to use it because when i log into it from a web browser  at home i get there but i dont know where there is. if that makes sense. i have no idea what folder im in. 

when i try it from my office computer i get this

An FTP protocol error occurred while trying to retrieve the URL: [ftp://xx.xx.xx.62:21](ftp://xx.xx.xx.62:21)

Squid sent the following FTP command:

    NLST

and then received this reply

    Use PORT or PASV first.

Your cache administrator is webmaster. 

then when i use a client it asks for user name and password. 

So what i would like to do is set up the ftp site so i can go to any folder in  the server or at least the wp-content folder for more wordpress themes. Also how do i set up user names and passwords. 

But i guess the first thing is is to make sure i have ftp. i think i do...

thanx

Are you sure you want FTP? It is very insecure. Using SSH would be much simpler and more secure.
```

sudo apt-get install openssh-server

```

Then, from the client, you can connect with:
-Filezilla (Windows or Linux)
-WinSCP (Windows)
-Nautilus (Places>Connect to Server...)

You just login with your system user. If you want to write to a directory like /var/www, you would need to give yourself write permission.

---

### Post by LT72884 on 2008-11-21
just as long as i can get themes from my computer at home to my wordpress server at work. Because when im at home and i feel like workin on my site and i see i new theme, i need to be able to upload it to /var/www/wordpress/wp-content/themes folder

ssh is all threw command line right?

---

### Post by cdenley on 2008-11-21
> **LT72884 said:**
> just as long as i can get themes from my computer at home to my wordpress server at work. Because when im at home and i feel like workin on my site and i see i new theme, i need to be able to upload it to /var/www/wordpress/wp-content/themes folder

ssh is all threw command line right?

No. There is also an sftp subsystem which kind of mimics an FTP server, but everything is sent through your encrypted connection.

---

### Post by LT72884 on 2008-11-21
i have putty at home so i will just use that to connect. but then how do i grab stuff of my desktop at home and copy over ot the server? 

i have only used ssh to remotly connect to my firewall for configuration

ok i have openssh-server installed. Any configuration need to be done. Do i need any client software at my house or whereever i am to upload through the sftp

---

### Post by cdenley on 2008-11-21
> **LT72884 said:**
> i have putty at home so i will just use that to connect. but then how do i grab stuff of my desktop at home and copy over ot the server? 

i have only used ssh to remotly connect to my firewall for configuration

I already gave you a few options.
> 
Then, from the client, you can connect with:
-Filezilla (Windows or Linux)
-WinSCP (Windows)
-Nautilus (Places>Connect to Server...)


---

### Post by LT72884 on 2008-11-21
> **cdenley said:**
> I already gave you a few options.

opps i posted at the same time. lol. ok ill give it a shot and see what happens. thanx

---

