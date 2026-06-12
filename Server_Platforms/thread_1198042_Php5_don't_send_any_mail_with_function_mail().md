---
title: "Php5 don't send any mail with function mail()"
date: 2009-06-26
forum: Server Platforms
---

### Post by shakaran on 2009-06-26
Hi, I use a php script with mail function on my localhost.

The script is something like:

```
...
if(mail(...,...)) echo "Mail sent";
else echo "Mail NOT sent";
...
```

The script display "Mail sent", but on my gmail account I don't recieve any mail.

I tried this:

Install sendmail:

```
sudo apt-get install sendmail

```

Check if sendmail works:

```
$ ps -aux | grep sendmail
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
root      2810  0.0  0.0   9316  2040 ?        Ss   04:49   0:00 sendmail: MTA: accepting connections          
shakaran  3745  0.0  0.0   3168   812 pts/1    R+   05:03   0:00 grep sendmail
```

Edit my php.ini on /etc/php5/apache2/ to uncomment sendmail:

```
    where
    ;sendmail_path =

    put
    sendmail_path =  /usr/sbin/sendmail -t -i 
```

Restart Apache:
```
sudo apache2ctl restart
```

I don't see any mail yet. What am I doing wrong?

---

### Post by HermanAB on 2009-06-27
Howdy,

Use nullmailer.  It only has two lines of confguration: Who are you and where to send the mail to.

Google will find it for you.

---

### Post by Kareeser on 2009-06-27
Multiple possibilities:
1. Your ISP may block SMTP port 25 by default, as hijacked machines will send spam from compromised systems on that port by default.
2. Your hostname is incorrect (a local name instead of a domain name, maybe), and the remote server is rejecting it on that premise.

---

### Post by shakaran on 2009-06-27
@HermanAB:
I install nullmail:

```
sudo apt-get install nullmailer
```

In apt/dpkg configuration I put:
```

mail.server.com smtp --port=25
```

mail.server.com is correct? or is my localhost or which?

With nullmail, nothing, no mails sent.

The tutorial that I follow: [http://undesigned.org.za/2007/11/22/nullmailer-a-developers-best-friend](http://undesigned.org.za/2007/11/22/nullmailer-a-developers-best-friend)

@Kareeser

I open the 25 port for SMTP on my router (I don't know if it is needed).

But nmap don't say that is open or in use:
```
$ nmap -T4 192.168.1.33

Starting Nmap 4.76 ( http://nmap.org ) at 2009-06-27 17:13 CEST
Interesting ports on 192.168.1.33:
Not shown: 998 closed ports
PORT   STATE SERVICE
53/tcp open  domain
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 0.18 seconds
```

I read that it is possible that I need put this on the sources (but I use a ubuntu package)

```
echo '#define HAVE_SENDMAIL 1' >> main/php_config.h
```

> 1. Your ISP may block SMTP port 25 by default, as hijacked machines will send spam from compromised systems on that port by default.


How to check it? Nmap don't say anything.

> 2. Your hostname is incorrect (a local name instead of a domain name, maybe), and the remote server is rejecting it on that premise.

My machine name is otorion,you mean that? How to check that the remote server is rejecting it?

---

