---
title: "Home / personal mail server"
date: 2010-06-16
forum: Server Platforms
---

### Post by SlugSlug on 2010-06-16
Hello,
I would like someone to go through a mail server setup with me...

I have regged an domain with co.cc and would now like to send / receive mail with that domain from my ubuntu box..  and am a bit lost

I have a dynamic IP which is updated to dnydns via dnyclient (cannot have static due to isp issues)

has anyone done this that could give me a step by step?

---

### Post by Bachstelze on 2010-06-16
There are a lot of issues that need to be taken care of.

First, because of your dynamic IP, you will probably not be able to send mail directly, because most mail servers automatically reject mail that comes from dynampic IPs as an anti-spam measure. This is not a big problem, though, you can just use your ISP's SMTP server to send mail.

Second, your domain. Can you set the MX records for it? If you can't, you won't be able to receive mail with that domain and you will have to use another one (a No-IP free domain works).

Third, does your ISP block incoming port 25? If it does, you will have to use a third-party service to receive mail for you and forward it to you on a non-standard port of your choice. No-IP has a service for that, I think it's about $40 per year.

---

### Post by SlugSlug on 2010-06-16
Thanks for reply..

> **Bachstelze said:**
> There are a lot of issues that need to be taken care of.

First, because of your dynamic IP, you will probably not b able to send mail directly, because most mail servers automatically reject mail that comes from dynampic IPs as an anti-spam measure. This is not a big problem, though, you can just use your ISP's SMTP server to sen mail.

Second, your domain. Can you set the MX records for it? If you can't, you won't be able to receive mail with that domain..
                     --- I believe I can, I have two boxes to fill host and value -- along with type (mx/cname etc..)


> **Bachstelze said:**
> 
Third, does your ISP block incoming port 25? .

Dont think so...

---

### Post by Bachstelze on 2010-06-16
Then just install Postfix and get started. :) Debconf will let you do the main configuration easily (chOose "Internet with smarthost"). You might want to set the machine's hostname to your .co.cc hostname beforehand. Also don't forget to forward port 25 on your router.

Good luck , feel free to post back if you have problems. :)

---

### Post by SlugSlug on 2010-06-16
> **Bachstelze said:**
> Then just install Postfix and get started. :) Debconf will let you do the main configuration easily (chOose "Internet with smarthost"). You might want to set the machine's hostname to your .co.cc hostname beforehand. Also don't forget to forward port 25 on your router.

Good luck , feel free to post back if you have problems. :)

am in install now but the read about machine name..


my machine is called something different say 'bob' - - do I have to rename bob to name.co.cc ?

---

### Post by Bachstelze on 2010-06-16
> **SlugSlug said:**
> am in install now but the read about machine name..


my machine is called something different say 'bob' - - do I have to rename bob to name.co.cc ?

You don't have to, but it would make your life much easier.

---

### Post by SlugSlug on 2010-06-16
> **Bachstelze said:**
> You don't have to, but it would make your life much easier.


sorry, not sure what I should be putting in...
System mail name:     {machinename} ?        &#9474; 

                                                                         
&#9474; SMTP relay host (blank for none):                                         &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; smtp.localdomain_____

---

### Post by Bachstelze on 2010-06-16
Put name.co.cc as system mail name. The SMTP relay host is the server you will use to send mail, it is the SMTP server of your ISP.

---

### Post by SlugSlug on 2010-06-16
right ok.

