---
title: "Problem with ssh tunnel to smtp server"
date: 2009-02-12
forum: Security
---

### Post by allaboutsam on 2009-02-12
I'm trying to set up an SSH tunnel from my laptop to my SMTP server at (say) smtp.example.com. Because of example.com's policies, no connections to port 25 are allowed; all connections must be auth'ed to port 465. (For why I would want to do SSH + SSL, see note at bottom.)

This works just fine if I invoke the tunnel manually as follows:

ssh -L 2525:smtp.example.com:465 -l username -i /path/to/key/file -N smtp.example.com

But I'd rather invoke it on demand using inetd. Trouble is I can't get the (local) inetd.conf and (remote) authorized_keys2 syntax right. Following a tutorial I found, I tried the following:

inetd.conf: 127.0.0.1:2525  stream  tcp     nowait  root    /usr/bin/ssh    -q -T -i /path/to/key/file [email]username@smtp.example.com[/email]

authorized_keys2: command="nc localhost 465",no-X11-forwarding,no-agent-forwarding,no-port-forwarding ssh-rss ....

I've also tried:

inetd.conf: 127.0.0.1:2525  stream  tcp     nowait  root    /usr/bin/ssh    -L 2525:smtp.example.com:465 -l username -i /path/to/key/file -N smtp.example.com

with and without the "command...no-port-forwarding" section in authorized_keys2, but no luck.

Can anyone point me in the right direction?

Many thanks,
allaboutsam

======

Why I want to do this: I used to just connect straight to port 465, but recently some networks have started blocking my e-mails as spam (which they emphatically are not) because my local IP address resolves to what they consider a generic DNS, cf. blah-###-###-###_###.blah.comcast.net. If I connect via an SSH tunnel, my local IP address isn't recorded in the message headers, and the e-mails go through just fine.

---

### Post by HermanAB on 2009-02-13
I don't understand what you are trying to do, since if your mail server uses port 465, then it should already be SSL encapsulated and Thunderbird, Outlook and Evolution all support SSL connections directly.

Cheers,

Herman

---

### Post by pavel.fibich on 2009-09-18
look at: [http://pavelfibich.blogspot.com/search/label/smtp%20over%20ssh]("http://pavelfibich.blogspot.com/search/label/smtp%20over%20ssh")

for me it works

---

