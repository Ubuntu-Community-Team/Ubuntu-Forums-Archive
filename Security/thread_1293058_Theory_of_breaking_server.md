---
title: "Theory of breaking server"
date: 2009-10-16
forum: Security
---

### Post by Hguest on 2009-10-16
Hi, people:
      I'm studying network programming. An idea of email hacking suddenly came to me and I don't know whether it is feasible or not. I'll explain it and hope you can join the discussion, too. Of course, I'm not about to hack into someone's email box. I'm just using this hacking background to better illustrate some network programming ideas. Everything in this thread is for study purpose.


Normally, when we go to an email log-in page like hotmail's log-in page, we are required to fill in our username and password. A decent email service provider would limit your number of attempts to log in a certain account. If you've tried many times and fail to provide the correct password, they would freeze the account.

However, I'm talking about those email service providers who don't do this: i.e. they don't have the "limit - freeze" precaution for hackers.

So in this situation, I wanna write a C program using socket programming to connect to the server, intereact with the server ( meaning I receive and send data packets ). Here I'm very vague with "intereaction with the server". And that's exactly where my questions lie:

1. I have only the ip address of the server, how can I determine the socket type I need in order to communicate with the server?

2. What form do the data from the server take? I mean, if I put the data I receive in a file, how can I interpret them?

3. What should I send if I want to break into the server?
should I, say, 
connect to server;
send username
send a password
close connection

and repeat? (let's temporarily live with brutal force for simplicity)


If someone could provide some opensource c files that do similar things, that'll be great.

---

### Post by __p1n__ on 2009-10-16
1. Lol

2. Pen-testers understand the technology that they're working with and devise tests/exploits based upon that understanding.  Script kiddies toy around with security tools and waste everybody's time.

Read up on http (check the current RFC) and you'll have a chance to develop the understanding necessary to answer your questions.

Good luck!

edit: although you cite e-mail the content of your post indicates web as the target.  Please note that you absolutely require the written authorization of the target prior to performing any assessment.

---

### Post by update_manager on 2009-10-16
> **Hguest said:**
> 
If someone could provide some opensource c files that do similar things, that'll be great.

These tools might help you. Source is available of course.

[http://www.hping.org/download.php](http://www.hping.org/download.php)
[http://www.secdev.org/projects/scapy/](http://www.secdev.org/projects/scapy/)

---

### Post by ApEkV2 on 2009-10-16
> **__p1n__ said:**
> 1. Lol

@ Hguest, Happy reading

[http://packetstormsecurity.nl/programming-tutorials/raw_socket.txt](http://packetstormsecurity.nl/programming-tutorials/raw_socket.txt)
[http://en.wikipedia.org/wiki/IPv4](http://en.wikipedia.org/wiki/IPv4)
[http://en.wikipedia.org/wiki/Transmission_Control_Protocol](http://en.wikipedia.org/wiki/Transmission_Control_Protocol)
[http://mike.passwall.com/networking/samplepacket.html](http://mike.passwall.com/networking/samplepacket.html)
[http://ubuntuforums.org/](http://ubuntuforums.org/)
[http://www.securityfocus.com/infocus/1674](http://www.securityfocus.com/infocus/1674)
[http://support.novell.com/techcenter/articles/nc2001_03.html](http://support.novell.com/techcenter/articles/nc2001_03.html)
[http://linux.die.net/man/8/hping3](http://linux.die.net/man/8/hping3)
[http://cuppycake.ytmnd.com/](http://cuppycake.ytmnd.com/)
[http://www.ssfnet.org/Exchange/tcp/tcpTutorialNotes.html](http://www.ssfnet.org/Exchange/tcp/tcpTutorialNotes.html)
[http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)
[http://ss64.com/bash/](http://ss64.com/bash/)
[http://www.youtube.com/watch?v=DrLwnNvIORE](http://www.youtube.com/watch?v=DrLwnNvIORE)
[http://www.planet-source-code.com/vb/default.asp?lngWId=3#categories](http://www.planet-source-code.com/vb/default.asp?lngWId=3#categories)
[http://www.tenouk.com/cnlinuxsockettutorials.html](http://www.tenouk.com/cnlinuxsockettutorials.html)
[http://linux.die.net/man/8/tcpdump](http://linux.die.net/man/8/tcpdump)
[http://linux.die.net/man/1/nmap](http://linux.die.net/man/1/nmap)
[http://lcamtuf.coredump.cx/oldtcp/tcpseq.html](http://lcamtuf.coredump.cx/oldtcp/tcpseq.html)
[http://en.wikipedia.org/wiki/Password_cracking](http://en.wikipedia.org/wiki/Password_cracking)
[http://linux.die.net/man/1/wireshark](http://linux.die.net/man/1/wireshark)


FIN

---

### Post by scorp123 on 2009-10-17
> **ApEkV2 said:**
> @ Hguest, Happy reading

[http://cuppycake.ytmnd.com/](http://cuppycake.ytmnd.com/)


:lolflag:

---

### Post by CharlesA on 2009-10-18
Interesting spam post.

---

### Post by koenn on 2009-10-18
> **Hguest said:**
> Hi, people:
      I'm studying network programming. ...
If you're really studying network programming, you still have a long way to go, because right now, you apparently don't even know enough to ask the right questions.


Answers:
1- [http://en.wikipedia.org/wiki/Internet_socket](http://en.wikipedia.org/wiki/Internet_socket)
2- text, most likely
3- depends on the server protocols (which are known, if you think about it ...) and on how the server handles the logins (might be visible in the page source, or from a packet dump - see links by ApEkV2)

---

### Post by ApEkV2 on 2009-10-18
> **CharlesA said:**
> Interesting spam post.

How the heck did you get 165 posts in 15 days?
That's a lot of energy drinks

> **scorp123 said:**
> :lolflag:

I had to do it.

---

### Post by CharlesA on 2009-10-18
> **ApEkV2 said:**
> How the heck did you get 165 posts in 15 days?
That's a lot of energy drinks

169 now.. and mostly asking questions. :P

---