according to this([http://forum.o2.co.uk/viewtopic.php?p=4085](http://forum.o2.co.uk/viewtopic.php?p=4085))  I set smtp to relay.o2broadband.co.uk

now what?

---

### Post by Bachstelze on 2010-06-16
Now you must set the MX record for your domain (something like [font=monospace]MX 10 name.co.cc.[/font]) and forward port 25 on your router. Also check to see whether or not your ISP blocks incoming port 25 (i.e. do [font=monospace]telnet name.co.cc 25[/font] from a machine outside your LAN).

---

### Post by SlugSlug on 2010-06-16
> **Bachstelze said:**
> Now you must set the MX record for your domain (something like [FONT=monospace]MX 10 name.co.cc.[/FONT]) and forward port 25 on your router. Also check to see whether or not your ISP blocks incoming port 25 (i.e. do [FONT=monospace]telnet name.co.cc 25[/FONT] from a machine outside your LAN).

need you help a bit more on that point....

wheres the mx records  is that on co.cc site I regged with -- heres the options..



**                          2. Zone Records                **

                                                                     
                                                 [U][COLOR=#000000]**Edit / Add Zone  Records(A, MX, NS, CNAME, TXT)**                         
[COLOR=#e75107]Advanced Service / It  can be difficult[/COLOR][/COLOR][/U]                                                            
                                                                                                                                                                                                      **Current zone records :                                  **                                                                                                    **Host                                 ****TTL                                 ****Type/Priority                                  ****Value                                         **                                         [COLOR=#f13f48]**Empty                                **[/COLOR]                                                                                   
                                                                                                                                                                                                                                                                        [COLOR=#045758]**Add  a record**                                         [/COLOR]                                                                                                                                                                     
                                        
                                        **Host  [   ]**  
:                                                                                                                                                                      **TTL**  :                                                                                                                                                           7 D                                                         4 D                                                         3 D                                                         2  D                                                        1 D                                                         12 H                                                         8  H                                                        6 H                                                         4 H                                                         3 H                                                         2 H                                                         1 H                                                                                                                                          **Type**  :                                                                                                                                                                                                                                                                                                                                                                       A                                                         MX                                                         NS                                                         CNAME                                                         TXT                                                                                                                                                                                                              **Priority** :                                                                                                    
                                                 _Type?_                                                                                  **Value** :  [   ]

---

### Post by Bachstelze on 2010-06-16
Type MX, priority whatever since you will only have one, put for example 10, value name.co.cc. (final period might or might not be required, try with it first).

---

### Post by SlugSlug on 2010-06-16
ok and host?

---

### Post by Bachstelze on 2010-06-16
name.co.cc. too.

---

### Post by SlugSlug on 2010-06-16
right ok, thats done,

says may take 24 hours..

is that all is needed? I dnt see the bit that ties my box into that domain via any passwords..?

how would I config thunderbird from that would it point to local host 

passwordless?

---

### Post by Bachstelze on 2010-06-16
Now you only have a MTA, incoming mail will be delivered in the user's mailbox on the system, and will not be accessible from outside. If you want to read it from another computer, you will have to install a POP and/or IMAP server, like Dovecot or Courier.

---

### Post by SlugSlug on 2010-06-16
> **Bachstelze said:**
> Now you only have a MTA, incoming mail will be delivered in the user's mailbox on the system, and will not be accessible from outside. If you want to read it from another computer, you will have to install a POP and/or IMAP server, like Dovecot or Courier.


not quite sure what that means..

so I have name.co.cc --  someone mails [email]bob@name.co.cc[/email] -- what happens??

it goes to my box {somewhere?} and then I can get that from thunderbird?? at the moment telnet is going to wrong IP so I have to wait 24hrs..

how should mail client look?


Big Thanks for your help!!!!

---

### Post by Bachstelze on 2010-06-16
> **SlugSlug said:**
> 
it goes to my box {somewhere?}

By default, /vaR/mail/bob.

>  and then I can get that from thunderbird??

If Thunderbird is running on the server, maybe (I don't remember right now whether or not it supports local mailboxes). If it is not, no. Postfix only receives your mail and puts it into /var/mail/bob, nothing else. Reading your mail from there and making it available to other machines via POP or IMAP is Dovecot's or Courier's job.

---

### Post by SlugSlug on 2010-06-16
> **Bachstelze said:**
> By default, /vaR/mail/bob.



If Thunderbird is running on the server, maybe (I don't remember right now whether or not it supports local mailboxes). If it is not, no. Postfix only receives your mail and puts it into /var/mail/bob, nothing else. Reading your mail from there and making it available to other machines via POP or IMAP is Dovecot's or Courier's job.


right ok so my mail is getting dumped to var/mail... (hopefully) so IMAP -- we use that at work would I be right in thinking that all mail is dumped in /var/mail and then imap sorts it out to /home/imap/*
?

---

### Post by Bachstelze on 2010-06-16
> **SlugSlug said:**
> right ok so my mail is getting dumped to var/mail... (hopefully) so IMAP -- we use that at work would I be right in thinking that all mail is dumped in /var/mail and then imap sorts it out to /home/imap/*
?

Right, though if you want to use IMAP, it's usually recommended to have your MTA (Postfix) deliver your mail in a maildir, and not a mailbox.

Basically, a mailbox (the default format) is just a big text file, where all your emails are stored one after the other. It's fine if you just want to download your mail on your computer (with e.g. Thunderbird) and delete it from the server afterwards.

With IMAP, though, mail is retained on the server after downloading (or is even not downloaded at all, and read directly on the server). Obviously, if you have a lot of mail, having it stored in one big text file will be very inefficient, hence maildir, where each email is stored in one separate text file in a given directory.

For now, though, you can just stay will the default config until we're sure all the basic functionality works. Then yoou can move on to setupp IMAP with maildir.

---

### Post by SlugSlug on 2010-06-16
> **Bachstelze said:**
> Right, though if you want to use IMAP, it's usually recommended to have your MTA (Postfix) deliver your mail in a maildir, and not a mailbox.

Basically, a mailbox (the default format) is just a big text file, where all your emails are stored one after the other. It's fine if you just want to download your mail on your computer (with e.g. Thunderbird) and delete it from the server afterwards.

With IMAP, though, mail is retained on the server after downloading (or is even not downloaded at all, and read directly on the server). Obviously, if you have a lot of mail, having it stored in one big text file will be very inefficient, hence maildir, where each email is stored in one separate text file in a given directory.

For now, though, you can just stay will the default config until we're sure all the basic functionality works. Then yoou can move on to setupp IMAP with maildir.


Cheers man - really appreciate your help 

If its OK with you I'll pop back up tomorrow or day after when telnet routes to my ip



Cheers!!

Neil

---

### Post by Bachstelze on 2010-06-16
Sure. I might not be on, though, but feel free to send a mail or a pm.

---

### Post by SlugSlug on 2010-06-17
again - thanks for al your help so far.

I can now use sendmail and that works great but am not receiving any mail

A telent 25  goes to the wrong IP address..
what I have I missed out?

---

### Post by Bachstelze on 2010-06-17
Means you have misconfigured your domain.

---

### Post by SlugSlug on 2010-06-17
any idea where? am not sure what bit is telling co.cc my ip address? as am on dynamic too....

---

### Post by Bachstelze on 2010-06-17
> **SlugSlug said:**
> any idea where? am not sure what bit is telling co.cc my ip address? as am on dynamic too....

I don't know whether co.cc supports dynamic addresses, you might have to get another one (from no-ip or dyndns).

---

### Post by SlugSlug on 2010-06-17
**Host**     name.co.cc **TTL **7D **   Type/Priority **MX 10 **   Value** my.homeftp.net

does that look right to you?

also found out my ISP is blocking port 25 coming into router...

---

### Post by SlugSlug on 2010-06-17
Its all working now !!!

Cheers mate not sure what was wrong before

---

### Post by SlugSlug on 2010-06-17
so whats the best way to have it store emails in separate files so its not one big mess?

---

### Post by Bachstelze on 2010-06-17
Add something like this to your main.cf:

```
home_mailbox = .mail/
```

Will deliver a user's mail in ~/.mail.

---

### Post by SlugSlug on 2010-06-17
.

---

### Post by SlugSlug on 2010-06-17
all working perfect now - thankyou for all your help !!

:popcorn:

---

