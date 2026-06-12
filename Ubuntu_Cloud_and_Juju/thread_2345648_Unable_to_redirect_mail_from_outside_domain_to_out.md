---
title: "Unable to redirect mail from outside domain to outside domain"
date: 2016-12-06
forum: Ubuntu Cloud and Juju
---

### Post by fabioescabrita on 2016-12-06
I have a smart host working in a MacosX 10.9.5 with Server App 3 (who uses postfix mail_version = 2.9.4), and i have notice that i am just able to redirect mail inside of my smart host (Outlook, Mail app and roundcubemail installed in this server), for example i am just able to send mails from [EMAIL="user1@domainX.pt"]user1@domainX.pt[/EMAIL] to [EMAIL="user2@domainX.pt"]user2@domainX.pt[/EMAIL] where i have a redirection to [EMAIL="user1@domianY.pt"]user1@domianY.pt[/EMAIL], if i try to send mail from [EMAIL="user1@domainY.pt"]user1@domainY.pt[/EMAIL] to [EMAIL="user1@domainX.pt"]user1@domainX.pt[/EMAIL] who is redirecting mail to [EMAIL="user2@domainY.pt"]user2@domainY.pt[/EMAIL], i will get this message at mail.log:

```
Dec  6 14:37:12 remote.domainX.pt postfix/smtp[28504]: 0B8BD259F57: to=<user2@domainY.pt>, orig_to=<user1@remote.domainX.pt>, relay=mail.domainX.pt[]:25, delay=0.1, delays=0/0.01/0.07/0.02, dsn=5.0.0, status=bounced (host mail.domainX.pt[] said: 550-Verification failed for <Xserver@remote.domainX.pt> 550-No Such User Here 550 Sender verify failed (in reply to RCPT TO command))
```

From what it seems instead of using orig_to=<user1@domainX.pt> i am getting orig_to=<user1@remote.domainX.pt>, and my remote mail server will give that response. I am just using domainX.pt instead of remote.domainX.pt that i am not using at all.
My mail server remote.domainX.pt is connected to my remote mail server mail.domainX.pt.

Anyone knows how can i solve this?

---

### Post by lisati on 2016-12-06
It looks like you have [sender verification]("http://www.postfix.org/ADDRESS_VERIFICATION_README.html") turned on. When I was running my own server a few years ago, I liked the idea, but found that it was usually better to use other methods of filtering spam.

Some people believe that it's a bad idea to do address verification. Have a look here: [http://www.circleid.com/posts/sender_address_verification/](http://www.circleid.com/posts/sender_address_verification/)

---

### Post by fabioescabrita on 2016-12-06
I dont have a field for sender verification, could you please check my main.cf? 

[http://pastebin.com/d9hZaTwp](http://pastebin.com/d9hZaTwp)

---

### Post by fabioescabrita on 2016-12-07
After trying virtual_alias_maps instead of alias_maps, i notice that if i try to send from an outside domain to redirect locally and send again to another outside domain, i would send like this:

Dec  7 16:23:06 remote.domainX.pt postfix/smtp[94531]: B85A0275128: to=<user2@domainY.pt>, orig_to=<user1>, relay=127.0.0.1[127.0.0.1]:10024, delay=5.4, delays=0.02/0/0/5.4, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as 23A3427514A)

It removes all the domain part from [EMAIL="user1@domainX.pt"]user1@domainX.pt[/EMAIL] =/ and send it locally to nowhere. I cannot even see this message at mailq, in my smart host.

---

### Post by lisati on 2016-12-07
> **fabioescabrita said:**
> I dont have a field for sender verification, could you please check my main.cf? 

