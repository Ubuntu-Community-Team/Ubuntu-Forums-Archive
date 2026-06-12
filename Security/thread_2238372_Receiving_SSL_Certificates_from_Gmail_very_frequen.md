---
title: "Receiving SSL Certificates from Gmail very frequently"
date: 2014-08-07
forum: Security
---

### Post by linuxyogi on 2014-08-07
Hi,

I have configured my Gmail account under Claws Mail. 

Problem is today I am receiving these certificates very frequently.

I even received 2 of them in just 10 minutes.

Is this normal ? If not what should I do ?  

[IMG]http://ibin.co/1W1ZPrXcREFY[/IMG]

---

### Post by TheFu on 2014-08-07
google has thousands of servers around the world. It is likely that you are connecting to different ones based on their DNS round-robin, so the cert changes.  If you are security conscious, you'll need to validate the cert every time there is a change.

Of course, there could be someone in the middle screwing around - I'd worry more if I were in a country where the government is known for blocking internet or tracking their people.   Anywhere in the middle east, *stan, Thailand, Singapore, certain central American, Caribbean and south American countries.... and the if the NSA has fingers there, of course. :)

---

### Post by linuxyogi on 2014-08-08
> **TheFu said:**
> google has thousands of servers around the world. It is likely that you are connecting to different ones based on their DNS round-robin, so the cert changes.  If you are security conscious, you'll need to validate the cert every time there is a change.

Of course, there could be someone in the middle screwing around - I'd worry more if I were in a country where the government is known for blocking internet or tracking their people.   Anywhere in the middle east, *stan, Thailand, Singapore, certain central American, Caribbean and south American countries.... and the if the NSA has fingers there, of course. :)

AFAIK our government only blocks certain porn sites, thats it. They haven't started tracking yet.

When I see the dialog box all I read is 

> Certificate from pop.gmail.com has changed. 

Do you want to accept it ? 

Signature Status : Correct


Now, if this is really from Google or not I don't have the expertise to find that out.

So, I want to know since I am getting these 15-20 times a day, is there a way to make Claws Mails auto accept these certificates if the basic criteria matches. That is 

"Signature Status : Correct" ?

---

### Post by bashiergui on 2014-08-10
Not sure, but according to [this]("http://www.axllent.org/docs/view/gmail-pop3-with-fetchmail/") you should have ```
ca-certificates
``` installed. Perhaps it needs installing/updating? Not sure how often Ubuntu releases updates for it...

---

### Post by andrew.46 on 2014-10-14
As far as I was aware Gmail uses Equifax Secure CA and Thawte Premium Server CA and I have used these 2 since the infamous [expired cert saga of 2008]("https://www.sslshopper.com/article-ssl-certificate-renewal-even-google-forgets.html")...

---

