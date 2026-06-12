---
title: "Apache2 Beginner #2"
date: 2011-12-26
forum: Server Platforms
---

### Post by mike_abc on 2011-12-26
[SIZE=2]Hi everybody,

In a previous post, on 24 December, I tried to install a Virtualhost on Apache 2 for Ubuntu. Unfortunately, after lots of headbanging and with gracious help from Lars Nooden, I didn't succeed.

I am now trying to install a PLAIN Apache 2 webserver and tying to catch all the loose ends in the configuration files in the Ubuntu-style Apache 2 configuration (10+ files instead of one httpd.conf file).

Some questions for you:

(1) In a PLAIN, i.e. **[COLOR=Blue]NO virtualhost[/COLOR] **installation, which are the configuration files that Ubuntu-Apache reads ? I am still not in the clear if it reads the [/SIZE][SIZE=2] /etc/apache2/[/SIZE][SIZE=2]httpd.conf or ignores it and reads the other 10+ files :confused:.

(2)Can someone point me towards a really good tutorial Ubuntu-Apache2 configuration how-to ?

I've already read the Ubuntu Documentation [/SIZE][SIZE=3][ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP?action=fullsearch&context=180&value=linkto%3A%22ApacheMySQLPHP%22")[/SIZE][SIZE=2] - nothing interesting about Apache, except that by using the **default** file in **etc/apache2/sites-enabled** for configuration, I managed the rare performance to obtain the following message in terminal: 

```


"* starting web server apache2      [fail]"


``` - with no warning, no error message, no nothing.

Cheers,

Mike

[/SIZE][SIZE=2] [/SIZE]

---

### Post by lisati on 2011-12-26
Anything helpful show up in /var/log/apache2/access.log?

---

### Post by Lars Noodén on 2011-12-26
Merry Christmas!

Seeing as [font=Courier New]httpd.conf[/font] has a size of 0, no, it is not supposed to be read.  [font=Courier New]httpd.conf[/font].  Apache2 reads the many other files instead.  Yes, it's much more complex in some ways but it makes it about a thousand times easier if you are managing multiple virtual hosts in a production environment each with different administrators.  Almost all your changes will take place inside [font=Courier New]000-default[/font].  Since you won't be adding other virtual hosts, there will be no need to make other files.

Most of the tutorials I've run across are a bit out of date.  What are the top three things you want to do first with your web server?

