---
title: "Help!! Email returned to sender!!"
date: 2008-04-30
forum: Server Platforms
---

### Post by exaviorn on 2008-04-30
Ok I recently had to reinstall ubuntu server (7.10,soon to be updated!!)Ever since my ip address has been blacklisted by Gmail!
I rebooted my router and got a new ip address and tried again,it did not work! Here is the complete message:

```

This is the mail system at host host.com.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<@gmail.com>: host gmail-smtp-in.l.google.com[66.249.91.27] said:
    550-5.7.1 [86.134.205.58] The IP you're using to send mail is not
    authorized 550-5.7.1 to send email directly to our servers. Please use the
    SMTP 550-5.7.1 relay at your service provider instead. Learn more at
    550 5.7.1 http://mail.google.com/support/bin/answer.py?answer=10336
    b30si1630244ika.3 (in reply to end of DATA command)

```

There it is :cool: thx!

---

### Post by cdenley on 2008-04-30
> 
Gmail refuses mail when the sending IP address does not match the sending domain


It sounds like if the message you are sending is from [email]myuser@mysite.com[/email], it must be coming from the actual mail server for the domain mysite.com. Are you trying to send a message using your own mail server to a person's gmail account?

---

### Post by MJN on 2008-05-01
It will be down to one of GMail's anti-spam measures - which one is anyone's guess as they (commonly) do not specify. Furthermore you could be tripping a number of different traps.

My best-guess assumption is that it is your dynamic IP address. Aside from getting a static IP account with your ISP your only real option is relaying via your ISP's mail server (using the relayhost directive in Postfix).

Other potential traps might be lack of SPF records for the domain (although unlikely) and/or no/mismatched reverse PTR records, amongst others. My money is still on the dynamic IP though...

Mathew

---

### Post by exaviorn on 2008-05-01
I use BT how would I relay:confused:

---

### Post by MJN on 2008-05-01
You just need to find out what BT's outgoing mail server is (e.g. smtp.bt.com) and then stick that into your Postfix config as **relayhost = [smtp.bt.com]**

Mathew

---

### Post by exaviorn on 2008-05-01
I have now got this other problem as well!! I can't send mail!
I tried telnet localhost smtp and it just hangs!! I looked at the mail logs and it says every time:
```
jumpserve postfix/tlsmgr[21618]: fatal: open database /var/lib/postfix/smtpd_scache.db: Permission denied
 jumpserve postfix/master[21401]: warning: process /usr/lib/postfix/tlsmgr pid 21618 exit status 1

```
All of this happened after I installed 8.04!! (I think)
Has this got anything to do with this entire problem??
p.s:I have not added relayhost yet!

---

### Post by MJN on 2008-05-01
I don't know what that is, but I do know it's nothing to do with your GMail problems.

Try restarting Postfix (not very helpful I know but it's not an error I've seen before).

Was there nothing else relevant in the log? Post the whole lot if you like (from restarting Postfix).

Mathew

---

### Post by exaviorn on 2008-05-01
I restarted postfix and reinstalled it :lolflag: but it made no differance!! when I type telnet this is what happens:
```
telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

```
as you see there is no welcome message and I can not quit!

---

### Post by MJN on 2008-05-01
Show the logs..

---

### Post by exaviorn on 2008-05-01
```
May  1 19:06:28 myhost postfix/postfix-script[21278]: refreshing the Postfix mail system
May  1 19:06:28 myhost postfix/master[20823]: reload configuration /etc/postfix
May  1 19:08:57 myhost postfix/master[20823]: terminating on signal 15
May  1 19:08:58 myhost postfix/master[21401]: daemon started -- version 2.5.1, configuration /etc/postfix
May  1 19:09:06 myhost dovecot: Killed with signal 15
May  1 19:30:52 myhost postfix/tlsmgr[21562]: fatal: open database /var/lib/postfix/smtpd_scache.db: Permission denied
May  1 19:30:53 myhost postfix/master[21401]: warning: process /usr/lib/postfix/tlsmgr pid 21562 exit status 1
```
That is the error and the command from before the smtp went wrong

---

