---
title: "Tracing Ip address of remote Chat users"
date: 2008-08-26
forum: Security
---

### Post by ivikas on 2008-08-26
Hello all,

         I want to know whether there is any software package,command to trace down ip address of remote chat users using gtalk,yahoo and other IM.

Thanks in advance

---

### Post by Oldsoldier2003 on 2008-08-27
Since this thread has gone unanswered in networking and wireless I'm moving it here for more visibility from folks "in the know".

With that said its simple enough to get IP addresses from clients if you have a direct connection. If the chat server actually stands between you and the other client then it becomes an issue as getting this information requires admin access or tactics of dubious legality.

---

### Post by rogeriopvl on 2008-08-27
You can always persuade the person to send you a file or accept one from you. generally file sending uses direct connection so it won't overload the chat servers.

While the file is being transferred just do a netstat command and check the ip address.

The command I use is something like this:
```
netstat tupl|grep tcp
```

---

### Post by drubin on 2008-08-27
> **rogeriopvl said:**
> You can always persuade the person to send you a file or accept one from you. generally file sending uses direct connection so it won't overload the chat servers.

Gtalk is bassed on XMPP that uses client->server->client communication even for file transfer. 
[http://www.xmpp.org/extensions/xep-0096.html](http://www.xmpp.org/extensions/xep-0096.html)

So running `netstat tupl|grep tcp` for gtalk users is relatively point less

---

### Post by rogeriopvl on 2008-08-27
That's why I said "generally". I've tested it with MSN, AIM and IRC.

Anyway there are tons of ways to get someone's IP address. Another one is, to have a pretty common website with visitor counter & statistics, then just give the link to the person... the IP will show up in the stats page.

---

### Post by drubin on 2008-08-27
I do have to ask why would you not just ask them? 

Post is a  hacking attempt?

---

### Post by jerome1232 on 2008-08-27
> **rubinboy said:**
> I do have to ask why would you not just ask them? 

Post is a  hacking attempt?

I agree, I can't think of a legit reason I would need to trick someone into giving me their IP, IM spam comes to mind but that can be blocked via the IM client software.

That and pulling a prank on my friends of course lol, which I would consider a legit reason.

Any ways it boils down to tricking them into somehow hitting your computer to track their ip down, or another server. There doesn't seem to be a known way to query the IM server to get ip's.

---

### Post by Dr Small on 2008-08-27
You could always do it with other methods, such as directing them to your personal website that has apache access logs, or creating a Php script that will log their IP address to a file. Of course, with this method, you must direct the target user to the URL which is not exactly what the OP was asking about.

Needless to say, when chatting over an instant messaging protocol, the messages are being relayed by the server. So the only IP address you receive is that of the server.

Dr Small

---

### Post by drubin on 2008-08-27
I am not going to comment any more, But carefully reads other replies.

---

