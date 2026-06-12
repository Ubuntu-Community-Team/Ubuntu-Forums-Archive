---
title: "Mail server ! dns registration"
date: 2008-06-30
forum: Server Platforms
---

### Post by krsnavan on 2008-06-30
I want to setup mail server which can host for ex: corporate,com and company.corporate.com.

I have to register corporate.com to internic and point the dns to my dns server.Do i need to register company.corporate.com also to Domain register? 

My purpose is to deliver mail to corporate.com and company.corporate.com both to my single mail server.


thanx

---

### Post by hyper_ch on 2008-07-01
both belong to the same domain name. "corporate.com" so you only need to setup a wildcard sub.domain.com

---

### Post by krsnavan on 2008-07-01
Hi !

U mean i have to register corporate.com only in INTERNIC.

WIldcard has to set in my DNs Server? Plz. explain in detail.

Vanna

---

### Post by hyper_ch on 2008-07-01
you can't register at "sub.domain.com" ... only "domain.com"... everything else will be handeld by the dns entry for the domain.

---

### Post by krsnavan on 2008-07-01
Thank U so much !

By the way, In your experience What is the best mail server which work flawlessly with spam control,without virus infection and suitable for enterprise.

Vanna

---

### Post by hyper_ch on 2008-07-01
I like postfix as it has quite a few anti-spam measures integrated in it (although not activated by the default configuration). Have a look here:

[http://jimsun.linxnet.com/misc/postfix-anti-UCE.txt](http://jimsun.linxnet.com/misc/postfix-anti-UCE.txt)

The smtpd_recipient_restrictions are important. Regarding the blacklists to use you'll have to check yourself what each blacklist uses as criteria for someone to get blacklisted.

Furthermore I use greylisting: [http://www.howtoforge.com/greylisting_postfix_postgrey](http://www.howtoforge.com/greylisting_postfix_postgrey)  -  however I don't know for sure how well that would integrate into a business environment because mails will get "delayed" due to greylisting (at least from those email addresses that haven't whitelisted themselves for some time).

And as final "defense" I use spamassassin to tag mails as possible spam.

---

### Post by krsnavan on 2008-07-01
Hi !


What about the Virus Detection.WHat virus Guard U are using ? and wht about the signatue updates.

GIve me some more details. WHere r u storing the Mail boxes?
In linux server it self?

I seen an article about using POSTFIX AS ANTIVIRUS and ANTISPAM 
 RELAY Server for Exchange .


Thank U !

---

### Post by hyper_ch on 2008-07-01
I don't use any AV software... and I use maildir storage for the mailboxes under the system users.

---

### Post by windependence on 2008-07-01
I would recommend Zimbra. Everything in one package, clamav, spamassassin, etc.

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

-Tim

---

### Post by krsnavan on 2008-07-02
If u don't use any AV, then how do u control the viruses in the attachement in case u r using windows clients.

vanna

---

### Post by hyper_ch on 2008-07-02
Windows clients should protect themselves... as I run my server for private matter only and for a couple of friends I can take this stance...

However in a professional environment you might want to filter viruses out...

---

