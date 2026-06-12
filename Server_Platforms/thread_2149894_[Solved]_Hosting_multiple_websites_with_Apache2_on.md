---
title: "[Solved] Hosting multiple websites with Apache2 on Server 12.04"
date: 2013-05-30
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2013-05-30
Hi all

With previous versions of Ubuntu server, following the article posted at [http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412) always worked.

With 12.04, the websites are not available outside the LAN.

Any suggestions, please?

TIA

---

### Post by Shrek01 on 2013-05-30
Have you set your firewall (router, box) to forward the apache ports (80, 443) to the LAN IP?

---

### Post by ChrisRChamberlain on 2013-05-30
Shrek01

Thanks for your reply - 80, yes, 443, no.

Will try it.

---

### Post by SeijiSensei on 2013-05-30
Let's start with the logs.  What do you see in /var/log/apache2/error.log?

How about a representative virtual host definition from /etc/apache2/sites-available/?

---

### Post by ChrisRChamberlain on 2013-05-30
```

```Redirecting port 443 did not resolve the issue.

By way of further explanation, this is a fresh install of Ubuntu server 12.04 - Unity desktop installed and only the websites added and defined as per the article link posted.

Each of the 3 websites has only index.html in the /htdocs/ folders for testing purposes.

Redirection is via [www.zonedit.com](www.zonedit.com) and ip addresses match correctly.

Content of /var/log/apache2/error.log including reboots as required.
```
[Thu May 30 10:10:22 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.5 with Suhosin-Patch configured -- resuming normal operations
[Thu May 30 10:50:18 2013] [notice] caught SIGTERM, shutting down
[Thu May 30 10:51:37 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.5 with Suhosin-Patch configured -- resuming normal operations
[Thu May 30 11:42:11 2013] [notice] caught SIGTERM, shutting down
[Thu May 30 11:43:06 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.5 with Suhosin-Patch configured -- resuming normal operations
[Thu May 30 11:44:35 2013] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu May 30 11:44:35 2013] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu May 30 12:05:47 2013] [notice] caught SIGTERM, shutting down
[Thu May 30 12:06:41 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.5 with Suhosin-Patch configured -- resuming normal operations
[Thu May 30 13:58:11 2013] [notice] caught SIGTERM, shutting down
[Thu May 30 13:59:06 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.5 with Suhosin-Patch configured -- resuming normal operations
```

Content of /etc/apache2/sites-available/www.specbilda.com, one of three such files

```
#
#  specbilda.com (/etc/apache2/sites-available/www.specbilda.com)
#
<VirtualHost *>
        ServerAdmin [email]webmaster@specbilda.com[/email]
        ServerName  [www.specbilda.com](www.specbilda.com)
        ServerAlias specbilda.com [www.specbilda.com](www.specbilda.com)

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /var/www/www.specbilda.com/htdocs/

        # CGI Directory
        ScriptAlias /cgi-bin/ /var/www/www.specbilda.com/cgi-bin/
        <Location /cgi-bin>
        #   Options +ExecCGI
        </Location>

        # Logfiles
        ErrorLog  /var/www/www.specbilda.com/logs/error.log
        CustomLog /var/www/www.specbilda.com/logs/access.log combined
</VirtualHost>
```

---

### Post by Shrek01 on 2013-05-30
If it is accessible from the inside (LAN) and not from the outside, then it is getting blocked by either your router, or by the server itself.

Besides the error log, have you seen any non local IP on the apache access logs?  If not, it would confirm my firewall theory.

I would double check your server's LAN ip (ifconfig), your _router_ redirecting to the correct LAN's IP and port, and check that your _server_ doesn't have a firewall aswell (sudo iptables -L).

---

### Post by ChrisRChamberlain on 2013-05-31
LAN IP is correct, port forwarding appears correct, ports 80 and 443 to the designated LAN IP address.

Can successfully ping the 'www.domainname.com'.

Not sure what 'sudo iptables -L' would return if there was a a firewall as well?

As this is a default installation of Ubuntu Server 12.04, presumably no firewall?

Any quick way to determine if data is being forwarded to this server?

---

### Post by ChrisRChamberlain on 2013-05-31
Checked out port 80 using ths tool :- 

[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)

so seems OK.

Any quick way to setup a single website as opposed to multiple websites and progress from there?

---

### Post by Shrek01 on 2013-05-31
> **ChrisRChamberlain said:**
> Can successfully ping the 'www.domainname.com'.
This is the router responding to the ping, not the server.
> **ChrisRChamberlain said:**
> Not sure what 'sudo iptables -L' would return if there was a a firewall as well?
Have you tried it?  
This is what you get when there is no firewall:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