[http://pastebin.com/d9hZaTwp](http://pastebin.com/d9hZaTwp)

I had a quick look at your main.cf file. Your setup is a bit different to what I used to use with Postfix, and I suspect that my initial thoughts about why verification failed appears to have failed might be mistaken. I will happily defer to someone who might have a more useful suggestion.

---

### Post by fabioescabrita on 2016-12-07
Thanks lisati!

I didnt say it but, i have used getmail to receive mail and send locally through sendmail to postfix.

I dont know if could be from that =/ I have used this arguments, not sure if is messing or if it could help to solve this:

```
[FONT=Menlo][destination][/FONT]
[FONT=Menlo]type = MDA_external[/FONT]
[FONT=Menlo]path = /usr/sbin/sendmail[/FONT]
[FONT=Menlo]arguments = ("-bm", "user1")[/FONT]
[FONT=Menlo]unixfrom = true[/FONT]

```

I already tried to use [EMAIL="user1@domainX.pt"]user1@domainX.pt[/EMAIL] instead of user1, but i am unable to receive mail in my local accounts with that syntax =/

:confused::confused::confused:

---

### Post by fabioescabrita on 2016-12-09
After some tests at sendmail through getmail, i also notice that i could only use local user account names as destination (Example1) or use full email name only with @remote.domainX.pt and not @domainX.pt as i was expecting.

Example 1:

[HTML][destination]
type = MDA_external
path = /usr/sbin/sendmail
arguments = ("-bm", "test")
unixfrom = true[/HTML]

Example 2: 

[HTML][destination]
type = MDA_external
path = /usr/sbin/sendmail
arguments = ("-bm", "test@remote.domainX.pt")
unixfrom = true[/HTML]

[COLOR=#242729][FONT=Arial]So i am trying to figure out how can i solve this with postfix, to handle just @domainX.pt to receive mail instead of [/FONT][/COLOR]@remote.domainX.pt but i am not seeing a way to fix this.

I have also tested with virtual_alias_maps instead of aliases from alias_maps but with that there is no domain associated to my local accounts, it can only be used to local delivery.

---

### Post by fabioescabrita on 2016-12-09
Until it starts to redirect mail to test3 and test4 from other domain it sends locally through sendmail from local user test to [EMAIL="test@remote.domainX.pt"]test@remote.domainX.pt[/EMAIL]:
[HTML]
Dec  9 11:50:06 remote.domainX.pt postfix/smtp[1734]: C39B729E55F: to=<test@remote.domainX.pt>, orig_to=<test>, relay=127.0.0.1[127.0.0.1]:10024, delay=5.5, delays=0.01/0/0/5.5, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as 41CE429E581)    
Dec  9 11:50:06 remote.domainX.pt postfix/pipe[99700]: 41CE429E581: to=<test3@domainX.pt>, orig_to=<test@remote.domainX.pt>, relay=dovecot, delay=0.03, delays=0/0/0/0.03, dsn=2.0.0, status=sent (delivered via dovecot service)    
Dec  9 11:50:06 remote.domainX.pt postfix/local[1823]: 41CE429E581: to=<test@remote.domainX.pt>, relay=local, delay=0.03, delays=0/0/0/0.03, dsn=2.0.0, status=sent (forwarded as 48E2929E585)    
Dec  9 11:50:06 remote.domainX.pt postfix/smtp[1879]: 48E2929E585: to=<test4@domainY.pt>, orig_to=<test@remote.domainX.pt>, relay=mail.domainX.pt[94.126.172.X]:587, delay=0.09, delays=0/0.01/0.06/0.02, dsn=5.0.0, status=bounced (host mail.domainX.pt[94.126.172.X] said: 550-Verification failed for <Xserver@remote.domainX.pt> 550-No Such User Here 550 Sender verify failed (in reply to RCPT TO command))[/HTML]

But when i try to send directly i send as @domainX.pt:


    [HTML]Dec  9 11:53:54 remote.domainX.pt postfix/pickup[99897]: A3CAC29E670: uid=70 from=<test@domainX.pt>    
Dec  9 11:53:54 remote.domainX.pt postfix/qmgr[97642]: A3CAC29E670: from=<test@domainX.pt>, size=510, nrcpt=1 (queue active)    
Dec  9 11:53:54 remote.domainX.pt postfix/qmgr[97642]: B0C3E29E677: from=<test@domainX.pt>, size=957, nrcpt=1 (queue active)[/HTML]

---

### Post by fabioescabrita on 2016-12-09
If i set sendmail to send as [EMAIL="test@domainX.pt"]test@domainX.pt[/EMAIL] i get this:


[HTML]Dec  9 12:13:06 remote.domainX.pt postfix/local[1823]: A508B29EAEA: to=<teste@domainX.pt>, relay=local, delay=0.01, delays=0/0/0/0, dsn=5.4.6, status=bounced (mail forwarding loop for teste@domainX.pt)    
Dec  9 12:13:06 remote.domainX.pt postfix/smtp[2561]: 3E66429EAC9: to=<teste@domainX.pt>, relay=127.0.0.1[127.0.0.1]:10024, delay=5.4, delays=0/0/0/5.4, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as A508B29EAEA)[/HTML]

A loop but i cannot figure out why

---

### Post by fabioescabrita on 2016-12-09
Well i was able to fix @remote.domainX.pt to @domainX.pt but through virtual_alias_maps but its relaying locally and not to my remote mail server, at least i have it pointed to that server as well as with sasl authentications per user in main.cf:

Dec  9 12:52:06 remote.domainX.pt postfix/smtp[4026]: 9C4B029F3E0: to=<test@domainY.pt>, orig_to=<test@domainX.pt>, relay=127.0.0.1[127.0.0.1]:10024, delay=5.5, delays=0.02/0/0/5.5, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as 1723529F40A)

---

