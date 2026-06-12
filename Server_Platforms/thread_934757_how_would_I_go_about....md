---
title: "how would I go about..."
date: 2008-09-30
forum: Server Platforms
---

### Post by shdw.puppet on 2008-09-30
I wish to create a basic home server that will be running 24/7. I want this server to be able to dish out files and act as a storage server via internal network and internet (with a web based interface so no software needed) as well as be expandable to include an apache web server with the works and a mail server/ftp etc. I was just wondering if it was possible to this easily and with the ubuntu desktop edition so that I can use the GUI I have come to love.

If so, how would I go about doing this?

thank you
shdw

---

### Post by devonps on 2008-10-01
Hi,

I see 2 options for you:

1. Install the Ubuntu Server edition v8.04 over your existing desktop solution and add the services you mentioned. You can always add a GUI desktop if you want. 

OR 

2. Install each of the services, one at a time, onto your existing desktop environment. This way you can use your GUI file/application manager to install the services.

I have no experience with the GUI - so I can't help you with the commands.

Hope this helps,

Steve.

---

### Post by lykwydchykyn on 2008-10-01
It's certainly possible; all versions of Ubuntu use the same package repositories, and the difference between any of them is just the default package selection.  Apart from the GUI, the only significant difference  i know of is the kernel.

---

### Post by shdw.puppet on 2008-10-03
Thank you for the responses, but a large part of my question remains unanswered. What I really wanted to know was what packages/services I need to use to set up this home server. I realize that I can set up a web server and found lots of docs for that, but none on how to make a home fileserver simply and easily

---

### Post by noren on 2008-10-04
> **shdw.puppet said:**
> Thank you for the responses, but a large part of my question remains unanswered. What I really wanted to know was what packages/services I need to use to set up this home server. I realize that I can set up a web server and found lots of docs for that, but none on how to make a home fileserver simply and easily


I have the same question.

plus my ISP provider uses DHCP to give IP, so how can i host any webpage with a static IP..

If possible, waiting for an solution.

Rgds

---

### Post by lisati on 2008-10-04
> **noren said:**
> I have the same question.

plus my ISP provider uses DHCP to give IP, so how can i host any webpage with a static IP..

If possible, waiting for an solution.

Rgds

There are a number of services available to help with DNS registration when your ISP uses DHCP. One example is [http://www.no-ip.com/](http://www.no-ip.com/) who include options to automatically update the IP associated with your web address via software you can download (including a Linux-friendly version). They offer a free version of their services.

---

### Post by Noux on 2008-11-27
I used this [HOWTO]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts")  to install 

    *  Web Server: Apache 2.2 with PHP 5.2.4 and Ruby
    * Database Server: MySQL 5.0
    * Mail Server: Postfix
    * DNS Server: BIND9
    * FTP Server: proftpd
    * POP3/IMAP: Courier-POP3/Courier-IMAP.
    * Webalizer for web site statistics

And sofar its been working like a charm (although Im not quite sure on how to get the mail server working so that I can actually use it to sent e-mails, problem with isp blocking port 25 and so-forth..) 

but the install is clean, its just my lack of 1337'nes thats keeping me down :roll:

A good tip for you is to search for howto + the thing you wanna do (+ ubuntu 'whatever realease') 

Actually, Im gonna go do that just now, since I don't have samba atm.. Im gonna try [THIS ONE]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto+sticky") that I found in like 20 seconds ;)

Duno if this helps ya out, but if it did I'm happy, you're happy, everyones happy!  \\:D/

[edit]
[THIS]("http://www.howtoforge.com/ubuntu-home-fileserver-p3") is probably what you are looking for, pretty simple really!

---

### Post by rslrdx on 2008-11-27
> **Noux said:**
> I used this [HOWTO]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts")  to install 

    *  Web Server: Apache 2.2 with PHP 5.2.4 and Ruby
    * Database Server: MySQL 5.0
    * Mail Server: Postfix
    * DNS Server: BIND9
    * FTP Server: proftpd
    * POP3/IMAP: Courier-POP3/Courier-IMAP.
    * Webalizer for web site statistics

And sofar its been working like a charm (although Im not quite sure on how to get the mail server working so that I can actually use it to sent e-mails, problem with isp blocking port 25 and so-forth..) 

but the install is clean, its just my lack of 1337'nes thats keeping me down :roll:

A good tip for you is to search for howto + the thing you wanna do (+ ubuntu 'whatever realease') 

Actually, Im gonna go do that just now, since I don't have samba atm.. Im gonna try [THIS ONE]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto+sticky") that I found in like 20 seconds ;)

Duno if this helps ya out, but if it did I'm happy, you're happy, everyones happy!  \\:D/

[edit]
[THIS]("http://www.howtoforge.com/ubuntu-home-fileserver-p3") is probably what you are looking for, pretty simple really!

Noux, you need to set your server to use a smart host, basically your local email server will login to another email server, with a per user credentials config in order to send messages, one other thing is, if you want to recieve mail on your local server, you need to change your domain dns settings, the MX records of your domain must point to your ip address, but there is a chance you are using a dynamic ip, and that will not work only you use some sort of dynamic dns client, and point your mx records to the dynamic dns address. Also, if the port is really blocked, you need a service like mailhop from dyndns.org. basically you setup your domain mx records to send mail to their servers, which will route email to your local server on a different port number :P 

its tricky...

---

