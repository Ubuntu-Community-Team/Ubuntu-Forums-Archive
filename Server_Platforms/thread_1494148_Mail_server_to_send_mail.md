---
title: "Mail server to send mail"
date: 2010-05-26
forum: Server Platforms
---

### Post by mansonthomas on 2010-05-26
Hi,

  I handle several hundreds of domains. Mails are handled with google apps (but previously I used to have a full postfix/courrier setup with virtualhosting).

  Now what I need is to be able to send mail (newsletter etc...) from my web servers, but I don't need to receive mail on these servers.

  any idea on how to do that very simply ? (postfix exim etc... ? i've no religion I just need something that works)

Regards,
Thomas.

---

### Post by volkswagner on 2010-05-27
I'm not sure, but I think you may have an issue with sent mails marked as spam.  Some mail servers check for reverse DNS.  If you MX records don't match, you sent mail may get rejected.  I have successfully sent mail to some servers, but I believe gmail was one that rejected mail, until I corrected my reverse DNS record.

---

### Post by lisati on 2010-05-27
> **volkswagner said:**
> I'm not sure, but I think you may have an issue with sent mails marked as spam.  Some mail servers check for reverse DNS.  If you MX records don't match, you sent mail may get rejected.  I have successfully sent mail to some servers, but I believe gmail was one that rejected mail, until I corrected my reverse DNS record.

I agree, not to mention having a potential administrative nightmare on your hands managing a large number of domain names. 

You might want to check the IP address of the machine you wish to use as a server at [http://debouncer.com](http://debouncer.com) and [http://blacklistalert.org](http://blacklistalert.org) for potential problems.

---

### Post by mansonthomas on 2010-05-27
Well, when you host several domain on a unique mail server, what are you  suppose to do ?   

you can only set one reverse DNS on one IP  address, can't you.

I've checked the ip of my servers, and they  are blacklisted by 2 online site, not the ip explicitely but the entire  subnet... (Thanks for the link btw)



Thomas.

---

### Post by mansonthomas on 2010-05-27
That said, my servers have valid reverse DNS, when I check with blacklistalert.org

[FONT=arial][SIZE=2]**DNS-Status of ** 88.166.6.71 [IMG]http://blacklistalert.org/flags/fr.gif[/IMG] :
[/SIZE][/FONT] [FONT=arial][SIZE=2][B][COLOR=#009900]Reverse DNS (PTR)  exists and claims to be: home.paquerette.com.
[/COLOR][/B][/SIZE][/FONT]
 [FONT=arial][SIZE=2][B][COLOR=#009900][B][COLOR=#009900]Forward DNS for home.paquerette.com is: 88.166.6.71.
[/COLOR][/B][/COLOR][/B][/SIZE][/FONT]
 [FONT=arial][SIZE=2]**[COLOR=#009900][B][COLOR=#009900]DNS is consistent.[/COLOR]**[/COLOR][/B][/SIZE][/FONT]

It doesn't check the MX records.

Also typical MX records indicates several server that recieve mails, it says nothing about who is legitimate to send mail.

That's what SPF (Send Policy Framework) is for, I think.

I've configured it for my domain paquerette.com but when I tryed to send mail from other smtp gateway that google's one, it works...

thomas@daisybox:~/Documents$ dig paquerette.com TXT

; <<>> DiG 9.7.0-P1 <<>> paquerette.com TXT
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 5742
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;paquerette.com.            IN    TXT

;; ANSWER SECTION:
paquerette.com.        86400    IN    TXT    "v=spf1" "include:aspmx.googlemail.com" "~all"

;; Query time: 34 msec
;; SERVER: 212.27.40.241#53(212.27.40.241)
;; WHEN: Thu May 27 20:48:23 2010
;; MSG SIZE  rcvd: 85

thomas@daisybox:~/Documents$

---

