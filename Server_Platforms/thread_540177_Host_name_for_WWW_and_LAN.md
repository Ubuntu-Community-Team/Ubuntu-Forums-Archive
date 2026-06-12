---
title: "Host name for WWW and LAN?"
date: 2007-09-01
forum: Server Platforms
---

### Post by Raymond Day on 2007-09-01
Running a Ubuntu server in my house. I named it small because the system I have it in is small. That's it's host name.

I have a port open to it so some people I know can get to it over the WWW.

Setup no-ip so now I have a no-ip address to it.

I can get to it from my home typing small or the no-ip address.

What I like to know is how do I set it up so Ubuntu server know both names and that one is for the LAN and one for the WWW?

I guess in /etc/host?

I would put small and the no-ip names both in there just a space between them? Is that all it takes to set it up?

-Raymond Day

---

### Post by koenn on 2007-09-01
yes.

but maybe not : you may also need to tell your web server what its hostname is. 

Try, see what gives, undo your changes if it doesn't work out. easy.

---

### Post by NewbieNik on 2007-09-01
setting the host names just tells the server which IP address to attach to the host names/
Are you trying to restrict WWW traffic to certain services such as http and ftp and LAN to others such as ldap and file-sharing?
In which case a firewall is your best bet, check out the GUI interface of firestarter (apt-get install firestarter)
Very good interface and easy to follow

---

### Post by Raymond Day on 2007-09-01
Here is what I get if when it boots up or restarts:

> root@small:~/noip-2.1.4# /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                                    apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
root@small:~/noip-2.1.4#

I like to get to it still on my LAN with the name just small and all some times get to it from other places using my no-ip name for it. How do you tell it both names? Does it need to know one is LAN and one is WWW?

When I am at home I don't want to out the WWW to get to it. Just my LAN but I don't want to stop the WWW ether.

This is on a Ubuntu server. I can only type on it to give it commands. I guess firestarter would not help me. Looks like it's to do settings on the firewall. It's working like it is but like the apache2 gets that error.

-Raymond Day

---

### Post by NewbieNik on 2007-09-01
sounds like its the hosts file. You need to tell the server iwhich name for which IP address. In your /etc/hosts file you should have something like:-

127.0.0.1 localhost localhost.localdomain
*192.168.0.1* small small.*no-ipdomain*

change the 192.168 address to whatever IP address your eth card is set to, change the no-ipdomain to whatever your no-ip domain name is.
You the need to configure youre router to pass whichever WWW traffic you want to the server.
This means  the server now knows how to talk to itself (localhost) by using the loopback interface 127.0.0.1 and it also knows anything looking for *small* will come through te eth card.
You will need to restart the server to pick up on these ip addresses.

---

### Post by Raymond Day on 2007-09-01
Thank you NewbieNik

My /etc/hosts looks like this with my no-ip not showing. I don't want lots of people to know it else it will slow down my home Internet. So I replaced that part with XXXXXX

> 127.0.0.1	localhost	localhost.localdomain
127.0.1.1	small
192.168.1.109	small		XXXXXX.no-ip.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Then to test it I did:

> root@small:~# /etc/init.d/hostname.sh
root@small:~# /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                                    apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
root@small:~#

So it looks like it did not work. I guess something is not right with the /etc/hosts file?

-Raymond Day

---

### Post by NewbieNik on 2007-09-01
nah, host file seems fine then, but very concerned you cannot ping  loopback. Will look into it and get back to you asap

you did the correct thing, hiding your no-ip account, dont worry

quick question...have you installed squid?

---

### Post by Raymond Day on 2007-09-02
No I don't have squid installed. I looked to see what it is. To speed up web pages by caching them. It don't look like squid would help me.

I looked on the google for "apache2: Could not reliably determine the server's fully qualified domain name" but it has not help me. Looks like a lot have this type error.

I would think a lot have it at home and want to use both names like me. It's LAN name and WWW name.  It looks like that's were it's hard to know how to do it.

-Raymond Day

---

### Post by Raymond Day on 2007-09-02
I rebooted just to make sure. But I still get the error. I changed the /etc/hosts file a little. This is how it works after a reboot:

```
root@small:~# /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                                    apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
root@small:~# cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost
127.0.1.1       small
192.168.1.109   xxxxxx.no-ip.com        xxxxxx

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
root@small:~#
```

-Raymond Day

---

### Post by lamnk on 2007-09-02
Do you want to access your server from outside by WWW ? If that is the case then you must change the server name, ip & port in your httpd.conf