> **ChrisRChamberlain said:**
> Any quick way to determine if data is being forwarded to this server?
Quick?
Here are some tools to see the network traffic incoming and outgoing from your server:
[LIST]
[*]wireshark (GUI) 
[*]tshark (console) 
[*]tcpdump (console) 
[/LIST]

---

### Post by sandyd on 2013-05-31
Try something like
```

tcpdump -i eth0 'port 80'
```

---

### Post by SeijiSensei on 2013-05-31
If you have access to a machine with a Linux or Unix terminal outside your network, you can simulate an HTTP connection with telnet like this:

```

$ telnet www.example.com 80[color=blue]
Trying 10.10.10.10
Connected to www.example.com.
Escape character is '^]'.[/color]
GET / HTTP/1.0

[color=blue]HTTP/1.1 200 OK
[stuff][/color]

```

The server replies are blue.  Note that you have to hit Enter twice after the GET command. Use Ctrl-] followed by "quit" to end your session.

To test for a specific virtual host use this syntax:
```

GET / HTTP/1.1
Host: virtual.example.com


```

You will see the HTTP headers followed by the contents of the index page for virtual.example.com.

---

### Post by Shrek01 on 2013-05-31
> **ChrisRChamberlain said:**
> Checked out port 80 using ths tool :- 

[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)

so seems OK.

Any quick way to setup a single website as opposed to multiple websites and progress from there?

Once again, this might be the router responding.
Some routers require a reboot for the new forwarding rules to apply.  Did you reboot it?

By default apache comes with a site with a single page saying "**It works**".  That should be accessible from the server [http://localhost](http://localhost) or from the outside [http://yourIP](http://yourIP)

---

### Post by ChrisRChamberlain on 2013-06-01
Many thanks for all the advice - going to start again from scratch, ie reinstall, and see if the default webpage can be accessed.

Will report output from "tcpdump -i eth0 'port 80'" when [www.domainname.com](www.domainname.com) is used.

Thanks for your patience

---

### Post by Shrek01 on 2013-06-01
Too bad you didn't try or reported back on the "sudo iptables -L", the "tcpdump", and the "telnet".  Your responses would have guided us on what was wrong.  BTW most of IT stuff is like solving a mystery... if you are careful on the details, you might learn something and even solve the problem, for you and other readers.

Anyway, good  luck.

---

### Post by ChrisRChamberlain on 2013-06-02
Getting very frustrated with this issue so considered a clean start would make it easier to resolve.

Clean install of Ubuntu Server 12.04, sudo apt-get update followed by sudo apt-get install ubuntu-desktop.

Logged in, 'http://localhost' brings up the default html page

Router has been rebooted after checking port forwarding is to attached device.

'sudo iptables -L' - no indication of a firewall

'telnet: Unable to connect to remote host: Connection timed out'

"tcpdump -i eth0 'port 80'" - first entry

09:42:43.134391 IP urayuli.canonical.com.http > ubuntu-antec.local.49456: Flags [P.], seq 1415349:1415614, ack 11390, win 257, options [nop,nop,TS val 588077929 ecr 335694], length 265

---

### Post by Shrek01 on 2013-06-02
So clearly the server works, apache works, and there is nothing on the server that blocks incoming requests. Nothing wrong there.

It is either on the router or the domain dns settings. Have you tried accessing it from the outside by IP?

---

### Post by SeijiSensei on 2013-06-02
You might want to check and make sure the ISP isn't blocking port 80.  Try forwarding another port to the server's 80, say 8000, then use [http://www.example.com:8000/](http://www.example.com:8000/) from outside and see if that works.

You do have a rule on the router to open port 80 as well as forward it, yes?

---

### Post by ChrisRChamberlain on 2013-06-03
So, some progress. :)

Replaced the router with another with same rules, etc as before, just in case it's router specific.

If you access the webite as 'http://nnn.nnn.nnn.nnn", the default page appears.

At [www.zoneedit.com](www.zoneedit.com) the IPv4 Addresses are correct, and have republished all three to be sure.

If you access the webite as 'http://www.specbilda.com" or any of the others, it times out.

So, where from here might one ask?

---

### Post by Shrek01 on 2013-06-03
Good :)

When I access [http://www.specbilda.com](http://www.specbilda.com) I see the Apache default page.

---

### Post by ChrisRChamberlain on 2013-06-03
Needed to clear the cache on the pc used to access the sites - all 3 available now. 

Going to follow the article at [http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412) and see what happens.

May have been a router problem all along?

---

### Post by Shrek01 on 2013-06-03
Yup

---

### Post by ChrisRChamberlain on 2013-06-04
Many thanks to all who patiently contributed to this thread.

Faithfully followed the instructions in the previously posted link and everything works as expected.

So, the problem on this occasion does appear to be caused by the router.

---

