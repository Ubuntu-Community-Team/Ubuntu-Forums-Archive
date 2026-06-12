---
title: "How to edit &quot;Zone File Editor&quot;?"
date: 2014-06-20
forum: Server Platforms
---

### Post by satimis on 2014-06-20
Hi all,

Any folk on the forum is experienced on editing the "Zone File Editor" ? (pls see attached file) 

I'm subscribing Godaddy's "Ultimate Hosting Plan".  Now only email accounts of the Hosting Domain can receive emails.  Other email accounts of addon domains unable to receive emails.  They can send emails and receive emails sent only from the email accounts of the hosting domain.  The emails sent to them on Internet are bouncing saying "recipient NOT found".

Lately Godaddy has cancelled all written online supports by way of email leaving behind only the call support by phone.  It is NOT convenient for customers living on other continents.  I have been googling 2 days and couldn't find links related.

Please help, if possible.

Regards
satimis

---

### Post by Habitual on 2014-06-20
[http://support.godaddy.com/help/article/680/managing-dns-for-your-domain-names](http://support.godaddy.com/help/article/680/managing-dns-for-your-domain-names)

---

### Post by satimis on 2014-06-21
> **Habitual said:**
> [http://support.godaddy.com/help/article/680/managing-dns-for-your-domain-names](http://support.godaddy.com/help/article/680/managing-dns-for-your-domain-names)

Hi,

Thanks for your link.  I have been working on those articles listed on that link before but couldn't find a solution.

All domains (four) are registered with Godaddy.  "nowgopublic" is the hosting domain of the "Ultimate Hosting Plan".  

All email accounts created with the FREE mail plan coming with their domains can receive emails but with POP3 protocol support only.  Thunderbird mail client can't download the "Sendbox" on their webmails.  Email accounts created on the "Ultimate Hosting Plan" are with IMAP protocol support.  Then I can download the "Sendbox" to Thunderbird mail clients.

The last advice from Godaddy was to remove on MX Record that points to smtp.secureserver.net.   I should only have one MX Record pointed to mail.nowgopublic.com.

Problem is still remained after more than 96 hours.

Regards
satimis

---

### Post by Habitual on 2014-06-21
it appears that howgorepublic.com's mx record does point to mail.nowgorepublic.com
```
host mail.nowgopublic.com
mail.nowgopublic.com is an alias for nowgopublic.com.
nowgopublic.com has address 23.229.152.227
nowgopublic.com mail is handled by 0 mail.nowgopublic.com.
```

Interesting that the godaddy NSs don't have any A record for mail.nowgopublic.com
```
dig mail.nowgopublic.com @ns73.domaincontrol.com +short
dig mail.nowgopublic.com @ns74.domaincontrol.com +short
```

23.229.152.227 is a godaddy IP:
```
whois 23.229.152.227 | grep NetName
NetName:        GO-DADDY-COM-LLC
```

Phone support may be a better option using this 800 number?
1-877-818-4575

---

### Post by satimis on 2014-06-21
Hi,

Thanks for your advice.

Email accounts of nowgopublic.com created on cPanel can receive and send emails without problem.  But email accounts of other domains can only send emails but unable to receive emails.  It is multi-hosting plan.

$ dig mail.nowgopublic.com```

; <<>> DiG 9.8.1-P1 <<>> mail.nowgopublic.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18623
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 2, ADDITIONAL: 0

;; QUESTION SECTION:
;mail.nowgopublic.com.          IN      A

;; ANSWER SECTION:
mail.nowgopublic.com.   3600    IN      CNAME   nowgopublic.com.
nowgopublic.com.        600     IN      A       23.229.152.227

;; AUTHORITY SECTION:
nowgopublic.com.        630     IN      NS      ns24.domaincontrol.com.
nowgopublic.com.        630     IN      NS      ns23.domaincontrol.com.

;; Query time: 433 msec
;; SERVER: 203.80.96.33#53(203.80.96.33)
;; WHEN: Sat Jun 21 22:13:16 2014
;; MSG SIZE  rcvd: 120

```


I don't understand why Godaddy pulling out email support lately.

On their support page
[http://support.godaddy.com/](http://support.godaddy.com/)

Tag
Hablamos Español (We speak Spanish) - the tag is there.  On clicking it starts the support form but in Spanish only.
(see file attached)

It is exactly the same form which I submitted previously for help.  I don't understand why now they only entertain Spanish speakers.  


> **Habitual said:**
>  - snip -
Phone support may be a better option using this 800 number?
1-877-818-4575
I'm in Asia.  Each time I have to send a distant call for support which is quite expensive.  I'm now searching for whether there is a way to send FREE call?

Regards
satimis

---

### Post by Habitual on 2014-06-22
> **satimis said:**
> Hi,

Thanks for your advice.

Email accounts of nowgopublic.com created on cPanel can receive and send emails without problem.  But email accounts of other domains can only send emails but unable to receive emails.  It is multi-hosting plan.

$ dig mail.nowgopublic.com```

; <<>> DiG 9.8.1-P1 <<>> mail.nowgopublic.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18623
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 2, ADDITIONAL: 0

;; QUESTION SECTION:
;mail.nowgopublic.com.          IN      A

;; ANSWER SECTION:
mail.nowgopublic.com.   3600    IN      CNAME   nowgopublic.com.
nowgopublic.com.        600     IN      A       23.229.152.227

;; AUTHORITY SECTION:
nowgopublic.com.        630     IN      NS      ns24.domaincontrol.com.
nowgopublic.com.        630     IN      NS      ns23.domaincontrol.com.

;; Query time: 433 msec
;; SERVER: 203.80.96.33#53(203.80.96.33)
;; WHEN: Sat Jun 21 22:13:16 2014
;; MSG SIZE  rcvd: 120

```


I don't understand why Godaddy pulling out email support lately.

On their support page
[http://support.godaddy.com/](http://support.godaddy.com/)

Tag
Hablamos Español (We speak Spanish) - the tag is there.  On clicking it starts the support form but in Spanish only.
(see file attached)

It is exactly the same form which I submitted previously for help.  I don't understand why now they only entertain Spanish speakers.  



I'm in Asia.  Each time I have to send a distant call for support which is quite expensive.  I'm now searching for whether there is a way to send FREE call?

Regards
satimis

Wish I could help you there, but Skype Premium will allow you to call the US Toll Free Number, I believe.
The beauty of Skype is that if|when you ask for a refund, they'll give it to you. At least they refunded my entire 58.00 USD subscription (in error).
The blurb on refunds said "if you haven't used it". We'll, I've been a Skype Premium user for 5 years and I've definitely used it.
They've done this before when my CC 'expired' (it got a new CCV).

You'd think that "Ultimate Hosting Plan" would have 'options'.

These addon domains, they similarly have A Records that point to a GoDaddy IP?
Use the host -t mx <domain> and dig commands in my second reply to check.

If you like, PM me a list of them and I can check what the issue(s) seems to be...

Have a Great Day!

---

### Post by satimis on 2014-06-22
> **Habitual said:**
> Wish I could help you there, but Skype Premium will allow you to call the US Toll Free Number, I believe.
The beauty of Skype is that if|when you ask for a refund, they'll give it to you. At least they refunded my entire 58.00 USD subscription (in error).
The blurb on refunds said "if you haven't used it". We'll, I've been a Skype Premium user for 5 years and I've definitely used it.
They've done this before when my CC 'expired' (it got a new CCV).

You'd think that "Ultimate Hosting Plan" would have 'options'.

These addon domains, they similarly have A Records that point to a GoDaddy IP?
Use the host -t mx <domain> and dig commands in my second reply to check.

If you like, PM me a list of them and I can check what the issue(s) seems to be...

Have a Great Day!
Hi  Habitual,

I sorted out the problem.

I found "Live Chat" on Godaddy Support.  Previously I thought it was "Voice communication".  Actually the communication is through typing on a popup window.  It took me some time digging out the mic and earphone to make preparation.

Problem is now solved.  I must cancel the old email accounts and on MX set @ pointing to mail.domain.com (all domains).  Previously Godaddy Support Team should check the "Zone File Editor" of my domains first before providing me advice.  All domains are registered with Godaddy.

Anyway lot of thanks for your help.

Regards
satimis

---

### Post by Habitual on 2014-06-22
> **satimis said:**
> Anyway lot of thanks for your help.

Regards
satimis
Glad to be of help.

Bookmark Live Chat!

---