### Post by fugu2 on 2014-10-17
from [https://ssl-tools.net/webservers/google.com](https://ssl-tools.net/webservers/google.com) ```
 Servers
Hostname / IP address 	Certificates 	Protocol 	
google.com 173.194.65.139 	*.google.com 	 PFS    supported DANE     missing Heartbleed     not vulnerable Poodle     vulnerable  	2014-10-17
google.com 173.194.65.100 	*.google.com 	 PFS    supported DANE     missing Heartbleed     not vulnerable Poodle     vulnerable  	2014-10-17
google.com 173.194.65.101 	*.google.com 	 PFS    supported DANE     missing Heartbleed     not vulnerable Poodle     vulnerable  	2014-10-17
google.com 173.194.65.113 	*.google.com 	 PFS    supported DANE     missing Heartbleed     not vulnerable Poodle     vulnerable  	2014-10-17
google.com 173.194.65.102 	*.google.com 	 PFS    supported DANE     missing Heartbleed     not vulnerable Poodle     vulnerable  	2014-10-17
google.com 173.194.65.138 	*.google.com 	 PFS    supported DANE     missing Heartbleed     not vulnerable Poodle     vulnerable  	2014-10-17
google.com 2a00:1450:4013:c00::8b	*.google.com 	PFS    supported DANE     missing Heartbleed     not vulnerable Poodle     vulnerable  	2014-10-17
Certificates
First seen at: 2014-10-03
*.google.com
Certificate chain
  *.google.com
    2014-12-23 remaining
    256 bit
    sha1WithRSAEncryption
      Google Internet Authority G2
        2016-12-31 remaining
        2048 bit
        sha1WithRSAEncryption
          GeoTrust Global CA
            2018-08-21 remaining
            2048 bit
            sha1WithRSAEncryption
              Equifax Secure Certificate Authority (Certificate is self-signed.)
                2018-08-22 remaining
                1024 bit
                sha1WithRSAEncryption
Subject
Country (C)      US
State (ST)       California
Locality (L)     Mountain View
Organization (O) Google Inc
Common Name (CN) *.google.com
Alternative Names
        *.google.com
        *.android.com
        *.appengine.google.com
        *.cloud.google.com
        *.google-analytics.com
        *.google.ca
        *.google.cl
        *.google.co.in
        *.google.co.jp
        *.google.co.uk
        *.google.com.ar
        *.google.com.au
        *.google.com.br
        *.google.com.co
        *.google.com.mx
        *.google.com.tr
        *.google.com.vn
        *.google.de
        *.google.es
        *.google.fr
        *.google.hu
        *.google.it
        *.google.nl
        *.google.pl
        *.google.pt
        *.googleadapis.com
        *.googleapis.cn
        *.googlecommerce.com
        *.googlevideo.com
        *.gstatic.cn
        *.gstatic.com
        *.gvt1.com
        *.gvt2.com
        *.urchin.com
        *.url.google.com
        *.youtube-nocookie.com
        *.youtube.com
        *.youtubeeducation.com
        *.ytimg.com
        android.com
        g.co
        goo.gl
        google-analytics.com
        google.com
        googlecommerce.com
        urchin.com
        youtu.be
        youtube.com
        youtubeeducation.com

```

---

### Post by linuxyogi on 2014-10-21
I thought it was all over but the trend is back.

[ATTACH=CONFIG]257433[/ATTACH]

Click to enlarge.

---

### Post by fugu2 on 2014-10-22
i'd say send [email]security@gmail.com[/email] an email, but thier response will probably be a joke. You might do better to find a more reliable and secure email service.

---

### Post by linuxyogi on 2014-10-22
> **fugu2 said:**
> You might do better to find a more reliable and secure email service.

I am looking for an alternative. Suggest one.

---

### Post by CharlesA on 2014-10-22
> **linuxyogi said:**
> I thought it was all over but the trend is back.

[ATTACH=CONFIG]257433[/ATTACH]

Click to enlarge.

Do you get the same problem if you use imap? I've been using pop for a while and I haven't seen any of those messages on Thunderbird. Have you tried a different mail program to see if it was limited to Claws?

---

### Post by linuxyogi on 2014-10-22
> **CharlesA said:**
> Do you get the same problem if you use imap? I've been using pop for a while and I haven't seen any of those messages on Thunderbird. Have you tried a different mail program to see if it was limited to Claws?

I just configured IMAP for my existing account. I haven't received those certificates yet. Lets hope this works.

There's no point is testing with Thunderbird coz even if the Thunderbird/Gmail combination solves this issue I 

don't have enough Ram to multitask with Firefox and Thunderbird.

---

### Post by CharlesA on 2014-10-22
Hope it resolves your issue.

FWIW, I think the issue is Claws, not google. See this (old) bug report:
[http://www.thewildbeast.co.uk/claws-mail/bugzilla/show_bug.cgi?id=2580](http://www.thewildbeast.co.uk/claws-mail/bugzilla/show_bug.cgi?id=2580)
[http://lists.claws-mail.org/pipermail/users/2013-September/007336.html](http://lists.claws-mail.org/pipermail/users/2013-September/007336.html)

Work around:
[http://claws-mail.org/pipermail/users/2012-January/001099.html](http://claws-mail.org/pipermail/users/2012-January/001099.html)


There was also more bug reports about this, but it seems to be limited to older versions of Claws. Does 14.10 have a newer version available?

---

### Post by linuxyogi on 2014-10-22
Bookmarked that workaround. In case I don't like IMAP for some reason and decide 

to use POP3 again I will apply that fix.

Utopic has 3.10.1-2ubuntu2

Latest release : 3.11.0 (20th Oct 2014)

---

