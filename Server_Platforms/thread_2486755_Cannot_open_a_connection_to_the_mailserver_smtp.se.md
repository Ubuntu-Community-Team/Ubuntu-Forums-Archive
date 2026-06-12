---
title: "Cannot open a connection to the mailserver smtp.sendgrid.net:587 -- Operation now in"
date: 2023-05-09
forum: Server Platforms
---

### Post by haivcci on 2023-05-09
Hi all expert Bros,

I have two VPS(s), one is running Debian 11 with Hesiacp (Nginx) and another is Ubuntu 22.04 is running OpenLiteSpeed (CyberPanel).

I installed Monit for both to monitor my VPS(s). With the same configuration but it's _only working on Debian 11_ (I received alert emails). 

It didn't work on Ubuntu 22.04. The errors from the Monit log below:

> 
[2023-05-09T14:47:45+0000] error    : Mail: Delivery failed -- no mail server is available
[2023-05-09T14:47:45+0000] info     : Adding event to the queue file /var/lib/monit/events/1683643665_55e9fe7cd6f0 for later delivery
[2023-05-09T14:48:45+0000] error    : Cannot connect to [smtp.sendgrid.net]:587 -- Connection timed out
[2023-05-09T14:48:45+0000] error    : Cannot open a connection to the mailserver smtp.sendgrid.net:587 -- Operation now in progress
[2023-05-09T14:48:45+0000] error    : Mail: Delivery failed -- no mail server is available
[2023-05-09T14:48:45+0000] error    : Alert handler failed, retry scheduled for next cycle
[2023-05-09T14:51:45+0000] error    : Cannot connect to [smtp.sendgrid.net]:587 -- Connection timed out
[2023-05-09T14:51:45+0000] error    : Cannot open a connection to the mailserver smtp.sendgrid.net:587 -- Operation now in progress
[2023-05-09T14:51:45+0000] error    : Mail: Delivery failed -- no mail server is available
[2023-05-09T14:51:45+0000] error    : Alert handler failed, retry scheduled for next cycle



[COLOR=#0000ff]**The mail settings for Monit that working well on Debian 11 are below:**[/COLOR]

> 
#Mail settings


 set mail-format {
     from: [EMAIL="info@fiverservices.com"]info@[/EMAIL]example.com
  subject: MAXKVM Server - monit alert --  $EVENT $SERVICE
  message: $EVENT Service $SERVICE
                Date:        $DATE
                Action:      $ACTION
                Host:        $HOST
                Description: $DESCRIPTION


           Your faithful employee,
           Monit }
  set mailserver smtp.sendgrid.net port 587
     username "apikey" password "SG.uUX2-I1jQdO1p78bic2Jcw.v6zq2ztsrasfddfsdxjabwc-HU0_VLO5aeTsFz8JliXXXX"
     using TLS with timeout 30 seconds
     set alert [EMAIL="exampleemail@gmail.com"]exampleemail@gmail.com[/EMAIL] #email address which will receive monit alerts


Could you please give me a hint?

I don't know why it *Cannot connect to [smtp.sendgrid.net]:587 -- Connection timed out*

port is not block, I even disabled CSF firewall but still the problem.

Thanks

---

