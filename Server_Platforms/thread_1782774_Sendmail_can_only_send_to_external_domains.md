---
title: "Sendmail can only send to external domains"
date: 2011-06-15
forum: Server Platforms
---

### Post by CA1900 on 2011-06-15
I'm a fairly new administrator of an Ubuntu 10.04 server.  Everything's working very well except for **sendmail**. This is probably something simple, but as a guy who's fairly new to both linux and server administration, I'm stumped!

When I use **sendmail** (or, most commonly, a PHP or Perl script uses it) to send to any other domain except my own, it works great.

When I use it to send to my *own* domain, however, it's trying to deliver it to localhost. Problem is, all our mail is handled by an Exchange server on a different machine, so I really don't want 

If I run **sendmail** manually for a test message to myself, here's how it comes up after the message is closed out:
```
echo "Subject: test" | /usr/sbin/sendmail -v *me@domain.com*
354 Enter mail, end with "." on a line by itself
>>> .
050 <*me@domain.com*>... Connecting to local...
050 <*me@domain.com*>... Sent
250 2.0.0 p5F6YwDW015675 Message accepted for delivery

...
```And so on.  The message then gets dropped into my box at /var/mail/xxxx, but that's really not helpful to me -- I need to to connect to that other machine to deliver the mail there. This machine isn't used as a mail server at all.

Also, if it's trying to send to a username that doesn't have an account on this server (we have many), it just fails entirely with "user unknown" (that makes sense, as there are only a couple of user accounts on the web server).

Any ideas on how to get sendmail to connect to our mail server instead of "local"?

Thanks!

---

### Post by SeijiSensei on 2011-06-15
First, if you run the command "host -t mx domain.name" on the Linux box, what does it return as the primary MX server?  It should point to the Exchange server.  By default, sendmail will rely on the MX records for the domain to determine where to send a message.

However, you should also look at the file /etc/mail/local-host-names and see whether your domain is listed there.  Sendmail uses this file to determine which addresses require local delivery.  Even if the MX records correctly point to the Exchange server, sendmail will deliver locally for domains listed in the local-host-names file.  It's possible this file is called something else.  To make sure you have the correct file, run this command

```
grep '^Fw' /etc/mail/sendmail.cf
```

and see what file it lists there.  The file named in the "Fw" directive determines local delivery.  If your domain appears in that file, remove it.

If you don't control the MX records, or can't override them for some reason, you'll need to use a "mailertable."  First, use a text editor to create the file /etc/mail/mailertable like this:

```
domain.name      relay:[ip.of.exch.server]
```

Next run the commands

```
cd /etc/mail
makemap -v hash mailertable < mailertable
```

This will use the file you created to build a database file called mailertable.db.  Now mail for domain.name should be forwarded to the Exchange server regardless of what the DNS says.

Most of these changes won't require restarting sendmail, but it doesn't hurt to do so anyway.

---

### Post by CA1900 on 2011-06-15
Thank you!

The hostname -t mx *domain.com* returned this:

*domain.com* mail is handled by 10 *domain.com*.pri-MX.smtproutes.com.
*domain.com* mail is handled by 20 *domain.com*.bak-MX.smtproutes.com.

Not sure if that's a good thing or a bad thing.  I've been tasked with administering the server, but the domain name registration was handled by someone else through GoDaddy, so I don't have direct access to those settings.

So I went ahead and set up the **localhostnames** file with the relay entry. At first it didn't work, until I realized I needed the square brackets around the IP. ;)  It's now sending through the Exchange server as expected.

One thing, though: it seems to take quite a while to send out (about 45 seconds), which is kind of unusual.  When I test it from the command line, it gets this far:

```
...
354 Enter mail, end with "." on a line by itself
>>> .

```After that, it appears to lock up, although it does show up in the proper mailbox (via the Exchange server) about 40-50 seconds later.  And the command is basically locked up at that point; I have to close the SSH window and open a new one to get back in.  Not ideal, but at least the messages are getting out!

Thanks again for the help.

---

### Post by SeijiSensei on 2011-06-15
> **CA1900 said:**
> *domain.com* mail is handled by 10 *domain.com*.pri-MX.smtproutes.com.
*domain.com* mail is handled by 20 *domain.com*.bak-MX.smtproutes.com.

Not sure if that's a good thing or a bad thing.  I've been tasked with administering the server, but the domain name registration was handled by someone else through GoDaddy, so I don't have direct access to those settings.

Apparently your organization only has a single set of domain name records visible from both inside and outside your network.  Many organizations maintain a separate set of internal nameservers that provide name resolution for the local network.  If you had an internal nameserver, you could make the MX records on it point to the Exchange server.  Senders outside the organization would use the mx.smtproutes.com servers to reach your domain.

