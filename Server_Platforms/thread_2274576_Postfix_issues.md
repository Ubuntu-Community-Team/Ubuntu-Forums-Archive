---
title: "Postfix issues"
date: 2015-04-20
forum: Server Platforms
---

### Post by Mike_Hughes on 2015-04-20
I went line by line trying to install Postfix so I can install Mailman for my mailing list. When I try to connect to dovecot,  with telnet mail.biblematters.net 25 which was installed as well, this is the error message I received.

root@ubuntuServer:/etc/dovecot/conf.d# telnet mail.biblematters.net 25
Trying 192.1xx.xxx...
telnet: Unable to connect to remote host: Connection refused
If I leave off the mail portion I get in.

Where would I open up permissions so it would communicate?

On the browser side I see this error message - [COLOR=#000000][FONT=Times]The requested URL /cgi-bin/mailman/listinfo was not found on this server.[/FONT][/COLOR][HR][/HR]Apache/2.4.7 (Ubuntu) Server at biblematters.net Port 80

---

### Post by electronico_nc on 2015-04-21
Not only a simple DNS issue ?```
dig mail.biblematters.net
```> telnet mail.biblematters.net 25will connect to Postfix.
Which tutorial / how did you installed postfix & mailman ?
Nicolas

---

### Post by Mike_Hughes on 2015-04-21
What I received when I ran the dig mail.biblematters.net

```
; <<>> DiG 9.9.5-3ubuntu0.2-Ubuntu <<>> mail.biblematters.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 45765
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;mail.biblematters.net.         IN      A


;; AUTHORITY SECTION:
biblematters.net.       599     IN      SOA     ns69.domaincontrol.com. dns.jomax.net. 2015041801 28800 7200 604800 600


;; Query time: 109 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Tue Apr 21 09:29:32 CDT 2015
;; MSG SIZE  rcvd: 118
```

Would be nice if there was a working iso of Mailman that I could get on my server some how and then make changes needed for my list.

I tried to use the Ubuntu install guide for Mailman

I have been working on getting Mailman to work on Ubuntu 14.04 the last 3 days. A tough one indeed. I got it all in and can even telnet to it. But when I try and type in [http://www.biblematters.net/cgi-bin/mailman/listinfo](http://www.biblematters.net/cgi-bin/mailman/listinfo)

I get this error message - [h=1]Forbidden[/h]You don't have permission to access /cgi-bin/mailman/listinfo on this server.
[HR][/HR]Apache/2.4.7 (Ubuntu) Server at [www.biblematters.net](www.biblematters.net) Port 80

Now What I am wondering. Is this. When I installed Apache2 and set up Virtual Hosting. I set up these directories. /var/www/www.mikealrhughes.com/public-html for my [www.mikealrhughes.com](www.mikealrhughes.com) website and it is working. 
I also setup /var/www/www.biblematters.net/public-html. This is the Mail Server Doman. Should I get rid of the Biblematters directories? I couldn't get the bloody Italic to shut off so I bolded it to set it apart from the above error message. I can't find the cgi-bin/mailman directories on my server either.

---

### Post by nerdtron on 2015-04-21
premission denied can mean that there are now read permissions on that folder. have you tried changing permission something like:

chmod -R a+r /var/ww/path/to/folder/with/error

---

### Post by Mike_Hughes on 2015-04-21
That was my thinking I went in to try and find the cgi-bin directory and it says it isn't there.

---

### Post by electronico_nc on 2015-04-21
Do you have a directive like this in your apache conf file:```
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride AuthConfig
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>
```

---

### Post by Mike_Hughes on 2015-04-21
Where do I put this - You must configure your web server to enable CGI script permission in the $prefix/cgi-bin to run CGI scripts. The line you should add might look something like the following, with the real absolute directory substituted for $prefix, of course:    Exec        /mailman/*      $prefix/cgi-bin/*

or:
    ScriptAlias /mailman/       $prefix/cgi-bin/

Yes it is in my mods-enabled. Well I got with the folks on mailman-users and it turns out the Mailman install on Ubuntu.help is way behind the times. One of the people there is helping me fix the issues. 
Seems now I have an issue with Postfix again the install guide here needs updated to what mailman wants now. From what I understand it is at least 3 versions behind.

---

### Post by electronico_nc on 2015-04-21
> **Mike_Hughes said:**
> I tried to use the Ubuntu install guide for MailmanWhere is this guide online ?

---

### Post by Mike_Hughes on 2015-04-21
it is under help.ubuntu

I am using the help.ubuntu.org's Mailman install "recipe". I was running through Postfix configuration again. I get to - Associate the domain lists.example.com to the mailman transport with the transport map. Edit the file /etc/postfix/transport:lists.example.com      mailman:Now have Postfix build the transport map by entering the following from a terminal prompt:sudo postmap -v /etc/postfix/transport

I looked in /etc/postfix there is not a file called transport or a directory called transport so I could not get lists.biblematters.net mailman: to run.


So I am thinking that is where my issue is that lists.biblematters.net is not associating with mailman.

Anyone have any ideas on this one? My server configuration is to run Virtual Hosting for Web Hosting on this machine and a mail server for my Biblematters.net mailing list. The [www.mikealrhughes.com](www.mikealrhughes.com) site is working ok. Even though the next step once I get the mail server to work is install Word Press. All help greatly appreciated.




Thanks to Mark Sapiro on the Mailman-User Forum got the Mail Server up and going. If you are going to install Mailman on Ubuntu got to list.org and get their Installation guide.

---

