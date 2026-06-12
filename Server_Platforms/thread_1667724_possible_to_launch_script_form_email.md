---
title: "possible to launch script form email"
date: 2011-01-15
forum: Server Platforms
---

### Post by mfaust731 on 2011-01-15
K, so this is my goal.
I have my server sending me all kinds of stuff from shell scripts.
reboots, access logs, yadaydayada.

I thought it would be swell if I could reply back to the server.
the server gets the mail, verifies that it came from me, and depending on the subject line - launch various scripts.

for example , I send one to it with reboot as the subject. the server would reboot
If I sent it a hyperlink, the server would print the page to pdf and stick it in my /SharedFiles/PDF folder.

I know that dropbox could handle some of this, but ahh this seems cooler.

So anyone know how to do it, lol?

---

### Post by sj1410 on 2011-01-15
yes you can. but you need to know a  little programming. you can write a script which would check mail from a pop3 server, and when it gets the mail can parse it and execute the command.

---

### Post by mfaust731 on 2011-01-15
yeah, one thing ive learned in my Linux en devours - is that anything it "possible", if you are willing to learn how....

Found this just now, gonna try it our later

[http://ubuntuforums.org/archive/index.php/t-1173613.html](http://ubuntuforums.org/archive/index.php/t-1173613.html)

---

### Post by mfaust731 on 2011-01-15
ok, I have made progress!
the above tutorial is great and it works, though it doesnt cover parsing the actual email. It just checks to see if one exists.
I want to go a bit further and specify commands in the message.

so far i have been able to send it a email with download as the subject, then ive added to his script for grep to find a url inside the email and download it with wget.
My problem is that my regular expression is catching 3 url for everyone I include in the message. I need to fine tune the expression to only return the url that starts with a whitespace.
that should get rid of the other duplicates found in the email formatting.
Havent found the right combo yet though, any help?
Ive tried simply adding [[:space:]] infront of http:// but it dont jive.

here is the grep command Im using and Ill post a sample of the file aswell

```
grep -o -e http://[^[:space:]\"]* $HOME/gmail/download/new/* | xargs wget
```

sample email file:
```


Received: by 10.216.0.134 with HTTP; Sat, 15 Jan 2011 10:39:33 -0800 (PST)
From: Matt Faust <matt@mydomain.com>
Date: Sat, 15 Jan 2011 13:39:33 -0500
Message-ID: <AANLkTinD05DAtR-FsPz=JQeZzSk5fZyQWRJJ0uFo62c5@mail.gmail.com>
Subject: download
To: homeserver@mydomain.com
Content-Type: multipart/alternative; boundary=20cf301fbae58550800499e71246

--20cf301fbae58550800499e71246
Content-Type: text/plain; charset=ISO-8859-1

http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/10.10/release/xubuntu-10.10-alternate-i386.iso

--20cf301fbae58550800499e71246
Content-Type: text/html; charset=ISO-8859-1

<a href="http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/10.10/release/xubuntu-10.10-alternate-i386.iso">http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/10.10/release/xubuntu-10.10-alternate-i386.iso</a>

--20cf301fbae58550800499e71246--


```

thanks

---

### Post by elico on 2011-01-15
if you are asking me...
i dont like the idea of email running scripts...
i think it's better to setup some https server with a cgi script shortcut.
im using caouple of scripts on my server (10) and for that i just did some security evaluations and i got a secure "do that"
and "do that"

---

### Post by elico on 2011-01-15
if you are asking me...
i dont like the idea of email running scripts...
i think it's better to setup some https server with a cgi script shortcut.
im using caouple of scripts on my server (10) and for that i just did some security evaluations and i got a secure "do that"
and "do that"

---

### Post by elico on 2011-01-15
if you are asking me...
i dont like the idea of email running scripts...
i think it's better to setup some https server with a cgi script shortcut.
im using caouple of scripts on my server (10) and for that i just did some security evaluations and i got a secure "do that"
and "do that"

---

### Post by mfaust731 on 2011-01-15
Could you please repeat that

---

### Post by Girya on 2011-01-15
check out  fetchmail and procmail to accomplish what you are trying to do at least thats what I used for the script I wrote. I looked at the tutorial mentioned above and what I did was a differnt way. 

use fetchmail to download emails every few minutes then pass it to procmail which parses the email or sms and if a keyword is in the subject line it executes a specific script. 

the script i wrote would log into my online checking account and sms me back my balance.

---

### Post by mfaust731 on 2011-01-15
sort $HOME/gmail/download/new/copy* | uniq | grep -o -e http://[^[:space:]\"]*


This does the trick!

---

### Post by vortmax on 2011-01-15
> **Girya said:**
> check out  fetchmail and procmail to accomplish what you are trying to do at least thats what I used for the script I wrote. I looked at the tutorial mentioned above and what I did was a differnt way. 

use fetchmail to download emails every few minutes then pass it to procmail which parses the email or sms and if a keyword is in the subject line it executes a specific script. 

the script i wrote would log into my online checking account and sms me back my balance.

I wrote a helpdesk program that fetched emails from a server and parsed them into a database with this method.  Fetchmail to pull in the email, then procmail to do low order filtering.  I had procmail pipe the contents into a PHP script which tore the email apart and ran the database queries.

I agree that running server commands over email is risky.  Email is easy to spoof.  If you decide the risk is low, make sure to restrict the commands anyway......do not let the script arbitrarily execute code in the email body.  I would also have it send an email back to you (not just a reply) with the results of the action and include an email command to shut down the mail service. That would let you know if someone else was running scripts and give you a way to shut it down in a hurry.

---