> One thing, though: it seems to take quite a while to send out (about 45 seconds), which is kind of unusual.  When I test it from the command line, it gets this far:

This is usually a DNS issue.  sendmail, like most mail exchangers, checks the forward and reverse name resolution for the machine on the other end of the connection.  Since you don't have an internal DNS, it waits for the name service queries to time out before completing the message transfer.

The simplest solution to this is to add entries in the "[hosts]("http://en.wikipedia.org/wiki/Hosts_(file)")" files on both machines that include the other's name and IP address.  You can learn exactly what names the mail servers expect using the following steps on the Linux box.  First, determine the name of the Exchange server by running "telnet ip.of.exch.server 25" and seeing what the banner reports.  Then repeat this procedure but replace the Exchange server's IP with the IP of the network-connected interface on the Linux box.  Finally add the two machines' IP addresses and hostnames to the hosts file on each server.  On the Linux box, edit /etc/hosts; in Windows, it's usually C:\Windows\system32\drivers\etc\hosts.

---

### Post by CA1900 on 2011-06-15
Excellent, I'll give that a try tonight.

I did tons of searching, but couldn't find anything for this exact set of circumstances. This whole thing has been a learning experience, but it's been neat seeing how powerful a server this software can create. Thanks for your help tying up this loose end!

---

### Post by dogdaynoon on 2012-12-19
I know this is old but it is the only place over the last month that i have been able to find anything remotely close to my problem... Please help. I am not exactly sure how sendmail flows but here is my dilema. I have the same scenario as Cal900. I have an ubuntu box(not part of the domain) and an exchange box. Ubuntu box sendmail sends fine externally and not internal. When i follow directions here and set the mailertable.db, sendmail sends fine internally but not externally!!! argh... any ideas on what's going on with this?

Thanks,
dogdaynoon

---

### Post by CA1900 on 2012-12-19
Hey dogdaynoon --

The last piece of the puzzle I had to fix was to get the Exchange server to relay for an outside server. I don't manage the Exchange server so I don't know exactly what they did, but I know our Exchange admin had to explicitly allow the Ubuntu server's IP address before it would work.

Could that be it?

---

### Post by SeijiSensei on 2012-12-21
> **dogdaynoon said:**
> I know this is old but it is the only place over the last month that i have been able to find anything remotely close to my problem... Please help. I am not exactly sure how sendmail flows but here is my dilema. I have the same scenario as Cal900. I have an ubuntu box(not part of the domain) and an exchange box. Ubuntu box sendmail sends fine externally and not internal. When i follow directions here and set the mailertable.db, sendmail sends fine internally but not externally!!! argh... any ideas on what's going on with this?

Thanks,
dogdaynoon

Let's start at the beginning.  You want sendmail to forward mail for your domain to Exchange and send the rest out the door using MX records.

/etc/mail/mailertable should have just these lines:

```

example.com      relay:[ip.of.exch.server]
.example.com     relay:[ip.of.exch.server]

```

The second line is only necessary if mail is sent to subdomains or specific hostnames like @www.example.com. As the OP mentioned, you need to include the square brackets around the IP address.  If you have DNS running, you can use "relay:hostname" instead.

You ran the "makemap" command to create the database, too, right?

You might be missing the mailertable code from sendmail.cf.  Last I looked the default sendmail.cf with Ubuntu is woefully lacking compared to the RedHat/CentOS configuration.  I posted some instructions on adding mailertable support to Ubuntu [here](http://ubuntuforums.org/showpost.php?p=12404961&postcount=2).

---

### Post by dogdaynoon on 2013-01-25
@SeijiSensei :
Thank you SeijiSenis for your responses. I was able to get sendmail to route local mail to the exchange server.
my steps were as follows. They are very simalar to what you have described above:

create text file in /etc/mail called mailertable
add line -  ```
mydomain.com    relay:[ip.address.of.exchange]
```
 - note there's no space after "relay:"

from inside /etc/mail run  ```
makemap -v hash mailertable < mailertable
```
then in sendmail.mc add the following after the line that reads FEATURE(`access_db',,....)
```
FEATURE(`mailertable', `hash -o /etc/mail/mailertable.db')dnl
```
save and exit
then reconfig sendmail with ```
/usr/sbin/senmailconfig
```

finally restart sendmail.
did i miss anything? 


dogdaynoon

---

### Post by SeijiSensei on 2013-01-25
Looks good to me.  If it works, then you know you did the right thing!

---

