---
title: "MSN privacy?"
date: 2006-01-09
forum: The Cafe
---

### Post by 23meg on 2006-01-09
I've been away from all instant messaging software for a long time, partly due to the fact that I prefer asynchronous communication and find instant messaging too interruptive, and partly because the few people I have any reason to talk to instantly are only using MSN, which I tried to avoid.

Recently I've noticed that I'm getting out of touch with this bunch of people, so I thought I'd give using the MSN protocol with Gaim a shot. But upon hearing from someone that the MSN protocol sends all conversation data through Microsoft's servers instead of transporting it directly between clients with TCP/IP the way it should be done, I decided to pause and think twice.

So forgive my ignorance and laziness, but I have questions:

1) Is what I heard true?

2) Can a proxy be used with Gaim + MSN, and would putting an anonymous proxy between myself and Microsoft's server be a good privacy measure? How about privoxy + tor?

3) Are there any other ways to maximize privacy and anonymity while using the MSN protocol?

---

### Post by BSDFreak on 2006-01-09
[QUOTE=23meg]I've been away from all instant messaging software for a long time, partly due to the fact that I prefer asynchronous communication and find instant messaging too interruptive, and partly because the few people I have any reason to talk to instantly are only using MSN, which I tried to avoid.

Recently I've noticed that I'm getting out of touch with this bunch of people, so I thought I'd give using the MSN protocol with Gaim a shot. But upon hearing from someone that the MSN protocol sends all conversation data through Microsoft's servers instead of transporting it directly between clients with TCP/IP the way it should be done, I decided to pause and think twice.

So forgive my ignorance and laziness, but I have questions:

1) Is what I heard true?

2) Can a proxy be used with Gaim + MSN, and would putting an anonymous proxy between myself and Microsoft's server be a good privacy measure? 

3) Are there any other ways to maximize privacy and anonymity while using the MSN protocol?[/QUOTE]


1) Yes.

2) Yes, if it's a good privacy measure depends on the proxy.

3) Encryption, [http://software.newsforge.com/software/04/09/28/1554200.shtml](http://software.newsforge.com/software/04/09/28/1554200.shtml)

---

### Post by nocturn on 2006-01-09
[QUOTE=23meg]
1) Is what I heard true?

2) Can a proxy be used with Gaim + MSN, and would putting an anonymous proxy between myself and Microsoft's server be a good privacy measure? How about privoxy + tor?

3) Are there any other ways to maximize privacy and anonymity while using the MSN protocol?[/QUOTE]

AFAIK, yes it is true.  Although it can send directly, sometimes ICQ also defaults to this behavior.

Proxying is partially useless, because any message will reveal a wealth of information, including your screenname and probably the originating IP in the headers. 

Then again, most of the clients transfer everything over TCP/IP in plain text, so there is effectively little to no security in it.

Jabber can use https connections, so anything between you and the server is encrypted, there are plugins to encrypt your jabber converstations with GnuPG.

---

### Post by nocturn on 2006-01-09
Not to make you uncomfortable, but the same applies to E-mail...

Every mail you send passes through at least one mailserver, and often many more.  It can be intercepted and read during transmission at each point and anyone with sufficient access to the servers can read it (without you ever knowing it).

I have heard of sysadmins at ISP's that just read E-mail during night or weekend shifts to pass the time.

Basicly, I never got how people can send important or compromising mails without using encryption...

---

### Post by 23meg on 2006-01-09
Thanks for the replies. I know that everything I send unencrypted is basically there for all to see; actually my main concern was with the third party involved being Microsoft, and the way they're handling this: email has to pass through mail servers to be transported, but relaying instant messages through your own server when you can just make your clients send them directly among themselves (and then going down every now and then due to server shortage) is most likely a political decision rather than a technical one.

---

### Post by BSDFreak on 2006-01-09
[QUOTE=23meg]Thanks for the replies. I know that everything I send unencrypted is basically there for all to see; actually my main concern was with the third party involved being Microsoft, and the way they're handling this: email has to pass through mail servers to be transported, but relaying instant messages through your own server when you can just make your clients send them directly among themselves (and then going down every now and then due to server shortage) is most likely a political decision rather than a technical one.[/QUOTE]

ICQ, Jabber and Yahoo also relays everything through a server, is there any client that doesn't? Obviously this is for a reason, first of all, it's for your own security, leaving a port open for clients to connect to with protocols that accept file transfer is a disaster waiting to happen, by connecting to MSN/ICQ/Yahoo/Jabber servers you'll have that port only accepting incoming connections from those servers. There are probably a hundred more reasons for it, none of them political.

Just use encryption and you'll be fine privacy wise, if you really need to be anonymous too then use a good anonymous proxy.

---

### Post by 23meg on 2006-01-09
[QUOTE=BSDFreak]ICQ, Jabber and Yahoo also relays everything through a server, [/QUOTE]I'm not informed about Jabber and Yahoo but the last time I checked out ICQ defaulted to sending messages (it handles file transfers separately AFAIK) directly and only resorted to relaying through the server if there was a connection problem or if the user explicitly specified so. 

I know that encryption is definitely the way to go but it's a two way street; is there any option/feature in the official MSN client (that **all** of my peers will be using) for encryption? I bet not, and I hope I'm wrong.

Anyone using Privoxy + Tor + Gaim + MSN? That looks like my best bet.

---

### Post by BSDFreak on 2006-01-09
[QUOTE=23meg]I'm not informed about Jabber and Yahoo but the last time I checked out ICQ defaulted to sending messages (it handles file transfers separately AFAIK) directly and only resorted to relaying through the server if there was a connection problem or if the user explicitly specified so. 

I know that encryption is definitely the way to go but it's a two way street; is there any option/feature in the official MSN client (that **all** of my peers will be using) for encryption? I bet not, and I hope I'm wrong.

Anyone using Privoxy + Tor + Gaim + MSN? That looks like my best bet.[/QUOTE]

You are quite correct about the original ICQ protocol, however, the protocol used for AIM/ICQ today isn't the original ICQ protocol, it's Oscar and all messages are routed through AOL's servers. :(

I'm using the encryption in gaim and an anonymous server as a proxy, it's easy to configure and it works.

Unfortunantly there is no built in encryption in the MSN Messenger client so either you'll have to get your friends to download GAIM or get them to install an encryption solution for MSN.

---

