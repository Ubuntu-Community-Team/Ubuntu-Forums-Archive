---
title: "E-Mail won't send to  other (internal) server, Postfix and /etc/hosts"
date: 2012-08-23
forum: Server Platforms
---

### Post by the1joker on 2012-08-23
Hey Every1!

I'm running two Ubuntu 12.04 servers here and they both are installed fine and dandy, running all services. 

They both are connected to the same router with two different outside IP's (through 1-on-1 NAT).

They have similer  inside ip's (server1: 10.1.10.101, server2: 10.1.10.102);

I have my hosts setup correctly so that the servers should go to their other respective internal ip's and that works when i need to call to the other servers in PHP, but not when i try to send mail from one e-mail address on server1 to another e-mail address on server2.

In my mail.log:
Aug 23 11:46:34 server2 postfix/smtp[8030]: connect to mail.example.nl[XXX.XXX.XXX.XXX]:25: Connection refused 

And where the XXX.XXX.XXX.XXX is the correct Outside IP of my server1, it is the same in reverse when i send the other way.
So the problem is, is that postfix doesn't listen to my /etc/hosts

I've been reading, and it seems i might need to do something with either "mydestination" or with alias' but i'm not sure what....

I found one thing that said to go something in /etc/postfix/virtual  but that dir doesn't exist on my installation of either server.

Any help in any direction would be greatly appreciated.

Tobias

---

### Post by SeijiSensei on 2012-08-23
Mail routing relies on MX records in most instances.  That's why Postfix is ignoring entries in /etc/hosts.

Do you have an internal DNS server for your domain on either of these machines?  If so, adjust the MX and A records to use the machines' internal addresses.  If not, you might consider setting one up.

I don't use Postfix so I can't help with that.  In sendmail, you can override MX records with an entry in /etc/mail/[mailertable]("http://www.sendmail.com/sm/open_source/docs/m4/mailertables.html").  For instance, a mailertable entry like

```

server1.example.com     relay:[10.1.10.101]
server2.example.com     relay:[10.1.10.102]

```

would direct mail for [email]someone@server1.example.com[/email] to 10.1.10.101.

---

### Post by the1joker on 2012-08-23
The actual DNS runs externally, but you did get in the direction of postmap, which i have no clue about yet, but i'll prolly find more.

 if anyone has an example of how i would add a specific line to postmap that would be great cause what ive tried up to now comes back with 

postmap: fatal: open /etc/postfix/transport: No such file or directory

which according to postfix should be the location for this...


i do see a "mysql-virtual_transports.cf" which makes me think i can create a transport file, but then in what file would i reference my new transport file? or am i thinking wrong here?

---

