---
title: "Need assistance with configre IMAP/SMTP in Citadel"
date: 2017-03-21
forum: Server Platforms
---

### Post by fflax on 2017-03-21
Dear all, 

i setup a Citadel Server which "works" fine so far.
But iam not able to configure the remote retrieval settings to pick my GMail mail.
I tried something like remote Host: pop.gmail.com (or : pop.gmail.com:995 ) plus Username and Password
But its not working :-( from Citadel documentation, support or www iwasnt able to pick some help.
So if somebody is able to help me out would be great !

best regards

ffflax

---

### Post by slickymaster on 2017-03-21
Hello fflax, welcome to the forums.

I'm moving your thread to the ***Server Platforms*** sub-forum, as it is a better venue for it.

---

### Post by fflax on 2017-03-28
...nobody any idea ?
i thought this is a common tool and common problem. 
i dont get any errormessages but also no mails :-(
What are your entries you are using for remote mail retrieval ?

best regards

fflax

---

### Post by darkod on 2017-03-28
The problem is that 3rd party applications even when based on ubuntu, usually have their own setup and rules. You can't view them as default ubuntu system. I have never installed citadel and don't know what it brings into the game to comment on it.

A setting for remote retrieval might be different compared between ubuntu and citadel. Plus, no, I don't do remote retrieval for my gmail. My gmail is my gmail and if I am setting up mail server to serve some domain, that's what it is for...

Also, are you sure the connection is not refused on gmail side? Sometimes it can be picky about allowing mail servers to connect to it and get its messages. That's what someone trying to rob your emails would do...

Check the logs on the server and post any error messages you find relevant, and maybe someone can help with it. You have given no much relevant data.

---

### Post by fflax on 2017-03-28
..unfortunately i dont  found helpful stuff on the citadel logfiles... :-( 
checked on 
/var/lib/citadel/data -> clean
/var/logs/mail.err -> clean
/var/logs/mail.warn -> clean
/var/logs/mail.info -> Mar 28 15:15:39 XXXX citserver[4819]: IO[17]CC[18][18]POP3: [email]XXXX@pop.gmail.com[/email]: fetched 0 new
 of 0 messages in 127.379954s. bye.
 
whereelse can i look to check whatsgoing wrong ?

Thanks in advance

fflax

---

### Post by darkod on 2017-03-28
Well, it looks like it is trying to establish a connection. Are you sure gmail is not blocking it?

Check also:
/var/log/mail.log
/var/log/syslog

---

### Post by fflax on 2017-03-29
Thanks  Darko, 

Good hint !
in  /var/log/mail.log  i found a lot of this : 
...
Mar 29 08:30:32 YYYYYY citserver[4819]: IO[121]CC[124][119]POP3: IO[121]CC[124][119]POP3: < 1 13832
Mar 29 08:30:32 YYYYYY citserver[4819]: IO[121]CC[124][119]POP3: POP3: POP3SetTimeout
Mar 29 08:30:32 YYYYYY citserver[4819]: IO[121]CC[124][119]POP3: IO[121]CC[124][119]POP3: < 2 60649
Mar 29 08:30:32 YYYYYY citserver[4819]: IO[121]CC[124][119]POP3: POP3: POP3SetTimeout
...
Mar 29 08:32:39 YYYYYY citserver[4819]: IO[124][121]POP3: POP3: POP3_C_ConnFail
Mar 29 08:32:39 YYYYYY citserver[4819]: IO[124][121]POP3: POP3: POP3_C_Terminate
Mar 29 08:32:39 YYYYYY citserver[4819]: IO[124]CC[127][121]POP3: [email]XXXX@pop.gmail.com[/email]:995: fetched 0 new of 0 messages in 127.363110s. bye.

/var/log/syslog is repeating 
...
Mar 29 08:36:38 YYYYYY citserver[4819]: -- db checkpoint --
Mar 29 08:37:39 YYYYYY citserver[4819]: Network full processing in 3173 seconds.
Mar 29 08:37:39 YYYYYY citserver[4819]: SMTPCQ: processing outbound queue
Mar 29 08:37:39 YYYYYY citserver[4819]: SMTPCQ: queue run completed; 0 messages processed 0 activated
Mar 29 08:37:39 YYYYYY citserver[4819]: network: no neighbor nodes are configured - not polling.
Mar 29 08:37:39 YYYYYY citserver[4819]: No external notifiers configured on system/user

... no glue if this means i have an issue

thanks in advance for sharing your thoughts.

fflax

---

### Post by darkod on 2017-03-29
I would say the POP3_C_ConnFail means that the pop connection to gmail is failing. Check if the dns is resolving it, and then check if gmail is blocking it. You should be able to try telnet to it too. Something like:
```
nslookup pop.gmail.com
telnet pop.gmail.com 995
```

If you do manage to telnet into gmail, you can try authenticating with your credentials which should show you if gmail is accepting them. You can google how to test authenticate in telnet pop session.

So far, it looks to me like gmail is not letting you download your emails. Either you haven't enabled the option (it is not enabled by default), or they don't like your server connecting to it to download emails.

---

### Post by fflax on 2017-03-29
Hi Darko, 

here is the output :
YYYYYY ~ $ nslookup pop.gmail.com
Server:        192.168.178.1
Address:    192.168.178.1#53

Non-authoritative answer:
pop.gmail.com    canonical name = gmail-pop.l.google.com.
Name:    gmail-pop.l.google.com
Address: 66.102.1.109
Name:    gmail-pop.l.google.com
Address: 66.102.1.108

YYYYY ~ $ telnet pop.gmail.com 995
Trying 66.102.1.109...
Connected to gmail-pop.l.google.com.
Escape character is '^]'.
Connection closed by foreign host.

Not sure what does this mean for me, (iam not so familiar with this stuff ;-))
When iam checking my gmail settings that POP and IMAP is activated.

Thanks in advance

Fflax

---

### Post by darkod on 2017-03-29
The telnet to 995 seems to open. Try this short tutorial how to test if it will accept your username and password:
[https://blog.yimingliu.com/2009/01/23/testing-a-pop3-server-via-telnet-or-openssl/](https://blog.yimingliu.com/2009/01/23/testing-a-pop3-server-via-telnet-or-openssl/)

You need to telnet to 995, not to 110 like in their example. The rest should be the same, especially the part to enter the USER and PASS and to use STAT to get the status of the mailbox.

---

### Post by fflax on 2017-03-29
Darko, 

thanks for beeing patient. 
Here the output
YYYYY ~ $ openssl s_client -crlf -connect pop.gmail.com:995 -starttls pop3CONNECTED(00000003)
1995774048:error:140790E5:SSL routines:SSL23_WRITE:ssl handshake failure:s23_lib.c:177:
---
no peer certificate available
---
No client certificate CA names sent
---
SSL handshake has read 0 bytes and written 295 bytes
---
New, (NONE), Cipher is (NONE)
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : 0000
    Session-ID: 
    Session-ID-ctx: 
    Master-Key: 
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    Start Time: 1490783856
    Timeout   : 300 (sec)
    Verify return code: 0 (ok)
---

my understanding is he doesnt like my machine because of any certificate stuff.
So do i need to create a certifcate on my server, which kind of certificate is required ?

best regards
fflax

---

### Post by darkod on 2017-03-29
That's not what I meant. The telnet pop.gmail.com 995 got you connected to port 995 as it seems. From there on continue with the auth test.

I don't think you need the openssl connection attempt if telnet lets you in already...

---

### Post by fflax on 2017-03-29
sorry little bit lost. 
the first part want successfull. 
YYYYY ~ $ telnet pop.gmail.com 995
Trying 64.233.167.109...
Connected to gmail-pop.l.google.com.
Escape character is '^]'.
Connection closed by foreign host.

:-/ not seeing any place for log in 

best regards

fflax

---

### Post by darkod on 2017-03-29
Sorry, I thought the connection is closed only after you press Ctrl+]. So yes, the gmail server is kicking you out...

The certificate should not be an issue because gmail server should provide the cert (the one you are connecting to). But I do not know how their servers work and what requirements they have in place for someone trying to use pop connections from his own mail server.

I don't think I can help much more than this. At least now you know that it is not the citadel configuration that is giving you issues. You have to investigate whether the connection you are trying to establish is possible at all, and under which circumstances.

---