Change these two lines in httpd.conf
> Listen 192.168.1.109:80
ServerName xxxxxx.no-ip.com:80

---

### Post by inphektion on 2007-09-02
In the apache2 config dir where the dir sites-available and sites-enabled is should be a file called local-host-names.  In there put 
XXXX-no-ip.com
small
localhost

---

### Post by Raymond Day on 2007-09-02
Thank you Lamnk. That did make a change but looks like it did not fix it. My /etc/httpd/httpd.conf file had nothing in it. So I did just what you said put in it. But replaced the XXXXXX with my real noip name. After I restarted apache it came back like this then.

```
root@small:/etc/apache2# /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                                    (99)Cannot assign requested address: make_sock: could not bind to address 192.168.1.109:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]
root@small:/etc/apache2#
```

The [fail] is red color.

Maybe it needs my noip IP. But that can change a lot. How would I tell it that in a file if I need to?

-Raymond Day

---

### Post by Raymond Day on 2007-09-02
I did what you said inphektion apache will not start then! I put the same file in both folder sites-enabled and sites-available when I restart apache it gives this error I have here. I copy the local-host-names with a ~ at the end then deleted them and restarted apache and it works but with the same "Could not reliably determine the server's fully qualified domain name" then.


> root@small:~# cp /etc/apache2/sites-enabled/local-host-names~ /etc/apache2/sites-enabled/local-host-names
root@small:~# /etc/init.d/apache2 restart                                        * Forcing reload of web server (apache2)...                                    Syntax error on line 1 of /etc/apache2/sites-enabled/local-host-names:
Invalid command 'XXXXXX.no-ip.com', perhaps misspelled or defined by a module not included in the server configuration
                                                                         [fail]
root@small:~# rm /etc/apache2/sites-enabled/local-host-names
root@small:~# /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                                    apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
root@small:~#

When the red [fail] is there going to it's web page with ether small or noip name the page can not be displayed error I get. I even put a http:// before the XXXXX.no-ip.com

---

### Post by inphektion on 2007-09-02
no local-host-names goes in /etc/apache2 not inside the sites-whatever folder.

---

### Post by Raymond Day on 2007-09-02
Still did not work. It comes back with the error 2 times now. At lest apache still runs.

```
root@small:~# cp /etc/apache2/sites-enabled/local-host-names~ /etc/apache2/local-host-names
root@small:~# /etc/init.d/apache2 restart                                        * Forcing reload of web server (apache2)...                                    apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
root@small:~#
```

-Raymond Day

---

### Post by Raymond Day on 2007-09-02
Looks like it's fixed!

I just changed my /etc/hosts file.

> root@small:~# rm /etc/apache2/local-host-names
root@small:~# /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                             [ OK ]
root@small:~# cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost
127.0.1.1       XXXXXX.no-ip.com        small

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
root@small:~#

Thank you for all the help people!

I guess on ubuntu set up they should ask LAN server name then WWW server name. That way all this would be set up for you.

-Raymond Day

---

### Post by Raymond Day on 2007-09-02
I found this out by going to a Ubuntu server a person installed on a Toshiba Magnia SG20 I have. He made a image that can put on it and it is headless. He got it to control the fans and LCD display.

So I looked on it in it's /etc/hosts file. That's were I got what mine should look like.

Because I set up this Ubuntu server from 2 other severs. I now have it all on this one. I had .org and .com to it. Can still go to both the .com and .org so all the links to it still work. Do I need the .org too in the /etc/hosts ?

I guess it look something like:

127.0.0.1	localhost.localdomain	localhost	
127.0.1.1	XXX.no-ip.com	small
127.0.1.1       XXX.no-ip.org         small

Or like this:

127.0.0.1	localhost.localdomain	localhost	
127.0.1.1	XXX.no-ip.com	XXX.no-ip.org      small

I called the person who made the image were I looked at /etc/hosts. He said I don't need the org address in the /etc/hosts file.

-Raymond Day

---

### Post by scarwear on 2007-11-25
Do you know where a person can get the ubuntu image for the Toshiba SG20?  Thanks in advance.

---

### Post by Raymond Day on 2007-11-25
Yes. The link is:

[http://www.wildsong.biz/index.php?title=Otter]("http://www.wildsong.biz/index.php?title=Otter")

The download is near the top of the page. It talks a lot about how he did it on that page.

-Raymond Day

---

