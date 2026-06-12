---
title: "[SOLVED] Not Sending mail to our internal mail server"
date: 2008-07-30
forum: Server Platforms
---

### Post by rahmath on 2008-07-30
Dear Techies,

I need to setup in my Local update server to send mail to my mail account regarding the status of updates, disk usage, etc. I had succeeded in this preparation, but totally failed to send this mail to my local email account which is there with our internal mail server(Exchange 03)

Let me give you more idea;
internal domain: local.com
so, my local mail id; [email]rahmath@local.com[/email]
my ubuntu update server: system3.local.com
version: Ubuntu hardy Server Installation.

In system3.local.com;

i ran $ sudo dpkg-reconfigure exim4-config

then selected in first screen i selected;

1. option1: internet site; mail is sent.... 

2. then in next window; 
System mail name: system3.local.com

3. then;
IP address to listen on for incoming....; i specified my local ip of ubuntu update server (ip of system3.local.com)

4. then;
Other destination foe which mail is accepted; i left it blank, bcoz i feel like we dont want to specify anything here for our current requirement.

5. then;
Domains to relay mail for: local.com

6. then;
Machines to relay mail for; local-ip-of-our-exchange/subnetmask

7. then;
Keep number of DNS-quereies minimal: NO

8. then;
Delivery method for local mail; mbox format in /var/mail/

9. then;
Split conf files..; Yes

Thats my configuration...


In this setting i cant send mail to [email]rahmath@local.com[/email] (exchange 03 - mail server) to recieve mails on my lpatop(ubuntu).

in this it is not possible to send mail to my gmail account too. But if i change the value of "step 2" to local.com (which is a registered domain) i can send to gmail. but i dont want to send it to gmail, rather i want to get it to my company's email account.


Error message in my update server's exim log file is;

2008-07-30 12:02:35 1KO7Zr-0002zq-El <= [email]kmr@system3.local.com[/email] U=kmr P=local S=412
2008-07-30 12:02:35 1KO7Zr-0002zq-El ** [email]rahmath@local.com[/email] R=dnslookup_relay_to_domains T=remote_smtp: SMTP error from remote mail server after RCPT TO:<rahmath@local.com>: host local.com [192.x.x.x]: 550 5.7.1 Unable to relay for [email]rahmath@local.com[/email]
2008-07-30 12:02:35 1KO7Zr-0002zt-Ge <= <> R=1KO7Zr-0002zq-El U=Debian-exim P=local S=1425
2008-07-30 12:02:35 1KO7Zr-0002zq-El Completed
2008-07-30 12:02:35 1KO7Zr-0002zt-Ge => kmr <kmr@system3.local.com> R=local_user T=mail_spool
2008-07-30 12:02:35 1KO7Zr-0002zt-Ge Completed



Error message inside the bounce backed e-mail to my local account "kmr" in system3.local.com is;

To: [email]kmr@system3.local.com[/email]
Subject: Mail delivery failed: returning message to sender
Date: Wed, 30 Jul 2008 12:02:35 +0300

This message was created automatically by mail delivery software.

A message that you sent could not be delivered to one or more of its
recipients. This is a permanent error. The following address(es) failed:

  [email]rahmath@local.com[/email]
    SMTP error from remote mail server after RCPT TO:<rahmath@local.com>:
    host local.com [192.x.x.x]: 550 5.7.1 Unable to relay for [email]rahmath@local.com[/email]



NOTE: This exchange 2003 is the same mail server which we are using for Internal/External mail. i just replaced our actual domain name, to local.com bcoz of our company policy)

I hope someone will be here to help me...

Thanks in advance...

Eagerly awaiting for your response...

---

### Post by rahmath on 2008-08-03
i solved the issue...

---

### Post by jonabyte on 2008-08-03
Why not post the answer so we can all benefit from it...

---

### Post by maxidrom11 on 2008-08-03
yes, post the answer we all want to see

---

### Post by rahmath on 2008-08-03
When i didnt see any posting in this thread, i thought no one is interested on this thread. that's why i didnt put it here. 

i have another sad thing to say, i didnt got any single solution for many of the issues which i posted here... so i feel so sad in that case...

Anyway now i understood that people are interested, so coming to the ans... 

hope someone will give me atleast a thanks \\:D/

====== 

Run the command to reconfigure the exim4-config by

$ sudo dpkg-reconfigure exim4-config

Step 1. Then select the third option (here was the main problem which i faced, i chooses the wrong one in my first settings,) which is "mail sent by smarthost; no local mail"

then 
Step 2. system2    --> i just put the hostname (u can use here fqdn also)

Step 3. local ip address of system2 

Step 4. system2 --> hostname of this system (fqdn also possible here)

step 5. local.com --> your domain name

step 6. IP of mail server (in my case, it is the addr of MS Exchange)

step 7. NO

Step 8. YES


Thats all...

Now all my mail generated to my [email]me@local.com[/email] (that is my company id) is delivered successfully and i can access it through my Evolution....


k...

---