A lot of tasks are already covered by one or more [modules](http://httpd.apache.org/docs/2.2/mod/).

mod_rewrite is probably the most powerful tool in the package.  But it only comes into play when you are rearranging an existing site or CMS.

mod_perl allows efficient use of perl, which is built into your system already.  

mod_php is popular but if you only want it for standardized headers, footers and navigation menus then Server Side Includes (SSI) are a much better match.

mod_deflate allows you to save a lot on bandwidth by compressing output.

mod_negotiation allow for content negotiation which is *the* way to do multilingual sites.

mod_ssl allows for encryption

Perhaps the most all-around useful would be to set up SSL and the easiest would be to configure mod_deflate.

---

### Post by Lars Noodén on 2011-12-26
As lisati mentioned, you want to check [font=Courier New]/var/log/apache2/error.log[/font].  When actively changing the configuration, you may find it useful to leave open a terminal with [tail](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tail.1.html)

```

tail -f /var/log/apache2/error.log

```

---

### Post by mike_abc on 2011-12-26
[SIZE=2]Hi, Lars,
hi everybody,

My target is to write PHP code which finally will buid up a dynamic website consisting mainly of images of flowers (botany). I've never written a PHP line in my life, and I am now trying to buid a development environment which will be easily ported on a hosting site.

The first tutorial-book I was trying to use wanted its readers to configure virtual hosts.
Since for, at least the foreseeable future, I only intend to have one site, and that one hosted, I actually don't need virtual hosts, so, after reinstalling (apt-get) for the 5th time the LAMP package, I am at present trying to see the famed "It works" page, but I am not yet able to.

What Apache config directives do I need to write and where do I need to write them to in order to get Apache started ?

I tried to write the directives in **../sites-enabled/default**, and also, when it didn't work, in **/etc/apache2/httpd.conf**, with NO positive result (see first post of this thread).

In the meantime I googled some more, and found a pretty good tutorial that explains the order in which the .conf files are read - and especially that all files in the **../conf.d/** directory are read - which is a vast number of files - at least for a beginner like me which knows nothing of Apache.

What I want to write is the simplest possible directives to achieve this:

To be able to do the development on the local machine
To have DocumentRoot in **/var/www/phpweb20/htdocs **with the subsequent folder structure

[B]and any other security related directive / other directive that is mandatory.
[/B]
I know I sound quite silly and impotent, but my Apache server hasn't started yet !!

I wish Apache was a BMW, or a Skoda, and I had the ignition keys, and could get in,  and  drive away to my business.

Regards,

Mike






[/SIZE]

---

### Post by Lars Noodén on 2011-12-26
The 'It works!' page should be visible from the moment you first install Apache.  I have it one one machine and in virtual machine on another machine.  Both worked out of the box.  Rather than proposing trying to re-install, let's work through the errors in the log file.  Can you open a terminal (resize the height if you wish) and leave it running [font=Courier New]tail -f /var/log/apache2/error.log[/font]?  That will allow you to see the errors as they occur.  Then try restarting Apache while watching the logs.

---

### Post by Lars Noodén on 2011-12-26
Another method that I find indispensable is to check the configuration files for syntax errors:

```

/usr/sbin/apache2ctl configtest

```

---

### Post by mike_abc on 2011-12-26
[SIZE=2]As I was saying, I reinstalled LAMP the 5-th time, and, when rebooting the computer, Apache starts. Its 000-default** is the out-of-package 000-default** BUT MENTIONS A VIRTUALHOST.
For the moment the error is gone - but with the tradeoff (in my opinion) of using virtualhosts.

[COLOR=Red]**I DON'T WANT VIRTUALHOSTS ! I WANT A (SINGLE) NORMAL HOST !**[/COLOR]

OR, do I get it wrong ?? Is the <Virtualhost *:80> etc. etc. my (SINGLE) NORMAL HOST, and ubuntu treats all hosts as virtualhosts ?! That would be Ubuntu-style Apache, at least in my understanding.

I ask this because **in the Linux httpd.conf** file YOU HAVE TO EXPRESSLY mention **virtualhosts** to configure them and use them. If you don't want them, you just don't use the VirtualHost directive.


[/SIZE]

---

### Post by mike_abc on 2011-12-26
[SIZE=2]I also found this post:

[/SIZE][SIZE=2]**IP-Based Virtual Hosts**[/SIZE]
 [SIZE=2]This alternative requires the setup of multiple IPs for a machine. In  this case, one instance of Apache hosts several domains, each of which  is assigned a different IP. 
[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]The following example shows how Apache can  be configured to host the original IP (192.168.1.10) plus two additional  domains on additional IPs (192.168.1.20 and 192.168.1.21). This  particular example only works on an intranet, because IPs ranging from  192.168.0.0 to 192.168.255.0 are not routed on the Internet.[/SIZE]
[SIZE=2]
[/SIZE]
 [SIZE=2]**Configuring IP Aliasing**[/SIZE]
 [SIZE=2]For Apache to host multiple IPs, the underlying machine must accept  requests for multiple IPs. This is called multi-IP hosting. [SIZE=3][COLOR=Blue]**For this  purpose, IP aliasing must be activated in the kernel.**[/COLOR][/SIZE][/SIZE]
 [SIZE=2]
[/SIZE]
[SIZE=2][SIZE=2]**Once the kernel has been configured for IP aliasing**[/SIZE], the commands  ifconfig and route can be used to set up additional IPs on the host.  These commands must be executed as root. For the following example, it  is assumed that the host already has its own IP, such as 192.168.1.10,  which is assigned to the network device eth0.[/SIZE]
 [SIZE=2]
[/SIZE]
[SIZE=2]Enter the command ifconfig to find out the IP of the host. Further IPs can be added with commands like the following:[/SIZE]
 [SIZE=2]
[/SIZE]
[SIZE=2][/SIZE]```

[SIZE=2]/sbin/ifconfig eth0:0 192.168.1.20
/sbin/ifconfig eth0:1 192.168.1.21[/SIZE]
 
```
[SIZE=2]
[/SIZE]
[SIZE=2]All these IPs are assigned to the same physical network device (eth0).[/SIZE]

---

### Post by Lars Noodén on 2011-12-26
> **mike_abc said:**
> ...OR, do I get it wrong ?? Is the <Virtualhost *:80> etc. etc. my (SINGLE) NORMAL HOST, and ubuntu treats all hosts as virtualhosts ?! ...

Yes.  All hosts are treated as virtual hosts in Apache2.  In Apache 1.3 you had only one host unless you expressly configured virtual hosts.  So the old default was a single host per server.   The new default is a single virtual host per server.  For a one-man IT shop it's not much of an improvement.  However, where you have more than a few people sharing responsibility for the vhosts, the new set up is much nicer.

---

### Post by mike_abc on 2011-12-26
[SIZE=2]OK !

If this is an Apache 2 thing, then we'll dance to the music. 

Unfortunately, on the Apache.org site there's no **visible** place where anything about** 000-default** is written, and there's NO WAY to look it up in the Version 2.2 Section (there's only the absurdly useless "Google Search"). I guess that even "for free" has its price.

Thanks Lars - there might be some additional questions down the road.

[/SIZE]

---

### Post by Lars Noodén on 2011-12-26
You're welcome.  I'm not sure what to say about the lack of documentation for Apache2.  There was tons of really good material for 1.3 but none of that got updated for 2.x  If one is already familiar with 1.3, then it's not so hard to figure out 2.x.  However, that leaves people who are just starting out in the cold.  

Even the Ubuntu documentation does not mention 000-default:
[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

As afterthought about SSI, if you do SSI, use [IncludesNOEXEC](http://httpd.apache.org/docs/2.3/mod/core.html#options).

---

### Post by mike_abc on 2011-12-27
[SIZE=2]This morning, I tried to run the famed "test.php".

Surprize ! PHP wasn't running. I tried to **locate** php.ini, the only PHP file I surely know should exist if PHP is installed. Surprize #2 ! No php.ini file was "located". There are the 2 php.ini example files located in ... - production and - development. I'll copy the - development to wherever the Ubuntu Documentation says, and rename it to php.ini.

Question #1: Why DID THAT happen ? When I previously installed PHP with MAKE, PHP was up and running. Now, with Synaptic, it isn't.

Question #2: Who starts PHP ? Ubunt, at boot time - or you have to start it manually (I don't think so..) ?

Cheers,

Mike 
[/SIZE]

---

### Post by mike_abc on 2011-12-27
[SIZE=2]DISREGARD PREVIOUS MAIL !

I reinstalled PHP5 (WITH SYNAPTIC !), checking some additional modules, and now it works.
Will be more carefully next time when posting.

Happy vacation (for whoever took one and went skiing :D).

[/SIZE]

---

