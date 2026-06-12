---
title: "Edgy, Postfix and Mysql problem solved."
date: 2007-01-02
forum: Server Platforms
---

### Post by gtaskeraus on 2007-01-02
My upgrade to Edgy broke and caused me a huge number of problems.  The most recent problem has been my postfix installation not working.

Since I upgraded to Edgy my outgoing on postfix has not been working and since flurdy looks like a document under construction it fell to my lot to find a solution

My installation involves virtual users set up on a mysql database.   Some googling suggested that it must have had something to do with the location of smtpd.conf. ](*,) 

smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2

This setting had worked previously so the question was to find out where postfix was looking for it's smtpd.conf file.

I finally got down to the stage when I had to use strace to locate the source of the problem.  The question

Sympton: Able to receive mail but password fails when attempting to send out mail.  Log messages as follows.

postfix/smtpd[2088]: sql_select option missing
postfix/smtpd[2088]: auxpropfunc error no mechanism available 
taskerclan postfix/smtpd[2088]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql 

strace is a wonderful thing.

It showed that the value set in smtpd_sasl_path was being prepended by "/etc/postfix/sasl/"
If the value was taken out of main.cnf postconf showed a default value of "smtpd".

The value set in
#smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
causes the following path to be looked for in post fix

/etc/postfix/sasl//etc/postfix/sasl:/usr/lib/sasl2

It seems to me that by default postfix now prepends "/etc/postfix/sasl/" and appends ".conf" to whatever goes into "smtpd_sasl_path".

The upshot of this all is that when the
smtpd_sasl_path
is completely commented out of /etc/postfix/main.cf that the problem is resolved.

strace forever!!! Yay!

What is used to really to change the path that postfix looks for "smtpd.conf" I am not certain.  Right now with that smtpd_sasl_path value removed from main.cf the default file is "/etc/postfix/sasl/smtpd.conf"

On a sadder note it is only because I have had some programming experience that I was eventually able to figure out the cause of the problem.

A bit of a pity for mere mortals.  I'm not certain that the documentation has made this situation obvious to those trying to use the server.

---

### Post by showe1966 on 2007-01-03
Hi,

Seeing as you seem to know what you are talking about, can you answer a few questions for me ??

I am trying to set up my computer as a mail server and a web server.
I only have one computer hence 1 IP address, and I'd like to keep it that way as I believe in simplicity.
What I'd like to know is can my mail server and my web server have the same IP address?
That is to say my zone file will look something like below. Maybe I need to add an A record to say that mail.sdi-fabsurplus.com and server1.sdi-fabsurplus.com are the same thing.
i.e. mail A 88.198.19.46
Also, any idea what i can use for my 2nd name server ???
my isp seems to have some to use, but they don't seem to work right.

*****************************************************************
@ IN SOA server1.sdi-fabsurplus.com. root.localhost. (
2007010205 ; serial, todays date + todays serial #
28800 ; refresh, seconds
7200 ; retry, seconds
604800 ; expire, seconds
86400 ) ; minimum, seconds
;
NS server1.sdi-fabsurplus.com. ; Inet Address of name server 1
NS ns0.sdi-fabsurplus.com. ; ?? don't know what to put here as i only have one ip address
;

MX 10 server1.sdi-fabsurplus.com.;
MX 20 mail.fabsurplus.com.;
;
sdi-fabsurplus.com. A 88.198.19.46
www A 88.198.19.46

server1 A 88.198.19.46
ns0 A 88.198.19.46

ftp CNAME www.
****************************************************************************

---

### Post by gtaskeraus on 2007-01-03
Short answer to you question.

Yes you can have an email server and web server running off the same ip address.  I even have mine running off the same box in addition to an ftp server.

The big problem that you may have is that many mail servers these days reject email coming from servers with a dynamic IP address as apparently most spam comes from such servers.

The workaround to this is to use something like dnsexit.com or dyndns.org which provide a mail relay giving one a static ip address from which the mail appears to come making it acceptable to most servers.

In theory you can have as many names as you like pointing to the same IP address.  I have three that I set up pointing to the same IP address and it looks as if I have a fourth that I did not particularly choose to have but no harm done.

So far as primary and secondary name servers are concerned that is outside my domain.  I use dnsexit for both.

You could also try dyndns.  They have a wildcard on their server names which means that [www.myspot](www.myspot), mail.myspot, and ftp.myspot can be all made to point to the same computer.

Cheers.

---

### Post by Virtudude on 2007-03-11
> **gtaskeraus said:**
> My upgrade to Edgy broke and caused me a huge number of problems.  The most recent problem has been my postfix installation not working.

Since I upgraded to Edgy my outgoing on postfix has not been working and since flurdy looks like a document under construction it fell to my lot to find a solution

My installation involves virtual users set up on a mysql database.   Some googling suggested that it must have had something to do with the location of smtpd.conf. ](*,) 

smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2

This setting had worked previously so the question was to find out where postfix was looking for it's smtpd.conf file.

I finally got down to the stage when I had to use strace to locate the source of the problem.  The question

Sympton: Able to receive mail but password fails when attempting to send out mail.  Log messages as follows.

postfix/smtpd[2088]: sql_select option missing
postfix/smtpd[2088]: auxpropfunc error no mechanism available 
taskerclan postfix/smtpd[2088]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql 

strace is a wonderful thing.

It showed that the value set in smtpd_sasl_path was being prepended by "/etc/postfix/sasl/"
If the value was taken out of main.cnf postconf showed a default value of "smtpd".

The value set in
#smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
causes the following path to be looked for in post fix

/etc/postfix/sasl//etc/postfix/sasl:/usr/lib/sasl2

It seems to me that by default postfix now prepends "/etc/postfix/sasl/" and appends ".conf" to whatever goes into "smtpd_sasl_path".

The upshot of this all is that when the
smtpd_sasl_path
is completely commented out of /etc/postfix/main.cf that the problem is resolved.

strace forever!!! Yay!

What is used to really to change the path that postfix looks for "smtpd.conf" I am not certain.  Right now with that smtpd_sasl_path value removed from main.cf the default file is "/etc/postfix/sasl/smtpd.conf"

On a sadder note it is only because I have had some programming experience that I was eventually able to figure out the cause of the problem.

A bit of a pity for mere mortals.  I'm not certain that the documentation has made this situation obvious to those trying to use the server.

Thank you! I had this exact same problem on upgrade.

---

### Post by carlnelson on 2007-03-14
Thank you - being a mere mortal I would not have found the solution.
BTW - the tutorial/recipe was most useful.

---