### Post by MJN on 2008-05-01
What are the permissions on that file, and it's parent directory?

Have you done *anything* with the configuration? It's strange for it to just stop working without some external intervention...

Mathew

---

### Post by MJN on 2008-05-01
Also, your clock seems out - or was that log from before me asking to restart? If so, please restart!

Mathew

---

### Post by exaviorn on 2008-05-01
> **MJN said:**
> What are the permissions on that file, and it's parent directory?

The permissions are proftpd:confused: for the file (the group is postfix) the parent directory is postfix

---

### Post by exaviorn on 2008-05-01
> **MJN said:**
> Also, your clock seems out - or was that log from before me asking to restart? If so, please restart!

Mathew
do you mean restart the server:confused: or restart postfix (I have restarted postfix) The date was from when the problem started
P.S I live in UK

---

### Post by MJN on 2008-05-01
Oh right, I wasn't expecting that!

It sounds like some external library-related issue, I'm guessing TLS given the other log line.

I've just noticed you've upgraded to 8.04 - I've not done so so given it sounds like an issue related to that I'm afraid I have no ideas.

Mathew

---

### Post by MJN on 2008-05-01
> **exaviorn said:**
> do you mean restart the server:confused: or restart postfix (I have restarted postfix) The date was from when the problem started

I meant restart Postfix. The 19:30 stamps in the log were from before I asked you to restart.

Mathew

---

### Post by exaviorn on 2008-05-01
should i uninstall proftpd??

---

### Post by exaviorn on 2008-05-01
I uninstalled proftpd but it told me that the user proftpd did not exist:confused: I remember proftpd adding one:confused: anyway should I change permissons? If so how do i do it safely??

---

### Post by exaviorn on 2008-05-01
Hi works :guitar: the fix was to change permitions back to postfix (I did it with webmin!!)
Thx MJN!!! :lolflag:

---

### Post by MJN on 2008-05-01
I can't take the credit but if it led you in the right direction then that's good!

Mathew

---

### Post by exaviorn on 2008-05-02
> **MJN said:**
> You just need to find out what BT's outgoing mail server is (e.g. smtp.bt.com) and then stick that into your Postfix config as **relayhost = [smtp.bt.com]**

Mathew
where should I find out what bt outgoing mail server is:confused:

---

### Post by MJN on 2008-05-02
BT! ;-)

Or, as always, Google knows the answer - **mail.btinternet.com** if you're a 'BT Broadband' customer. [[Reference]]("http://pdoc.co.uk/btbroadband.shtml")

Mathew

---

### Post by exaviorn on 2008-05-03
Thx:) I could not find it !!
so all I do is add ```
relayhosts=[mail.btinternet.com]
``` to my postfix main.cf file !

---

### Post by MJN on 2008-05-03
That's it (but it's **relayhost**, i.e. no 's')

Mathew

---

### Post by exaviorn on 2008-05-04
I have also been thinking!! This problem has only happened since I did the virtualusers/domains ubuntu docs tutorial! would adding a certificate make any difference:confused:
I examined the website you linked to,it was talking about usernames and passwords,do I and if so where do i have to add my bt account password???

---

### Post by MJN on 2008-05-04
Many ISPs don't require explicit authentication - they restrict relay access to only their customers based on your IP address. Try it and if you cannot send then we can look at adding SASL authentication.

Regarding adding a certificate I'm not sure what you mean.

Mathew

---

### Post by exaviorn on 2008-05-05
I tried adding the relayhost command and I got a returned to sender email:
```
<myusername@gmail.com>: host mail.btinternet.com[217.146.188.192] said: 530
    authentication required - Your email could not be sent. To fix this you
    must make a simple change to your email (known as SMTP authentication). For
    advice visit www.btyahoo.com/smtp (in reply to MAIL FROM command)
```
I think it needs authentication!!

---

### Post by exaviorn on 2008-07-19
:confused:The link in the error reply links to a yahoo mail page ([http://www.btyahoo.com/smtp]("http://www.btyahoo.com/smtp")

---

### Post by MJN on 2008-07-19
<duff info removed - ignore this post!>

---

### Post by exaviorn on 2008-07-19
:confused:

---

