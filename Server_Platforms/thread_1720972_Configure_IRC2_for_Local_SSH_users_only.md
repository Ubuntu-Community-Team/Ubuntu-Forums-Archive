---
title: "Configure IRC2 for Local SSH users only"
date: 2011-04-03
forum: Server Platforms
---

### Post by HotDog1103 on 2011-04-03
Good evening,

I am trying to set up the IRCD-IRC2 server to allow local chat between users connected to my Ubuntu server through SSH. I have port forwarding all set up to the point when I open port 6667 on the localhost it immediately comes back with
":My.Irc.Com 020 * :Please wait while we process your connection."
Sounds promising. But it's not. It hangs for over a minute, then comes back with
"ERROR :Closing Link: [unknown@127.0.0.1] (Ping timeout)"
and closes the connection.

I don't want IRC2 to connect to any other servers. I just want it to facilitate chat between other users logged in through SSH as I said.

Here is my ircd.conf file

M:My.Irc.Com::BC, Canada:6667:0001
A:Canada:info@irc.com:Notes::SrvName:
P:127.0.0.1:::6667:
I:127.0.0.1::::10

Can anyone tell me what I'm doing wrong? Thank you!

---

### Post by HotDog1103 on 2011-04-04
Ho! Never mind - my IRCD is working perfectly! That'll teach me to try too many things at once. First time running my own Ubuntu server, and at the same time I'm writing an IRC client. After I fed my server the NICK and USER commands it logged me in and works perfectly! Hopefully this explanation will help somebody down the line.

---

