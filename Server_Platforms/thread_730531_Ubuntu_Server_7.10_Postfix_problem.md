---
title: "Ubuntu Server 7.10 Postfix problem"
date: 2008-03-21
forum: Server Platforms
---

### Post by Metro_Dan on 2008-03-21
Hi folks! Fist I want to say I am new to the forums but have been lurking for a few months. Generally speaking I am a total newbie to Linux. But onto my problem...

Ok so my friend wanted wanted me to set up Postfix on his Ubuntu 7.10 Server so I said what the heck I need to learn this sooner or later. When I SSHed in all the normals were set up (PHP. Apache, mySQL, ect.) except Postfix so I installed it using this[ tutorial]("http://howtoforge.com/perfect_server_ubuntu7.10_p5") everything seemed to go smooth I installed courier-pop all was well.
So I figured I would test the setup. So I did this
```
telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 frostcather.com ESMTP Postfix (Ubuntu)
ehlo localhost
250-frostcather.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: root@localhost
250 2.1.0 Ok
rcpt to:fmaster@localhost
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
subject: test
test test test
.
250 2.0.0 Ok: queued as DD19F6F019C
quit
221 2.0.0 Bye

```
Went perfect got the e-mail then I figured I would try to send it outside
did the same just sent to to my gmail address went fine, I got the e-mail

Just when I was thinking I was the man I figured I would test it again this time useing the domain name instead of just localhost it went like this:
```
 telnet mail.pinpunk.com 25
Trying 66.93.0.30...
Connected to mail.pinpunk.com.
Escape character is '^]'.
220 frostcather.com ESMTP Postfix (Ubuntu)
ehlo pinpunk.com
250-frostcather.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: root@pinpunk.com
250 2.1.0 Ok
rcpt to: dan@metroinnovations.com
554 5.7.1 <dan@metroinnovations.com>: Relay access denied
 
```
So I went back through the steps, uninstalled and reinstalled postfix about 10 times but I still have the same problem.

What I think maybe the problem is possibly is with the FQDN? in the Postfix setup it asks for the FQDN, so I just entered the domain I am trying to get to work for pinpunk.com still had the same problem so I put in the hostname which was ubuserver, nope same problem... so I decided to look in the logs and it refers to connection as frostcatcher.com (one of my friends other domains) so I put that in still nothing. If someone has any clue or can point me in the right direction I will so happy!!! thanks in advance.

Dan

---

### Post by bluefrog on 2008-03-21
I think this is because you are not accessing it from the local network.

if you try to send to metroinnovations.com from telnet localhost 25, it will work.

this is a security so that your server is not an open relay.

if you really want to send mail when accessing it from outside you will have to authorize a machine/network in <Local networks>.

James Dupin

---

### Post by Metro_Dan on 2008-03-21
> **bluefrog said:**
> I think this is because you are not accessing it from the local network.

if you try to send to metroinnovations.com from telnet localhost 25, it will work.

this is a security so that your server is not an open relay.

if you really want to send mail when accessing it from outside you will have to authorize a machine/network in <Local networks>.

James Dupin
Thanks for your reply.
Ok I get the open reply part. So isn't that what authentication is for? So how am I suppose to send mail from out side of the server? Normally it is as simple as using Evolution or Outlook but that is not working now.

---

### Post by crouton on 2008-03-21
It sounds like you have some domains mixed up.  The second telnet session seems to indicate that the mailserver thinks it is frostcather.com, even though you may have your hosts file/DNS set up to have it respond to mail.pinpunk.com.  So when you attempt to send mail as [email]root@pinpunk.com[/email] it determines that root@pinpunk is not a valid local user, and says 'I don't know you, I won't let you use me as a relay.'  

Of course I could be totally wrong too, so any information you can provide to further define the situation/problem would help.

---

### Post by MJN on 2008-03-21
> **Metro_Dan said:**
> Thanks for your reply.
Ok I get the open reply part. So isn't that what authentication is for? 

Yes, but you're not authenticating. If you're testing using telnet (as opposed to a mail client) then check out [this page](http://qmail.jms1.net/test-auth.shtml) for what seems like a good run-through guide of manually authenticating with your server.

Success obviously depends on your server being configured correctly.

Mathew

---

### Post by Metro_Dan on 2008-03-21
Thanks folks. I am going to do another reinstall. and see what I come up with thanks for your help. I will post back after I see how it goes.

---

### Post by MJN on 2008-03-21
Reinstall? Why? It's working as designed! :confused:

Mathew

---

### Post by Metro_Dan on 2008-03-22
> **MJN said:**
> Reinstall? Why? It's working as designed! :confused:

Mathew

Its not authenticating, and for some odd reason pop is not longer working.
I am just looking for a way to get mail up and running using a external mail client, and possibly get it working for webmin.

It shouldn't take me long to redo, that way maybe I will know what I am doing a little better.
---------------------------------------

Ok so I have reinstalled. POP is working I am able to get emails. Sending still does not work, I am testing with Evolution I get this error ```
Could not connect to mail.pinpunk.com: No route to host
```

I feel I am getting closer but I really don't have a clue

Thanks again guys and Ubuntu Rocks! :guitar:

---

### Post by MJN on 2008-03-22
Can you do **telnet mail.pinpunk.com 25** ?

Where is the machine that you're testing from, relative to the server you're connecting to?

Regarding the authentication, show me the stops you're doing to authenticate as neither of your manual testing above had any authentication attempts in them.

Mathew

---

### Post by Metro_Dan on 2008-03-22
Yeah I decide to try to do it through a mail client seemed easier.

But no I can not telnet mail.pinpunk.com 25  unless I am under SSH in his machine, my ISP is blocking me aren't they?

---

### Post by MJN on 2008-03-22
It looks like it (as I can connect from here).

Mathew

---

### Post by Metro_Dan on 2008-03-22
> **MJN said:**
> It looks like it (as I can connect from here).

Mathew

Mathew thank you so much! I will set it up to listen on 25 and 26 is that possible?

Again thank you!

---

### Post by MJN on 2008-03-22
It is, but before going down that road can you clarify where your server and client sit? If your server is using the same ISP, where outbound port 25 is blocked, it's not going to be much use as a mail server.

Mathew

---

### Post by Metro_Dan on 2008-03-22
> **MJN said:**
> It is, but before going down that road can you clarify where your server and client sit? If your server is using the same ISP, where outbound port 25 is blocked, it's not going to be much use as a mail server.

Mathew

They are on two different ISP's the server uses Speakeasy which has a open policy regarding servers and has port 25 open. I am using AT&T

Just figured it out. I added port 26 to the master.cf  and I can get in no problem and auth just fine.

Now I need to figure out how to tie this in with Webmin. But that can wait. But this problem is solved

Again thanks to everyone that chimed in!

---

