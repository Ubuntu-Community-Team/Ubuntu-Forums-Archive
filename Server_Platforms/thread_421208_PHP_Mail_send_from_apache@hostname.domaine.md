---
title: "PHP Mail send from apache@hostname.domaine"
date: 2007-04-24
forum: Server Platforms
---

### Post by prodsacnetworking on 2007-04-24
Hi,

I've compiled apache 2.24 with php5.

when I use PHP Mail function, the email is sent with [email]apache@hostname.doma[/email]ine in the FROM area.

Any ideas how I can change it?

Thanks.

---

### Post by joselin on 2007-04-24
From the php help:

bool **mail** ( string to, string subject, string message [,  string additional_headers [, string additional_parameters]])
[COLOR=#0000bb]
mail [/COLOR][COLOR=#007700]('[/COLOR][COLOR=#dd0000]nobody@example.com'[/COLOR][COLOR=#007700], '[/COLOR][COLOR=#dd0000]the subject'[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]$message[/COLOR][COLOR=#007700],
     [/COLOR]**[COLOR=#dd0000]"From: webmaster@{$_SERVER['SERVER_NAME']}\r\n" [/COLOR]**[COLOR=#007700]**.**
     [/COLOR][COLOR=#dd0000]"Reply-To:  webmaster@{$_SERVER['SERVER_NAME']}\r\n" [/COLOR][COLOR=#007700].
     [/COLOR][COLOR=#dd0000]"X-Mailer: PHP/" [/COLOR][COLOR=#007700]. [/COLOR][COLOR=#0000bb]phpversion[/COLOR][COLOR=#007700]());
[/COLOR][COLOR=#007700]

Regards
[/COLOR]

---

### Post by strixy on 2007-04-24
I have the same/similar problem. It's not in the PHP code, but rather somewhere in the system.

I've renamed my computer's domain so the email now sends from [email]www-data@domain.com[/email]

I thought maybe the emails were being bounced for lack of a valid address, so I created the [email]www-data@domain.com[/email]

That didn't work.

I tried a completely new install of the entire Ubuntu system. Reinstalled sendmail  and no luck.

I've spent hours configuring sendmail then restarting it, sending test emails and waiting for the mail servers to go though and still, sadly, my php scripts (which work nicely on other servers) are not sending email using the php mail(). SMTP works fine...

Strangely, the mail.err log says the email was sent and is being held in queue.

Weird...

---

### Post by strixy on 2007-04-26
I discovered last night that nmap shows port 25 open on 

#nmap localhost

but not on my LAN 

nmap 192.168.1.6

I checked my firewall, turned it right off actually, but still it was closed. I thought that my router might be interfering, but I double checked to see if port 25 was being forwarded to the proper computer and it was. I set my server to be the DMZ host on the router, but that didn't help.

Of course, my router is 7+ years old and I've been suspicious (for other reasons) that it might be about to blow up. Maybe this is another symptom? 
If (0) {
then $trixy = stumped
}

---

### Post by strixy on 2007-05-06
I scrapped the sendmail approach and installed exim4 then used the exim4 config program (I think it was exim-config?). That worked like a charm!

---

